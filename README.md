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

##Penyimpanan Model
Model disimpan dalam tiga format berbeda agar bisa digunakan di berbagai platform:

| Format | File | Kegunaan |
|--------|------|-----------|
| SavedModel | `model_vehicle_cnn/` | Untuk server/cloud deployment |
| TF-Lite | `model_vehicle_cnn.tflite` | Untuk aplikasi mobile (Android) |
| TFJS | `model_tfjs/` | Untuk aplikasi berbasis web |

Selain itu, model terbaik juga disimpan sebagai `best_model.keras`.
