# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun:
- **Nama:** Komang Dina Kartika
- **NIM:** 2515091050
- **Program Studi:** Sistem Informasi
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek
Dataset yang digunakan merupakan data startup SaaS yang terdiri dari 650 Observasi dan 6 Variabel. Analisis yang saya lakukan yaitu untuk mencari tahu hubungan antara Pendapatan_Tahunan_MIliar_IDR (variabel dependen) dan Nilai_Pelanggan_Juta_IDR (variabel independen). Tujuan dari analisis ini adalah untuk:
1. Mendeskripsikan Karakteristik data pendapatan startup SaaS
2. Menguji apakah data pendapatan terdistribusi normal.
3. Mengetahui hubungan (korelasi) antara nilai pelanggan dan pendapatan tahunan.
4. Membangun model regresi linier sederhana untuk memprediksi pendapatan tahunan berdasarkan nilai pelanggan.

---

## 3. Struktur Proyek
Proyek ini diorganisir ke dalam beberapa folder sebagai berikut:
- `/data` : berisi dataset mentah yang digunakan dalam analisis.
- `/scripts` : berisi skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results` : berisi output analisis seperti grafik, plot, dan ringkasan hasil.
- `README.md` : dokumentasi lengkap proyek.

---

## 4. Cara Menjalankan Analisis
Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal pada Komputer.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi
### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - Mean: 31.88
  - Median: 31.30
  - modus 1.87
  - *Interpretasi*: Nilai Mean dan Median yang hampir sama mennjukan distribusi data pendapatan relatif simetris dan tidak mengalami penyimpangan ekstrem ke salah satu sisi, yang artinya sebagian besar nilai pendapatan terkonsentrasi di sekitar nilai tengah data. Sedangkan Modus yang bernilai lebih kecil dibandingkan Mean dan Median menunjukan bahwa nilai pendapatan yang paling sering muncul berada pada pendapatan yang relatif rendah.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - Standar Deviasi: 19.79
  - Range: 1.00-66.89
  - Kuartil: (Q1-Q3): 14.31-49.04
  - *Interpretasi:* Standar deviasi yang cukup besar menunjukan data pendapatan memiliki tingkat variasi yang tinggi antar startup. Nilai Range yang lebar menandakan adanya perbedaan pendapatan antara startup pendapatan terendah dan tertinggi. Rentang kuartil (Q1-Q3) menunjukan pendapatan berada pada kisaran 14.31-49.04 miliar rupiah, artinya sebaran pendapatan menengah dalam dataset
- **Visualisasi (Histogram/Boxplot):**
  - *Interpretasi*: Histogram menunjukan distribusi pendapatan yang cenderung miring ke kanan, artinya sebagian besar startup memiliki pendapatan relatif rendah, sementara hanya sebagian kecil startup yang memiliki pendapatan sangat tinggi. Boxplot terdapat outlier di bagian atas distribusi, yang menunjukan keberadaan startup dengan pendapatan jauh di atas rata-rata

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - Statistik W: 0,94664
  - p-value: 1.497e-14
  - *Interpretasi:* Karena p-value ≤ 0.05, maka hipotesis nol ditolak. Yang artinya data Pendapatan_Tahunan_Miliar_IDR tidak terdistribusi normal.
- **Plot Q-Q:**
  *interpretasi*: Plot Q-Q menunjukan titik-titik data tidak sepenuhnya mengikuti garis diagonal, terutama pada bagian ekor distribusi. Artinya terdapat penyimpangan dari distribusi normal dan mendukung hasil uji Shapiro-Wilk

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - Koefisien korelasi (r): 0.997
  - p-value: 2.2e-16
  - *Interpretasi:* Nilai koefisien sebesar 0.997 menunjukan hubungan linear positif yang sangat kuat antara nilai pelanggan dan pendapatan tahunan. Nilai p-value yang sangat kecil menunjukan hubungan tersebut signifikan. Artinya, peningkatan nilai pelanggan secara konsisten diikuti oleh peningkatan pendapatan tahunan startup.
- **Visualisasi (Scatter Plot):**
*Interpretasi:* Scatter plot menunjukkan pola hubungan linear yang jelas antara nilai pelanggan dan pendapatan tahunan, di mana titik-titik data membentuk tren naik. Pola ini memperkuat hasil uji korelasi dan menunjukkan hubungan antar variabel bersifat linier.

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
    Pendapatan = -0.99 + 0.33 x Nilai_Pelanggan 
  - *Interpretasi:* Koefisien intercept menunjukkan nilai pendapatan ketika nilai pelanggan bernilai nol, sedangkan koefisien slope menunjukkan bahwa setiap kenaikan 1 juta rupiah nilai pelanggan akan meningkatkan pendapatan tahunan sekitar 0.33 miliar rupiah.
- **Evaluasi Model (R-squared):**
  - Adjusted R-squared: 0.994 (99.4%)
  - *Interpretasi:* Nilai Adjusted R-squared sebesar 0.994 menunjukkan 99.4% variasi pendapatan tahunan dapat dijelaskan oleh variabel nilai pelanggan. Ini menunjukkan model regresi yang dibangun memiliki tingkat ketepatan dan kemampuan prediksi yang sangat tinggi.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Interpretasi:* Scatter plot antara Nilai_Pelanggan_Juta_IDR dan Pendapatan_Tahunan_Miliar_IDR yang dilengkapi dengan garis regresi menunjukkan hubungan linear positif yang sangat kuat. Garis regresi mengikuti pola sebaran titik data secara konsisten, dengan sebagian besar titik berada sangat dekat dengan garis regresi. Artinya model regresi linier yang dibangun memiliki tingkat kecocokan yang baik. Kedekatan titik-titik data dengan garis regresi juga mendukung nilai Adjusted R-squared yang tinggi, sehingga secara visual dan numerik model regresi dapat dikatakan mampu merepresentasikan hubungan antara nilai pelanggan dan pendapatan tahunan secara akurat.
---

## 6. Kesimpulan
Berdasarkan hasil analisis, pendapatan startup SaaS memiliki distribusi yang tidak normal dengan tingkat variasi yang cukup tinggi. Terdapat hubungan positif yang sangat kuat dan signifikan antara nilai pelanggan dan pendapatan tahunan. Model regresi linier sederhana menunjukkan bahwa nilai pelanggan merupakan prediktor yang sangat kuat dalam menjelaskan dan memprediksi pendapatan tahunan startup SaaS. Wawasan penting yang diperoleh dari analisis ini adalah bahwa nilai pelanggan merupakan faktor kunci yang sangat menentukan pendapatan tahunan startup SaaS. 
