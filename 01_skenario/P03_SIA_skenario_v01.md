Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil, sistem menyimpan pengajuan berstatus menunggu persetujuan dosen wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan

|=========================================================================================|
|ID .....| Kebutuhan tugas................................................................|
|-----------------------------------------------------------------------------------------|
|SIA-R01 | Mahasiswa dapat melihat jadwal kuliah..........................................|
|SIA-R02 | Admin akademik dapat mengelola jadwal kuliah...................................|
|SIA-R03 | Mahasiswa dapat mengajukan KRS.................................................|
|SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan................................|
|SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan......|
|SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS......................|
|=========================================================================================|

Batas dan asumsi:
• Pengguna telah terautentikasi.
• Data mata kuliah, prasyarat, dan jadwal tersedia.
• Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
• Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
• KRS tersimpan belum berarti disetujui.
• Pembayaran, pengisian nilai, dan implementasi basis data berada di luar tugas

Langkah 2 — Identifikasi aktor dan use case

|=========================================================================================|
| Aktor ...............| Tujuan terhadap sistem...........................................|
|-----------------------------------------------------------------------------------------|
| Mahasiswa ...........| Melihat jadwal kuliah, mengajukan KRS, dan mengunduh bukti.......|
| Dosen wali.......... | memproses persetujuan atau penolakan KRS.........................|
| Admin akademik...... | mengelola jadwal kuliah..........................................|
|=========================================================================================|

Langkah 3 Tentukan include

SIA-R03 «include» SIA-R04
Alasan: System menjadi bagian validasi pengajuan KRS.

SIA-R01 «include» SIA-R02
Alasan : untuk melihat jadwal kuliah mahasiswa harus melakukan request kepada pengelola jadwal kuliah (Admin Akademik)

Langkah 4 Tentukan extend
SIA-R05 «extend» SIA-R03
Extension point: Bukti pengajuan KRS tersedia.
Kondisi: [mahasiswa memilih Unduh].
Alasan: pengajuan tetap Tesimpan tanpa Pengunduhan.

|=========================================================================================|
| ID ....| Nama use case...................| Peran dalam model............................|
|-----------------------------------------------------------------------------------------|
|SIA-R01 | melihat jadwal kuliah...........| Fungsi Utama Mahasiswa.......................|
|SIA-R02 | dapat mengelola jadwal kuliah...| Fungsi utama Admin akademik..................|
|SIA-R03 | mengajukan KRS..................| Fungsi Utama Mahasiswa.......................|
|SIA-R04 | memvalidasi KRS ................| Perilaku yang di sertakan SIA-R0.............|
|SIA-R05 | mengunduh bukti.................| Tambahan bersyarat pada SIA-R03..............|
|SIA-R06 | memproses persetujuan KRS.......| Fungsi utama Dosen wali......................|
|=========================================================================================|

Langkah 5 Susun deskripsi
==========================================================================================|
a. SIA-UC03 — Ajukan KRS
==========================================================================================|
| Elemen................| Keterangan......................................................|
|-----------------------|-----------------------------------------------------------------|
| Elemen................| SIA-UC03 — Ajukan KRS...........................................|
| Tujuan................| Menghasilkan pengajuan KRS yang tersimpan.......................|
| Aktor utama...........| Mahasiswa.......................................................|
| Sumber kebutuhan......| SIA-R03, SIA-R04, dan SIA-R05...................................|
| Pemicu................| Mahasiswa memilih fungsi pengajuan KRS..........................|
| Prasyarat.............| Mahasiswa telah terautentikasi; data jadwal kuliah tersedia.....|
| Pascakondisi berhasil.| Pengajuan tersimpan dengan status Menunggu Keputusan............|
| Pascakondisi gagal....| Tidak ada pengajuan baru yang berhasil tersimpan; validasi gagal|
| Include...............| SIA-UC04 — Validasi KRS.........................................|
| Extension point.......| Bukti pengajuan tersedia, pada saat konfirmasi pengajuan........|
| Extend................| SIA-UC05 jika [mahasiswa memilih mengunduh bukti]...............|
==========================================================================================|

