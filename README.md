# TUGAS-BESAR-APPLIED-MACHINE-LEARNING
Menggunakan K-Means Clustering untuk segmentasi geografis dan penentuan prioritas penanganan masalah pendidikan Anak Tidak Sekolah (ATS). Dilengkapi deployment Gradio.

## 🎯 Tujuan Utama Proyek

1.  Melakukan pengelompokan (clustering) wilayah di Indonesia berdasarkan tingkat keparahan masalah ATS menggunakan K-Means.
2.  Menentukan zona prioritas penanganan (**Tinggi/Merah, Sedang/Kuning, Rendah/Hijau**) untuk memandu alokasi sumber daya.
3.  Membangun antarmuka aplikasi web interaktif berbasis **Gradio** untuk memberikan status prioritas dan rekomendasi kebijakan secara otomatis.

---

## ⚙️ Metodologi Proyek (CRISP-DM)

Proyek ini disusun secara sistematis mengikuti enam tahapan kerangka kerja **CRISP-DM** (*Cross Industry Standard Process for Data Mining*).

### 1. Business Understanding
* **Masalah:** Sulitnya menentukan prioritas intervensi pendidikan dari data mentah yang besar, menyebabkan kebijakan tidak tepat sasaran.
* **Solusi:** Menggunakan **Clustering** untuk segmentasi wilayah secara otomatis berdasarkan *magnitude* jumlah siswa putus sekolah.

### 2. Data Preparation
* **Data Cleaning:** Memastikan tidak ada *missing value* pada kolom 'Jumlah' ATS.
* **Normalisasi:** Melakukan *scaling* data 'Jumlah' menggunakan **MinMax Scaler** untuk memastikan akurasi perhitungan jarak pada K-Means (Euclidean Distance).

### 3. Modeling (K-Means Clustering)
* **Algoritma:** K-Means Clustering.
* **Penentuan K:** Jumlah optimal *cluster* (K) dicari menggunakan metode Elbow.
* **Hasil Clustering:** Data dikelompokkan menjadi 3 *cluster* utama yang diberi label zona prioritas:
    * **Zona Merah (Prioritas Tinggi):** ATS Sangat Tinggi.
    * **Zona Kuning (Prioritas Sedang):** ATS Sedang.
    * **Zona Hijau (Prioritas Rendah):** ATS Rendah.

### 4. Evaluation
Evaluasi dilakukan dengan menganalisis karakteristik *centroid* setiap *cluster* untuk memverifikasi bahwa pengelompokan memisahkan wilayah berdasarkan tingkat keparahan masalah dengan jelas.

### 5. Deployment (Aplikasi Gradio)
Model yang telah dilatih diterapkan ke dalam antarmuka web interaktif sederhana menggunakan **Gradio**, yang memungkinkan pengguna untuk:

| Input | Output Status | Output Rekomendasi Kebijakan |
| :--- | :--- | :--- |
| Jumlah Anak Tidak Sekolah | **Prioritas Tinggi (Zona Merah)** | **DARURAT!** Perlu intervensi segera. Alokasikan anggaran khusus dan tim *task force*. |
| Jumlah Anak Tidak Sekolah | **Prioritas Sedang (Zona Kuning)** | **PERHATIAN:** Perlu monitoring intensif dan program beasiswa tambahan. |
| Jumlah Anak Tidak Sekolah | **Prioritas Rendah (Zona Hijau)** | **AMAN:** Pertahankan program yang ada, lakukan *maintenance* rutin. |
