# 📘 Chapter 7 — Ensemble Learning and Random Forests  
*Hands-on Machine Learning with Scikit-Learn, Keras & TensorFlow (Aurelien Géron)*

## 🎯 Ringkasan Bab
Chapter 7 membahas konsep **Ensemble Learning**, yaitu teknik menggabungkan beberapa model lemah (*weak learners*) untuk membentuk model gabungan (*ensemble*) yang lebih kuat dan memiliki generalisasi lebih baik. Prinsip utamanya: *sekelompok model yang bekerja bersama biasanya mengungguli satu model tunggal.*  

Bab ini menjelaskan beberapa metode ensemble populer seperti **Voting Classifiers**, **Bagging**, **Random Forests**, **Boosting**, dan **Stacking**, lengkap dengan konsep matematis yang mendasarinya.

---

# 🧠 1. Konsep Dasar Ensemble Learning
Ensemble bekerja berdasarkan ide bahwa berbagai model berbeda memiliki kesalahan berbeda, sehingga jika digabungkan, error dapat saling mengkompensasi.

Jika setiap model memiliki error rate \( p \), dan total model berjumlah \( N \), maka error ensemble mayoritas dapat dihitung menggunakan distribusi binomial:

$$
P(\text{majority error}) = \sum_{k=\lceil N/2 \rceil}^{N} \binom{N}{k} p^k (1 - p)^{N-k}
$$

Semakin besar \( N \) dan semakin kecil korelasi antar model, semakin kuat ensemble.

---

# 🗳️ 2. Voting Classifiers
Voting Classifier menggabungkan beberapa model menggunakan:
- **Hard voting** → memilih kelas mayoritas  
- **Soft voting** → memilih kelas dengan rata-rata probabilitas tertinggi  

Soft voting lebih baik karena mempertimbangkan probabilitas setiap kelas.

---

# 🌲 3. Bagging (Bootstrap Aggregating)
Bagging melatih beberapa model pada subset data yang diambil dengan **bootstrap sampling** (sampling dengan pengembalian).  

Prediksi dilakukan dengan voting (klasifikasi) atau averaging (regresi):

$$
\hat{y} = \frac{1}{N} \sum_{i=1}^{N} \hat{y}_i
$$

Bagging mengurangi **variance**, tetapi tidak selalu mengurangi bias.

## 📌 Contoh: BaggingClassifier
Scikit-Learn menyediakan BaggingClassifier untuk membuat ensemble dari model apa pun.

---

# 🌳 4. Random Forests
Random Forest adalah versi bagging khusus untuk **Decision Trees**, dengan dua perbedaan:
1. Setiap pohon menggunakan data bootstrap.
2. Setiap split hanya mempertimbangkan subset acak fitur.

Hal ini membuat pohon-pohon menjadi kurang berkorelasi → performa meningkat.

## 📌 Importance Fitur  
Random Forest menghitung kontribusi setiap fitur terhadap pengurangan impurity:

$$
\text{Importance}(f) = \sum_{t=1}^{T} \left( \frac{N_t}{N} \times \Delta I_t(f) \right)
$$

Di mana:
- \( T \) = jumlah tree  
- \( N_t \) = jumlah sample di node  
- \( \Delta I_t(f) \) = penurunan impurity saat memilih fitur \( f \)

Impurity dapat berupa **Gini** atau **Entropy**.

---

# 🚀 5. Boosting
Boosting melatih model secara berurutan, setiap model baru fokus memperbaiki kesalahan model sebelumnya.

## 5.1 AdaBoost
Masing-masing sample diberikan bobot, bobot kesalahan akan naik:

$$
w_i := w_i \cdot e^{\alpha}
$$

Dengan:

$$
\alpha = \eta \ln\left( \frac{1 - \epsilon}{\epsilon} \right)
$$

Di mana:
- \( \epsilon \) = error model  
- \( \eta \) = learning rate  

## 5.2 Gradient Boosting
Menggunakan konsep *gradient descent* untuk mengurangi error secara bertahap.

Model dibangun berdasarkan **residual error**:

$$
r_i = y_i - \hat{y}_i
$$

Setiap tree berikutnya mencoba memprediksi residual ini.

---

# 🏗️ 6. Stacking (Stacked Generalization)
Stacking menggabungkan prediksi beberapa model dasar melalui model meta-learner (misal Linear Regression atau Logistic Regression).

Flow-nya:
1. Train multiple base models  
2. Gunakan output mereka sebagai fitur baru  
3. Train meta-model untuk memprediksi final output  

Stacking sering mengalahkan ensemble lain karena mempelajari cara terbaik mengombinasikan model.

---

# 🧾 7. Inti Pembelajaran Bab 7
- Ensemble mengurangi variance dan meningkatkan stabilitas model.  
- Random Forests sangat kuat dan jarang overfitting.  
- Boosting (terutama Gradient Boosting) menjadi dasar model-model modern seperti XGBoost, LightGBM, dan CatBoost.  
- Stacking memberikan performa terbaik saat base-learner berbeda.  
- Kombinasi model lemah yang tepat dapat menghasilkan model yang *sangat kuat*.

---
  
