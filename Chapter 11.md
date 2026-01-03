# Chapter 11 - Training Deep Neural Networks

## 1. Masalah Vanishing/Exploding Gradients
Salah satu tantangan utama saat melatih deep neural networks adalah masalah **vanishing gradients** dan **exploding gradients**. 
- **Vanishing gradients** terjadi ketika gradien menjadi sangat kecil selama backpropagation, membuat pembaruan bobot sangat lambat, bahkan tidak signifikan.
- **Exploding gradients** terjadi ketika gradien menjadi sangat besar, menyebabkan pembaruan bobot yang tidak stabil dan membuat model gagal untuk konvergen.

Masalah ini dapat diatasi dengan teknik seperti **normalisasi bobot** atau menggunakan **fungsi aktivasi** yang tidak mengalami saturasi, seperti **ReLU**.

## 2. Inisialisasi Bobot
Penting untuk menginisialisasi bobot dengan benar untuk mencegah masalah vanishing atau exploding gradients. Beberapa metode inisialisasi bobot yang umum digunakan adalah:
- **Inisialisasi Glorot (Xavier)**: Untuk jaringan dengan fungsi aktivasi sigmoid atau tanh.
- **Inisialisasi He**: Lebih cocok untuk **ReLU** dan varian fungsi aktivasi lainnya.

Inisialisasi yang tepat membantu mencegah masalah gradien dan memungkinkan pelatihan yang lebih stabil.

## 3. Fungsi Aktivasi yang Tidak Menyebabkan Vanishing Gradients
Pemilihan fungsi aktivasi yang tepat sangat penting dalam deep learning. Fungsi aktivasi yang lebih baik menghindari masalah **vanishing gradients**, seperti:
- **ReLU (Rectified Linear Unit)**: Fungsi aktivasi yang sangat populer karena dapat mengatasi masalah vanishing gradients dan memungkinkan pelatihan lebih cepat.
- **Leaky ReLU**: Versi dari ReLU yang memungkinkan gradien kecil untuk nilai negatif, sehingga menghindari masalah "dying ReLU."
- **ELU (Exponential Linear Unit)**: Alternatif yang lebih canggih untuk ReLU, yang dapat memberikan kinerja lebih baik pada beberapa masalah.

## 4. Batch Normalization
**Batch Normalization** adalah teknik yang digunakan untuk menstabilkan pelatihan jaringan saraf dengan menormalkan output dari setiap lapisan. Hal ini mengurangi masalah vanishing/exploding gradients dan mempercepat pelatihan. Batch normalization juga membantu model mencapai konvergensi yang lebih cepat dan mengurangi ketergantungan pada inisialisasi bobot.

## 5. Dropout dan Regularisasi
**Dropout** adalah teknik regularisasi yang membantu mencegah **overfitting** dengan menonaktifkan sebagian neuron selama pelatihan. Teknik ini secara acak "menghapus" neuron dari jaringan pada setiap iterasi pelatihan, mencegah model untuk terlalu bergantung pada neuron tertentu.

Beberapa teknik regularisasi lainnya termasuk **L2 regularization** dan **early stopping**, yang digunakan untuk menghindari overfitting dan meningkatkan kemampuan generalisasi model.

## 6. Optimizer yang Lebih Cepat
Untuk mempercepat pelatihan dan mengatasi masalah vanishing/exploding gradients, beberapa optimizer lebih canggih daripada **Stochastic Gradient Descent (SGD)**, antara lain:
- **Momentum**: Membantu mempercepat konvergensi dengan memberikan "momentum" pada langkah sebelumnya.
- **Nesterov Accelerated Gradient (NAG)**: Menggunakan momentum tetapi dengan memperbaiki posisi sebelum memperbarui bobot.
- **AdaGrad**: Menyesuaikan laju pembelajaran berdasarkan parameter, mengurangi laju pembelajaran untuk parameter yang sering diperbarui.
- **RMSProp**: Mengatasi kelemahan AdaGrad dengan menggunakan rata-rata pergerakan kuadrat gradien.
- **Adam**: Kombinasi dari Momentum dan RMSProp, sangat populer karena efisiensinya dalam berbagai jenis tugas deep learning.

## 7. Transfer Learning
**Transfer Learning** adalah teknik di mana model yang sudah dilatih pada satu tugas digunakan kembali dan disesuaikan (fine-tuned) untuk tugas lain. Ini memungkinkan model untuk memanfaatkan pengetahuan yang telah dipelajari sebelumnya, sangat berguna jika data terbatas untuk tugas baru.

Contohnya adalah **fine-tuning** pada model yang telah dilatih pada dataset besar (seperti ImageNet) untuk tugas spesifik seperti klasifikasi gambar medis.

## 8. Pretraining Jaringan Saraf
**Pretraining** adalah teknik di mana model dilatih pada tugas lain terlebih dahulu, sebelum dilatih untuk tugas utama. Teknik ini sering digunakan dengan **autoencoders** atau **unsupervised pretraining** pada deep belief networks (DBNs), dan dapat membantu model menghindari masalah local minima serta meningkatkan kinerja pada tugas utama.

## 9. Kesimpulan
Melatih **Deep Neural Networks** (DNNs) melibatkan tantangan yang lebih kompleks dibandingkan dengan model jaringan saraf yang lebih sederhana. Namun, dengan teknik-teknik seperti **Batch Normalization**, **Dropout**, **optimizers canggih**, dan **transfer learning**, kita dapat mengatasi masalah yang muncul selama pelatihan dan memanfaatkan potensi penuh dari DNNs untuk menyelesaikan masalah yang lebih rumit. Memahami dan mengimplementasikan teknik-teknik ini sangat penting untuk mencapai pelatihan yang stabil dan hasil yang optimal.
