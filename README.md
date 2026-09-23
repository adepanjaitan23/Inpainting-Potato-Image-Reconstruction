<div align="center">

<!-- Ganti URL ini dengan URL Banner/Logo proyek Anda -->
<img src="https://raw.githubusercontent.com/username/repo/main/assets/banner.png" alt="Potato Inpainting Banner" width="100%">

# 🥔 Potato Image Reconstruction (Inpainting) 🎨

[![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)](#)
[![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=Keras&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](#)
[![Jupyter](https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white)](#)

*Proyek Deep Learning untuk memulihkan dan merekonstruksi bagian yang hilang pada citra kentang menggunakan arsitektur U-Net Autoencoder.*

</div>

---

## 🎯 Demo Hasil (Inpainting Results)

Berikut adalah performa model dalam merekonstruksi gambar kentang yang telah dipotong (*masked*) secara acak:

<div align="center">
  <!-- Gunakan format tabel HTML untuk menyejajarkan gambar dengan rapi -->
  <table>
    <tr>
      <td align="center"><b>Original Image</b></td>
      <td align="center"><b>Masked Input (Corrupted)</b></td>
      <td align="center"><b>Reconstructed Output</b></td>
    </tr>
    <tr>
      <td><img src="https://raw.githubusercontent.com/username/repo/main/assets/original_sample.png" width="250"></td>
      <td><img src="https://raw.githubusercontent.com/username/repo/main/assets/masked_sample.png" width="250"></td>
      <td><img src="https://raw.githubusercontent.com/username/repo/main/assets/reconstructed_sample.png" width="250"></td>
    </tr>
  </table>
</div>

*(Opsional: Jika Anda memiliki proses GIF dari epoch awal hingga akhir, Anda bisa menampilkannya di sini)*
<!-- <img src="https://raw.githubusercontent.com/username/repo/main/assets/training_progress.gif" width="400"> -->

---

## 🧠 Arsitektur & Metodologi

Proyek ini memanfaatkan **U-Net Autoencoder** yang dimodifikasi. Model menerima gambar yang rusak dan belajar memprediksi piksel yang hilang dengan memahami konteks dari area di sekitarnya.

<div align="center">
  <img src="https://raw.githubusercontent.com/username/repo/main/assets/unet_architecture.png" alt="U-Net Architecture Diagram" width="80%">
  <br>
  <i>Ilustrasi Arsitektur U-Net (Encoder-Decoder dengan Skip Connections)</i>
</div>

### ✨ Sorotan Fitur
- **Custom U-Net Architecture**: Menggunakan *Group Normalization* untuk menstabilkan pelatihan.
- **Dynamic Cutout Masking**: Augmentasi dinamis yang memotong 10%-20% area gambar secara acak saat *training*.
- **Hybrid Loss Function (SSIM + Weighted MAE)**: Memaksa model untuk menghasilkan tekstur kentang yang realistis (SSIM) sekaligus meminimalkan kesalahan piksel pada area spesifik yang rusak (Weighted MAE).

---

## 📊 Evaluasi Model

Kinerja model dipantau melalui kurva Loss dan metrik *Mean Absolute Error* (MAE) selama proses pelatihan.

<div align="center">
  <img src="https://raw.githubusercontent.com/username/repo/main/assets/loss_graph.png" alt="Training & Validation Loss Graph" width="600">
</div>

---

## 🗂️ Dataset

Dataset diunduh secara otomatis via `kagglehub` dari:
👉 **[mukaffimoin/potato-diseases-datasets](https://www.kaggle.com/datasets/mukaffimoin/potato-diseases-datasets)**

> Proyek ini berfokus secara eksklusif pada kelas **"Healthy Potatoes"** (80% untuk *training*, 20% untuk *validation*).

---

## 🚀 Panduan Eksekusi

1. Clone repositori ini atau buka langsung di **Google Colab**.
2. Pastikan pustaka yang dibutuhkan sudah terinstal:
   ```bash
   pip install tensorflow numpy matplotlib scikit-image kagglehub
   ```
