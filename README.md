# Implementasi Transformer dan Image Super-Resolution

## 📘 Deskripsi

Repository ini berisi implementasi model **Transformer** untuk tugas klasifikasi teks dan gambar, serta eksplorasi model **image super-resolution** sebagai bagian dari mata kuliah *Pembelajaran Mesin*.

Eksperimen dilakukan untuk membandingkan performa Transformer dengan model baseline seperti **LSTM** (teks) dan **CNN** (citra), serta memahami perilaku model pada dataset dengan skala terbatas.

---

## 🎯 Tujuan

* Mengimplementasikan **Text Transformer** dari awal menggunakan PyTorch
* Mengimplementasikan **Vision Transformer (ViT)** sederhana
* Membandingkan performa dengan model baseline
* Menganalisis akurasi, efisiensi, dan stabilitas model
* Mengimplementasikan model non-klasifikasi untuk *image super-resolution*

---

## 📂 Dataset

### 1. Text Classification

* Dataset: IMDb Movie Reviews
* Jumlah data: 50.000 ulasan (digunakan subset 10.000)
* Kelas: Positif & Negatif
* Preprocessing:

  * Lowercase
  * Menghapus HTML tag
  * Tokenisasi & padding (max length = 120)
  * Vocabulary: 15.000 kata

### 2. Vision Classification

* Dataset: MNIST
* Jumlah data: 70.000 gambar digit
* Preprocessing:

  * Resize ke 32×32
  * Normalisasi (mean = 0.5, std = 0.5)

---

## 🧠 Model yang Digunakan

### A. Text Classification

* **Transformer**
* **LSTM (Baseline)**

Arsitektur Transformer:
Input → Embedding → Positional Encoding → Transformer Encoder → Pooling → Linear → Output

---

### B. Vision Classification

* **Vision Transformer (ViT)**
* **Simple CNN (Baseline)**

Arsitektur ViT:
Image → Patch Splitting → Patch Embedding → Positional Encoding → Transformer Encoder → Classification Head

---

## 🖼️ Implementasi Non-Klasifikasi (Image Super-Resolution)

Selain klasifikasi, proyek ini juga mengimplementasikan model dari repository eksternal yaitu Real-ESRGAN untuk tugas *image super-resolution*.

### 🎯 Tujuan

Meningkatkan kualitas gambar beresolusi rendah menjadi gambar yang lebih tajam dan detail.

### ⚙️ Detail Implementasi

* Model: RealESRGAN_x4plus (pretrained)
* Input: Gambar resolusi rendah
* Output: Gambar resolusi tinggi

### 🔧 Modifikasi yang Dilakukan

* Mengubah parameter:

  * `--outscale 4` → `--outscale 2`
* Memperbaiki kompatibilitas library:

  * Mengganti import deprecated pada modul `basicsr`

### 📊 Hasil

* **Scale 4x**: gambar sangat tajam dan detail tinggi, namun ukuran besar
* **Scale 2x**: lebih cepat dan ringan, dengan kualitas tetap meningkat signifikan

### 🧠 Analisis

* Tugas ini bukan klasifikasi karena output berupa **gambar baru**, bukan label
* Model bekerja secara generatif untuk merekonstruksi detail gambar
* Parameter skala memengaruhi trade-off antara kualitas dan kecepatan

---

## 📊 Hasil Eksperimen

| Model              | Dataset | Accuracy | Parameter | Catatan              |
| ------------------ | ------- | -------- | --------- | -------------------- |
| Transformer (Text) | IMDB    | 75.50%   | 2.4M      | Lebih lambat         |
| LSTM               | IMDB    | 65.60%   | 1.4M      | Lebih stabil         |
| Vision Transformer | MNIST   | 97.83%   | 849K      | Lebih kompleks       |
| CNN                | MNIST   | 98.92%   | 268K      | Lebih cepat & akurat |

---

## 📈 Evaluasi

Evaluasi model mencakup:

* Training loss
* Accuracy (training & testing)
* Confusion matrix
* Jumlah parameter
* Waktu training

---

## 🔍 Analisis Singkat

* Transformer tidak selalu lebih unggul pada dataset kecil
* LSTM lebih stabil untuk teks dengan data terbatas
* CNN lebih efisien dan akurat untuk gambar kecil seperti MNIST
* Vision Transformer membutuhkan data lebih besar agar optimal
* Self-attention memiliki kompleksitas lebih tinggi dibanding CNN

---

## 🛠️ Teknologi

* Python
* PyTorch
* Google Colab
* NumPy
* Matplotlib
* Scikit-learn

---

## 📁 Struktur Repository

```
.
├── transformer_experiment.ipynb
├── laporan_transformer.pdf
└── README.md
```

---

## 🚀 Cara Menjalankan

1. Buka notebook di Google Colab
2. Install dependency jika diperlukan:

   ```
   pip install torch torchvision scikit-learn matplotlib
   ```
3. Jalankan semua cell secara berurutan
4. Hasil training dan evaluasi akan muncul di output notebook

---

## 👤 Author

Putri Torsia Aura Prameswary
NIM: 2546000083
Mata Kuliah: Pembelajaran Mesin

---

## 📌 Catatan

Repository ini dibuat untuk keperluan akademis sebagai tugas implementasi Transformer dan eksplorasi model deep learning.