==========================================================================================|
b. SIA-UC04 — Validasi KRS
==========================================================================================|
| Elemen................| Keterangan......................................................|
|-----------------------|-----------------------------------------------------------------|
| Elemen................| SIA-UC04 — Validasi KRS.........................................|
| Tujuan................| Memverifikasi kelayakan daftar mata kuliah pada pengajuan KRS...|
| Aktor utama...........| Sistem..........................................................|
| Sumber kebutuhan......| SIA-R04.........................................................|
| Pemicu................| Dipanggil oleh proses pengajuan KRS (SIA-UC03)..................|
| Prasyarat.............| Mahasiswa sedang dalam proses melakukan pengajuan KRS...........|
| Pascakondisi berhasil.| KRS tervalidasi dan siap untuk disimpan.........................|
| Pascakondisi gagal....| Validasi KRS gagal dan sistem menampilkan pesan kesalahan.......|
| Include...............| -...............................................................|
| Extension point.......| -...............................................................|
| Extend................| -...............................................................|
==========================================================================================|

==========================================================================================|
c. SIA-UC05 — Unduh Bukti Pengajuan KRS
==========================================================================================|
| Elemen................| Keterangan......................................................|
|-----------------------|-----------------------------------------------------------------|
| Elemen................| SIA-UC05 — Unduh Bukti Pengajuan KRS............................|
| Tujuan................| Mengunduh berkas bukti pengajuan KRS............................|
| Aktor utama...........| Mahasiswa.......................................................|
| Sumber kebutuhan......| SIA-R05.........................................................|
| Pemicu................| Mahasiswa memilih opsi unduh bukti pada konfirmasi pengajuan....|
| Prasyarat.............| Pengajuan KRS berhasil dilakukan dan opsi unduh bukti dipilih...|
| Pascakondisi berhasil.| Berkas bukti pengajuan KRS berhasil diunduh oleh mahasiswa......|
| Pascakondisi gagal....| Berkas bukti pengajuan KRS gagal diunduh........................|
| Include...............| -...............................................................|
| Extension point.......| -...............................................................|
| Extend................| -...............................................................|
==========================================================================================|

==========================================================================================|
d. SIA-UC06 — Proses Keputusan KRS
==========================================================================================|
| Elemen................| Keterangan......................................................|
|-----------------------|-----------------------------------------------------------------|
| Elemen................| SIA-UC06 — Proses Keputusan KRS.................................|
| Tujuan................| Memproses persetujuan atau penolakan KRS yang diajukan mahasiswa|
| Aktor utama...........| Dosen Wali......................................................|
| Sumber kebutuhan......| SIA-R06.........................................................|
| Pemicu................| Dosen Wali memilih fungsi pemrosesan/keputusan KRS..............|
| Prasyarat.............| Dosen Wali telah terautentikasi; data pengajuan KRS tersedia....|
| Pascakondisi berhasil.| Status pengajuan KRS berhasil diperbarui (Disetujui / Ditolak)..|
| Pascakondisi gagal....| Status pengajuan KRS tidak berubah dan keputusan tidak tersimpan|
| Include...............| -...............................................................|
| Extension point.......| -...............................................................|
| Extend................| -...............................................................|
==========================================================================================|

Langkah 6 Pemeriksaan konsistensi diagram dan deskripsi
Sumber pemeriksaan: 04_model_analisis/P03/SIA/P03_2406017_SIA_usecase_analisis_v01.drawio
bersama tabel deskripsi use case pada langkah 5.

Ringkasan:
| Situasi | Hasil pemeriksaan |
| Validasi berhasil, mahasiswa tidak mengunduh bukti | KONSISTEN |
| Validasi gagal | KONSISTEN, tetapi alur alternatif hanya dijelaskan di deskripsi |
| Validasi berhasil, mahasiswa memilih mengunduh bukti | TIDAK SEPENUHNYA KONSISTEN |

==========================================================================================|
a. Validasi berhasil dan mahasiswa tidak mengunduh bukti
==========================================================================================|
| Elemen | Pemeriksaan |
| SIA-UC03 «include» SIA-UC04 | Dieksekusi tanpa syarat, sehingga validasi tetap terjadi. Sesuai. |
| SIA-UC05 «extend» SIA-UC03 | Kondisi [mahasiswa memilih Unduh] bernilai salah, sehingga SIA-UC05 tidak dieksekusi. Sesuai. |
| Pascakondisi SIA-UC04 | "KRS tervalidasi dan siap untuk disimpan" tercapai. |
| Pascakondisi SIA-UC03 | "Pengajuan tersimpan dengan status Menunggu Keputusan" tercapai. |
| Aturan batas sistem | "Unduh bukti tidak menjadi syarat keberhasilan pengajuan" dihormati, sehingga tidak mengunduh tidak menggagalkan pengajuan. |
| KESIMPULAN | KONSISTEN. Diagram dan deskripsi menghasilkan hasil yang sama. |

