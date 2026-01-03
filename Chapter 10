# Chapter 10 - Introduction to Artificial Neural Networks with Keras

## 1. Pengenalan Neural Networks
**Neural Networks** adalah model komputasi yang terinspirasi oleh cara kerja otak manusia. Mereka terdiri dari lapisan-lapisan neuron yang saling terhubung. Setiap neuron menerima input, mengolahnya dengan fungsi aktivasi, dan menghasilkan output. Neural networks digunakan untuk memecahkan masalah kompleks dalam berbagai domain seperti klasifikasi gambar, analisis teks, dan prediksi data.

## 2. Struktur dan Komponen Neural Network
**Neural network** terdiri dari tiga jenis lapisan:
- **Input Layer**: Lapisan pertama yang menerima input fitur dari data.
- **Hidden Layers**: Lapisan yang berada di antara input dan output, di mana data diproses lebih lanjut.
- **Output Layer**: Lapisan terakhir yang menghasilkan prediksi atau klasifikasi.

Setiap lapisan terdiri dari neuron yang terhubung ke neuron di lapisan berikutnya dengan bobot yang dapat disesuaikan.

## 3. Fungsi Aktivasi
Fungsi aktivasi digunakan untuk memperkenalkan non-linearitas ke dalam jaringan saraf, memungkinkan model untuk belajar dan memodelkan hubungan yang kompleks dalam data. Beberapa fungsi aktivasi yang umum digunakan adalah:
- **ReLU (Rectified Linear Unit)**: Fungsi aktivasi yang paling populer untuk jaringan saraf dalam.
- **Sigmoid**: Digunakan terutama pada model biner untuk menghasilkan output probabilitas.
- **Softmax**: Digunakan pada output layer untuk tugas klasifikasi multi-kelas.

## 4. Menggunakan Keras untuk Membangun Neural Networks
**Keras** adalah API tingkat tinggi yang memungkinkan pengguna untuk membangun dan melatih neural networks dengan mudah. Keras berjalan di atas berbagai backend seperti **TensorFlow**, **Theano**, atau **Microsoft Cognitive Toolkit**.

Langkah-langkah dasar untuk membangun model neural network dengan Keras:
1. **Menentukan Arsitektur Model**: Memilih jumlah lapisan tersembunyi, jumlah neuron per lapisan, dan fungsi aktivasi.
2. **Kompleksitas Model**: Menambahkan lapisan sesuai kebutuhan untuk menangani data yang lebih kompleks.
3. **Kompilasi Model**: Menyusun model dengan memilih optimizer, fungsi kerugian, dan metrik untuk evaluasi.
4. **Melatih Model**: Melatih model dengan data menggunakan metode **fit()**.

## 5. Optimizer dan Pembaruan Bobot
**Optimizer** digunakan untuk memperbarui bobot jaringan selama proses pelatihan, dengan tujuan meminimalkan fungsi kerugian. Beberapa optimizer yang umum digunakan termasuk:
- **Gradient Descent**: Metode dasar untuk optimasi.
- **Adam**: Optimizer yang lebih canggih yang menggabungkan manfaat dari momentum dan RMSProp.

## 6. Menilai Kinerja Model
Setelah model dilatih, penting untuk mengevaluasi kinerjanya menggunakan data uji yang tidak terlihat selama pelatihan. Beberapa metrik yang digunakan untuk menilai kinerja model dalam tugas klasifikasi adalah **accuracy**, **precision**, **recall**, dan **F1-score**.

## 7. Overfitting dan Regularisasi
**Overfitting** terjadi ketika model terlalu menyesuaikan data pelatihan, sehingga tidak dapat menggeneralisasi dengan baik pada data baru. Beberapa teknik untuk mencegah overfitting adalah:
- **Early Stopping**: Menghentikan pelatihan lebih awal ketika kinerja pada data validasi mulai menurun.
- **Dropout**: Menonaktifkan sebagian neuron selama pelatihan untuk mencegah jaringan saraf terlalu bergantung pada neuron tertentu.

## 8. Building an Image Classifier with Keras
Sebagai contoh aplikasi praktis, **Keras** digunakan untuk membangun classifier gambar menggunakan **Convolutional Neural Networks (CNNs)**, yang sangat efektif untuk tugas pengenalan gambar. CNN memanfaatkan lapisan konvolusi untuk mendeteksi pola dalam gambar, seperti tepi, tekstur, dan bentuk.

## 9. Building a Regression MLP with Keras
**Multilayer Perceptron (MLP)** adalah jenis neural network yang digunakan untuk tugas regresi. Dalam regresi, model mencoba untuk memprediksi nilai kontinu, bukan kelas. MLP dapat digunakan untuk memprediksi harga rumah, suhu, atau jenis prediksi lainnya yang memerlukan keluaran numerik.

## 10. Kesimpulan
**Neural Networks** adalah alat yang sangat kuat untuk memecahkan masalah yang kompleks, dan Keras menyediakan cara yang mudah dan efisien untuk membangun dan melatih model-model ini. Dengan memahami dasar-dasar neural networks dan cara menggunakan Keras, Anda dapat membangun model untuk berbagai tugas machine learning, dari klasifikasi gambar hingga prediksi numerik.
