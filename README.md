# Klasifikasi Gambar Zanthoxyli Pericarpium

### Deskripsi Proyek

Proyek ini bertujuan untuk mengklasifikasikan gambar tanaman Zanthoxyli Pericarpium (kulit buah tanaman dari genus Zanthoxylum) ke dalam 5 jenis yang berbeda. Model dibangun menggunakan Convolutional Neural Network (CNN) dengan pendekatan transfer learning menggunakan arsitektur DenseNet201.

### Dataset

Dataset berasal dari Kaggle : https://www.kaggle.com/datasets/chaoquntan/image-dataset-of-zanthoxyli-pericarpium

- Jumlah gambar: Total ribuan gambar (jumlah pasti dapat dilihat di sumber).
- Kelas: 5 jenis tanaman, yaitu:

1. 0hong_sichuan
   
2. 1qing_qingjiao
 
3. 2qing_tengjiao
 
4. 3hong_derong

5. 4hong_hanyuan

Model yang dihasilkan disimpan dalam tiga format:

- SavedModel (untuk deployment di TensorFlow Serving)

- TFLite (untuk perangkat mobile/edge)

- TFJS (untuk aplikasi web)
