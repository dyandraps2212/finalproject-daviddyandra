# Prediksi Pembatalan Reservasi Hotel

## Deskripsi Proyek
Proyek ini bertujuan untuk membangun model pembelajaran mesin yang dapat memprediksi kemungkinan pembatalan reservasi hotel (canceled booking) berdasarkan berbagai fitur pelanggan dan karakteristik pemesanan. Model ini dibuat menggunakan data historis reservasi hotel yang mencakup periode tahun 2015–2017.

Proyek ini dilakukan dalam konteks bisnis untuk membantu manajemen hotel dalam mengantisipasi pembatalan, mengoptimalkan strategi penjualan ulang kamar, serta meningkatkan efisiensi operasional.

---

## Tujuan Utama
1. Memprediksi apakah suatu reservasi akan dibatalkan atau tidak.  
2. Mengidentifikasi faktor-faktor penting yang memengaruhi pembatalan reservasi.  
3. Menyediakan insight bagi pengambilan keputusan bisnis terkait strategi mitigasi pembatalan.  

---

## Dataset
Dataset yang digunakan merupakan data historis reservasi hotel dengan fitur seperti:
- Lead Time  
- Waiting List  
- Country  
- Market Segment  
- Distribution Channel  
- Customer Type  
- Deposit Type  
- Special Requests  
- dan fitur-fitur lainnya  

Dataset mencakup dua tipe hotel:
- City Hotel  
- Resort Hotel  

Proyek ini difokuskan pada **City Hotel**.

---

## Metodologi
1. **Preprocessing Data**  
   - Menangani missing values dan data duplikat  
   - Menangani anomali (Lead Time dan Waiting List ekstrem)  
   - Penyederhanaan kategori pada fitur kategorikal seperti Country  
   - Penyeimbangan kelas target (canceled vs not canceled)  
2. **Feature Engineering**  
   - Encoding variabel kategorikal (One-hot dan Target Encoding)  
   - Transformasi log pada fitur dengan distribusi tidak normal  
   - Pembuatan fitur tambahan seperti flag outlier  
3. **Modeling**  
   - Menggunakan algoritma klasifikasi (Random Forest, XGBoost, dll.)  
   - Melakukan tuning hyperparameter untuk meningkatkan performa model  
4. **Evaluasi Model**  
   - Menggunakan metrik Recall, F1-score, PR-AUC, dan Confusion Matrix sebagai fokus utama  
   - Menghindari ketergantungan pada akurasi karena data tidak seimbang  

---

## Metrik Evaluasi
Metrik utama dan pelengkap yang digunakan:
- **Recall (Sensitivity):** Fokus utama untuk meminimalkan false negative.  
- **F1-score:** Menyeimbangkan antara Precision dan Recall.  
- **PR-AUC:** Mengukur performa model terhadap kelas positif (cancel).  
- **ROC-AUC:** Kemampuan model membedakan kelas positif dan negatif secara umum.  
- **Confusion Matrix:** Analisis error (TP, FP, FN, TN).  
- **Accuracy:** Pelengkap, bukan metrik utama karena dataset tidak seimbang.  

---

## Temuan dan Batasan
1. Model cenderung memiliki bias karena fitur bersifat tamu-sentris dan tidak mempertimbangkan kondisi pasar eksternal.  
2. Nilai anomali pada Lead Time dan Waiting List diatasi dengan winsorization (maksimal 99th percentile).  
3. Kategori Country disederhanakan menjadi 5 besar dan kategori Others, yang dapat mengurangi akurasi pada negara tertentu.  
4. Model hanya berlaku untuk City Hotel, tidak disarankan digunakan untuk jenis hotel lain.  
5. Dataset tidak seimbang antara kelas canceled dan not canceled.  
6. Model bersifat probabilistik, bukan kepastian. Hasil prediksi tetap perlu interpretasi bisnis.  
7. Data yang digunakan berasal dari tahun 2015–2017 sehingga hasil model bisa tidak relevan jika diterapkan pada kondisi terbaru.  

---

## Solusi Pengembangan
1. Menambah fitur eksternal (harga kompetitor, tingkat okupansi pasar, event lokal).  
2. Menggunakan pendekatan encoding yang lebih adaptif (target encoding atau embeddings).  
3. Melatih model secara berkala dengan data terbaru.  
4. Menerapkan drift detection (PSI) untuk memantau relevansi model terhadap kondisi terkini.  
5. Menggunakan threshold berbasis biaya (cost-sensitive thresholding) untuk menyeimbangkan risiko FN dan FP.  

---

## Output  
- Model klasifikasi terlatih (dalam format .pkl)
- Laporan metrik performa model (Precision, Recall, F1, PR-AUC, ROC-AUC)
- Visualisasi Confusion Matrix dan Feature Importance
- Analisis faktor utama pembatalan reservasi

---

## Tableau Dashboard  
Dashboard dapat diakses melalui link berikut: https://public.tableau.com/app/profile/dyandra.prakasita/viz/HotelBookingAnalytics_17593115891690/Overview?publish=yes

<img width="1836" height="763" alt="Screenshot (129)" src="https://github.com/user-attachments/assets/be751c78-a992-4fe1-a462-0bdc1e1797cb" />
<img width="1831" height="754" alt="Screenshot (130)" src="https://github.com/user-attachments/assets/0e4d239f-facc-488a-b916-7952e3243676" />
<img width="1832" height="763" alt="Screenshot (131)" src="https://github.com/user-attachments/assets/9a40250a-3828-4a86-8273-de79f972ea9d" />


## Catatan  
Proyek ini dibuat untuk tujuan akademik dan demonstrasi.
Hasil model bersifat probabilistik dan tidak menggantikan keputusan bisnis secara langsung.
Penggunaan model ini dalam konteks operasional harus disertai validasi tambahan dengan data terbaru.

**Penulis**  
David Gosal dan Dyandra Prakasita
Purwadhika Final Project: Hotel Booking Cancellation Prediction
2025
