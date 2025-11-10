# 📘 Chapter 3: Classification  

## 🎯 Tujuan  
Bab ini membahas konsep **Klasifikasi (Classification)** dalam Machine Learning — yaitu proses melatih model untuk mengelompokkan data ke dalam kelas tertentu.  
Contoh kasus utama di bab ini adalah **pengenalan digit tulisan tangan (handwritten digit recognition)** menggunakan dataset **MNIST**.

## 🔢 Dataset  
Dataset **MNIST** berisi 70.000 gambar digit (0–9) dengan ukuran 28×28 piksel:  
- 60.000 gambar untuk data latih  
- 10.000 gambar untuk data uji  
Setiap gambar merepresentasikan satu angka dan digunakan untuk melatih model agar dapat mengenali angka baru.

## 🧩 Alur Proyek  

1. **Setup Lingkungan**  
   - Mengimpor library seperti `NumPy`, `Matplotlib`, dan `Scikit-Learn`.  
   - Menentukan konfigurasi awal dan *random seed* agar hasil eksperimen konsisten.

2. **Memuat dan Mengeksplorasi Data**  
   - Mengambil dataset MNIST menggunakan `fetch_openml('mnist_784')`.  
   - Melihat struktur data dan menampilkan beberapa contoh gambar digit untuk memahami pola visualnya.

3. **Membagi Data Latih dan Uji**  
   - Dataset dibagi menjadi data latih dan data uji agar model dapat dievaluasi secara adil.  
   - Biasanya digunakan 60.000 data latih dan 10.000 data uji.

4. **Membangun Model Klasifikasi**  
   - Menggunakan berbagai algoritma seperti:
     - **Stochastic Gradient Descent (SGDClassifier)**
     - **Random Forest**
     - **Support Vector Machine (SVM)**
   - Melatih model menggunakan fitur piksel (784 fitur per gambar).

5. **Evaluasi Model**  
   - Menggunakan metrik:
     - **Akurasi (Accuracy)**  
     - **Confusion Matrix**  
     - **Precision & Recall**  
     - **F1-Score**  
   - Membuat visualisasi seperti *confusion matrix* dan *precision-recall curve* untuk memahami performa model.

6. **Analisis Kesalahan (Error Analysis)**  
   - Melihat kelas mana yang paling sering salah diklasifikasikan.  
   - Menggunakan hasil *confusion matrix* untuk menemukan pola kesalahan.  
   - Membantu memperbaiki model atau fitur input.

7. **Fine-Tuning & Cross-Validation**  
   - Menggunakan *cross-validation* untuk mengevaluasi performa model secara lebih stabil.  
   - Melakukan *Grid Search* untuk menemukan kombinasi hyperparameter terbaik.

8. **Prediksi Akhir & Simpulan**  
   - Model terbaik diuji pada data uji.  
   - Hasilnya menunjukkan model dapat mengenali digit dengan tingkat akurasi tinggi (mendekati 97–98%).  

## 🧠 Insight  
- Klasifikasi merupakan salah satu tugas paling umum dalam Machine Learning.  
- MNIST adalah dataset klasik yang baik untuk memahami cara kerja algoritma klasifikasi.  
- Teknik seperti *cross-validation* dan *error analysis* sangat penting untuk meningkatkan kualitas model.  
- Evaluasi tidak hanya berdasarkan akurasi, tapi juga memperhatikan precision, recall, dan F1-score.


