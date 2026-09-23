# 🥔 Potato Image Reconstruction (Inpainting) 🎨

[![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)](#)
[![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=Keras&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](#)

## 📖 Deskripsi Proyek

Proyek ini mengimplementasikan arsitektur **U-Net Autoencoder** untuk melakukan tugas *Image Inpainting* pada gambar kentang (bukan daun). Tujuan utamanya adalah untuk merekonstruksi bagian gambar kentang yang rusak atau hilang (di-mask secara acak) agar kembali menyerupai gambar aslinya secara utuh. 

Pendekatan ini sangat berguna dalam pemrosesan citra agrikultur untuk memulihkan data visual yang terkorupsi.

## ✨ Fitur Utama

- **Arsitektur U-Net Modifikasi**: Menggunakan *Group Normalization* dan pola Encoder-Decoder dengan *Skip Connections* untuk mempertahankan detail spasial.
- **Random Cutout Masking**: Augmentasi dinamis yang memotong 10%-20% area gambar secara acak saat proses pelatihan untuk mengajari model cara melakukan *inpainting*.
- **Fungsi Loss Kustom (SSIM + Weighted MAE)**: Mengkombinasikan *Structural Similarity Index* (SSIM) dengan *Mean Absolute Error* (MAE) yang diberi bobot lebih besar (1.5x) pada area yang direkonstruksi untuk hasil yang lebih realistis dan tajam.
- **Callbacks Cerdas**: Dilengkapi dengan `EarlyStopping`, `ReduceLROnPlateau`, dan `ModelCheckpoint` untuk mengoptimalkan proses pelatihan.

## 🗂️ Dataset

Dataset yang digunakan diunduh langsung melalui `kagglehub` dari repositori:
👉 **[mukaffimoin/potato-diseases-datasets](https://www.kaggle.com/datasets/mukaffimoin/potato-diseases-datasets)**

*Catatan: Proyek ini hanya menggunakan kelas **"Healthy Potatoes"** yang secara otomatis dipisahkan sebesar 80% untuk pelatihan dan 20% untuk validasi.*

## ⚙️ Persyaratan Sistem (Tech Stack)

Pastikan Anda telah menginstal pustaka berikut sebelum menjalankan skrip:
- Python 3.8+
- TensorFlow & Keras
- NumPy
- Matplotlib
- Scikit-Image (`skimage`)
- KaggleHub

Anda bisa menginstalnya via pip:
```bash
pip install tensorflow numpy matplotlib scikit-image kagglehub
