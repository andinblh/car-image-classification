# Klasifikasi Gambar Mobil Menggunakan Deep Learning

## Deskripsi Proyek
Proyek ini bertujuan untuk membangun **sistem klasifikasi gambar mobil** menggunakan pendekatan *Deep Learning* berbasis **Convolutional Neural Network (CNN)**. Sistem ini mampu mengenali dan mengelompokkan gambar mobil ke dalam beberapa kelas secara otomatis berdasarkan pola visual yang dipelajari dari dataset pelatihan.

Model dilatih menggunakan **TensorFlow/Keras** dengan proses **augmentasi data dan normalisasi** untuk meningkatkan kemampuan generalisasi terhadap data baru. Setelah proses pelatihan selesai, model diekspor ke beberapa format agar dapat digunakan pada berbagai platform.

---

## Arsitektur Model
Model dibangun menggunakan **Convolutional Neural Network (CNN)** yang terdiri dari beberapa komponen utama:

- Convolution Layer  
- Activation Function (ReLU)  
- MaxPooling Layer  
- Fully Connected Layer  
- Softmax Output Layer  

Selain itu, **data augmentation** diterapkan untuk:
- meningkatkan variasi data,
- mengurangi risiko overfitting,
- serta meningkatkan kemampuan model dalam mengenali pola citra.

---

## 🚀 Alur Kerja Pelatihan
1. Melakukan preprocessing dataset  
2. Membangun arsitektur CNN  
3. Melakukan training model menggunakan training dan validation set  
4. Memilih model terbaik berdasarkan performa validasi  
5. Mengevaluasi model menggunakan test set  
6. Menyimpan model dalam beberapa format  

---

## Penyimpanan Model
Model yang sudah dilatih diekspor dalam beberapa format berikut:
1. TensorFlow SavedModel
2. TensorFlow Lite (TFLite)
3. TensorFlow.js (TFJS)
