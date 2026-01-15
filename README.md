1. Latar Belakang
Google Play Store menyediakan ribuan ulasan pengguna yang berisi opini terkait kualitas aplikasi, seperti performa, bug, dan fitur.
Jumlah ulasan yang besar menyulitkan analisis manual sehingga diperlukan sistem otomatis untuk mengklasifikasikan sentimen ulasan menjadi negatif, netral, dan positif.

Google Play Store merupakan salah satu platform utama untuk mengunduh aplikasi di perangkat Android,
di mana pengguna dapat memberikan ulasan terkait pengalaman mereka dalam menggunakan aplikasi tersebut (Prasetya, 2025)

Proyek ini bertujuan membangun sistem analisis sentimen berbasis deep learning (LSTM) 
menggunakan data hasil scraping mandiri dari Google Play Store serta mengevaluasi performanya berdasarkan akurasi data testing. 

Long-Short Term Memory (LSTM) merupakan salah satu jenis Machine Learning berbasis pendekatan Recurrent Neural Network 
yang dapat memprediksi kondisi mesin saat ini dengan menggunakan spark mesin pengolah data skala besar (Wisyaldin et al., 2020)

2. Pemrosesan Data
1. Scraping Data
Data diambil langsung dari Google Play Store menggunakan library google-play-scraper. Informasi yang diambil meliputi:
content → teks ulasan
score → rating (1–5)
Data dikumpulkan hingga > 3.000 ulasan dan disimpan dalam format CSV (dataset_scraping.csv).

2. Data Cleaning
Tahapan pembersihan data yang sesuai dengan kode:
- Menghapus data kosong
- Mengonversi teks menjadi huruf kecil
- Menghapus URL
- Menghapus karakter non-alfabet
- Menghapus spasi berlebih

3. Preprocessing
Dilakukan preprocessing Bahasa Indonesia menggunakan:
Stopword Removal → NLTK (stopwords Indonesia)
Stemming → Sastrawi
Teks bersih disimpan ke kolom clean_review.

4. Pelabelan Data
Pelabelan dilakukan otomatis dari rating:
1–2 → Negatif
3 → Netral
4–5 → Positif
Label dikonversi ke numerik menggunakan LabelEncoder.

5. Model
Model yang digunakan adalah Long Short-Term Memory (LSTM).
Arsitektur Model:
Embedding (5000, 128)
→ LSTM (64 unit)
→ Dense (3 neuron, Softmax)

Parameter:
Optimizer: Adam
Loss: Categorical Crossentropy
Epoch: disesuaikan hingga konvergen

6. Hasil
Hasil Training & Testing:
Metrik	Nilai
Akurasi Training	= ± 89%
Akurasi Testing = ± 90.33%
Loss Testing	= ± 0.33
Model memenuhi seluruh kriteria tugas karena akurasi testing > 85% dan menggunakan deep learning.

Daftar Pustaka

•	Prasetya, A. (2025). Analisis Sentimen Ulasan Gojek 
Pada Google Play Store Menggunakan Metode Naïve Bayes. 
Jurnal Nasional Komputasi Dan Teknologi Informasi (Jnkti), xx(xx), 1–8.

•	Wisyaldin, M. K., Luciana, G. M., & Pariaman, H. (2020). 
Pendekatan Long Short-Term Memory untuk Memprediksi Kondisi Motor 10 kV 
pada PLTU Batubara. Kilat, 9(2), 311–318. https://doi.org/10.33322/kilat.v9i2.997
