# 📘 Chapter 8 – Dimensionality Reduction  
### Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow (Geron)

Chapter 8 membahas teknik untuk **mengurangi dimensi fitur** sambil tetap mempertahankan informasi penting dalam data. Tujuan utama dimensionality reduction adalah membuat model lebih sederhana, lebih cepat, dan mengurangi risiko **overfitting**, karena data berdimensi tinggi sering rentan terhadap *curse of dimensionality*.

---


## 🧠 Konsep Utama

### 1. Curse of Dimensionality
Ketika jumlah fitur meningkat:
- Data menjadi semakin jarang.
- Jarak antar titik menjadi kurang bermakna.
- Model menjadi lebih sulit dilatih tanpa overfitting.
  
Oleh karena itu, mengurangi dimensi dapat meningkatkan performa model dan membuat data lebih mudah dipahami.

---

## 🔧 Teknik Dimensionality Reduction

### 2. Projection
Proyeksi dilakukan dengan mengubah data dari ruang berdimensi tinggi ke ruang berdimensi lebih rendah. Contoh: memproyeksikan titik 3D ke bidang 2D.

---

## 🔥 Principal Component Analysis (PCA)

PCA adalah teknik reduksi dimensi paling populer, mencari **arah variansi terbesar** pada data.

### ✨ Tujuan PCA
- Menemukan komponen utama (principal components).
- Memaksimalkan variansi sepanjang komponen tersebut.

### 🧮 Rumus Matematika PCA

#### Variansi maksimum
PCA mencari vektor unit \( \mathbf{w} \) yang memaksimalkan variansi:

$$
\max_{\mathbf{w}} \ \text{Var}(\mathbf{w}^\top \mathbf{x})
$$

Dengan kendala:

$$
\|\mathbf{w}\| = 1
$$

Solusinya: eigenvector dari matriks kovarians.

#### Matriks kovarians:

$$
\mathbf{C} = \frac{1}{m} \mathbf{X}^\top \mathbf{X}
$$

Komponen utama adalah eigenvector dari \( \mathbf{C} \) dengan eigenvalue terbesar.

### 🔢 PCA via SVD
Dalam praktiknya PCA dihitung dengan **Singular Value Decomposition (SVD)**:

$$
\mathbf{X} = \mathbf{U} \mathbf{\Sigma} \mathbf{V}^\top
$$

Principal components = kolom pertama dari matriks \( \mathbf{V} \).

---

## 🎚️ Menentukan Jumlah Komponen (Explained Variance Ratio)

Jumlah komponen dipilih dengan melihat *explained variance ratio*:

$$
\text{EVR}_k = \frac{\lambda_k}{\sum_{i=1}^{d} \lambda_i}
$$

Kita dapat memilih jumlah komponen \( k \) sehingga  
≥ 90% atau 95% variansi data dipertahankan.

---

## 🔄 PCA Transform & Inverse Transform

Transformasi ke dimensi lebih rendah:

$$
\mathbf{z} = \mathbf{X} \mathbf{W}_k
$$

Rekonstruksi data (approximation):

$$
\hat{\mathbf{X}} = \mathbf{z} \mathbf{W}_k^\top
$$

---

## ⚡ Randomized PCA
Digunakan untuk dataset besar (sampai jutaan sampel).  
Pendekatan ini merupakan aproksimasi cepat dari SVD.

---

## 📉 Incremental PCA
Digunakan ketika data terlalu besar untuk dimasukkan seluruhnya ke memori. PCA dihitung batch per batch.

---

## 🌈 Kernel PCA (kPCA)

Jika data tidak linier, PCA standar tidak cukup.  
Kernel PCA memetakan data ke ruang berdimensi lebih tinggi menggunakan kernel:

- RBF
- Polynomial
- Sigmoid

Lalu dilakukan PCA di ruang tersebut.

### Contoh kernel trick:

$$
K(\mathbf{x}, \mathbf{x}') = \exp\left(-\gamma \|\mathbf{x} - \mathbf{x}'\|^2\right)
$$

---

## 🔍 Evaluasi kPCA

Untuk regresi atau klasifikasi downstream, hyperparameter kernel dapat dioptimasi dengan:
- Grid Search
- Cross-Validation
- Reconstruction error (aproksimasi)

---

## 🎨 Locally Linear Embedding (LLE)

Teknik nonlinear yang berbasis manifold learning.  
LLE berusaha melestarikan **hubungan lokal** antar sampel.

### Ide Utama LLE:

1. Temukan tetangga terdekat setiap titik.
2. Hitung bobot agar titik dapat direkonstruksi dari tetangga-tetangganya.
3. Temukan representasi berdimensi rendah yang mempertahankan bobot tersebut.

### Persamaan rekonstruksi lokal:

