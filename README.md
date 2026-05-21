# 🌾 Early Warning System (EWS) Volatilitas Harga Pangan Strategis (Studi Kasus: KSP)

![Status](https://img.shields.io/badge/Status-Completed-success)
![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/Deep_Learning-TensorFlow%2FKeras-FF6F00.svg)
![Plotly](https://img.shields.io/badge/Dashboard-Plotly-3f4f75.svg)

> **Catatan Portofolio:** Proyek ini merupakan purwarupa *Early Warning System* (EWS) berbasis *Deep Learning* yang dirancang untuk mendukung **Kantor Staf Presiden (KSP)** dalam memantau dan memprediksi anomali harga pangan strategis (Beras Medium) sebagai dasar rekomendasi kebijakan Operasi Pasar.

---

## 📑 Latar Belakang

Stabilitas harga pangan adalah salah satu indikator utama kesejahteraan masyarakat dan pengendalian inflasi nasional. Kenaikan harga yang mendadak sering kali memicu *panic buying* dan instabilitas sosial. Oleh karena itu, pengambil kebijakan di tingkat eksekutif membutuhkan sistem peringatan dini yang tidak hanya merekam data historis, tetapi mampu **meramalkan masa depan (Forecasting)** secara akurat.

Proyek ini memanfaatkan data historis harga pangan (mensimulasikan tren dari SP2KP Kementerian Perdagangan) untuk membangun model prediktif. Jika prediksi harga 7 hari ke depan menembus Harga Eceran Tertinggi (HET), sistem akan menyalakan alarm peringatan.

## 🎯 Tujuan Proyek

1. **Time-Series Forecasting:** Memprediksi pergerakan harga Beras Medium selama 7 hari ke depan menggunakan arsitektur *Neural Network*.
2. **Robust Architecture:** Mengimplementasikan **Stacked LSTM** (Long Short-Term Memory bertumpuk) dengan *Dropout layers* untuk menangkap pola musiman dan tren jangka panjang tanpa mengalami *overfitting*. Pengalaman dalam memodelkan volatilitas harga komoditas historis yang fluktuatif membuktikan bahwa metode Stacked LSTM sangat andal untuk *use-case* ini.
3. **Executive Dashboarding:** Menyajikan hasil prediksi dalam bentuk *dashboard* HTML multi-panel yang interaktif (Forecast, Learning Curve, dan Residual Distribution) agar mudah dipahami oleh pimpinan non-teknis.

## 🛠️ Tech Stack yang Digunakan

* **Bahasa Pemrograman:** Python
* **Deep Learning Framework:** `TensorFlow` / `Keras` (Sequential API, LSTM, Dense, Dropout)
* **Data Preprocessing:** `scikit-learn` (MinMaxScaler), `pandas`, `numpy`
* **Visualisasi Interaktif:** `plotly` (Multi-panel subplots)

---

## 🧠 Arsitektur Model (Stacked LSTM)

Model ini dirancang khusus untuk memproses data sekuensial harian dengan *look-back window* selama 30 hari. 
* **Layer 1:** LSTM (50 units, `return_sequences=True`) + Dropout (0.2)
* **Layer 2:** LSTM (50 units, `return_sequences=False`) + Dropout (0.2)
* **Output Layer:** Dense (1 unit untuk prediksi harga kontinu)
* **Optimizer & Loss:** Adam Optimizer dengan metrik evaluasi Mean Squared Error (MSE) dan Mean Absolute Percentage Error (MAPE).

## 📊 Tampilan Dashboard Interaktif

<img width="1919" height="912" alt="image" src="https://github.com/user-attachments/assets/d0363507-d6d1-40bb-b060-275f4f4c48db" />


Sistem menghasilkan *dashboard* multi-panel yang memuat tiga matriks utama:
1. **Kurva EWS & HET:** Membandingkan harga aktual, harga validasi, dan prediksi masa depan terhadap garis batas HET (Rp 13.900).
2. **Learning Curve:** Memastikan model berkonvergensi dengan baik (Loss vs Validation Loss).
3. **Distribusi Residual:** Memverifikasi kesehatan statistik model melalui sebaran *error* prediksi.

---

## 🚀 Cara Menjalankan Proyek Secara Lokal

### 1. Prasyarat

Pastikan Python terinstal, lalu jalankan perintah berikut untuk menginstal seluruh dependensi:

```bash
pip install numpy pandas scikit-learn tensorflow plotly
