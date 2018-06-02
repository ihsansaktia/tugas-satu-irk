## Model dan Simulasi: Menjual Makanan Ringan di Laboratorium Teknik
Modelling adalah sebuah proses membuat model, termasuk komponen pembentuk dan cara model tersebut bekerja. Model ini dibuat menyerupai sebuah sistem di dunia nyata, digunakan untuk membuat analisa prediksi perubahan yang terjadi pada sistem. Simulation adalah mengoperasikan sebuah model untuk menganalisa performa sebuah sistem.  

Sebagai contoh, jika terdapat permasalahan menjual makanan di sebuah gedung bertingkat dengan rute terpendek tapi memiliki keuntungan maksimum. Bisa dimodelkan sebagai sebuah matrix 2D dengan tiap baris sebagai representasi tingkat pada gedung, dan nilai elemen >= 0 yang merepresentasikan pembeli potensial pada sebuah ruangan di tingkat tersebut.  

Dynamic Programming adalah sebuah teknik yang diciptakan untuk melakukan komputasi yang memperhitungkan beberapa kemungkinan yang ada dengan efisien. Lebih spesifik lagi, jika terdapat sebuah permasalahan yang dapat dibagi menjadi sebuah permasalahan yang lebih kecil, maka Dynamic Programming akan menghitung dan menyimpan solusi dari permasalahan yang lebih kecil untuk membangun solusi pada permasalahan utama.

Simulasi bisa dijalankan dengan mengubah tinggi gedung ataupun jumlah pembeli potensial pada tiap ruangan. Setelah melakukan survey minat pembelian sebuah produk, seorang pengusaha bisa melakukan perhitungan keuntungan maksimum dengan melakukan simulasi pada model yang telah dibuat.  

Permasalahan ini dapat digambarkan dengan mencari rute terpendek dari simpul awal ke simpul akhir sembari mengumpulkan nilai-nilai di tiap simpul yang di kunjungi. Untuk permasalahan ini kita definisikan model laboratorium teknik direpresentasikan dengan sebuah matriks 4x6. Titik awal kita definisikan berada di paling bawah, baris 0 kolom 0. Titik akhir yang berupa lantai di mana kelas sang mahasiswa berada dan ingin dicapai berada di lantai teratas.  

Di tiap cell matriks terdapat nilai-nilai yang merepresentasikan modelnya. Sebuah cell dengan nilai “-1” berada di sebelah kiri dan kanan matriks, hal ini merepresentasikan tangga yang ada di laboratorium teknik Institut Teknologi Bandung. Sebuah cell dengan nilai >= 0 merepresentasikan banyaknya pembeli potensial pada kelas tersebut.  

Oleh karena itu, sebuah laboratorium teknik di Institut Teknologi Bandung dapat dimodelkan sebagai:  

-1 0 0 0 0 -1
-1 4 5 0 1 -1
-1 0 0 6 4 -1
-1 1 1 0 1 -1

Dengan titik awal (0,0) berada di kiri bawah berwarna merah dan tujuan akhir adalah lantai paling atas berwarna biru.

Pemrograman dinamis dipilih sebagai strategi penyelesaian masalah ini dikarenakan properti-propertinya yang sesuai. Strategi bruteforce tidak akan mangkus dalam menyelesaikan masalah ini dikarenakan banyaknya upa-masalah yang diulang pencariannya. Sedangkan strategi greedy tidak akan mangkus dalam menyelesaikan masalah ini dikarenakan kecenderungannya untuk jatuh ke maksimum lokal. Strategi pemrograman dinamislah yang memastikan didapatkannya jawaban yang mangkus dan sangkil.  