$$
\min_{\{w_{ij}\}}
\sum_i \left\| \mathbf{x}_i - \sum_j w_{ij} \mathbf{x}_j \right\|^2
$$

dengan kendala:

$$
\sum_j w_{ij} = 1
$$

---

## 🪄 Teknik Lain Yang Dibahas Singkat

### • t-SNE
Visualisasi data berdimensi tinggi ke dimensi 2 atau 3.  
Menggunakan distribusi probabilistik untuk mempertahankan struktur lokal.

### • Isomap
Mirip PCA nonlinear, tetapi memakai jarak geodesik pada manifold.

---





## 🎯 1. Mengapa Dimensionality Reduction Diperlukan?

- **Mempercepat training**  
  Model dengan banyak fitur membutuhkan komputasi besar.
- **Mengurangi noise**  
  Fitur yang tidak relevan dapat merusak performa model.
- **Visualisasi**  
  Data kompleks bisa divisualisasikan dalam 2D/3D.
- **Mengatasi curse of dimensionality**  
  Ruang dimensi tinggi membuat jarak antar data menjadi kurang berbeda sehingga model sulit belajar.

---

## 🧩 2. Projection Methods

Metode ini memproyeksikan data dari dimensi tinggi ke dimensi lebih rendah.

Contoh: jika fitur sangat berkorelasi, data dapat diproyeksikan ke arah dengan variasi terbesar.

---

## 🧠 3. Principal Component Analysis (PCA)

PCA adalah metode paling populer untuk dimensionality reduction. Tujuannya adalah menemukan **principal components**, yaitu arah dengan variansi terbesar pada data.

### 📌 Rumus Penting

**Covariance Matrix**  
$$
\Sigma = \frac{1}{m} X^\top X
$$

**Eigendecomposition**  
Mencari eigenvectors dan eigenvalues:
$$
\Sigma \, v = \lambda v
$$

Eigenvector dengan **nilai eigen terbesar** adalah principal components.

**Transformasi PCA**  
$$
X_{\text{reduced}} = X \, W_k
$$  
di mana \( W_k \) adalah matriks yang berisi \( k \) eigenvector utama.

---

## 🔁 4. Explained Variance Ratio

Mengukur berapa banyak informasi (variansi) yang dipertahankan.

$$
\text{Explained Variance Ratio} = \frac{\lambda_i}{\sum_j \lambda_j}
$$

Ini digunakan untuk menentukan berapa banyak komponen yang cukup.

---

## 📉 5. PCA dengan SVD (Singular Value Decomposition)

Daripada menghitung covariance matrix, PCA lebih stabil dilakukan dengan:

$$
X = U \Sigma V^\top
$$

Komponen utama adalah kolom dari matriks \( V \).

---

## 🌀 6. Kernel PCA (kPCA)

Digunakan saat data tidak linier.  
Kernel PCA menggunakan fungsi kernel untuk memproyeksikan data ke ruang fitur yang lebih tinggi secara implisit.

Kernel umum:
- RBF (Gaussian)
- Polynomial
- Sigmoid

Tujuan kPCA:
- Mendapatkan representasi yang lebih baik untuk data non-linear
- Bisa digunakan sebelum training model supervised

---

## 🧹 7. LLE – Locally Linear Embedding

LLE adalah teknik **manifold learning** non-linear.

Langkah LLE:

1. Temukan *k nearest neighbors* setiap titik  
2. Hitung *weights* linear yang merekonstruksi tiap titik  
3. Cari embedding berdimensi rendah yang mempertahankan weights tersebut

Tujuan: mempertahankan struktur lokal data.

---

## 🧪 8. Perbandingan PCA vs kPCA vs LLE

| Metode | Kelebihan | Kekurangan |
|-------|-----------|------------|
| **PCA** | Cepat, stabil, mudah | Hanya linier |
| **Kernel PCA** | Menangani data non-linear | Lebih lambat, pemilihan kernel rumit |
| **LLE** | Tangkap manifold kompleks | Sensitif terhadap noise dan parameter k |

---

## ⚙️ 9. Pipeline Umum Dimensionality Reduction

1. Standardisasi fitur (wajib untuk PCA)  
2. Pilih metode (PCA, kPCA, LLE)  
3. Tentukan jumlah komponen  
4. Transformasi data  
5. Training model ML di ruang berdimensi rendah

---

## 📌 10. Ringkasan

Chapter 8 memberikan pemahaman penting tentang:

- Mengapa dimensionality reduction diperlukan  
- Bagaimana PCA bekerja secara matematis  
- Dimensionality reduction non-linear (Kernel PCA, LLE)  
- Cara memilih jumlah komponen  
- Cara menggabungkan metode ini dalam pipeline machine learning  

Dimensionality reduction adalah fondasi penting sebelum masuk ke model-model machine learning yang lebih kompleks di bab-bab selanjutnya.

---

