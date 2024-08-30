# Bank_Marketing_Campaiign
(Supervised Learning-Classification)

NOTE: Terdapat 3 file .ipynb
- main.ipynb merupakan file utama
- experiment_model.ipynb merupakan file yang berisi pengolahan eksperimen model
- model_lanjutan.ipynb merupakan file model improvement dari hasil model pertama

Folder Picture merupakan folder yang berisikan gambar-gambar yang berhubungan dengan analisis.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

- **Context :**  

    Produk keuangan kini semakin beragam, investasi depostito menjadi salah satu produk keuangan yang paling dikenal masyarakat. Mekanismenya adalah pelanggan menyetorkan sejumlah uang ke bank atau lembaga keuangan dan hanya dapat menariknya setelah periode tertentu, dengan imbalan bunga tetap sesuai jumlah deposito. Bagi bank, keuntungan nasabah yang berinvestasi pada deposito antara lain:

    - Sumber dana stabil: deposito menjadi aliran dana yang stabil bagi bank, sehingga memudahkan perencanaan keuangan dan manajemen [likuiditas](https://www.ojk.go.id/id/kanal/perbankan/regulasi/peraturan-ojk/Documents/Pages/POJK-Nomor-18.POJK.03.2016/SAL%20-%20POJK%20Manajemen%20Risiko%20.pdf).

    - Biaya dana rendah: suku bunga deposito lebih rendah dari pembiayaan lainnya, sehingga dapat memberikan biaya dana yang lebih efisien.

    - Pendapatan lebih tinggi: bank dapat memanfaatkan dana deposito untuk pinjaman atau investasi dengan keuntungan yang lebih tinggi, sehingga menghasilkan keuntungan dari selisih bunga.

    - [Diversifikasi](https://www.ocbc.id/id/article/2021/07/12/diversifikasi-adalah) produk: menawarkan deposito yang menarik bagi berbagai jenis nasabah, serta memperluas produk yang tersedia dapat meningkatkan data tarik dari bank.

    - Maintain nasabah: deposito dengan suku bunga kompertitif dapat menarik nasabah baru dan meningkatkan loyalitas nasabah, sehingga mengurangi kemungkin nasabah berpindah bank. Ketika nasabah tidak berpindah ke bank lain, kestabilan pemasukan untuk bank semakin baik.

    Berdasarkan hal yang telah disebutkan diatas, investasi deposito menjadi program yang penting untuk bank. Namun, bank harus terus bersaing untuk mempertahankan dan menarik nasabah. Salah satu strategi efektif untuk mendapatkan nasabah baru adalah melalui marketing campaign melalui telemarketing.

- **Problem Statement :**

    Target dalam konteks ini adalah `deposit`, yang mencerminkan apakah nasabah berinvestasi atau tidak terhadap deposito yang ditawarkan setelah menerima campaign dari telemarketing. Untuk meningkatkan efisiensi dan efektivitas campaign tersebut, bank perlu memprediksi dan mengidentifikasi nasabah yang memiliki kemungkinan tinggi untuk berinvestasi pada deposito ketika ditawarkan campaign via telemarketing. 

- **Goals :**

    Dengan memanfaatkan profil nasabah dan data hasil campaign sebelumnya, bank bertujuan untuk memanfaatkan teknik machine learning untuk menilai probabilitas setiap nasabah yang berpotensi investasi dengan meningkatkan akurasi prediksi. Selain itu, bank ingin mengetahui profil atau faktor apa saja dari nasabah yang memiliki potensi investasi deposito, sehingga dapat membuat campaign yang lebih tepat sasaran.

- **Analytic Approach :**

    Akan dilakukan analisi data untuk menemukan pola yang membedakan nasabah potensial dan tidak, kemudian akan dibangun model klasifikasi yang dapat membantu bank untuk memprediksi probabilitas seorang nasabah yang berpotensial atau tidak.

- **Metric Evaluation :**

    Maka target yang ditetapkan adalah sebagai berikut: 

    - 0: Nasabah tidak potensial melakukan investasi deposito

    - 1: Nasabah potensial melakukan investasi deposito.

    Dari sisi kepentingan false positives dan false negatives dalam kontesk telemarketing untuk investasi deposito, maka didapatkan analisa sebagai berikut:

    1. Definisi Kerugian

        - False Positives: Calon nasabah tidak potensial investasi deposito tapi diprediksi sebagai calon potensial. Kerugian utamanya adalah biaya telemarketing yang dikeluarkan untuk calon nasabah yang tidak potensial.
    
        - False Negatives : Calon yang potensial berinvestasi namuan diprediksi sebagai calon yang tidak potensial. Kerugian utamanya adalah kehilangan potensi pemasukan dari calon nasabah yang sebenarnya potensial.

    2. Analisa Dampak Finansial:

        - False Positives, biaya Telemarketing, yang akan disimulasikan sebagai berikut:

            - [Aplikasi telemarketing](https://qontak.com/harga/) premium untuk 1 bulan adalah Rp.3.499.999 untuk 10.000 nomor aktif.

            - Seorang telemarketer dalam [sehari bisa melakukan panggilan hingga 130 orang](https://www.vice.com/id/article/10-pertanyaan-bikin-penasaran-buat-telemarketer-yang-gigih-menelepon-kita-siang-malam/), namun untuk mempermudah perhitungan anggap saja sehari 100 orang yang ditelpon, maka untuk memaksimalkan kuota aplikasi telemaketing (10.000 nomor aktif), maka dibutuhkan 100 orang telemarketer.

            - Jika [gaji seorang telemarketer](https://www.kitalulus.com/blog/seputar-kerja/tugas-dan-karir-telemarketing/) adalah Rp.3.500.000, maka dalam sebulan dibutuhkan dana Rp.350.000.000 untuk gaji telemarketer.

            - **Total pengeluaran biaya telemaketing** (aplikasi+gaji) adalah  Rp.353.499.000 untuk 10.000 nomor aktif nasabah atau **Rp.35.349,9/bulan untuk satu nasabah**.

        - False Negatives, kehilangan pemasukan dari calon nasabah yang sebenarnya potensial, yang akan disimulasikan sebagai berikut:

            - Mengacu pada [simulasi deposito](https://www.bca.co.id/id/Individu/produk/simpanan/Deposito-Berjangka), maka deposito minimal sesorang adalah Rp.8.000.000, yang jika disimpan selama satu tahun, maka nasabah akan mendapatkan Rp.8.128.000.

            - Dalam bisnis, bank akan memutar dana tersebut untuk mendapatkan keuntungan dari dana tersebut. Misal bank akan meminjamkan uang tersebut kepada nasabah peminjam, maka mengacu pada [simulasi pinjaman personal](https://www.bca.co.id/id/Individu/produk/pinjaman/Pinjaman-Personal), yang apabila akan dikembalikan dalam satu tahun, maka nasabah peminjam harus mengembalikan Rp.8.960.004.
            
            - Berdasarkan simulasi tersebut, maka diperkirakan **keuntungan minimum** bank dari **seorang nasabah yang berinvestasi deposito** adalah RP.832.004/tahun atau **RP.69.333/bulan untuk satu nasabah**.

    3. Efek Jangka Panjang:

        - False POsitives: akan terjadi pemborosan berulang dari telemarketing yang tidak efektif.

        - False Negatives: kehilangan peluang jangka panjang yang dapat mempengaruhi pertumbuhan dan reputasi perusahaan.

    4. Prioritas:

        - False Negatives: mengacu pada keuntungan yang didapatkan oleh bank (yang telah dipaparkan sebelumnya), maka false negatives cenderung lebih keritikal karena artinya bank akan kehilangan potensi pemasukan yang signifikan

        - False POsitives: pentingnya mengurangi atau menghindari pemborosan biaya, tapi dampaknya umumnya lebih rendah daibandingkan kerugian dari kehilangan calon potensial.

    5. Perbandingan Keuntungan dan Biaya berdasarkan simulasi pada point 2:

        - Keuntungan mendapatkan investasi deposito : RP.69.333/bulan untuk satu nasabah
        
        - Kerugian biaya telemarketing : Rp.35.349,9/bulan untuk satu nasabah

    6. Strategi:

        - Meningkatkan akurasi prediksi untuk mengurangi false positives dan false negatives.

        - Analisis biaya dan manfaat dengan cara evealuasi strategi telemarketig secara berkala.

        - Memberikan masukan kepada bank untuk meningkatkan data agar lebih akurat dan segmentasi yang tepat untuk meminimalkan kedua jenis kesalahan tersebut.

    7. Matrix Evaluasi yang pertimbangkan:

        - Recall : mengukur seberapa baik model dalam menangkap calon nasabah potensial untuk investasi deposito, dengan fokus pada mengurangi false negatives. Meskipun efektif untuk menangkap banyak calon potensial, namun matrix ini memiliki resiko terhadap false positives, yang dapat meningkatkan biaya telemarketing tanpa hasil yang diinginkan.

        - F1 Score : menyeimbangkan antara identifikasi calon yang benar-benat potensial dan menghindari melakukan telemarketing yang tidak efektif. Kelebihannya adalah kemampuan untuk menggabungkan keuntungan dari Recall dan Precision, sehingga mengurangi kedua jenis kesalahan. Namun matrix ini tidak dapat sepenuhnya menangani trade-off antara biaya yang terkait dengan false positives dan kehilangan potensi dari false negative.

    8. Kesimpulan:

        - Akan diprioritaskan untuk mengoptimalkan model dalam mendapatkan calon nasabah yang benar-benar potensial sekaligus meminimalkan biaya marketing, sehingga matrix yang akan digunakan adalah F1-Score.

- **Feature dan Hipotesa**

    - Customer profile:

        -	`age` : menunjukkan usia nasabah. Memahami usia nasabah dapat membantu penyesuaian pesan campaign deposito dengan preferensi nasabah. Misalnya, nasabah yang usianya lebih muda mungkin tertarik pada produk yang memiliki resiko dan keuntungan yang lebih tinggi, sementara nasabah yang lebih tua mungkin lebih memilih investasi yang stabil dan resiko rendah seperti deposito.

        -	`job` : menunjukkan jenis pekerjaan nasabah. Hal ini dapat memberikan gambaran tentang stabilitas financial dan kebiasaan menabung nasabah. Profesi dengan pekerjaan yang stabil mungkin cenderung berinvestai, namun akan dilakukan analisa lagi berdasarkan dataset.

        -	`balance`: menunjukkan saldo nasabah. Saldo yang lebih tinggi kenungkinan cenderung memiliki kapasitas finansial dan potensi untuk investasi.
        
        -	`housing`: menunjukkan kepemilikan rumah. Kepemilikan rumah biasanya juga mempengaruhi kebiasaan menabung dan potensi investasi nasabah.

        -	`loan`: informasi status nasabah pada pinjaman. Informasi ini dapat menunjukkan kewajiban potensial dan kemampuan nasabah untuk berinvestasi dalam deposito.

    - Marketing data:

        -	`contact` : Feature ini menunjukkan jenis komunikasi yang digunakan untuk menghubungi nasabah untuk mempengaruhi efektivitas campaign

        -	`month` : Feature ini merupakan bulan terakhir nasabah di hubungi, yang dapapat membantu identifikasi waktu optimal untuk melakukan kontak.

        -	`campaign` : Feature ini akan menunjukkan seberapa sering bank menghubungi klien. 

        -	`pdays` : Feature ini menunjukkan berapa hari telah berlalu sejak nasabah terakhir dihubungi dalam campaign sebelumnya. Interval yang lebih pendek mungkin menunjukkan ketertarikan, sementara interval yang lebih panjang mungkin menunjukkan waktu yang tepat untuk kembali terlibat.
        
        -	`poutcome` : Feature ini merupakan hasil dari campaign sebelumnya, yang dapat memberikan wawasan startegi yang berhasil atau tidak berhasil. Menganalisa feature ini dapat membantu campaign mendatang untuk meningkatkan efektivitas
                                                                        
        -	`deposit` : Merupakan status deposito nasabah, yang menjadi indikator utama keberhasilan campaign.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Kesimpulan dan Rekomendasi:


**Kesimpulan Model 1:**

- F1-Score dangan CatBoostClassifier menunjukkan peforma 70% untuk kategori nasabah potensial.

- Learning Curves : stabil dengan bertambahnya data, meskipun ada indikasi overfitting pada data yang lebih sedikit.

- Feature importance : `balance`, `contact_unknown`, `cat_age` merupakan fitur-fitur berpengaruh.

- Fitur poutcome_unknown harus diperhatikan dan dapat memerlukan perbaikan lebih lanjut

- Confusion Matrix:

    - TP : 466, TN: 670, FP : 145, FN : 252

    - Net Benefit : Rp. 9.663.813,5

    - Penghematan : 90.5%

**Rekomendasi Model 1:**

- Untuk modeling berikutnya mungkin dapat dilakukan perbaikan di kategori potensial, mungkin melalui penyesuaian threshold ataupun hypertuning lebih dalam lagi, apabila memungkinkan gunakan GridSearch.

- Untuk Bank, dibutuhkan perbaikan value dalam input data. Pastikan data akurat, dengan mewarning pengisian 'unknown' atau 'other'. Inputan yang valid akan menghasilkan model machine yang pasti akan lebih baik.

- Dari model 1 kita sudah dapat mendeteksi nasabah-nasabah mana yang potensial, sehingga Bank dapat memanfaatkan data tersebut untuk menawarkan produk deposito dengan lebih tepat sasaran.


**Kesimpulan Model 2:**
- F1-Score dangan RandomForest menunjukkan peforma 82% untuk kategori nasabah potensial, yang menunjukkan peforma sangat baik setelah menghapus `poutcome` dengan value 'unknown'.

- Learning Curves : stabil dengan bertambahnya data, tanpa indikasi overfitting.

- Penanganan data imbalance: Menangani data tidak seimbang dengan cukup baik, namun mungkin membutuhkan teknik tambahan yang dapat meningkatkan deteksi kelas negatif.

- Feature importance : `poutcome_success`, `housing_yes`, `pdays`, dan `balance` merupakan fitur-fitur berpengaruh.

- Confusion Matrix:

    - TP : 225, TN: 83, FP : 44, FN : 41

    - Net Benefit : Rp. 11.224.195,4

    - Penghematan : 88.8%

- Model 2 menunjukkan bahwa data yang lebih valid, dapat menghasilkan peforma yang lebih baik. Sehingga memang penting untuk menggunakan data yang valid walaupun jumlah data minim.

**Rekomendasi Model 2:**

- Penanganan data imbalance: explorasi kembali teknink-teknik handling data imbalance agar peforma jadi lebih baik.

- Tingkatkan akurasi pada rentang probabilitas rendah, mungkin dengan cara menambahkan data valid dan menyesuaikan threshold untuk hasil yang lebih baik.

- Untuk Bank, optimalkan kampanye telemarketing kepada nasabah yang sudah terdeteksi potensial dan sesuaikan penawaran berdasarkan domain knowledge yang tepat sasaran pada target.

**Perbandingan Model 1 vs Model 2:**

- Model 1 menunjukkan peforma baik dengan penghematan biaya yang tinggi, namun memiliki ruang untuk perbaikan pada deteksi nasabah potensial dan pengelolaan data. Jika Bank ingin fokus pada penghematan biaya maksimal dan model stabil, serta mentolelir inputan 'unknown' pada `poutcome`, maka model 1 merupakan model yang lebih tepat dibandingkan model 2.

- Model 2 menunjukkna peforma yang sangat baik setelah penghapusan `poutcome` dengan value 'unknown' dan penanganan data imbalance yang cukup baik. Meskipun efisiensinya dalam penghematan lebih rendah dibandiingkan model 1, model ini tetap memberikan hasil yang solid dan memerlukan penyesuaian lebih lanjut untuk akurasi probabilitas rendah. Jika Bank ingin beranjak pada maturity leval data yang lebih baik dengan tidak mentolelir inputan 'unknown' pada `poutcome` untuk mendeteksi nasabah potensial deposito, maka model 2 merupakan model yang lebih tepat dibandingkan model 1.

- Penggunaan Model 1 dan Model 2 akan menjadi tepat jika didasari pada priritas yang lebih spesifik, kebutuhan bisnis dari Bank, serta kemampuan teknologi yang ada yang dapat dilihat dari parameter biaya dan waktu. 

**Rekomendasi untuk Bank:**

- Investasi dalam pengumpulan dan pengelolaan daya mungkin dapat menjadi alternatif untuk meningkatkan kualitas data, sehingga secara tidak langsung dapat meningkatkan akurasi model.

- Bank dapat menambahkan feature-feature informasi nasabah terkait kepentingan deposito. Hal ini dibuktikan oleh [sumber](https://colab.research.google.com/drive/1ezBwEtMX5I4L_01MGYezRvuvGkEad4pW?usp=share_link#scrollTo=yyUy-p3mptGR), dimana pemodelan machine untuk mendeketsi nasabah potensial investasi dapat mencapai diatas 90% dengan feature-feature tambahan terkait nasabah dan data marketing.
