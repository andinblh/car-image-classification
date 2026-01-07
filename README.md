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

## Alur Kerja Pelatihan
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
   
 # Image Classification Car using CNN

##Deskripsi Proyek
Proyek ini bertujuan untuk melakukan **klasifikasi jenis kendaraan** menggunakan **Convolutional Neural Network (CNN)**.  
Dataset yang digunakan adalah *Vehicle Images Dataset* dari Kaggle, yang berisi berbagai gambar kendaraan seperti:
- Sedan  
- SUV  
- Van  
- Truck  
- Big Truck  
- City Car  
- Multi Purpose Vehicle  

Model CNN dilatih menggunakan *TensorFlow dan Keras*, dengan pembagian dataset menjadi *train*, *validation*, dan *test set* untuk memastikan model dapat belajar dan melakukan generalisasi dengan baik.

##Struktur Dataset
Dataset berada di folder `dataset_all/` dengan subfolder untuk setiap kelas kendaraan.  
Dataset dibagi secara otomatis menggunakan `ImageDataGenerator` menjadi:
- *80% Training set*
- *10% Validation set*
- *10% Testing set*

Semua gambar diubah ke ukuran *150x150 piksel* sebelum dimasukkan ke dalam model.

---

##Arsitektur Model CNN
Model dibangun menggunakan *Sequential API* dengan susunan layer sebagai berikut:

1. `Conv2D(32, (3,3), activation='relu')`
2. `MaxPooling2D(2,2)`
3. `Conv2D(64, (3,3), activation='relu')`
4. `MaxPooling2D(2,2)`
5. `Flatten()`
6. `Dense(128, activation='relu')`
7. `Dropout(0.5)`
8. `Dense(num_classes, activation='softmax')`

Optimizer: `Adam`  
Loss Function: `categorical_crossentropy`  
Metrics: `accuracy`

---

##Callback
Model menggunakan callback *EarlyStopping* dengan parameter:
- `monitor='val_loss'`
- `patience=5`
- `restore_best_weights=True`

Callback ini akan otomatis menghentikan training ketika model tidak lagi mengalami peningkatan performa, untuk mencegah overfitting.

---

##Hasil Pelatihan
Model dilatih selama *maksimum 30 epoch* dengan EarlyStopping aktif.  
Hasil pelatihan menunjukkan:
- *Training Accuracy:* ~95–98%  
- *Validation Accuracy:* ~97–100%  

Visualisasi hasil pelatihan menunjukkan model stabil dan tidak overfitting.

---

##Penyimpanan Model
Model disimpan dalam tiga format berbeda agar bisa digunakan di berbagai platform:

| Format | File | Kegunaan |
|--------|------|-----------|
| SavedModel | `model_vehicle_cnn/` | Untuk server/cloud deployment |
| TF-Lite | `model_vehicle_cnn.tflite` | Untuk aplikasi mobile (Android) |
| TFJS | `model_tfjs/` | Untuk aplikasi berbasis web |

Selain itu, model terbaik juga disimpan sebagai `best_model.keras`.
