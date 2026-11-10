# Bike Sharing Demand Analytics & Predictive Modeling

## 1. Project Overview
Proyek ini berfokus pada analisis data dan pemodelan prediktif untuk sistem penyewaan sepeda (*Bike Sharing System*) menggunakan dataset historis dari Capital Bikeshare (Washington D.C., USA). Tujuan utama dari proyek ini adalah untuk menganalisis pola penggunaan sepeda harian maupun harian-berbasis-jam (*hourly*) berdasarkan faktor lingkungan, cuaca, dan tren musiman, serta membangun model prediktif untuk mengestimasi volume penyewaan sepeda.

---

## 2. Business Understanding & Problem Statement
Sistem penyewaan sepeda berfungsi sebagai jaringan sensor visual perkotaan (*virtual sensor network*) yang merekam mobilitas masyarakat. Pemahaman terhadap pola ini sangat krusial bagi penyedia layanan dan pemerintah kota untuk:
- **Optimalisasi Alokasi Armada:** Mengetahui kapan dan di mana permintaan sepeda melonjak agar distribusi unit sepeda lebih efisien.
- **Manajemen Operasional:** Memprediksi dampak kondisi cuaca ekstrem, hari libur, dan jam kerja terhadap jumlah pengguna (kasual vs. terdaftar).

---

## 3. Dataset Characteristics

Dataset terbagi menjadi dua skala agregasi:
- `day.csv`: Data agregasi harian (731 rekor hari dari tahun 2011–2012).
- `hour.csv`: Data agregasi per jam (17,379 rekor jam).

### Feature Dictionary:
- **`instant`**: Index catatan (*record index*).
- **`dteday`**: Tanggal catatan.
- **`season`**: Musim (1: Semi/Spring, 2: Panas/Summer, 3: Gugur/Fall, 4: Dingin/Winter).
- **`yr`**: Tahun (0: 2011, 1: 2012).
- **`mnth`**: Bulan (1 s.d. 12).
- **`hr`**: Jam (0 s.d. 23) *(hanya tersedia di `hour.csv`)*.
- **`holiday`**: Apakah hari tersebut merupakan hari libur nasional (1: Ya, 0: Tidak).
- **`weekday`**: Hari dalam seminggu.
- **`workingday`**: Hari kerja (1: Jika bukan akhir pekan/hari libur, 0: Lainnya).
- **`weathersit`**: Kondisi cuaca:
  - `1`: Cerah / Berawan tipis (*Clear, Few clouds, Partly cloudy*)
  - `2`: Berkabut / Mendung (*Mist + Cloudy, Mist + Broken clouds*)
  - `3`: Hujan ringan / Salju ringan / Badai (*Light Snow, Light Rain + Thunderstorm*)
  - `4`: Hujan lebat / Badai es / Kabut tebal (*Heavy Rain + Ice Pellets + Snow + Fog*)
- **`temp`**: Suhu yang dinormalisasi dalam Celcius (dibagi 41).
- **`atemp`**: Suhu yang dirasakan (*feeling temperature*) yang dinormalisasi (dibagi 50).
- **`hum`**: Kelembapan udara yang dinormalisasi (dibagi 100).
- **`windspeed`**: Kecepatan angin yang dinormalisasi (dibagi 67).
- **`casual`**: Jumlah pengguna non-berlangganan (*casual users*).
- **`registered`**: Jumlah pengguna terdaftar (*registered users*).
- **`cnt`**: Total keseluruhan sepeda yang disewa (`casual` + `registered`).

---

## 4. Analytical & Modeling Methodology
1. **Exploratory Data Analysis (EDA):**
   - Meneliti korelasi antara fitur cuaca (`temp`, `hum`, `windspeed`) terhadap variabel target (`cnt`).
   - Menganalisis perbedaan pola penyewaan pada `workingday` vs `holiday`, serta jam-jam sibuk (*peak hours*).
2. **Data Preprocessing:**
   - Penanganan missing values dan pembersihan outlier.
   - Ekstraksi fitur waktu dan *encoding* untuk variabel kategorikal.
3. **Machine Learning Modeling (Regression):**
   - Membangun dan mengevaluasi model regresi (seperti *Linear Regression*, *Random Forest*, atau *XGBoost*) untuk memprediksi `cnt`.
   - Menguji performa model menggunakan metrik evaluasi **RMSE**, **MAE**, dan **R² Score**.

---

## 5. How to Run
1. Clone repositori ini:
   ```bash
 git clone [https://github.com/username/bike-sharing-analytics.git](https://github.com/username/bike-sharing-analytics.git)
