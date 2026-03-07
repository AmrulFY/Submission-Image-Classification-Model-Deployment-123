# Klasifikasi Gambar Zanthoxyli Pericarpium

### Deskripsi Proyek

Proyek ini bertujuan untuk mengklasifikasikan gambar tanaman Zanthoxyli Pericarpium (kulit buah tanaman dari genus Zanthoxylum) ke dalam 5 jenis yang berbeda. Model dibangun menggunakan Convolutional Neural Network (CNN) dengan pendekatan transfer learning menggunakan arsitektur DenseNet201.

### Dataset

Dataset berasal dari Kaggle : https://www.kaggle.com/datasets/chaoquntan/image-dataset-of-zanthoxyli-pericarpium

- Jumlah gambar: Total ribuan gambar (jumlah pasti dapat dilihat di sumber).
- Kelas: 5 jenis tanaman, yaitu:

0hong_sichuan
1qing_qingjiao
2qing_tengjiao
3hong_derong
4hong_hanyuan

### Arsitektur Model

Base model: DenseNet201 yang telah dilatih pada ImageNet, dengan include_top=False dan input berukuran 150x150x3.
Layers tambahan:
MaxPooling2D(), Dropout(0.5), Dense dll
Strategi Transfer Learning:
Awalnya base model di-freeze, hanya layer baru yang dilatih dengan learning rate 0.0001.
Setelah beberapa epoch, dilakukan fine-tuning dengan membuka beberapa layer teratas dan learning rate sangat kecil (1e-5).

### Proses Pelatihan

Data Augmentasi : Rotation, shear, zoom, horizontal flip, dll. menggunakan ImageDataGenerator.
Pembagian Data: 80% training, 10% validasi, 10% testing (dengan metode split folder).
Optimizer: Adam dengan learning rate bertahap (ReduceLROnPlateau).
Callbacks: EarlyStopping dan ReduceLROnPlateau.
Batch size: 16.
Epoch: Maksimal 10 dengan early stopping.

### Hasil Model

Akurasi Training: Mencapai >= 95%.
Akurasi Validasi: Stabil di sekitar 95% .
Akurasi Test: Diperoleh sekitar 96% (evaluasi pada data testing yang tidak pernah digunakan selama pelatihan).

Model yang dihasilkan disimpan dalam tiga format:
SavedModel (untuk deployment di TensorFlow Serving)
TFLite (untuk perangkat mobile/edge)
TFJS (untuk aplikasi web)
