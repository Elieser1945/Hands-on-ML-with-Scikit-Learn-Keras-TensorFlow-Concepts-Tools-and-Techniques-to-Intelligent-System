# 📘 Chapter 5 — Support Vector Machines (SVM)
*Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow  
Concepts, Tools, and Techniques to Build Intelligent Systems*

---

## 🎯 1. Pendahuluan
Chapter 5 membahas **Support Vector Machines (SVM)**, salah satu algoritma paling kuat untuk tugas **klasifikasi**, **regresi**, dan **deteksi outlier**. SVM terkenal karena performanya yang kuat pada dataset berdimensi tinggi serta kemampuannya menemukan *decision boundary* yang memaksimalkan **margin** antara kelas.

Secara intuitif, SVM akan mencari garis/pesawat (hyperplane) yang paling “jauh” dari titik batas antara dua kelas, sehingga generalisasi model menjadi lebih baik.

---

## 🧩 2. Linear SVM Classification
Jika data dapat dipisahkan secara linier, SVM mencari **maximum-margin hyperplane**, yaitu garis batas dengan jarak terlebar terhadap titik-titik data terdekat (disebut *support vectors*).

### Persamaan Hyperplane:
\[
w^\top x + b = 0
\]

Tujuan SVM adalah memaksimalkan margin:
\[
\text{margin} = \frac{2}{\|w\|}
\]

Sehingga optimisasi utamanya:
\[
\min \frac{1}{2}\|w\|^2
\]
dengan syarat semua contoh terklasifikasi benar:
\[
y^{(i)}(w^\top x^{(i)} + b) \ge 1
\]

---

## 🔧 3. Soft-Margin Classification
Pada data nyata, terkadang titik-titik tidak bisa dipisahkan sempurna. Maka SVM menggunakan **soft margin**, yang mengizinkan beberapa pelanggaran margin menggunakan *slack variable* \(\zeta^{(i)}\).

### Optimisasi Soft-Margin:
\[
\min \frac{1}{2}\|w\|^2 + C\sum_{i=1}^m \zeta^{(i)}
\]

Dengan kendala:
\[
y^{(i)}(w^\top x^{(i)} + b) \ge 1 - \zeta^{(i)}, \quad \zeta^{(i)} \ge 0
\]

Parameter **C** mengontrol kompromi antara:
- margin besar  
- meminimalkan pelanggaran (misclassifications)

Semakin kecil **C**, semakin toleran terhadap misclassification (margin lebih lembut).

---

## ⚙️ 4. SVM’s Dual Form
Formulasi dual memperlihatkan bahwa bobot model dapat ditulis sebagai kombinasi linear dari *support vectors*:

\[
w = \sum_{i=1}^m \alpha^{(i)} y^{(i)} x^{(i)}
\]

Hanya titik dengan \(\alpha^{(i)} > 0\) yang berperan — merekalah **support vectors**.

Dual form juga memungkinkan penggunaan kernel tanpa eksplisit menghitung transformasi dimensi tinggi (kernel trick).

---

## 🌈 5. Nonlinear SVM Classification & Kernel Trick
Kadang data *tidak linier*. Untuk itu kita bisa memetakan fitur ke ruang dimensi lebih tinggi menggunakan **Kernel Trick**, tanpa menghitung transformasi eksplisit.

### Kernel Umum:
1. Polynomial Kernel  
2. Gaussian RBF Kernel  
   \[
   K(x, z) = \exp(-\gamma \|x - z\|^2)
   \]
3. Sigmoid Kernel

Dengan kernel, SVM menjadi sangat kuat dalam mempelajari pola non-linear.

---

## 🧪 6. SVM Regression (SVR)
SVM dapat digunakan untuk regresi dengan konsep **margin-insensitive loss** (ε-insensitive loss).

Tujuannya: menemukan fungsi yang sedekat mungkin dengan data tetapi membiarkan deviasi kecil sebesar ε.

### Fungsi Loss:
\[
L_\epsilon(y, \hat{y}) =
\begin{cases}
0 & \text{jika } |y - \hat{y}| \le \epsilon \\
|y - \hat{y}| - \epsilon & \text{jika lebih}
\end{cases}
\]

Regresi SVM juga memiliki parameter C dan kernel seperti SVM klasifikasi.

---

## 📐 7. Hyperparameter SVM
Hyperparameter penting SVM:

| Parameter | Penjelasan |
|----------|------------|
| **C** | Kontrol trade-off margin besar vs penalti kesalahan |
| **kernel** | Linear, poly, RBF, sigmoid |
| **degree** | Derajat polinomial (untuk kernel polynomial) |
| **gamma** | Kontrol radius pengaruh titik data (kernel RBF) |

### Pengaruh Gamma:
- Gamma tinggi → model lebih sensitif terhadap titik dekat → cenderung overfitting  
- Gamma rendah → model lebih halus → cenderung underfitting

---

## 📊 8. Skalasi Fitur
Sangat penting melakukan **feature scaling** (misalnya StandardScaler) sebelum menjalankan SVM.

Karena margin dan jarak antar titik pada SVM sangat bergantung pada skala fitur.

---

## 🧠 9. Support Vector Machines Summary
- SVM mencari hyperplane dengan margin terbesar.  
- Soft margin memungkinkan misclassification terkontrol menggunakan parameter C.  
- Kernel Trick membuat SVM mampu mempelajari pola non-linear.  
- SVM dapat diterapkan untuk klasifikasi, regresi, dan deteksi outlier.  
- SVM bekerja sangat baik pada data berdimensi tinggi.  
- Perlu scaling fitur agar hasil optimal.

---



---
