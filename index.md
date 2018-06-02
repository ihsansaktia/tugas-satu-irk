## Model dan Simulasi: Menjual Makanan Ringan di Laboratorium Teknik
Modelling adalah sebuah proses membuat model, termasuk komponen pembentuk dan cara model tersebut bekerja. Model ini dibuat menyerupai sebuah sistem di dunia nyata, digunakan untuk membuat analisa prediksi perubahan yang terjadi pada sistem. Simulation adalah mengoperasikan sebuah model untuk menganalisa performa sebuah sistem.  

Sebagai contoh, jika terdapat permasalahan menjual makanan di sebuah gedung bertingkat dengan rute terpendek tapi memiliki keuntungan maksimum. Bisa dimodelkan sebagai sebuah matrix 2D dengan tiap baris sebagai representasi tingkat pada gedung, dan nilai elemen >= 0 yang merepresentasikan pembeli potensial pada sebuah ruangan di tingkat tersebut.  

Simulasi bisa dijalankan dengan mengubah tinggi gedung ataupun jumlah pembeli potensial pada tiap ruangan. Setelah melakukan survey minat pembelian sebuah produk, seorang pengusaha bisa melakukan perhitungan keuntungan maksimum dengan melakukan simulasi pada model yang telah dibuat.  

### Pemodelan

Permasalahan menjual makanan ringan di laboratorium teknik dapat digambarkan dengan mencari rute terpendek dari simpul awal ke simpul akhir sembari mengumpulkan nilai-nilai di tiap simpul yang di kunjungi. Untuk permasalahan ini kita definisikan model laboratorium teknik direpresentasikan dengan sebuah matriks 4x6. Titik awal kita definisikan berada di paling bawah, baris 0 kolom 0. Titik akhir yang berupa lantai di mana kelas sang mahasiswa berada dan ingin dicapai berada di lantai teratas.  

Di tiap cell matriks terdapat nilai-nilai yang merepresentasikan modelnya. Sebuah cell dengan nilai “-1” berada di sebelah kiri dan kanan matriks, hal ini merepresentasikan tangga yang ada di laboratorium teknik Institut Teknologi Bandung. Sebuah cell dengan nilai >= 0 merepresentasikan banyaknya pembeli potensial pada kelas tersebut.  

Oleh karena itu, sebuah laboratorium teknik di Institut Teknologi Bandung dapat dimodelkan sebagai:  

**-1 0 0 0 0 -1**  
-1 4 5 0 1 -1  
-1 0 0 6 4 -1  
**-1** 1 1 0 1 -1  

Dengan titik awal (0,0) berada di kiri bawah dan tujuan akhir adalah lantai paling atas.

Dynamic Programming adalah sebuah teknik yang diciptakan untuk melakukan komputasi yang memperhitungkan beberapa kemungkinan yang ada dengan efisien. Lebih spesifik lagi, jika terdapat sebuah permasalahan yang dapat dibagi menjadi sebuah permasalahan yang lebih kecil, maka Dynamic Programming akan menghitung dan menyimpan solusi dari permasalahan yang lebih kecil untuk membangun solusi pada permasalahan utama.  

Pemrograman dinamis dipilih sebagai strategi penyelesaian masalah ini dikarenakan properti-propertinya yang sesuai. Strategi bruteforce tidak akan mangkus dalam menyelesaikan masalah ini dikarenakan banyaknya upa-masalah yang diulang pencariannya. Sedangkan strategi greedy tidak akan mangkus dalam menyelesaikan masalah ini dikarenakan kecenderungannya untuk jatuh ke maksimum lokal. Strategi pemrograman dinamislah yang memastikan didapatkannya jawaban yang mangkus dan sangkil.  

