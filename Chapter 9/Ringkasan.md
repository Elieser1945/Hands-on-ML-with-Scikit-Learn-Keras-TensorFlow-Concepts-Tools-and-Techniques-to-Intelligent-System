# 📘 Chapter 9 — Unsupervised Learning Techniques

_Ringkasan dari "Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow"_

Chapter 9 membahas konsep dan algoritma penting **unsupervised learning**, di mana sistem belajar dari data tanpa label. Tujuannya adalah menemukan struktur, pola, atau grup tersembunyi dalam data. Aplikasi utamanya meliputi _clustering_, _anomaly detection_, dan _density estimation_.

***

## 🔍 Konsep Dasar Unsupervised Learning
- **Tidak ada label target:** Model mencari struktur alami pada data, bukan memetakan input ke target.
- **Aplikasi utama:** eksplorasi data, segmentasi, pengurangan dimensi, dan deteksi anomali.

### Metode yang Dibahas
- Clustering (kelompokkan data yang mirip)
- Density estimation (mengukur kepadatan/sebaran data)
- Probabilistic models (menganggap data berasal dari campuran distribusi tertentu)
- Anomaly detection (mencari data yang menyimpang dari pola umum)

***

## 🎯 Clustering
Clustering mengelompokkan data sehingga anggota dalam satu kelompok _mirip_, sedangkan antar kelompok _berbeda_.

### 💠 K-Means Clustering
Salah satu algoritma clustering paling terkenal. Bertujuan meminimalkan jarak kuadrat dari setiap titik ke centroid cluster-nya.

#### Cara Kerja:
1. Pilih jumlah cluster  k 
2. Inisialisasi centroid secara acak
3. Ulangi sampai konvergen:
   - Assign tiap data ke centroid terdekat
   - Update centroid sebagai rata-rata anggota cluster

#### **Fungsi Objektif K-Means:**

$$
J = \sum_{j=1}^{k} \sum_{x \in C_j} \|x - \mu_j\|^2
$$

_Keterangan:_
- $$C_j$$ = cluster ke-j
- $$\mu_j$$ = centroid cluster ke-j

##### Tantangan:
- Sensitif terhadap inisialisasi centroid
- Tidak cocok untuk cluster yang sangat tidak bulat atau berbeda ukuran

##### Pemilihan $$k$$:
- **Elbow Method:** Mencari titik di mana penurunan _inertia_ mulai melambat
- **Silhouette Score:** Nilai [-1, 1] mengukur kualitas cluster

***

## 🔷 DBSCAN (Density-Based Spatial Clustering)
Algoritma clustering berbasis densitas.

**Kelebihan:**
- Tidak membutuhkan jumlah cluster $$k$$
- Bisa mengenali cluster berbentuk tak beraturan
- Otomatis mengenali outlier/noise

**Parameter:**
- $$ \varepsilon $$: radius neighborhood
- `min_samples`: minimal titik dalam radius untuk menjadi _core point_

**Prinsip kerja:**
- Identifikasi _core points_ (area ber-densitas tinggi)
- Hubungkan core points bertetangga → cluster
- Titik tak terhubung → noise

***

## 🔶 Gaussian Mixture Models (GMM)
Model probabilistik yang mengasumsikan data dihasilkan dari campuran distribusi Gaussian.

**Definisi densitas campuran:**

$$
p(x) = \sum_{j=1}^{k} \phi_j \; \mathcal{N}(x | \mu_j, \Sigma_j)
$$

_Keterangan:_
- $$\phi_j$$: bobot campuran komponen ke-$$j$$
- $$\mathcal{N}$$: distribusi Gaussian dengan rata-rata $$\mu_j$$, kovarian $$\Sigma_j$$

### Expectation-Maximization (EM) untuk GMM
Proses melatih GMM melalui dua tahap berulang-ulang:
- **E-Step:** Hitung probabilitas tiap data berasal dari tiap komponen

$$
\gamma_{j}(x^{(i)}) = \frac{\phi_j \cdot \mathcal{N}(x^{(i)}|\mu_j,\Sigma_j)}{\sum_{l=1}^{k} \phi_l \cdot \mathcal{N}(x^{(i)}|\mu_l , \Sigma_l)}
$$

- **M-Step:** Update parameter berdasarkan probabilitas tersebut:
  - Mean:
    $$
    \mu_j = \frac{\sum_i \gamma_j(x^{(i)}) x^{(i)}}{\sum_i \gamma_j(x^{(i)})}
    $$
  - Covariance:
    $$
    \Sigma_j = \frac{\sum_i \gamma_j(x^{(i)}) (x^{(i)} - \mu_j)(x^{(i)} - \mu_j)^T}{\sum_i \gamma_j(x^{(i)})}
    $$
  - Mixing weight:
    $$
    \phi_j = \frac{1}{m} \sum_i \gamma_j(x^{(i)})
    $$

    

***

## 🚨 Anomaly Detection
Model probabilistik (misal: GMM) dapat mendeteksi _anomaly_ jika densitas data sangat rendah:

$$
p(x) = \sum_j \phi_j \mathcal{N}(x|\mu_j, \Sigma_j)
$$

Jika $$p(x)$$ sangat kecil, $$x$$ dianggap sebagai outlier.

***

## 🎓 Semi-Supervised Learning
Cluster dapat dimanfaatkan untuk mempercepat _data labeling_:
- Lakukan clustering
- Labeli representative cluster (misal: centroid)
- Sebarkan label ke seluruh anggota cluster

***

## 📝 Ringkasan
Chapter 9 menunjukkan bahwa **unsupervised learning** sangat penting untuk:
- Eksplorasi & segmentasi data
- Deteksi anomali & pemahaman struktur
- Pengurangan dimensi
- Semi-supervised learning

**Algoritma utama:**
- **K-Means** (clustering berbasis jarak)
- **DBSCAN** (clustering berbasis densitas)
- **GMM+EM** (clustering probabilistik)

Setiap pendekatan memiliki kelebihan dan keterbatasan, sehingga pemilihan bergantung pada tujuan analisis dan sifat data.

