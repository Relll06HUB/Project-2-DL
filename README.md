# Deteksi dan Klasifikasi Aktivitas Cyberbullying Mengunakan Multilayer Perceptron (MLP) dengan Teknik Natural Language Processing (NLP) TF-IDF dan Gated Recurrent Unit (GRU) dengan Teknik Natural Language Processing (NLP) Word2Vec (Pre-Trained FastText)

## Gambaran Proyek
Proyek ini bertujuan untuk mendeteksi pola kalimat indikasi aktivitas cyberbullying yang beragam di media sosial sebagai potensi sumber melukai korban pada ruang digital menggunakan metode Multi-Class Classification berbasis Deep Learning sebagai model klasifikasi utama dan NLP sebagai teknik representasi fitur data teks

Dua pendekatan utama yang diimplementasikan dan dibandingkan dalam proyek ini:
- Multilayer Perceptron (MLP) dengan representasi fitur TF-IDF
- Gated Recurrent Unit (GRU) dengan representasi fitur Word2Vec (Pre-Trained FastText)

Proyek ini juga mengeksplorasi, mengevaluasi, dan menganalisis pengaruh pendekatan representasi fitur yang berbeda terhadap kualitas model Deep Learning dalam memahami dan mempelajari konteks makna jenis teks cyberbullying yang berbeda

---

## Tujuan Proyek
- Mengimplementasikan MLP dengan teknik Representasi Teks TF-IDF dan GRU dengan teknik Representasi Teks Word2Vec untuk deteksi dan klasifikasi aktivitas cyberbullying
- Membandingkan kualitas kinerja model menggunakan metrik evaluasi klasifikasi yang relevan
- Mengintepretasi & Menganalisis kualitas kinerja model dari nilai metrik evaluasi yang dihasilkan
- Menganalisis kemampuan generalisasi model terhadap pola data teks cyberbullying
- Meningkatkan kualitas kinerja model melalui proses hyperparameter tuning

---

## Dataset
- **Dataset Name:** Cyberbullying Classification Dataset
- **Sumber:** Kaggle
- **Jumlah Data Setelah Pramosresan (termasuk penghapus nilai duplikat dan null values):** 47,354
- **Jumlah Kelas:** 6 kelas
- **Jumlah Kolom:** 2 kolom fitur
- **Nama Kolom Setelah Pramosresan:**
	- `clean_tweet_text`
	- `cyberbullying_type`

### Kelas label yang digunakan 
- age
- ethnicity
- gender
- religion 
- other_cyberbullying
- not_cyberbullying