### Penyelesaian
Implementasi solusi dimulai dengan deklarasi:  
  1.	Variable untuk menyimpan banyak lantai, kelas perlantai, makanan ringan yang akan dijual.  
  2.	Matriks (Banyak Lantai)x(Banyak Kelas + 2) sebagai representasi dari model laboratorium teknik.  
  3.	Vector sebuah Pair <Integer dan Vector sebuah Integer> bernama DP. Integer pada Pair berisi banyaknya langkah yang sudah dilakukan dan Vector sebuah Integer di dalam pair berisi rute dari langkah tersebut. Vector DP ini memiliki 3 dimensi. Dimensi pertama merepresentasikan lantai. Dimensi kedua merepresentasikan datangnya dari tangga kiri atau kanan. Dimensi ketiga merepresentasikan banyaknya makanan ringannya yang tersisa.  
  4.	 Arrah sebuah Vector sebuah Pair<Integer & Integer> bernama pembeliPotensial. Vector ini digunakan untuk mengingat letak dari pembeli potensial pada suatu lantai dan kelasnya.  

Langkah-langkah penyelesaian berupa:  
  1.	Masukan berupa banyaknya lantai, kelas perlantai, makanan ringan yang akan dijual akan diterima.   
  2.	Kemudian sebuah integer sebanyak (banyak lantai X (kelas perlantai + 2)) akan diterima dan dimasukan ke dalam matriks. 
  3.	Selanjutnya, pembeliPotensial diisi berdasarkan matriks.  
  4.	Selanjutnya, sebuah fungsi rekursif pencari solusi dari titik (0,0) dengan total makanan yang akan dijual dipanggil. Fungsi ini akan melakukan:  
    a.	 Pengecekan apakah sudah masuk kasus basis, jika sudah sampai lantai paling atas dan semua makanan ringan sudah terjual maka kembalikan hasilnya dan rutenya. Jika makanan belum terjual habis, maka keluarkan sebuah nilai tak hingga (atau sebuah nilai atas yang didefinisikan).  
    b.	Jika bukan kasus basis, lakukan pengunjungan ke kombinasi kunjungan yang mungkin (diambil dari pembeliPotensial) baik dari tangga kiri maupun tangga kanan dengan cara memanggil fungsi penyelesaian secara rekursif dengan parameter yang sudah disesuaikan.  
    c.	Hasil dari tiap kunjungan dibandingkan nilai langkahnya yang terkecil.  
    d.	Hasil yang terkecil dijadikan nilai pada matriks 3 dimensi DP[lantai saat itu][posisi tangga][banyak makanan tersisa]
    e.	Kembalikan nilai DP[lantai saat itu][posisi tangga][banyak makanan tersisa]  
  5.	Hasil dari pemanggilan fungsi rekursif pencari solusi tersebut lalu cetak.  


### Eksekusi
Masukkan ke dalam program ditebalkan.

Masukkan:
Banyak lantai: **4**  
Kelas perlantai: **4**  
Banyak makanan: **9**  
**-1 0 0 0 0 -1**  
**-1 4 5 0 1 -1**  
**-1 0 0 6 4 -1**  
**-1 1 1 0 1 -1**  

Keluaran:  

Banyak langkah untuk memperoleh hasil maksimum: 7  
Langkah:  
(0,0)->(0,1)->(0,2)->(1,2)->(2,2)->(1,2)->(0,2)->(0,3)

### Analisis
1.	Hasil keluaran merupakan rute paling mangkus dan sangkil dengan langkah terkecil dan seluruh danus makanan ringan terbeli.   
2.	Jika strategi yang digunakan adalah Greedy, program akan terjebak dengan memilih simpul (1,0) yang nampaknya lebih menguntungkan terlebih dahulu.   
3.	Jika menggunakan strategi Bruteforce, akan banyak upa-masalah yang dikalkulasi ulang mengakibatkan tidak mangkusnya program.  
4.	Kekurangan dari program ini adalah diperlukannya pendataan mengenai hasil penjualan hari-hari sebelumnya agar didapatkan senarai pembeli potensial tiap kelas.  

### Kesimpulan  
Penggunaan pemrograman dinamis dalam menyelesaikan masalah rute penjualan danus makanan ringan menghasilkan keluaran yang mangkus dan sangkil. Hanya saja, diperlukan data pembeli potensial tiap kelas terlebih dahulu. Dengan koordinasi antar panitia program kerja sebuah himpunan atau organisasi untuk mendata penjualan tiap harinya agar mendapatkan senarai pembeli potensial, pendekatan ini dapat digunakan untuk memaksimalkan pendapatan dana usaha sembari meminimalkan energi dan waktu yang habis dalam penjualan.  
