# Capstone Project IBM Watsonx.ai - NewsClassification using AutoAI

### Latar Belakang
Dalam era informasi yang begitu dinamis, akses cepat dan efisien ke berita adalah kebutuhan yang semakin mendesak. Dengan jumlah berita yang terus bertambah setiap hari, menyusun berita ke dalam kategori yang relevan adalah tugas yang memakan waktu. Oleh karena itu, proyek ini bertujuan untuk mengembangkan sebuah model Machine Learning yang mampu mengklasifikasikan berita berdasarkan judulnya ke dalam berbagai kategori.

### Latar Belakang
Laporan ini bertujuan untuk menjelaskan metode, proses, dan hasil dari proyek pengembangan model Machine Learning untuk mengklasifikasikan berita berdasarkan judulnya. Dengan laporan ini, dijelaskan bagaimana model machine learning yang dibuat menggunakan salah satu service di platform IBM, yaitu watsonx.ai AutoAI, yang dapat membantu pengguna media, berita antusias, dan developer dalam mengakses dan mengelola berita dengan lebih efisien.

## Implementasi

### Data yang Digunakan
Data yang digunakan dalam proyek ini berasal dari dataset berita dari media kompas, dimana judul-judul berita sudah diklasifikasi ke berbagai kategori seperti, properti, bola, otomotif, health, dan lainnya. Dataset ini diambil dari website Kaggle, dimana dataset tersebut berisi koleksi berita dari media kompas untuk seluruh kategori di tahun 2021. https://www.kaggle.com/datasets/yusriyahim/kompas-articles-full-text-category-link-time

### Setup IBM Watsonx
Sebelum bisa menggunakan servis utama IBM watsonx, ada beberapa servis yang harus disiapkan di platform IBM Cloud, yaitu 
- Watson Machine Learning with (Auto AI)
- Watson Studio  
- Cloud Object Storage 

### Setup AutoAI
Setelah mendaftarkan ketiga layanan di IBM cloud, langkah selanjutnya adalah mulai membuat machine learning secara otomatis menggunakan AutoAI.
- [guideline.pdf](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/IBM%20Watsonx.ai%20-%20guideline.pdf)

### Hasil dan Analisis

![](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/1.PNG)

> Klasifikasi multi kelas dari beberapa sample input

