# 📘 Chapter 6 — Decision Trees  
*Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow (Aurélien Géron)*  

Chapter 6 membahas salah satu algoritma paling intuitif dan kuat dalam machine learning: **Decision Trees**. Model ini bekerja dengan cara membagi ruang fitur menjadi area-area yang homogen berdasarkan aturan keputusan (*decision rules*). Decision tree dapat digunakan untuk **klasifikasi**, **regresi**, dan juga sebagai fondasi metode ensemble seperti **Random Forest** dan **Gradient Boosting**.

---

## ⭐ 1. Konsep Dasar Decision Trees  
Decision Tree membangun struktur pohon biner yang berisi:
- **Node internal** → berisi kondisi/pertanyaan, misal: `x1 < 2.5?`
- **Cabang (branches)** → hasil dari kondisi tersebut (true/false)
- **Leaf node** → prediksi akhir (kelas atau nilai)

Tujuan Decision Tree adalah membuat pembagian (split) yang menghasilkan kelompok paling “murni”.

---

## ⭐ 2. Impurity Measures (Ukuran Ketidakmurnian)

### **2.1 Gini Impurity**
Digunakan sebagai default pada klasifikasi.

$$
Gini = 1 - \sum_{k=1}^{K} p_k^2
$$

- \( p_k \) = proporsi kelas \( k \)
- Nilai 0 → murni sempurna (hanya 1 kelas)

### **2.2 Entropy**
Alternatif impurity measure dari Teori Informasi.

$$
Entropy = -\sum_{k=1}^{K} p_k \log_2(p_k)
$$

- Entropy = 0 → leaf murni  
- Semakin acak → entropy meningkat

### **2.3 Information Gain**
Digunakan untuk memilih split terbaik:

$$
IG = Entropy(parent) - \sum_{children} \frac{n_i}{n} Entropy(i)
$$

Semakin besar **Information Gain**, semakin baik split tersebut.

---

## ⭐ 3. Decision Tree untuk Regresi
Pada regresi, impurity menggunakan **Mean Squared Error (MSE)**.

$$
MSE = \frac{1}{m} \sum_{i=1}^{m} (y^{(i)} - \hat{y})^2
$$

Prediksi leaf adalah:
$$
\hat{y} = \frac{1}{m} \sum_{i=1}^{m} y^{(i)}
$$

Split terbaik meminimalkan total MSE dari anak-anak node.

---

## ⭐ 4. Overfitting pada Decision Trees  
Decision Tree *sangat mudah overfit* karena dapat membuat struktur sangat dalam hingga seluruh data terpisah sempurna.

Cara mengatasinya:
- `max_depth`
- `min_samples_split`
- `min_samples_leaf`
- `max_leaf_nodes`
- pruning (pemangkasan pohon)

---

## ⭐ 5. Regularization dalam Tree
Model di-regularisasi dengan membatasi kompleksitas pohon.  

Contoh hyperparameter:
- **max_depth** – kedalaman maksimal
- **min_samples_split** – jumlah minimum data untuk melakukan split
- **min_samples_leaf** – ukuran minimum leaf
- **max_leaf_nodes** – jumlah leaf maksimal
- **max_features** – jumlah fitur yang dievaluasi per split

---

## ⭐ 6. CART Algorithm (Classification and Regression Tree)

Scikit-Learn menggunakan algoritma **CART**, yang bekerja dengan memilih split terbaik berdasarkan impurity.

### Rumus optimisasi CART:

Untuk klasifikasi/regresi:

$$
J(split) = \frac{m_{left}}{m} \cdot impurity(left) + \frac{m_{right}}{m} \cdot impurity(right)
$$

CART memilih split dengan nilai J terkecil.

Note: CART *hanya melakukan greedy search*, bukan optimasi global.

---

## ⭐ 7. Keuntungan & Kelemahan Decision Trees

### ✔️ Keuntungan
- Mudah dipahami dan divisualisasikan  
- Tidak memerlukan scaling fitur  
- Mampu memodelkan hubungan non-linear  
- Dapat menangani data kategorikal dan numerik  

### ❌ Kelemahan
- Rentan **overfitting**  
- Tidak stabil terhadap perubahan kecil pada data  
- Cenderung menghasilkan model kompleks jika tidak di-regularisasi

---

## ⭐ 8. Visualisasi Tree
Scikit-Learn menyediakan tools untuk menampilkan struktur tree:

```python
from sklearn.tree import plot_tree
plot_tree(model, filled=True)
```

Atau dalam file `.dot` menggunakan:

```python
from sklearn.tree import export_graphviz
```

---

## ⭐ 9. Feature Importance  
Decision Tree dapat menghitung pentingnya fitur menggunakan impurity reduction.

Importance dihitung sebagai:

$$
FI_j = \sum_{splits\ on\ feature\ j} \frac{m_{node}}{m_{total}} \cdot \Delta impurity
$$

Semakin besar peran fitur dalam mengurangi impurity, semakin besar feature importance-nya.

---

## 📌 10. Ringkasan Singkat

Chapter 6 mengajarkan bahwa:
- Decision Trees adalah model kuat yang mudah dipahami.
- Impurity measures (Gini, Entropy) menentukan kualitas split.
- CART memilih split terbaik menggunakan minimisasi impurity.
- Trees cenderung overfit sehingga perlu regularisasi.
- Feature importance dapat dievaluasi dari impurity reduction.

Bab ini juga menjadi dasar untuk mempelajari metode ensemble yang lebih kuat: **Random Forest**, **Gradient Boosting**, dan **XGBoost**.

---

  