### Link Dataset
[Cyberbullying Classification Dataset - Kaggle](https://www.kaggle.com/datasets/andrewmvd/cyberbullying-classification)

### Cara Menggunakan Dataset
1. Download dataset dari link yang disertakan di atas
2. Letakkan folder dalam bentuk zip yang diperoleh pada tempat penyimpanan sesuai kenyamanan
3. Ekstrak folder zip tersebut
4. Ambil file bernama `cyberbullying_tweets.csv` yang diperoleh setelah proses ekstraksi folder zip sebelumnya

---

## Workflow Pipeline

```bash
Koleksi Data
        ↓
Pramosresan Teks
        ↓
Ekstraksi Fitur
(TF-IDF & Word2Vec)
        ↓
Pemisahan Data
        ↓
Pembangunan & Pelatihan Model
(MLP & GRU)
        ↓
Hyperparameter Tuning
        ↓
Evaluasi Model
        ↓
Analisis Hasil
```

---

## Pramosresan Teks
Tahapan Pramosresan Data yang Dilakukan:
- Pengubahan huruf kapital menjadi huruf kecil
- Penghapusan simbol dan karakter spesial
- Tokenisasi
- Penghapusan stopwords
- Lemmatization
- Penghapusan nilai duplikat & null

Tujuan utama adalah mengurangi noise, meningkatkan kualitas data, serta menjaga konsistensi representasi data teks sebelum proses modelling

---

## Ekstraksi Fitur
Dua pendekatan representasi fitur yang digunakan:

### TF-IDF
Digunakan bersama model MLP untuk menghasilkan representasi fitur sparse berbasis frekuensi kata

### Word2Vec (Pre-Trained FastText)
Digunakan bersama model GRU untuk menghasilkan representasi fitur dense berbasis sekuens dan pola konteks semantik

---

## Model Deep Learning

### 1. Multilayer Perceptron (MLP)
Karakteristik:
- Artificial Neural Network berbasis feed-forward neural network
- Mampu mempelajari hubungan fitur non-linear
- Menggunakan representasi fitur TF-IDF

### 2. Gated Recurrent Unit (GRU)
Karakteristik:
- Recurrent Neural Network berbasis sekuens
- Mampu memahami urutan kata dan konteks makna kalimat
- Menggunakan representasi fitur Word2Vec

---

## Pemisahan Data
Dataset dibagi menjadi:
- 70% Data Pelatihan
- 20% Data Validasi
- 10% Data Pengujian

---

## Hyperparameter Tuning
Hyperparameter Tuning dilakukan pada kedua model untuk meningkatkan:
- Stabilitas Proses Pelatihan
- Kemampuan generalisasi model
- Kualitas Kinerja Klasifikasi

Beberapa parameter yang disesuaikan:
- Hidden Layer
- Regularization
- Dropout Tambahan
- Dense Layer Tambahan
- Learning Rate
- Jumlah epoch
- Early Stopping

---

## Metrik Evaluasi
Model dievaluasi menggunakan:
- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

Pendekatan klasifikasi yang digunakan adalah Multi-Class Classification

---

## Rangkuman Hasil Evaluasi Secara Keseluruhan
| Model | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|
| TF-IDF + MLP (Baseline) | 0,763 | 0,759 | 0,763 | 0,760 |
| TF-IDF + MLP (Tuned) | 0,769 | 0,765 | 0,769 | 0,766 |
| Word2Vec + GRU (Baseline) | 0,840 | 0,849 | 0,840 | 0,839 |
| Word2Vec + GRU (Tuned) | 0,847 | 0,856 | 0,847 | 0,845 |

### Insight Utama
- Model **GRU dengan Word2Vec** menghasilkan kualitas kinerja terbaik secara keseluruhan
- Proses **Hyperparameter Tuning** memberikan peningkatan kualitas kinerja pada kedua model

---

## Simpulan
- Model **GRU dengan Word2Vec** lebih efektif dalam deteksi dan klasifikasi data teks cyberbullying daripada model **MLP dengan TF-IDF**
- Model **MLP dengan TF-IDF** menunjukkan indikasi overfitting moderat
- Model **GRU dengan Word2Vec** menunjukkan indikasi generalisasi yang lebih baik
- Model dan teknik representasi teks berbasis sekuens lebih efektif dalam memahami konteks makna teks cyberbullying
- Kelas dengan kompleksitas dan ambiguitas tinggi seperti:
	- `other_cyberbullying`
	- `not_cyberbullying`
	
	masih menjadi tantangan utama bagi keseluruhan model

---

## Perbaikan Pengembangan Kedepannya
- Implementasikan model Deep Learning yang lebih kuat seperti LSTM
- Tingkatkan kualitas data pada kelas dengan kompleksitas dan ambiguitas tinggi dalam dataset
- Eksplorasi dan Implementasi konfigurasi hiperparameter berdasarkan saran global untuk keseluruhan model Deep Learning berikutnya
- Eksplorasi dan Implementasi lebih lanjut teknik persiapan keluncuran model Deep Learning
- Kolaborasi dengan researcher dan ahli di bidang Teknik Informatika berbasis Machine Learning/Deep Learning

---

## Struktur Proyek

```bash
│
├── AOL2code.ipynb
│   Notebook utama berisi keseluruhan proses:
│   pramosresan data, ekstraksi fitur, pelatihan model,
│   hyperparameter tuning, evaluasi, dan analisis hasil
│
├── cyberbullying_tweets.csv
│   Dataset utama klasifikasi cyberbullying
│
├── requirements.txt
│   Daftar dependensi/library yang digunakan
│
├── README.md
│   Dokumentasi proyek	

```

---

## Environment
Pengerjaan project ini dibangun mengunakan bahasa pemograman:
- Python 3.12.13

---

## Requirements

Library utama yang digunakan dalam proyek ini:

```bash
Pandas
NumPy
Scikit-Learn
TensorFlow
NLTK
Matplotlib
Seaborn

```

Dengan setiap versi library utama yang digunakan tersedia dalam `requirements.txt`

---

## Instalasi Dependensi

Install dependency menggunakan file `requirements.txt`:
### 1. Clone Repository

```bash
git clone https://github.com/Relll06HUB/Project-2-DL.git
```

Atau download repository secara manual dalam bentuk ZIP.

---

### 2. Install Dependensi

```bash
pip install -r requirements.txt
```

---

### 3. Persiapkan Dataset
- Download dataset dari link Kaggle yang disediakan
- Ambil file:

```bash
cyberbullying_tweets.csv
```

- Pastikan file dataset diletakan pada lokasi penyimpanan folder yang sama seperti notebook utama

---

### 4. Jalankan Notebook

Buka notebook berikut menggunakan:

- Jupyter Notebook
- JupyterLab
- Google Colab
- VS Code

File notebook:

```bash
AOL2code.ipynb
```

Kemudian jalankan seluruh cell secara berurutan

---

## Reproduksibilitas Percobaan

Untuk menjaga konsistensi hasil eksperimen, proyek ini menggunakan:
- Random Seed = 42
- NumPy Seed = 42
- TensorFlow Seed = 42

Pendekatan tersebut membantu menjaga stabilitas hasil pelatihan dan evaluasi model

---

## Catatan Visualisasi

Visualisasi Hasil evaluasi seperti:
- Bar Chart Accuracy & F1 Score
- Confusion Matrix
- Log Pelatihan (Progress Bar)

tersedia langsung di dalam notebook utama `AOL2code.ipynb`

---

## Catatan Tambahan
- Model GRU memerlukan waktu pelatihan dan sumber daya komputasi yang lebih besar dibandingkan MLP
- Hasil evaluasi dapat sedikit berbeda tergantung perangkat keras dan lingkungan pelatihan
- Hyperparameter Tuning dilakukan dengan mempertimbangkan keterbatasan sumber daya komputasi

---

## Lisensi
- Proyek ini dibuat untuk keperluan akademik dan tidak ditujukan untuk penggunaan komersial atau pengerjaan yang tidak ada hubungan dengan riset
- Dataset mengikuti lisensi dari sumber aslinya (Kaggle)

---

## Author

**Darrell Delrando Tjokro**

Project:
AOL 2 - Deep Learning & Its Applications

