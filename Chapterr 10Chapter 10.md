# Chapter 10
## Introduction to Artificial Neural Networks with Keras

---

## 1. Pengenalan Neural Networks

**Artificial Neural Networks (ANN)** adalah model komputasi yang terinspirasi oleh cara kerja otak manusia. Model ini terdiri dari lapisan-lapisan neuron yang saling terhubung.

Setiap neuron:
- menerima input,
- mengolahnya menggunakan fungsi aktivasi,
- menghasilkan output.

Neural networks digunakan untuk menyelesaikan masalah kompleks seperti:
- klasifikasi gambar,
- analisis teks,
- prediksi data.

---

## 2. Struktur dan Komponen Neural Network

Neural network umumnya terdiri dari tiga jenis lapisan utama:

- **Input Layer**  
  Lapisan pertama yang menerima data masukan.

- **Hidden Layers**  
  Lapisan di antara input dan output untuk pemrosesan data.

- **Output Layer**  
  Lapisan terakhir yang menghasilkan prediksi atau klasifikasi.

Setiap lapisan terdiri dari neuron yang terhubung melalui bobot (weights) yang dapat diperbarui selama pelatihan.

---

## 3. Fungsi Aktivasi

Fungsi aktivasi digunakan untuk memperkenalkan non-linearitas agar model dapat mempelajari hubungan kompleks dalam data.

Fungsi aktivasi yang umum digunakan:
- **ReLU (Rectified Linear Unit)**
- **Sigmoid**
- **Softmax**

---

## 4. Menggunakan Keras untuk Membangun Neural Networks

**Keras** adalah API tingkat tinggi untuk membangun dan melatih neural network. Keras dapat berjalan di atas beberapa backend seperti:
- TensorFlow
- Theano
- Microsoft Cognitive Toolkit

Langkah dasar membangun model dengan Keras:
1. Menentukan arsitektur model
2. Menentukan kompleksitas model
3. Melakukan kompilasi model
4. Melatih model menggunakan metode `fit()`

---

## 5. Optimizer dan Pembaruan Bobot

Optimizer digunakan untuk memperbarui bobot jaringan selama pelatihan guna meminimalkan fungsi loss.

Optimizer yang umum digunakan:
- **Gradient Descent**
- **Adam (Adaptive Moment Estimation)**

---

## 6. Menilai Kinerja Model

Evaluasi model dilakukan menggunakan data uji yang tidak digunakan saat pelatihan.

Metrik evaluasi yang umum digunakan:
- Accuracy
- Precision
- Recall
- F1-Score

---

## 7. Overfitting dan Regularisasi

Overfitting terjadi ketika model terlalu menyesuaikan data pelatihan dan gagal melakukan generalisasi.

Teknik pencegahan overfitting:
- **Early Stopping**
- **Dropout**

---

## 8. Building an Image Classifier with Keras

Keras dapat digunakan untuk membangun image classifier menggunakan **Convolutional Neural Networks (CNNs)**.

CNN efektif dalam mendeteksi:
- tepi
- tekstur
- pola
- bentuk objek

---

## 9. Building a Regression MLP with Keras

**Multilayer Perceptron (MLP)** digunakan untuk tugas regresi, yaitu memprediksi nilai kontinu.

Contoh penggunaan:
- prediksi harga rumah
- prediksi suhu
- prediksi nilai numerik lainnya

---

## 10. Kesimpulan

Neural Networks merupakan alat yang sangat kuat untuk menyelesaikan masalah kompleks. Keras menyediakan cara yang mudah dan efisien untuk membangun serta melatih model.

Dengan memahami dasar neural networks dan Keras, pengguna dapat membangun model untuk berbagai tugas machine learning.