==========================================================================================|
b. Validasi gagal
==========================================================================================|
| Elemen | Pemeriksaan |
| SIA-UC03 «include» SIA-UC04 | Tetap dieksekusi, karena «include» tidak bersyarat. |
| Pascakondisi SIA-UC04 | "Validasi KRS gagal dan sistem menampilkan pesan kesalahan" tercapai. |
| Pascakondisi SIA-UC03 | "Tidak ada pengajuan baru yang berhasil tersimpan; validasi gagal" tercapai. |
| Extension point SIA-UC03 | Tidak tercapai, karena titik ekstensi berada pada konfirmasi pengajuan yang hanya tampil setelah validasi berhasil. |
| SIA-UC05 «extend» SIA-UC03 | Tidak dieksekusi karena extension point tidak tercapai. Konsisten, tetapi sifatnya berasal dari deskripsi, bukan dari diagram. |
| KESIMPULAN | KONSISTEN pada tingkat pascakondisi. |
| CATATAN | Diagram tidak menandai bahwa SIA-UC04 memiliki dua hasil (berhasil dan gagal) dan bahwa kegagalan membatalkan SIA-UC03. Diagram use case UML memang tidak menyatakan alur sukses dan gagal, sehingga ini bukan kesalahan notasi, tetapi alur alternatif ini hanya hidup di dalam deskripsi use case. |

==========================================================================================|
c. Validasi berhasil dan mahasiswa memilih mengunduh bukti
==========================================================================================|
| Elemen | Pemeriksaan |
| SIA-UC03 «include» SIA-UC04 | Validasi dieksekusi dan berhasil. |
| Extension point SIA-UC03 | "Bukti pengajuan tersedia" tercapai pada konfirmasi pengajuan. |
| SIA-UC05 «extend» SIA-UC03 | Kondisi bernilai benar, sehingga SIA-UC05 dieksekusi, lalu aliran kembali ke SIA-UC03. |
| Prasyarat SIA-UC05 | "Pengajuan KRS berhasil dilakukan dan opsi unduh bukti dipilih" terpenuhi. |
| Pascakondisi SIA-UC03 | "Pengajuan tersimpan dengan status Menunggu Keputusan" tetap tercapai setelah SIA-UC05 selesai. |
| KESIMPULAN | KONSISTEN pada alur unduhan yang berhasil. |
| KETIDAKSESUAIAN | SIA-UC05 memiliki "pascakondisi gagal: berkas bukti pengajuan KRS gagal diunduh". Diagram dan deskripsi tidak menyatakan dampaknya terhadap SIA-UC03, yaitu apakah pengajuan tetap berstatus Menunggu Keputusan atau ikut gagal. Aturan "Unduh bukti tidak menjadi syarat keberhasilan pengajuan" mengarah pada pilihan pertama, tetapi pilihan itu belum ditulis eksplisit dan belum digambarkan. Selain itu, kegagalan setelah validasi berhasil memakai istilah "gagal" yang sama dengan kegagalan validasi, sehingga dua kegagalan berbeda dapat tertukar. |
| TINDAKAN PERBAIKAN | Tambahkan pada baris Extend SIA-UC03 catatan bahwa kegagalan SIA-UC05 tidak membatalkan SIA-UC03, dan tambahkan catatan pada diagram di jalur «extend». |

==========================================================================================|
Ringkasan temuan
==========================================================================================|
| No | Temuan | Lokasi | Perbaikan yang diperlukan |
| 1 | Kegagalan unduh tidak memiliki dampak yang dinyatakan pada hasil SIA-UC03 | Deskripsi SIA-UC03 dan SIA-UC05 | Tulis eksplisit bahwa pengajuan tetap berhasil. |
| 2 | Alur kegagalan validasi hanya dijelaskan di deskripsi, tidak pada diagram | Diagram SIA | Tambahkan catatan "validasi gagal menghentikan pengajuan". |
| 3 | Istilah "gagal" dipakai untuk dua kejadian berbeda | Deskripsi SIA-UC03 dan SIA-UC05 | Bedakan "gagal validasi" dan "gagal unduh". |
