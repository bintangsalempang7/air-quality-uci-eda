# Analisis Data Eksploratif (EDA): Air Quality Dataset (UCI)

Repositori ini berisi proyek **Exploratory Data Analysis (EDA)** yang komprehensif terhadap dataset kualitas udara perkotaan dari *UCI Machine Learning Repository*. Analisis mencakup tahapan pemahaman data, pembersihan dan prapemrosesan data deret waktu (*time-series*), analisis statistik univariat dan bivariat, hingga reduksi dimensi dan pengelompokan (*clustering*) multivariat.

---

## 📌 Deskripsi Dataset

* **Sumber Dataset:** [UCI Machine Learning Repository - Air Quality Data Set](https://archive.ics.uci.edu/dataset/360/air+quality)
* **Referensi Asli:** S. De Vito et al. (2008), *On field calibration of an electronic nose for benzene estimation in an urban pollution monitoring scenario*, Sensors and Actuators B: Chemical.
* **Periode & Lokasi:** Maret 2004 – April 2005 (pencatatan per jam) di area perkotaan dengan tingkat lalu lintas padat di Italia.
* **Dimensi Awal:** 9.357 observasi valid (setelah pembersihan baris kosong) dan 15 atribut (tanggal, waktu, 5 respons sensor kimia oksida logam `PT08.S1–S5`, 5 konsentrasi referensi bersertifikat `(GT)`, serta 3 parameter meteorologi: suhu, kelembapan relatif, dan kelembapan absolut).

---

## 🗂️ Struktur Analisis dalam Notebook

Notebook disusun secara sistematis ke dalam beberapa tahapan utama:

| Bagian | Tahapan Analisis | Ringkasan Aktivitas |
| :--- | :--- | :--- |
| **A** | **Data Understanding** | Pemeriksaan dimensi, tipe data, penyusunan kamus variabel, deteksi duplikat, dan identifikasi nilai *missing* berkode `-200`. |
| **B** | **Data Preparation** | Penghapusan variabel dengan *missing values* ekstrem (`NMHC(GT)` > 90%), imputasi *time-series* (interpolasi linear untuk *gap* $\le$ 6 jam & median per jam untuk *gap* panjang), analisis *outlier* (metode IQR), serta *feature engineering* variabel kategorik turunan. |
| **C** | **Analisis Univariat** | Distribusi statistik deskriptif, kemencengan (*skewness*), dan visualisasi variabel numerik maupun kategorik. |
| **D** | **Analisis Bivariat** | Korelasi antar polutan dan respons sensor (numerik–numerik), uji asosiasi antar kategori (kategorik–kategorik), serta perbandingan tingkat polusi berdasarkan periode waktu dan musim (numerik–kategorik). |
| **E** | **Analisis Multivariat** | Standardisasi fitur, reduksi dimensi menggunakan **Principal Component Analysis (PCA)**, dan segmentasi pola kualitas udara menggunakan **K-Means Clustering** (evaluasi *Elbow* & *Silhouette Score*). |

---

## 🛠️ Fitur Kategorik Turunan (*Feature Engineering*)

Untuk memperkaya analisis pola waktu dan kondisi lingkungan, beberapa variabel kategorik baru dibentuk dari data mentah:
* `day_type` *(Nominal)*: Hari kerja (*Weekday*) vs. Akhir pekan (*Weekend*).
* `time_period` *(Ordinal)*: Dini hari (`00–05`), Pagi (`06–11`), Siang (`12–17`), dan Malam (`18–23`).
* `season` *(Nominal)*: Musim Semi, Panas, Gugur, dan Dingin (berdasarkan iklim belahan bumi utara).
* `CO_level` *(Ordinal)*: Rendah, Sedang, Tinggi, dan Sangat Tinggi (berdasarkan kuartil `CO(GT)`).
* `T_category` *(Ordinal)*: Dingin, Sejuk, Hangat, dan Panas (berdasarkan ambang batas suhu domain).

---

## 💻 Teknologi & Pustaka (*Libraries*)

Proyek ini dikembangkan menggunakan **Python 3** (dijalankan di Google Colab) dengan pustaka utama berikut:
* **Manipulasi Data:** `pandas`, `numpy`
* **Visualisasi Data:** `matplotlib`, `seaborn`
* **Statistika & Machine Learning:** `scipy`, `scikit-learn` (`StandardScaler`, `PCA`, `KMeans`, `silhouette_score`)

---
