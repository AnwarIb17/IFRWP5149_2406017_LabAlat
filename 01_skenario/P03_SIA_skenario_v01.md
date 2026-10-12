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
| ID ....| Nama use case...................| Peran dalam model
|-----------------------------------------------------------------------------------------|
|SIA-R01 | melihat jadwal kuliah...........| Fungsi Utama Mahasiswa.......................|
|SIA-R02 | dapat mengelola jadwal kuliah...| Fungsi utama Admin akademik..................|
|SIA-R03 | mengajukan KRS..................| Fungsi Utama Mahasiswa.......................|
|SIA-R04 | memvalidasi KRS ................| Perilaku yang di sertakan SIA-R0.............|
|SIA-R05 | mengunduh bukti.................| Tambahan bersyarat pada SIA-R03..............|
|SIA-R06 | memproses persetujuan KRS.......| Fungsi utama Dosen wali......................|
|=========================================================================================|
