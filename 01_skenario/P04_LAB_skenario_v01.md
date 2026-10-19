<!-- Deskripsi skenario -->

Skenario berikut merupakan bahan latihan yang ditetapkan untuk jobsheet, bukan hasil pengumpulan kebutuhan laboratorium nyata. Skenario ini melanjutkan potongan model Pertemuan 3. Selain mahasiswa, dosen juga meminjam peralatan laboratorium untuk kegiatan praktikum dan penelitian.
Mahasiswa dan dosen sama-sama dapat melihat ketersediaan peralatan dan mengajukan peminjaman.
Petugas laboratorium mengelola data peralatan: menambah peralatan baru, mengubah data peralatan, dan menghapus data peralatan yang tidak lagi dipakai. Setelah peminjaman disetujui dan alat diambil, petugas mencatat pengembalian peralatan.
Pada saat mencatat pengembalian, petugas memeriksa dan mencatat kondisi peralatan.
Dua use case utama pada potongan model ini, Ajukan Peminjaman dan Catat Pengembalian Peralatan, ditunjukkan realisasinya oleh collaboration yang bersesuaian.
Seluruh fungsi Pertemuan 3 tetap berlaku dan tetap digambar: pemeriksaan ketersediaan di dalam pengajuan, pencetakan bukti pengajuan oleh mahasiswa, proses keputusan peminjaman oleh petugas, dan laporan peminjaman untuk kepala laboratorium.
Diagram Pertemuan 4 adalah diagram Pertemuan 3 yang ditambah, bukan diagram baru yang menggantikannya.

+.....................+..............................................+....................................................................................+
|.Aktor...............|.Kedudukan....................................|.Tujuan.terhadap.sistem.............................................................|
+.....................+..............................................+....................................................................................+
|.Peminjam............|.Umum.(general) baru.pada Pertemuan.4.........| Peran umum bagi peminjam peralatan Mewariskan fungsinya kepada Mahasiswa dan Dosen |
+.....................+..............................................+....................................................................................+
|.Mahasiswa...........|.Khusus dari Peminjam,.tetap dari.Pertemuan.3 |.Melihat.ketersediaan.dan.mengajukan peminjaman.(diwarisi.dari.Peminjam)............|
|.....................|..............................................|.ditambah.mencetak.bukti.pengajuan sebagai.asosiasi.khususnya.sendiri...............|
+.....................+..............................................+....................................................................................+
|.Dosen...............|.Khusus.dari Peminjam baru pada.Pertemuan.4...|.Melihat.ketersediaan.dan.mengajukan peminjaman.(diwarisi.dari.Peminjam)............|
+.....................+..............................................+....................................................................................+
|.Petugas.Laboratorium|.Tetap.dari.Pertemuan.3.......................|.Mengelola.data.peralatan,.memproses keputusan.peminjaman,.dan.mencatat.pengembalian|
|.....................|..............................................| peralatan..........................................................................|
+.....................+..............................................+....................................................................................+
|.Kepala.Laboratorium.|.Tetap.dari.Pertemuan.3.......................|.Melihat.laporan.peminjaman.........................................................|
+.....................+..............................................+....................................................................................+

Mahasiswa adalah bentuk khusus dari Peminjam, dan Dosen adalah bentuk khusus dari Peminjam. Alasan: keduanya berbagi fungsi yang sama, yaitu melihat ketersediaan peralatan dan mengajukan peminjaman.
• Asosiasi ke LAB-UC01 dan LAB-UC03 digambar satu kali, yaitu dari Peminjam. Jangan menggambar garis yang sama dari Mahasiswa dan dari Dosen.
• Asosiasi Mahasiswa ke LAB-UC05 Cetak Bukti Pengajuan tidak ikut dipindahkan dan tidak dihapus, karena fungsi itu khusus mahasiswa. Asosiasi ini menjadi contoh asosiasi tambahan milik aktor khusus.
• Periksa arah panah pada gambar: ujung segitiga kosong harus menempel pada Peminjam, bukan pada Mahasiswa dan bukan pada Dosen. Karena Peminjam digambar di tengah, panah Mahasiswa mengarah ke bawah dan panah Dosen mengarah ke atas; keduanya berakhir pada Peminjam.

<!-- Langkah 3 Susun katalog use case-->

