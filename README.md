# SaaS Sales Analytics

### JDSOL-014 Grup 2 (Alfa Isa Dewa)

## **DAFTAR ISI**
1. [Tech](#tech)
2. [Requirements](#requirements)
3. [Instalasi Dengan VsCode](#instalasi-dengan-vscode)
1. [Latar Belakang](#latar-belakang)
2. [Pernyataan Masalah](#pernyataan-masalah)
3. [Data](#data)
4. [Data Understand And Cleaning](#data-understand-and-cleaning)
5. [Data Analisis Dan Visualisasi](#data-analisis-dan-visualisasi)
    - Tren Penjualan
    - Karakteristik Pelanggan
    - Kontribusi Produk dan Polanya
    - Pengaruh Rate Diskon
    - Lokasi Negara Yang Menunjukkan Potensi Pertumbuhan
6. [Kesimpulan Dan Rekomendasi](#kesimpulan-dan-rekomendasi)
7. [Credit](#credit)

## Tech
Analisis ini dibangun dengan:
- [Python 3.12.3] - Adalah salah satu bahasa pemrograman komputer yang biasa dipakai untuk membangun berbagai hal seperti desktop app, mobile app, website, dan lain-lain.
- [Visual Studio Code] - Kode editor gratis yang dibuat untuk membangun web modern, aplikasi cloud, dan aplikasi lain.

### Requirements:
- Python (lebih baik dengan versi sama atau terbaru agar tidak mengalami perubahan atau kendala saat menjalankan file).
- Ekstensi Jupyter Notebook pada Visual Studio Code, atau aplikasi lain yang dapat menjalankan ekstensi file '_.ipynb_'.
- Library sudah terdapat dalam file notebook mulai dari pandas sampai uji statistik (install dengan pip install bila terdapat library yang belum terinstal).

### Instalasi Dengan VsCode:
1. Taruh file Capstone2_AlfaIsaDewa.ipynb ke dalam folder apapun
2. Buka VsCode dan arahkan ke file Capstone2_Alfa.ipynb
3. Taruh file yang dijelaskan di bawah (link _sumber_ pada section Data) pada satu folder yang sama dengan file notebook.


## **LATAR BELAKANG**
**Amazon AWS** (_Amazon Web Service_), salah satu raksasa e-commerce dunia, telah merambah ke layanan SaaS (Software as a Service) untuk memperluas jangkauan bisnisnya. Dengan portofolio produk yang beragam, Amazon SaaS menyediakan solusi berbasis cloud yang mencakup penyimpanan data, analitik, dan layanan kecerdasan buatan. Meskipun telah berhasil menarik sejumlah pelanggan, persaingan ketat di pasar SaaS menuntut Amazon untuk terus meningkatkan strategi penjualannya. Penggunaan pemasaran digital yang lebih agresif dan program insentif bagi pelanggan setia menjadi bagian dari upaya peningkatan penjualan. Dengan pendekatan yang komprehensif ini, Amazon berharap dapat memperkuat posisinya di pasar SaaS global.

![AWS Logo](https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg)

## **Pernyataan Masalah**
Untuk menjawab keinginan dari Amazon AWS, kita akan membutuhkan beberapa pertanyaan pembantu seperti :
- Bagaimana tren penjualan keseluruhan selama periode waktu yang berbeda (misalnya bulanan, tahunan)?
- Bagaimana karakteristik customer SaaS Amazon?
- Produk manakah yang memiliki penjualan dan kontribusi pendapatan tertinggi dan apakah ada pola atau tren musiman dalam penjualan produk?
- Bagaimana tingkat _discount_ mempengaruhi profit transaksi penjualan secara keseluruhan?
- Negara manakah yang menunjukkan potensi pertumbuhan tertinggi berdasarkan data penjualan?

## **Data**
Telah disediakan data yang dikumpulkan oleh perusahaan untuk menjawab pertanyaan masalah di atas. Data tersebut berasal dari: [Sumber](https://www.kaggle.com/datasets/nnthanh101/aws-saas-sales). Dataset ini berisi data transaksi dari perusahaan SaaS yang menjual software penjualan dan pemasaran ke perusahaan lain (B2B). Dalam kumpulan data, setiap baris mewakili satu transaksi/pesanan (9.994 transaksi), dan kolomnya meliputi:
- Row ID    : Pengidentifikasi unik untuk setiap transaksi.
- Order ID  : Pengidentifikasi unik untuk setiap pesanan.
- Order Date : Tanggal saat pesanan dilakukan.
- Date Key : Representasi numerik dari tanggal pemesanan dengan format tahun-bulan-hari.
- Contact Name : Nama orang yang melakukan pemesanan.
- Country : Negara tempat pemesanan dilakukan.
- City : Kota tempat pemesanan dilakukan.
- Region : Wilayah tempat pemesanan dilakukan.
- Subregion : Subwilayah tempat pemesanan dilakukan.
- Customer : Nama perusahaan yang melakukan pemesanan.
- Customer ID : Pengidentifikasi unik untuk setiap pelanggan.
- Industry : Industri tempat pelanggan berada.
- Segment : Segmen pelanggan (SMB, Strategic, Enterprise, dll).
- Product : Produk yang sudah dipesan.
- License : Kunci lisensi untuk produk.
- Sales : Jumlah total penjualan untuk transaksi.
- Quantity : Jumlah total item dalam transaksi.
- Discount : Diskon yang berlaku untuk transaksi.
- Profit : Keuntungan dari transaksi tersebut.

**Informasi Data**
- Dataset SaaS-Sales mempunyai 19 kolom dan 9994 baris.
- Data ini diambil dari tanggal 04-01-2020 sampai 31-12-2023
- Kolom `Row ID` lebih baik dihapuskan karena berisi hanya ID setiap baris, sehingga tidak relevan dalam proses analisis nanti.
- Kolom `License` bisa dihapus saja karena berisikan kode unik tiap baris atau transaksi yang terjadi.
- Kolom `Date Key` bisa dihapus karena hanya representasi tanpa symbol dari kolom `Order Date`

## **Data Understand And Cleaning**
Sebelum melakukan analisis data, kita perlu memahami dataset yang telah disediakan. Di dalam proses _data understanding_ ini akan memberikan informasi apakah ada anomali data di dalam setiap kolom. Jika terdapat anomali, maka kita perlu melakukan _data cleaning_ agar ke depannya dataset yang digunakan menjadi lebih akurat dalam proses analisis data nantinya. Akan dijelaskan langkah yang dilakukan dalam proses _data cleaning_ jika terdapat anomali baik itu secara pengetahuan umum atau metode statistik.

Langkah-langkahnya :
### 1. Data Understanding :
    + Cek Tipe Data
    + Cek Total Data Unik.
    + Cek Rentang Waktu Pengambilan Dataset.
### 2. Data Cleaning :
    + Penanganan _Missing Value_.
    + Data Duplikat.
    + _Miss Spelled_ 
    + Penanganan _Outliers_ 
    + Kolom Kurang Relevan.
    + Penamaan Kolom.

Sebelum dibersihkan, kita memiliki 19 Kolom, namun sekarang hanya menjadi 17 dikarenakan telah menghapus kolom yang kurang relevan seperti `Row ID` dan `Date Key`. Dan sebelum dibersihkan, kita memiliki 9994 baris. Setelah dibersihkan kita memiliki 9842 baris. Kita juga telah membuat kolom yang memiliki nama dengan spasi (' ') didalamnya diganti dengan _underscore_ ('_').

## **Data Analisis Dan Visualisasi**
## 1. Tren Penjualan
Dari grafik-grafik di atas, kita bisa menjawab pertanyaan:
- Bagaimana tren penjualan berdasarkan waktu? (bulan, tahun)
     * Berdasarkan tahun:
          + Tren penjualan selalu meningkat setiap tahun. Hal ini berkaitan dengan dipaksa majunya peradaban teknologi dengan adanya masalah pandemi _covid-19_. Kemungkinan bisa terjadi karena semua orang mendapat perlakuan _stay at home_ di 2020, namun hal ini tidak hanya berhenti di 2020, namun _life style_ baru ini melekat hingga tahun setelahnya.
          + Di situasi seperti ini, Amazon sudah siap akan pasar yang akan datang.
     * Berdasarkan bulan:
          + Tren penjualan tiap bulan di setiap tahun selalu fluktuatif, namun menunjukkan tren yang mirip di setiap tahunnya.
          + Lonjakan pada bulan September terjadi dikarenakan Amazon selalu mengadakan _event_ bernama _AWS Innovate Online Conference_.
          + Lalu pada bulan November dan Desember, Amazon juga selalu membuat _best deals_ yang membuat banyak diskon dengan _event_ November _Black Friday_ dan _event_ natal pada bulan Desember.
          + Hampir semua titik terendah setiap bulan selalu terjadi pada bulan Februari (tahun 2021 bukan Februari yang terendah, tetapi bulan Februarinya masih salah satu yang terendah). Hal ini kemungkinan terjadi karena banyaknya kompetitor, salah satunya adalah _IBM Cloud_ yang memiliki lebih banyak promosi di bulan Februari untuk segmen _Enterprise_.

*catatan kaki : **_AWS Innovate Online Conference_** :
Secara singkat ini adalah _event_ konferensi online **gratis** yang bertujuan untuk membantu para profesional dan berbagai organisasi atau industri untuk mendapatkan pengetahuan tentang teknologi.

### 2. Karakteristik Pelanggan
Dari grafik-grafik yang telah dibuat pada notebook kita dapat menjawab pertanyaan:
- Bagaimana karakteristik mereka?
    - Dari Transaksi:
        + Pelanggan dengan jumlah pembelian yang lebih tinggi (di atas 100) merupakan kontributor utama terhadap total penjualan, sering kali melebihi $20,000 pada _sales_.
        + Pelanggan bervolume tinggi (mereka yang melakukan banyak pembelian) sangat penting untuk mendorong total _sales_.
        + Profitabilitas tidak secara langsung terkait dengan volume penjualan saja, menunjukkan bahwa faktor-faktor lain (misalnya, diskon, jenis pelanggan) mempengaruhi margin keuntungan.
    - Dari _Segment_:
        + Segmen SMB mendominasi penjualan dengan total tertinggi, menunjukkan bahwa usaha kecil dan menengah adalah basis `pelanggan utama`.
        + Segmen Enterprise berkontribusi lebih kecil daripada segmen UKM dan Strategis, namun tetap merupakan bagian penting dari basis pelanggan.
        + Segmen strategis, meskipun lebih sedikit, memberikan porsi penjualan yang signifikan, menunjukkan upaya yang terfokus pada klien bernilai tinggi seperti _Valero Energy_, _American Express_, _Volkswagen_, dan _Allianz_ yang memiliki _Sales_ rata-rata menyentuk $15,000.
    - Dari Industri :
        + Dari sisi industri, sektor _finance_, _energy_, dan _tech_ sangat penting, dengan pelanggan yang sebagian besar berasal dari segmen SBM dan Strategic.
        + Industri kesehatan dan produk konsumen mewakili peluang pertumbuhan, yang mengindikasikan potensi ekspansi di sektor-sektor ini.
        + Pelanggan dari industri ini cenderung mendorong penjualan di masa depan dan harus ditargetkan dengan penawaran khusus.

### 3. Kontribusi Produk Dan Polanya
Dari grafik-grafik pada notebook, kita dapat menjawab pertanyaan :
- Produk manakah yang memiliki penjualan dan kontribusi pendapatan tertinggi dan apakah ada pola atau tren musiman dalam penjualan produk?
    + Produk yang memiliki _Sales_ tertinggi adalah _FinanceHub_. Kombinasi skalabilitas, efisiensi biaya, keamanan, teknologi canggih, jangkauan global, kemampuan integrasi, dan dukungan yang kuat membuat AWS menjadi pilihan yang menarik bagi UKM keuangan. Faktor-faktor ini secara kolektif memungkinkan SMB _Finance_ untuk berinovasi, tumbuh, dan beroperasi secara efisien dengan tetap mempertahankan tingkat keamanan dan kepatuhan yang tinggi.
    + Produk yang berkontribusi tertinggi secara profitabilitas adalah _Data Smasher_. Adalah berbagai alat bantu dan layanan yang terkait dengan pemrosesan data, integrasi, dan analitik. Hal ini wajar saja, karena dimanapun itu, pengolahan data menjadi salah satu kebutuhan penting dalam sebuah usaha dari semua _segment_.
    + Terdapat pola pada tren musiman (bulanan) dalam penjualan produk:
        - Puncak penjualan yang signifikan terjadi sekitar bulan September sampai Desember. Hal ini dapat terjadi karena banyaknya permintaan atau promosi yang sukses pada periode ini. Dikarenakan secara kalender terdapat banyak _event_ yang terjadi pada bulan-bulan tersebut.
        - Pada bulan Feburari sampai Juli, pola dari _sales_ produk terbilang stabil.
    + Terdapat pola pada tren musiman (bulanan) pada profitabilitas produk:
        - Produk seperti Data Smasher dan FinanceHub menunjukkan profitabilitas yang konsisten.
        - Keuntungan mencapai puncaknya secara signifikan pada bulan September sampai Desember, serupa dengan tren _sales_.

### 4. Pengaruh Rate Diskon
Dari analisa di atas kita dapat menjawab pertanyaan :
- Bagaimana tingkat _discount_ mempengaruhi profit transaksi penjualan secara keseluruhan?
    + Tingkat diskon yang lebih tinggi memiliki dampak negatif yang nyata terhadap laba, terutama ketika diskon meningkat melebihi 20%. Hal ini menunjukkan perlunya pertimbangan yang cermat ketika menawarkan diskon tinggi, karena dapat menyebabkan penurunan laba yang signifikan.

### 5. Lokasi Negara Yang Menunjukkan Potensi Pertumbuhan

Dari visualisasi pada notebook, kita dapat menjawab pertanyaan :
- Negara manakah yang menunjukkan potensi pertumbuhan tertinggi berdasarkan data penjualan?
    + Amerika Serikat dan Inggris menunjukkan potensi pertumbuhan yang paling menjanjikan dengan peningkatan penjualan yang substansial.
    + Jepang, selain memimpin di wilayah APJ, juga menunjukkan stabilitas dan pertumbuhan pasar yang kuat.
    + Pasar negara berkembang seperti India dan Brasil menunjukkan potensi ekspansi yang signifikan dengan tren kenaikannya.

## **Kesimpulan Dan Rekomendasi**
- **Kesimpulan :**
    - Tren Penjualan:
        + Dari data di atas, dapat disimpulkan bahwa tren _sales_ terus naik dari tahun ke tahun mulai dari 2020 dengan jumlah transaksi di bawah 2000, menjadi lebih dari 3200 pada tahun 2023. Seiring dengan terus meningkatnya transaksi setiap tahun, namun tren penjualan cenderung sama pada setiap bulannya (selalu naik pada bulan September sampai Desember, dan cenderung stabil pada bulan sebelumnya).
    - Karakteristik Customer:
        + Pelanggan yang melakukan lebih banyak pembelian cenderung membelanjakan lebih banyak secara keseluruhan. Contohnya mulai dari pembelian di bawah _peak_ nya yaitu 100 cenderung sedikit karena harga barangnya yang tergolong tinggi, sehingga _customer_ akan cenderung hanya dapat melakukan pembelian dengan sedikit banyaknya.
        + Segmen SMB (_Small Medium Bussiness_) menjadi segmen dengan persentase terbesar dalam _total sales_ karena berbagai alasan, salah satunya adalah dalam fase pertumbuhan ketika mereka berinvestasi lebih besar pada produk dan layanan untuk meningkatkan skala operasi mereka.
        + Customer teratas dengan ID 1009 memiliki _total sales_ $33936,7.
        + Pelanggan dengan jumlah pembelian yang lebih tinggi umumnya memiliki total penjualan (_total sales_) yang lebih tinggi.
    - Kontribusi Produk:
        + Penjualan (_Sales_) tertinggi diperoleh produk bernama FinanceHub dengan total _sales_ $291749.94.
        + Profit tertinggi diperoleh produk bernama _Data Smasher_ dengan jumlah profit $38895.88.
    - Pengaruh Diskon:
        + Diskon terbesar adalah 80% dan diskon terendah adalah 10%.
        + Mulai tingkat diskon 20% sampai lebih dari 50%, bisa membuat profit penjualan mencapai negatif (merugikan).
    - Negara Dengan Potensi Pertumbuhan:
        + Negara yang menunjukkan perkembangan penjualan tertinggi (_sales_) dari _region_ EMEA adalah Inggris (_United Kingdom_), Region AMER adalah Amerika (_United States_), dan Region APJ adalah Jepang (_Japan_).

- **Rekomendasi :**
    - Promosi bulan-bulan sebelum kuartal ke-4 memiliki total _sales_ yang cenderung rendah, yaitu Januari sampai Agustus. Promosi ini bisa mengikuti _event_ yang ada di bulan tersebut seperti:
        + 24 Januari (Hari Pendidikan Internasional) : Dapat memberikan penawaran khusus seperti diskon 50% dalam rentang 7 hari untuk mengubah akun gratis menjadi akun premium.
        + 21 Maret (International Day for the Elimination of Racial Discrimination, World Poetry Day, International Day of Forests) : Mengadakan _event_ offline di hari ini, untuk mendapatkan _product awarness_ lebih.
        + 1 Mei (International Workers' Day) : Memberikan diskon 20% untuk semua produk dengan kuantitas pembelian di atas 5, dan 30% di atas kuantitas 10.
        + 30 Juli (International Day of Friendship) : Membuat kode refferal dan _reward_ dalam rentang waktu 7 hari untuk pengguna yang berhasil merekrut orang lain.
        + 12 Agustus (International Youth Day) : Membuat _event offline_ di sekolah sampai universitas.
    - Utamakan _customer_ dengan _high sales_ seperti _Valero Energy_, _American Express_, _Volkswagen_, dan _Allianz_
    - Fokus kepada segmen Enterprise, buat sosialisasi pentingnya AWS.
    - Terus jaga produk _FinanceHub_ karena memiliki _total sales_ yang paling tinggi.
        + Namun tidak menutup mata pada produk lain, bisa dilakukan bundling untuk setiap pembelian produk _FinanceHub_, sepert dengan menaikkan 20% harga beli _FinanceHub_ untuk langsung mendapatkan produk lain dengan pilihan produk dengan _sales_ dan _profit_ yang tergolong rendah seperti _ChatbotPlugin_ dan _Marketing Suites_.
    - Kurangi diskon di atas 50%, karena ini akan sangat memberikan dampak, yaitu profit negatif. Maksimalkan diskon di 35% saja untuk hari biasa. Kemudian untuk 1 hari pada hari - hari promosi untuk memberikan diskon di atas 50%. Ini dilakukan untuk mengurangi profit negatif.
    - Untuk kebijakan refund yang merupakan kesalahan pembeli, berikan potongan 20% dari total belinya.
    - Berikan promosi dan event pada negara-negara yang memiliki potensi pertumbuhan terendah. Ikuti tanggal kalender pada negara tersebut untuk menyiapkan event sesuai negara untuk menjaga tren dari pertumbuhan _sales_.
    - Berikan aplikasi dengan tema sakura untuk negara Jepang, dan sepakbola pada negara Brazil yang digunakan bukan sekedar hiasan, namun juga untuk menarik customer yang berasal dari kedua negara tersebut.

Dengan melakukan rekomendasi di atas, diharapkan perusahaan mampu mengepakkan sayap lebih lebar di berbagai negara, dan juga tentunya meningkatkan _sales_ dan _profit_ kedepannya.

### Credit:
Terima kasih untuk Tuhan, orang tua, sahabat, Purwadhika, lecture Purwadhika yang dengan sabar mengajari siswanya.