# Chapter 12 - Convolutional Neural Networks

## 1. Pengenalan Convolutional Neural Networks (CNNs)
**CNNs** adalah jenis jaringan saraf yang dilatih untuk mendeteksi pola dalam data berbentuk grid. CNN sering digunakan untuk tugas-tugas seperti **pengenalan gambar**, **deteksi objek**, **segmentasi gambar**, dan **pengenalan suara**. Mereka terdiri dari lapisan-lapisan yang dirancang untuk mengekstraksi fitur spasial dari data.

## 2. Struktur CNN
CNN terdiri dari beberapa lapisan utama yang bekerja bersama untuk mengenali fitur-fitur dalam data gambar:
- **Convolutional Layer**: Lapisan ini melakukan operasi konvolusi untuk mendeteksi fitur dari gambar. Setiap filter (kernel) di lapisan ini menggeser diri melalui gambar dan menghasilkan peta fitur.
- **Pooling Layer**: Lapisan ini mengurangi dimensi peta fitur (downsampling) dengan mengambil nilai maksimum atau rata-rata dari area tertentu, yang mengurangi kompleksitas komputasi dan membantu model berfokus pada fitur yang lebih signifikan.
- **Fully Connected Layer**: Lapisan ini terhubung dengan semua neuron di lapisan sebelumnya dan digunakan untuk klasifikasi berdasarkan fitur yang diekstraksi.
- **Activation Layer**: Fungsi aktivasi seperti **ReLU** digunakan untuk memperkenalkan non-linearitas ke dalam jaringan.

## 3. Konvolusi dan Filter
**Konvolusi** adalah operasi matematis di mana filter bergerak di atas gambar untuk menghasilkan peta fitur. Filter ini dapat mendeteksi berbagai pola dasar seperti tepi, sudut, dan tekstur pada gambar. Semakin banyak lapisan konvolusi yang ada, semakin kompleks fitur yang dapat diekstraksi.

- **Filter** atau **Kernel** adalah matriks kecil yang digunakan untuk melakukan konvolusi dengan gambar.
- **Stride** adalah langkah pergeseran filter di atas gambar.
- **Padding** digunakan untuk menambahkan pixel di sekitar gambar agar ukuran peta fitur tetap terjaga setelah konvolusi.

## 4. Pooling
**Pooling** digunakan untuk mengurangi ukuran peta fitur dan mempercepat komputasi. Dua jenis pooling yang umum digunakan adalah:
- **Max Pooling**: Mengambil nilai maksimum dari area yang ditentukan, sehingga mempertahankan informasi paling penting.
- **Average Pooling**: Mengambil rata-rata dari area yang ditentukan, tetapi lebih sensitif terhadap noise.

## 5. Arsitektur CNN
Arsitektur CNN umumnya terdiri dari beberapa lapisan konvolusi diikuti oleh lapisan pooling, dan diakhiri dengan beberapa lapisan fully connected. Arsitektur ini memungkinkan CNN untuk mengekstraksi fitur dari gambar secara hierarkis, mulai dari fitur rendah (seperti tepi) hingga fitur lebih kompleks (seperti bentuk dan objek).

Beberapa arsitektur CNN yang terkenal adalah:
- **LeNet**: Salah satu CNN pertama yang digunakan untuk pengenalan digit pada dataset MNIST.
- **AlexNet**: CNN yang memenangkan kompetisi ImageNet 2012, dengan arsitektur yang lebih dalam dan menggunakan GPU untuk pelatihan.
- **VGGNet**: Arsitektur CNN dengan lapisan-lapisan konvolusi yang lebih dalam dan sederhana.
- **ResNet**: CNN dengan lapisan residual yang memungkinkan pelatihan lebih dalam tanpa masalah gradien.

## 6. Melatih CNN
Pelatihan CNN melibatkan pemberian data gambar yang sudah diberi label untuk membiarkan jaringan saraf belajar dari data tersebut. Optimizer yang sering digunakan untuk melatih CNN adalah **Adam**, **SGD**, dan **RMSprop**. Selain itu, teknik **data augmentation** seperti rotasi, pemotongan, dan flipping gambar digunakan untuk meningkatkan keragaman data pelatihan dan mencegah overfitting.

## 7. Transfer Learning dengan CNN
**Transfer Learning** adalah teknik di mana model yang telah dilatih pada dataset besar, seperti **ImageNet**, digunakan untuk tugas yang lebih spesifik dengan sedikit penyesuaian (fine-tuning). Ini memungkinkan model untuk memanfaatkan pengetahuan yang telah dipelajari sebelumnya dan menerapkannya pada tugas yang serupa dengan dataset yang lebih kecil.

## 8. Regularisasi dalam CNN
Seperti model deep learning lainnya, CNN juga rentan terhadap **overfitting** jika terlalu banyak parameter yang dilatih. Beberapa teknik regularisasi yang dapat digunakan adalah:
- **Dropout**: Menonaktifkan secara acak neuron selama pelatihan untuk mencegah model terlalu bergantung pada fitur tertentu.
- **Early Stopping**: Menghentikan pelatihan lebih awal jika kinerja pada data validasi mulai menurun.
- **Data Augmentation**: Teknik untuk menghasilkan variasi data pelatihan untuk mencegah overfitting dengan cara merotasi, mengubah ukuran, atau memodifikasi gambar.

## 9. Aplikasi CNN
CNN digunakan dalam berbagai aplikasi, terutama yang melibatkan data visual, seperti:
- **Pengenalan objek**: Deteksi dan klasifikasi objek dalam gambar atau video.
- **Segmentasi gambar**: Pembagian gambar menjadi beberapa bagian untuk analisis lebih lanjut (misalnya, pemisahan bagian tubuh dalam citra medis).
- **Pengenalan wajah**: Penggunaan CNN untuk mengidentifikasi dan memverifikasi wajah dalam gambar atau video.
- **Otomatisasi kendaraan**: Pengenalan objek dan rambu lalu lintas untuk mengemudi otomatis.

## 10. Kesimpulan
**Convolutional Neural Networks (CNNs)** adalah teknologi yang sangat kuat untuk memproses dan menganalisis data visual. Dengan menggunakan berbagai lapisan seperti konvolusi, pooling, dan fully connected, CNN dapat mengekstraksi dan mempelajari fitur dari gambar dengan cara yang efisien. CNN sangat efektif untuk tugas-tugas seperti pengenalan gambar, deteksi objek, dan segmentasi. Selain itu, teknik seperti **transfer learning**, **data augmentation**, dan **regularisasi** membantu meningkatkan kinerja model dan mencegah overfitting.