===================================================================================================================================================================|
| ID ......| Nama Use Case ................| Peran dalam Model .................................................................................| Sumber Kebutuhan |
===================================================================================================================================================================|
| LAB-UC01 | Lihat Ketersediaan Peralatan .| Tetap dari Pertemuan 3; fungsi aktor umum Peminjam ................................................| LAB-R01, LAB-R07 |
| LAB-UC02 | Kelola Data Peralatan ........| Tetap dari Pertemuan 3; use case UMUM bagi LAB-UC08, LAB-UC09, LAB-UC10, LAB-UC11, LAB-UC12 ........| LAB-R02, LAB-R08|
| LAB-UC03 | Ajukan Peminjaman ............| Tetap dari Pertemuan 3; fungsi aktor umum Peminjam; menyertakan LAB-UC04; direalisasikan LAB-CO01 | LAB-R03, LAB-R07 .|
| LAB-UC04 | Periksa Ketersediaan .........| Tetap dari Pertemuan 3; perilaku yang disertakan LAB-UC03 .........................................| LAB-R03 .........|
| LAB-UC05 | Cetak Bukti Pengajuan ........| Tetap dari Pertemuan 3; tambahan bersyarat pada LAB-UC03 melalui «extend» .........................| LAB-R04 .........|
| LAB-UC06 | Proses Keputusan Peminjaman ..| Tetap dari Pertemuan 3; fungsi utama petugas ......................................................| LAB-R05 .........|
| LAB-UC07 | Lihat Laporan Peminjaman .....| Tetap dari Pertemuan 3; fungsi utama kepala laboratorium ..........................................| LAB-R06 .........|
| LAB-UC08 | Tambah Data Peralatan ........| Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02 ..............................................| LAB-R08 .........|
| LAB-UC09 | Ubah Data Peralatan ..........| Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02 ..............................................| LAB-R08 .........|
| LAB-UC10 | Hapus Data Peralatan .........| Baru pada Pertemuan 4; use case KHUSUS dari LAB-UC02 ..............................................| LAB-R08 .........|
| LAB-UC11 | Catat Pengembalian Peralatan .| Baru pada Pertemuan 4; fungsi utama petugas; direalisasikan LAB-CO02; KHUSUS dari LAB-UC02 ........| LAB-R09 .........|
| LAB-UC12 | Periksa Kondisi Peralatan ....| Baru pada Pertemuan 4; perilaku yang disertakan LAB-UC11; KHUSUS dari LAB-UC02 ....................| LAB-R10 .........|
===================================================================================================================================================================|

<!-- langkah 4 Tetapkan generalization aktor-->

Mahasiswa adalah bentuk khusus dari Peminjam, dan Dosen adalah bentuk khusus dari Peminjam. Alasan: keduanya berbagi fungsi yang sama, yaitu melihat ketersediaan peralatan dan mengajukan peminjaman.
• Asosiasi ke LAB-UC01 dan LAB-UC03 digambar satu kali, yaitu dari Peminjam. Jangan menggambar garis yang sama dari Mahasiswa dan dari Dosen.
• Asosiasi Mahasiswa ke LAB-UC05 Cetak Bukti Pengajuan tidak ikut dipindahkan dan tidak dihapus, karena fungsi itu khusus mahasiswa. Asosiasi ini menjadi contoh asosiasi tambahan milik aktor khusus.
• Periksa arah panah pada gambar: ujung segitiga kosong harus menempel pada Peminjam, bukan pada Mahasiswa dan bukan pada Dosen. Karena Peminjam digambar di tengah, panah Mahasiswa mengarah ke bawah dan panah Dosen mengarah ke atas; keduanya berakhir pada Peminjam

========================================================================================================================================================================|
| Kelompok .........................|Isi ...............................................................................................................................|
========================================================================================================================================================================|
| Tetap sama dari Pertemuan 3 ......| Aktor Mahasiswa, Petugas Laboratorium, dan Kepala Laboratorium; use case LAB-UC01 sampai LAB-UC07; relasi «include» LAB-UC03 ke ..|
|...................................| LAB-UC04; relasi «extend» LAB-UC05 ke LAB-UC03 lengkap dengan condition [mahasiswa memilih cetak] dan extension point Bukti ......|
|...................................| pengajuan tersedia; asosiasi Petugas Laboratorium ke LAB-UC02 dan LAB-UC06; asosiasi Kepala Laboratorium ke LAB-UC07; asosiasi....|
|...................................| Mahasiswa ke LAB-UC05. ...........................................................................................................|
| Berubah karena generalization ....| Asosiasi ke LAB-UC01 dan LAB-UC03 yang pada Pertemuan 3 digambar dari Mahasiswa kini digambar satu kali dari Peminjam. Fungsi ....|
|...................................| mahasiswa tidak hilang: mahasiswa mewarisinya dari Peminjam. Inilah satu-satunya perubahan garis pada diagram lama, dan alasannya.|
|...................................| adalah aturan generalization, bukan penghapusan fungsi. ..........................................................................|
| Ditambah pada Pertemuan 4 ........| Aktor Peminjam dan Dosen; dua generalization aktor; use case LAB-UC08, LAB-UC09, LAB-UC10 beserta tiga generalization use case ke |
|...................................| LAB-UC02; use case LAB-UC11 dan LAB-UC12 beserta relasi «include» di antara keduanya dan asosiasi Petugas Laboratorium ke LAB-UC11|
|...................................| collaboration LAB-CO01 dan LAB-CO02 beserta dua relasi realization. ..............................................................|
========================================================================================================================================================================|

