# Capstone Project IBM Watsonx.ai - NewsClassification using AutoAI

## Latar Belakang
Dalam era informasi yang begitu dinamis, akses cepat dan efisien ke berita adalah kebutuhan yang semakin mendesak. Dengan jumlah berita yang terus bertambah setiap hari, menyusun berita ke dalam kategori yang relevan adalah tugas yang memakan waktu. Oleh karena itu, proyek ini bertujuan untuk mengembangkan sebuah model Machine Learning yang mampu mengklasifikasikan berita berdasarkan judulnya ke dalam berbagai kategori.

## Latar Belakang
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
- [news_kompas.csv](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/news_kompas.csv)

## Hasil dan Analisis
### Hasil Pelatihan Model
#### Perbandingan Pipeline
![](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/images/9.PNG)
Dari hasil pipeline comparison, bisa dilihat bahwa algoritma dengan pipeline 4 memiliki hasil yang lebih optimal diantara pipeline lainnya, berikut analisa mengenai para metrics untuk multiclass classification:
- Accuracy:
Pipeline ke 4 memiliki nilai rasio akurasi yang lebih tinggi dari semua pipeline, dimana pipeline tersebut memiliki jumlah prediksi tepat yang lebih banyak berdasarkan sample input.
- F1 score:
Skor ini merupakan nilai keseimbangan antara precision dan recall.
- Precision:
Mengukur proporsi prediksi positif yang memang benar positif.
- Recall:
Mengukur proporsi positif aktual yang diprediksi dengan tepat.
                    
|               | Micro                    | Macro | Weighted                    |
| ------------- | ------------------------------ | ------------- | ------------------------------ |
| F1 Score      | 0.308       | 0.192     | 0.280       |
| Precision     | 0.308     | 0.255      | 0.290       |
| Recall        | 0.308     | 0.180      | 0.308       |

#### Model evaluation - ROC Curve
![](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/images/ROC%20curve.jpeg)

ROC curve berikut memiliki beberapa aspek untuk dianalisa:
1. ROC Curve terdiri dari true positive rate (TPR) untuk sumbu y dan false positive rate (FPR) untuk sumbu x. Model yang sempurna adalah model yang memiliki nilai TPR 1 dan FPR 0, dimana berarti berhasil mengklasifikasi nilai positif dan negatif dengan  seutuhnya benar.

2. Kasus ini, ROC curve lebih condong ke arah kiri bawah dan kanan atas, mengindikasi bahwa model tersebut memiliki performa yang cukup baik. TPR tinggi mengindikasi bahwa model dapat mengklasifikasi hasil positif dengan benar. FPR rendah mengindikasi model ini tidak membuat prediksi false positive terlalu banyak.

#### Threshold - F1
![](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/images/Threshold%20chart%20(2).jpeg)

Threshold - F1 berikut memiliki sumbu x yang merupakan representasi threshold dan sumbu y yang merupakan representasi nilai F1. Grafik ini menunjukan nilai threshold yang naik dengan nilai F1 yang konstan, lalu beberapa nilai F1 mulai menurun, mengindikasi model ini terlihat lebih konservatif dan tidak memprediksi nilai positif terlalu banyak.

Titik di mana skor F1 mulai menurun adalah titik di mana peningkatan precision sebanding dengan penurunan recall. Ini adalah titik di mana pengklasifikasi menghasilkan terlalu banyak false negative.

#### Threshold - Recall
![](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/images/Threshold%20chart%20(1).jpeg)

Grafik diatas menunjukkan recall untuk satu kelas seiring dengan peningkatan threshold. Ketika threshold meningkat, pengklasifikasi menjadi lebih konservatif dan kecil kemungkinannya untuk memprediksi kejadian positif untuk kelas tersebut. Artinya recall meningkat, namun presisi menurun.

Titik di mana recall mulai berkurang adalah titik di mana pengklasifikasi membuat terlalu banyak false negative untuk kelas tersebut. Ini berarti bahwa pengklasifikasi salah mengklasifikasikan beberapa contoh positif sebagai negatif.

