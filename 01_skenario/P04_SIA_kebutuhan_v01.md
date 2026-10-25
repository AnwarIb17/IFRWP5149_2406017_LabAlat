# P04 — Kebutuhan Tugas Sistem Informasi Akademik: Layanan Hasil Studi

## 1. Deskripsi skenario

Skenario berikut bersifat fiktif untuk Praktikum Pertemuan 4 dan berbeda dari tugas Pertemuan 2 (jadwal kuliah) serta Pertemuan 3 (pengajuan KRS).

Mahasiswa dan Dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration yang bersesuaian.

Fungsi Pertemuan 2 dan Pertemuan 3 tetap berlaku dan tetap digambar pada diagram kumulatif: SIA-UC01 Lihat Jadwal Kuliah dan SIA-UC02 Kelola Jadwal Kuliah, serta SIA-UC03 Ajukan KRS, SIA-UC04 Validasi KRS, SIA-UC05 Unduh Bukti Pengajuan KRS, dan SIA-UC06 Proses Keputusan KRS beserta relasi `«include»` dan `«extend»` di antara ketiganya.

## 2. Kebutuhan tugas

| ID | Kebutuhan tugas |
|----|-----------------|
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik. |
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya. |
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan. |
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa. |
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa. |
| SIA-R12 | Model menunjukkan collaboration yang merealisasikan Input Nilai Mata Kuliah dan Lihat KHS. |

Kebutuhan SIA-R01 dan SIA-R02 (Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap berlaku dan tidak diubah artinya. Kode baru dimulai dari SIA-R07 agar identitas kebutuhan lama tetap berbeda.

## 3. Batas dan asumsi

- Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
- Kalender akademik pada tugas ini adalah agenda resmi institusi (awal semester, batas KRS, masa ujian, dan sejenisnya); kalender ini bukan jadwal kuliah pada Pertemuan 2.
- Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut.
- Nilai yang diinput belum terpublikasi sebelum dinyatakan resmi. KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data akademik aktif. Ketentuan ini fiktif untuk latihan.
- Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari Pertemuan 3.
- Pembayaran dan perancangan basis data berada di luar tugas ini.
- Nilai di luar rentang yang sah ditolak dan tidak disimpan. Rentang yang dipakai pada model ini adalah 0–100 (asumsi, lihat pertanyaan terbuka).

## 4. Pertanyaan terbuka

1. Skala dan rentang nilai resmi institusi belum ditetapkan pada jobsheet. Model memakai asumsi 0–100; bila institusi memakai skala huruf atau bobot lain, aturan validasi harus disesuaikan.
2. Mekanisme dan kewenangan publikasi nilai belum dimodelkan. Belum ditetapkan apakah publikasi dilakukan oleh Dosen, Admin Akademik, atau proses terjadwal.
3. Definisi rinci "data akademik aktif" yang menghalangi Hapus Data Mahasiswa belum ditetapkan (KRS aktif, nilai yang sudah tercatat, atau status semester).
4. Apakah Dosen Wali boleh melihat KHS mahasiswa bimbingannya tidak diminta pada tugas ini, sehingga tidak dimodelkan.
5. Format KHS, cetak ulang KHS, dan pembatalan nilai belum dimodelkan.

## 5. Keterlacakan kebutuhan ke elemen model

| Kebutuhan | Aktor | Use case / collaboration |
|-----------|-------|--------------------------|
| SIA-R07 | Civitas Akademika (umum), Mahasiswa dan Dosen (khusus) | SIA-UC07 Lihat Kalender Akademik |
| SIA-R08 | Dosen | SIA-UC08 Input Nilai Mata Kuliah; SIA-CO01 Input Nilai Mata Kuliah |
| SIA-R09 | Mahasiswa | SIA-UC09 Lihat KHS; SIA-CO02 Lihat KHS |
| SIA-R10 | Admin Akademik | SIA-UC10 Kelola Data Mahasiswa |
| SIA-R11 | Admin Akademik (melalui pewarisan dari SIA-UC10) | SIA-UC11 Tambah Data Mahasiswa, SIA-UC12 Ubah Data Mahasiswa, SIA-UC13 Hapus Data Mahasiswa |
| SIA-R12 | — | SIA-CO01 dan SIA-CO02 beserta relasi `«realization»` |

## 6. Uji konsistensi (Langkah 8)

### Situasi A — Mahasiswa melihat kalender akademik tanpa garis asosiasi langsung dari Mahasiswa

**Hasil: KONSISTEN.** Mahasiswa adalah aktor khusus dari Civitas Akademika. Asosiasi ke SIA-UC07 Lihat Kalender Akademik digambar satu kali dari Civitas Akademika, lalu diwarisi oleh Mahasiswa dan Dosen. Aktor khusus dapat digunakan di setiap tempat aktor umum dapat digunakan, sehingga ketiadaan garis langsung bukan penghapusan fungsi. Menggambar garis dari Mahasiswa atau Dosen ke SIA-UC07 justru akan menggandakan asosiasi warisan dan melanggar aturan generalization.

### Situasi B — Dosen yang bukan pengampu mencoba menginput nilai

**Hasil: DITOLAK.** Prasyarat SIA-UC08 menyatakan bahwa dosen harus pengampu mata kuliah tersebut. Sistem menolak akses sebelum nilai ditampilkan atau disimpan, menampilkan pesan bahwa dosen tidak berhak menginput nilai mata kuliah itu, dan tidak ada nilai baru yang tersimpan (pascakondisi gagal). Diagram use case tidak menunjukkan pemeriksaan hak akses; aturan ini hidup pada prasyarat dan alur alternatif A1 di use case description.

### Situasi C — Admin Akademik menghapus data mahasiswa yang masih memiliki data akademik aktif

**Hasil: DITOLAK.** Aturan tugas menyatakan Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data akademik aktif. Sistem menolak penghapusan, mempertahankan seluruh data mahasiswa dan data akademiknya, serta menampilkan pesan bahwa data tidak dapat dihapus. Tidak ada data yang terhapus (pascakondisi gagal SIA-UC13).

## 7. Catatan review dan revisi

- Pemeriksaan mandiri: arah panah generalization aktor (Mahasiswa dan Dosen menuju Civitas Akademika) dan generalization use case (SIA-UC11, SIA-UC12, SIA-UC13 menuju SIA-UC10) sudah diperiksa.
- Pemeriksaan mandiri: nama collaboration sama persis dengan use case yang direalisasikan, yaitu SIA-CO01 Input Nilai Mata Kuliah dan SIA-CO02 Lihat KHS.
- Pemeriksaan mandiri: tidak ada garis dari aktor menuju collaboration; aktor hanya berinteraksi dengan use case.
- Review rekan atau asisten: belum dilakukan saat versi v01 disusun. Temuan review akan dicatat pada logbook dan dinaikkan ke v02 bila ada perubahan isi.

## 8. Riwayat versi

| Versi | Tanggal | Perubahan |
|-------|---------|-----------|
| v01 | 25-10-2026 | Kebutuhan SIA-R07 sampai SIA-R12, batas, asumsi, pertanyaan terbuka, keterlacakan, dan uji konsistensi A/B/C disusun. |