<!-- langkah 5 Tetapkan generalization use case -->

LAB-UC08, LAB-UC09, dan LAB-UC10 adalah bentuk khusus dari LABUC02 Kelola Data Peralatan. Alasan: ketiganya adalah bentuk khusus pengelolaan data peralatan.

<!-- langkah 6 Tetapkan collaboration dan realization -->

|====================================================================================================|
| ID ......| Nama collaboration (sama dengan nama use case) | Use case yang direalisasikan ..........|
|====================================================================================================|
| LAB-CO01 | Ajukan Peminjaman .............................| LAB-UC03: Ajukan Peminjaman ...........|
| LAB-CO02 | Catat Pengembalian Peralatan ..................| LAB-UC11: Catat Pengembalian Peralatan |
|====================================================================================================|
alasannya: kedua use case tersebut adalah use case utama pada potongan model ini, sehingga realisasinya ditunjukkan secara eksplisit. Collaboration untuk use case lain tidak digambar pada pertemuan ini.

<!-- langkah 7 Tulis use case description baru -->

|=====================================================================================================================================================|
| Elemen .................| Deskripsi ................................................................................................................|
|=====================================================================================================================================================|
| ID dan nama ............| LAB-UC11: Catat Pengembalian Peralatan ...................................................................................|
| Sumber kebutuhan .......| LAB-R09 dan LAB-R10 ......................................................................................................|
| Tujuan .................| Pengembalian tercatat dan status peminjaman serta kondisi peralatan terbarui .............................................|
| Aktor utama ............| Petugas Laboratorium .....................................................................................................|
| Pemicu .................| Petugas memilih fungsi pencatatan pengembalian dan menentukan peminjaman yang akan dikembalikan ..........................|
| Prasyarat ..............| Petugas telah terautentikasi; peminjaman terpilih berstatus Dipinjam .....................................................|
| Pascakondisi berhasil ..| Pengembalian tercatat dengan tanggal kembali dan kondisi peralatan; status peminjaman menjadi Selesai .....................|
| Pascakondisi gagal .....| Tidak ada pengembalian baru yang tercatat; status peminjaman tidak berubah ...............................................|
| Include ................| LAB-UC12: Periksa Kondisi Peralatan ......................................................................................|
| Collaboration ..........| LAB-CO02: Catat Pengembalian Peralatan ...................................................................................|
|=====================================================================================================================================================|

Tabel 4.5 Spesifikasi hubungan diagram kumulatif LAB (17 hubungan)
|========================================================================================================================================================|
| Sumber ........................................ | Hubungan ................................ | Tujuan .................................................. |
|========================================================================================================================================================|
| Peminjam ...................................... | Association ............................. | LAB-UC01 Lihat Ketersediaan Peralatan ................... |
| Peminjam ...................................... | Association ............................. | LAB-UC03 Ajukan Peminjaman .............................. |
| Mahasiswa ..................................... | Association (khusus, Pertemuan 3) ....... | LAB-UC05 Cetak Bukti Pengajuan .......................... |
| Mahasiswa ..................................... | Generalization .......................... | Peminjam ................................................ |
| Dosen ......................................... | Generalization .......................... | Peminjam ................................................ |
| Petugas Laboratorium .......................... | Association ............................. | LAB-UC02 Kelola Data Peralatan .......................... |
| Petugas Laboratorium .......................... | Association ............................. | LAB-UC06 Proses Keputusan Peminjaman .................... |
| Petugas Laboratorium .......................... | Association ............................. | LAB-UC11 Catat Pengembalian Peralatan ................... |
| Kepala Laboratorium ........................... | Association ............................. | LAB-UC07 Lihat Laporan Peminjaman ....................... |
| LAB-UC03 Ajukan Peminjaman .................... | «include» (Pertemuan 3) ................. | LAB-UC04 Periksa Ketersediaan ........................... |
| LAB-UC05 Cetak Bukti Pengajuan ................ | «extend» (Pertemuan 3) .................. | LAB-UC03 Ajukan Peminjaman .............................. |
| LAB-UC08 Tambah Data Peralatan ................ | Generalization .......................... | LAB-UC02 Kelola Data Peralatan .......................... |
| LAB-UC09 Ubah Data Peralatan .................. | Generalization .......................... | LAB-UC02 Kelola Data Peralatan .......................... |
| LAB-UC10 Hapus Data Peralatan ................. | Generalization .......................... | LAB-UC02 Kelola Data Peralatan .......................... |
| LAB-UC11 Catat Pengembalian Peralatan ......... | «include» ............................... | LAB-UC12 Periksa Kondisi Peralatan ...................... |
| LAB-CO01 (collaboration) ...................... | Realization ............................. | LAB-UC03 Ajukan Peminjaman .............................. |
| LAB-CO02 (collaboration) ...................... | Realization ............................. | LAB-UC11 Catat Pengembalian Peralatan ................... |
|========================================================================================================================================================|