#### Threshold - Precision
![](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/images/Threshold%20chart.jpeg)

Dalam grafik diatas, presisi meningkat seiring dengan peningkatan threshold hingga threshold sekitar 0,6 - 0,9. Setelah itu, presisinya mulai berkurang. Artinya, model menghasilkan lebih banyak false positive seiring dengan peningkatan threshold.

Alasannya adalah model menjadi lebih yakin dengan prediksinya seiring dengan peningkatan threshold. Namun, keyakinan ini tidak selalu dapat dibenarkan, dan model tersebut mulai membuat lebih banyak kesalahan.

#### Precision Recall
![](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/images/Precision%20recall%20curve.jpeg)

Precision recall curve berikut memiliki beberapa aspek untuk dianalisa:
Precision-recall diatas diplot berdasarkan precision untuk sumbu y dan recall untuk sumbu x. Precision berarti bagian nilai positif yang diprediksi dengan benar, recall berarti bagian nilai positif aktual yang diprediksi sebagai positif.
Jika nilai precision tinggi terhadap nilai recall yang rendah, berarti model tersebut tidak membuat banyak prediksi false positive. Tetapi jika nilai recall tinggi terhadap nilai precision yang tinggi, berarti model tersebut mengklasifikasi nilai positif dengan benar.

#### Hasil Prediksi
![](https://github.com/nOwenK/NewsClassification-AutoAI/blob/main/images/1.PNG)

Gambar diatas menunjukkan hasil prediksi untuk multi-class classification. Dari prediksi artikel berita tersebut, tampak beberapa judul berita masuk ke dalam salah satu dari beberapa kategori: regional, money, bola, properti, health, dll.

Hasil prediksi ditampilkan dalam tabel, dengan kolom sebagai berikut:

- **Prediksi**: Kategori prediksi untuk artikel berita.
- **Keyakinan**: Tingkat keyakinan prediksi, dinyatakan dalam persentase.
- **Judul**: Judul artikel berita.
- **Persentase prediksi**: Persentase frekuensi model memprediksi kategori yang benar untuk artikel berita ini dalam data pelatihan.

Tabel tersebut menunjukkan bahwa model tersebut paling yakin dengan prediksinya untuk kategori health dan hype (100%), tetapi model ini kurang yakin dengan prediksinya untuk kategori global (31%).

Secara keseluruhan dari 24 record data, model tersebut memiliki akurasi yang tinggi yaitu 92%. Artinya, model tersebut memprediksi dengan tepat kategori artikel berita sebanyak 92%.

Berikut beberapa observasi tambahan mengenai hasil prediksi:

- Model ini lebih yakin dengan prediksinya untuk artikel berita yang memiliki judul yang lebih menunjukkan kategorinya. Misalnya, model sangat yakin bahwa artikel berita berjudul “Jumlah penumpang MRT naik 142 persen sejak Jakarta Pusat terendam banjir” adalah kategori news, karena judul tersebut memuat kata “jumlah penumpang” (jumlah penumpang) dan “MRT " (Moda Raya terpadu).
- Model tersebut kurang yakin dengan prediksinya untuk artikel berita yang judulnya kurang menunjukkan kategorinya. Misalnya, model tersebut kurang yakin bahwa artikel berita berjudul "uji coba ganjil genap jalur puncak berlangsung pekan ini" adalah tentang kategori money, karena judul tersebut tidak mencantumkan kata kunci yang khusus berkaitan dengan money.
- Akurasi model untuk kategori regional hanya menyentuh persentase dibawah 90% dibandingkan kategori lainnya. Hal ini mungkin terjadi karena kategori regional lebih beragam dan mencakup artikel berita dengan topik yang lebih beragam.

Secara keseluruhan, hasil prediksinya menjanjikan. Model tersebut mampu memprediksi dengan tepat kategori suatu artikel berita dengan tingkat akurasi yang tinggi. Namun masih ada ruang untuk perbaikan khususnya pada kategori regional.



