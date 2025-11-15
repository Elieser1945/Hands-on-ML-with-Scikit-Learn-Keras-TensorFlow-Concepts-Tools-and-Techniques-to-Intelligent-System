# Chapter 4 – Training Linear Models  

## 1. Pengenalan  
Pada bab ini kita mulai menelaah bagaimana sebenarnya model-linear dilatih, bukan hanya sebagai “kotak hitam”. Memahami mekanisme di balik layar membantu kita memilih algoritma yang tepat, menentukan hyperparameter dengan lebih baik, serta melakukan analisis kesalahan (error analysis) dan debugging secara efektif. :contentReference[oaicite:2]{index=2}  
Fokus utama bab ini meliputi:  
- Regresi linear (Linear Regression)  
- Persamaan tertutup (Normal Equation) vs optimisasi iteratif (Gradient Descent)  
- Regresi polinomial (Polynomial Regression)  
- Learning curves untuk deteksi underfitting dan overfitting  
- Model linear ter-regulasi (Regularized Linear Models: Ridge, Lasso, Elastic Net)  
- Regresi logistik (Logistic Regression) dan Softmax untuk klasifikasi  

## 2. Regresi Linear  
Regresi linear mencari model dari bentuk:  
\[
\hat y = \theta_0 + \theta_1 x_1 + \theta_2 x_2 + \cdots + \theta_n x_n
\]  
untuk memprediksi target \(y\). Fungsi biaya yang umum digunakan adalah Mean Squared Error (MSE):  
\[
MSE(\theta) = \frac{1}{m} \sum_{i=1}^m \bigl(\hat y^{(i)} - y^{(i)}\bigr)^2
\]  
Dengan menuliskan dalam bentuk vektor/matriks: jika \(X\) adalah matriks fitur (termasuk kolom 1 untuk bias) dan \(y\) vektor target, maka \(\hat y = X\theta\), dan:  
\[
MSE(\theta) = \frac{1}{m} (X\theta - y)^\top (X\theta - y)
\]  

### 2.1 Normal Equation (Persamaan Tertutup)  
Solusi analitik untuk \(\theta\) yang meminimalkan MSE adalah:  
\[
\theta = \bigl(X^\top X\bigr)^{-1} X^\top y
\]  
Catatan: solusi ini hanya berlaku jika \(X^\top X\) invertible dan dataset tidak terlalu besar (karena komputasi matriks besar mahal). :contentReference[oaicite:3]{index=3}  

### 2.2 Gradient Descent  
Untuk dataset besar atau jumlah fitur banyak, kita biasanya menggunakan metode iteratif seperti Gradient Descent (GD) yang memperbarui parameter secara bertahap:  
\[
\theta := \theta - \eta \; \nabla_\theta MSE(\theta)
\]  
Turunan dari MSE adalah:  
\[
\nabla_\theta MSE(\theta) = \frac{2}{m} X^\top (X\theta - y)
\]  
Dimana \(\eta\) adalah *learning rate*. Ada beberapa varian:  
- Batch Gradient Descent: seluruh dataset digunakan tiap update  
- Stochastic Gradient Descent (SGD): satu contoh data tiap update  
- Mini-batch Gradient Descent: sejumlah kecil contoh tiap update  
Fitur sangat berbeda skala dapat memperlambat konvergensi, maka *feature scaling* (misalnya StandardScaler) sangat dianjurkan. :contentReference[oaicite:4]{index=4}  

## 3. Regresi Polinomial  
Jika data saja tidak cukup linier, kita dapat memperluas fitur dengan pangkat-pangkatnya (misalnya \(x^2, x^3\), …) lalu diterapkan model linear:  
\[
\hat y = \theta_0 + \theta_1 x + \theta_2 x^2 + \dots + \theta_d x^d
\]  
Meski model masih linear terhadap parameter \(\theta\), bentuk kurvanya bisa non-linier. Namun, jumlah fitur bertambah besar → model lebih rentan overfitting. Oleh karena itu kita perlu memeriksa dengan learning curves. :contentReference[oaicite:5]{index=5}  

## 4. Learning Curves & Diagnostik  
Learning curve menunjukkan bagaimana error (misalnya MSE) berubah terhadap ukuran dataset atau epoch pelatihan:  
- Jika *training error* tinggi dan *validation error* juga tinggi → model **underfitting**  
- Jika *training error* rendah tapi *validation error* jauh lebih tinggi → model **overfitting**  
Untuk mengatasinya dapat:  
- Underfitting → pilih model lebih kompleks atau fitur lebih baik  
- Overfitting → kurangi kompleksitas model, gunakan regularisasi, atau tambah data pelatihan :contentReference[oaicite:6]{index=6}  

## 5. Regularized Linear Models  
Untuk mengurangi overfitting, kita tambahkan penalti pada parameter \(\theta\):

### 5.1 Ridge Regression (L2)  
\[
J(\theta) = MSE(\theta) + \alpha \sum_{j=1}^n \theta_j^2
\]  

### 5.2 Lasso Regression (L1)  
\[
J(\theta) = MSE(\theta) + \alpha \sum_{j=1}^n |\theta_j|
\]  
Menarik karena dapat menghasilkan beberapa \(\theta_j = 0\) → seleksi fitur otomatis.

### 5.3 Elastic Net  
Gabungan antara L1 dan L2:  
\[
J(\theta) = MSE(\theta) + \alpha \Bigl( \rho \sum_{j=1}^n |\theta_j| + (1-\rho) \sum_{j=1}^n \theta_j^2 \Bigr)
\]  
Dimana \(\rho \in [0,1]\) mengatur proporsi antara L1 dan L2. :contentReference[oaicite:7]{index=7}  

## 6. Logistic Regression & Softmax Regression  
### 6.1 Logistic Regression (Binary)  
Model klasifikasi yang menggunakan fungsi sigmoid:  
\[
\hat p = \sigma(z) = \frac{1}{1 + e^{-z}}, \quad z = \theta^\top x
\]  
Prediksi kelas:  
\[
\hat y = 1 \;\; \text{jika} \;\; \hat p \ge 0.5
\]  
Fungsi loss yang umum: *Log-Loss* (Cross-Entropy) untuk binary.

### 6.2 Softmax (Multinomial) Regression  
Untuk lebih dari dua kelas:  
\[
p(y = k \mid x) = \frac{e^{\theta_k^\top x}}{\sum_{j} e^{\theta_j^\top x}}
\]  
Kemudian kelas diprediksi dengan probabilitas tertinggi. :contentReference[oaicite:8]{index=8}  

## 7. Ringkasan & Implikasi  
- Memahami cara kerja model linear (dan optimisasinya) penting karena banyak algoritma lanjutan (termasuk jaringan saraf) memakai prinsip serupa.  
- Pilihan metode:  
  - Normal Equation: cepat untuk dataset kecil/menengah  
  - Gradient Descent (dan variannya): cocok untuk dataset besar atau banyak fitur  
- Selalu pertimbangkan skala fitur, regularisasi, learning curves untuk diagnostik model  
- Walau fokus bab ini pada model linear, banyak konsep akan muncul kembali di deep learning (Part II buku).

---


