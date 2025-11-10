# 📘 Chapter 2: End-to-End Machine Learning Project  

## 🎯 Tujuan  
Bab ini membahas bagaimana membangun proyek Machine Learning secara menyeluruh — mulai dari menyiapkan data mentah hingga menghasilkan model yang siap digunakan.  

## 🏡 Dataset  
Dataset yang digunakan adalah **California Housing Dataset**, yang berisi berbagai fitur tentang wilayah di California, seperti:
- Latitude & Longitude  
- Jumlah kamar, kamar tidur, dan populasi  
- Median income  
- Median house value (sebagai target)

Dataset diunduh langsung dari GitHub resmi buku dengan format `.csv`.

## 🧩 Alur Proyek  
1. **Setup Lingkungan**  
   Mengimpor library penting (`NumPy`, `Pandas`, `Matplotlib`, `Scikit-Learn`) dan mengatur konfigurasi awal.  

2. **Mengambil dan Memuat Data**  
   - Mengunduh dataset perumahan.  
   - Membaca file `housing.csv` menggunakan Pandas.  

3. **Eksplorasi Data (EDA)**  
   - Melihat informasi dasar dataset.  
   - Mendeteksi data yang hilang.  
   - Membuat visualisasi seperti histogram dan scatter plot untuk memahami distribusi data.  

4. **Membuat Set Data Uji (Test Set)**  
   Data dibagi menjadi data latih dan uji menggunakan *stratified sampling* untuk menjaga keseimbangan distribusi pendapatan.  

5. **Persiapan Data untuk Model**  
   - Menangani nilai kosong (*imputation*).  
   - Mengubah data kategorikal menjadi numerik (*One-Hot Encoding*).  
   - Melakukan *feature scaling* (standarisasi).  
   - Menggabungkan semua proses dalam *Pipeline* agar efisien dan terstruktur.  

6. **Pemilihan dan Pelatihan Model**  
   - Mencoba beberapa algoritma seperti *Linear Regression*, *Decision Tree*, dan *Random Forest*.  
   - Mengevaluasi performa menggunakan metrik **RMSE (Root Mean Square Error)**.  

7. **Fine-Tuning Model**  
   - Menggunakan *Grid Search* dan *Randomized Search* untuk menemukan kombinasi hyperparameter terbaik.  
   - Melihat *feature importance* untuk mengetahui fitur yang paling berpengaruh terhadap prediksi harga.  

8. **Evaluasi Akhir dan Deployment**  
   - Menguji model pada *test set* yang belum pernah dilihat sebelumnya.  
   - Menyimpan model siap pakai untuk digunakan di masa depan.

## 🧠 Insight  
- Pendapatan median terbukti menjadi faktor paling berpengaruh terhadap harga rumah.  
- Penggunaan *Pipeline* dan *Grid Search* mempermudah proses otomatisasi dan tuning model.  
- Random Forest menghasilkan performa terbaik dibandingkan model lainnya.

