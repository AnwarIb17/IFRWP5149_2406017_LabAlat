# P04 — Skenario Tugas Sistem Informasi Akademik: Layanan Hasil Studi

## 1. Deskripsi skenario

Mahasiswa dan Dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration yang bersesuaian.

Diagram Pertemuan 4 bersifat kumulatif. Fungsi jadwal kuliah dari Pertemuan 2, fungsi pengajuan KRS dari Pertemuan 3, dan fungsi layanan hasil studi dari Pertemuan 4 digambar dalam satu diagram Sistem Informasi Akademik.

## 2. Aktor

| Aktor | Kedudukan | Tujuan terhadap sistem |
|-------|-----------|------------------------|
| Civitas Akademika | Umum (general), baru pada Pertemuan 4 | Peran umum bagi mahasiswa dan dosen. Mewariskan fungsi melihat kalender akademik kepada Mahasiswa dan Dosen. |
| Mahasiswa | Khusus dari Civitas Akademika, tetap dari Pertemuan 2 dan 3 | Melihat kalender akademik (diwarisi dari Civitas Akademika), melihat jadwal kuliah, mengajukan KRS, mengunduh bukti pengajuan KRS, dan melihat KHS. |
| Dosen | Khusus dari Civitas Akademika, baru pada Pertemuan 4 | Melihat kalender akademik (diwarisi dari Civitas Akademika) dan menginput nilai mata kuliah yang diampu. |
| Admin Akademik | Tetap dari Pertemuan 2 dan 3 | Mengelola jadwal kuliah dan mengelola data mahasiswa. |
| Dosen Wali | Tetap dari Pertemuan 3 | Memproses persetujuan atau penolakan KRS. |

## 3. Katalog use case gabungan

| ID | Nama use case | Aktor terkait | Sumber kebutuhan | Status |
|----|---------------|---------------|------------------|--------|
| SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa | SIA-R01 (Pertemuan 2) | Tetap |
| SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik | SIA-R02 (Pertemuan 2) | Tetap |
| SIA-UC03 | Ajukan KRS | Mahasiswa | SIA-R03 (Pertemuan 3) | Tetap |
| SIA-UC04 | Validasi KRS | Sistem, dipanggil oleh SIA-UC03 | SIA-R04 (Pertemuan 3) | Tetap |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa | SIA-R05 (Pertemuan 3) | Tetap |
| SIA-UC06 | Proses Keputusan KRS | Dosen Wali | SIA-R06 (Pertemuan 3) | Tetap |
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika (diwarisi Mahasiswa dan Dosen) | SIA-R07 | Baru |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen | SIA-R08 | Baru; direalisasikan SIA-CO01 |
| SIA-UC09 | Lihat KHS | Mahasiswa | SIA-R09 | Baru; direalisasikan SIA-CO02 |
| SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik | SIA-R10 | Baru; use case umum |
| SIA-UC11 | Tambah Data Mahasiswa | Admin Akademik (melalui pewarisan SIA-UC10) | SIA-R11 | Baru; use case khusus |
| SIA-UC12 | Ubah Data Mahasiswa | Admin Akademik (melalui pewarisan SIA-UC10) | SIA-R11 | Baru; use case khusus |
| SIA-UC13 | Hapus Data Mahasiswa | Admin Akademik (melalui pewarisan SIA-UC10) | SIA-R11 | Baru; use case khusus |

Catatan: nama SIA-UC01 dan SIA-UC03 diselaraskan dengan istilah pada jobsheet Pertemuan 4 ("Lihat Jadwal Kuliah" dan "Ajukan KRS"); ID dan makna use case tidak berubah dari Pertemuan 2 dan Pertemuan 3.

## 4. Generalization aktor

Keputusan pemodelan:

- Mahasiswa adalah bentuk khusus dari Civitas Akademika, dan Dosen adalah bentuk khusus dari Civitas Akademika. Alasan: keduanya berbagi fungsi yang sama, yaitu melihat kalender akademik (SIA-UC07).
- Asosiasi ke SIA-UC07 digambar satu kali, yaitu dari Civitas Akademika. Garis yang sama tidak digambar ulang dari Mahasiswa atau dari Dosen karena fungsi tersebut diwarisi.
- Mahasiswa tetap mempunyai asosiasi langsung ke SIA-UC01, SIA-UC03, SIA-UC05, dan SIA-UC09 karena fungsi-fungsi itu khusus mahasiswa. Dosen tetap mempunyai asosiasi langsung ke SIA-UC08 karena input nilai khusus dosen pengampu.
- Admin Akademik dan Dosen Wali tidak dijadikan aktor khusus karena tidak berbagi fungsi umum yang sama dengan Civitas Akademika. Keduanya tetap berdiri sendiri seperti pada Pertemuan 2 dan 3.
- Arah panah: ujung segitiga kosong menempel pada Civitas Akademika. Panah digambar dari Mahasiswa menuju Civitas Akademika dan dari Dosen menuju Civitas Akademika.

Fungsi yang diwarisi dan yang tidak diwarisi:

| Aktor khusus | Fungsi yang diwarisi dari Civitas Akademika | Fungsi tambahan milik sendiri |
|--------------|---------------------------------------------|-------------------------------|
| Mahasiswa | SIA-UC07 Lihat Kalender Akademik | SIA-UC01 Lihat Jadwal Kuliah, SIA-UC03 Ajukan KRS, SIA-UC05 Unduh Bukti Pengajuan KRS, SIA-UC09 Lihat KHS |
| Dosen | SIA-UC07 Lihat Kalender Akademik | SIA-UC08 Input Nilai Mata Kuliah |

## 5. Generalization use case

- SIA-UC10 Kelola Data Mahasiswa adalah use case umum.
- SIA-UC11 Tambah Data Mahasiswa, SIA-UC12 Ubah Data Mahasiswa, dan SIA-UC13 Hapus Data Mahasiswa adalah bentuk khusus dari SIA-UC10. Alasan: ketiganya sama-sama mengelola data mahasiswa, tetapi hasil akhirnya berbeda.
- Perilaku pembeda:
  - SIA-UC11 Tambah Data Mahasiswa menghasilkan data mahasiswa baru yang tersimpan.
  - SIA-UC12 Ubah Data Mahasiswa menghasilkan data mahasiswa yang berubah.
  - SIA-UC13 Hapus Data Mahasiswa menghasilkan data mahasiswa yang terhapus, dengan syarat mahasiswa tidak memiliki data akademik aktif.
- Arah panah: dari setiap use case khusus menuju SIA-UC10, dengan ujung segitiga kosong menempel pada SIA-UC10.

## 6. Collaboration dan realization

| ID | Nama collaboration (sama persis dengan nama use case) | Use case yang direalisasikan |
|----|--------------------------------------------------------|------------------------------|
| SIA-CO01 | Input Nilai Mata Kuliah | SIA-UC08: Input Nilai Mata Kuliah |
| SIA-CO02 | Lihat KHS | SIA-UC09: Lihat KHS |

Alasan: kedua use case tersebut adalah use case utama pada skenario layanan hasil studi, sehingga realisasinya ditunjukkan secara eksplisit. Collaboration untuk use case lain tidak digambar pada pertemuan ini. Collaboration digambar sebagai elips garis putus-putus di dalam batas sistem, tidak dihubungkan ke aktor, dan dihubungkan ke use case dengan relasi `«realization»` dari collaboration menuju use case.

## 7. Use case description

### 7.1 SIA-UC08 — Input Nilai Mata Kuliah

| Elemen | Deskripsi |
|--------|-----------|
| ID dan nama | SIA-UC08: Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 |
| Tujuan | Nilai mata kuliah yang diampu tersimpan untuk mahasiswa peserta dan siap dipublikasikan. |
| Aktor utama | Dosen |
| Aktor pendukung | — |
| Pemicu | Dosen memilih fungsi input nilai setelah masa perkuliahan berakhir. |
| Prasyarat | Dosen telah terautentikasi; dosen adalah pengampu mata kuliah tersebut; masa perkuliahan telah berakhir; daftar mahasiswa peserta mata kuliah tersedia. |
| Pascakondisi berhasil | Nilai tersimpan per mahasiswa dengan status Belum Dipublikasikan; nilai belum tampil pada KHS. |
| Pascakondisi gagal | Tidak ada nilai baru yang tersimpan; nilai yang sudah ada sebelumnya tidak berubah. |
| Collaboration | SIA-CO01: Input Nilai Mata Kuliah |
| Aturan bisnis | Satu nilai per mahasiswa per mata kuliah per semester; rentang nilai sah 0–100 (asumsi); hanya dosen pengampu yang boleh menginput; nilai yang belum dipublikasikan tidak tampil di KHS. |

Alur utama:

| Langkah | Tindakan Dosen | Respons sistem |
|---------|----------------|----------------|
| 1 | Memilih mata kuliah yang diampu | Menampilkan daftar mahasiswa peserta dan nilai yang sudah ada |
| 2 | Mengisi atau mengubah nilai mahasiswa | Menampung isian nilai |
| 3 | Memilih simpan | Memeriksa hak pengampu, kelengkapan isian, dan rentang nilai |
| 4 | Tidak ada | Menyimpan nilai berstatus Belum Dipublikasikan dan menampilkan konfirmasi |

Alur alternatif atau pengecualian:

- **A1: Dosen bukan pengampu (sebelum langkah 1).** Sistem menolak akses, menampilkan pesan bahwa dosen tidak berhak menginput nilai mata kuliah tersebut, dan tidak menampilkan atau mengubah data nilai. Pascakondisi gagal berlaku.
- **A2: Nilai di luar rentang sah (pada langkah 3).** Sistem menolak penyimpanan, menandai isian yang tidak sah, dan meminta dosen memperbaiki nilai. Tidak ada nilai yang tersimpan sampai isian berada pada rentang 0–100.
- **A3: Masa perkuliahan belum berakhir (pada langkah 1).** Sistem menolak pembukaan fungsi input nilai dan menampilkan pesan bahwa input nilai baru dapat dilakukan setelah masa perkuliahan berakhir.
- **A4: Isian nilai tidak lengkap (pada langkah 3).** Sistem menolak penyimpanan dan menampilkan daftar mahasiswa yang nilainya belum diisi.

### 7.2 SIA-UC09 — Lihat KHS (deskripsi ringkas)

| Elemen | Deskripsi |
|--------|-----------|
| ID dan nama | SIA-UC09: Lihat KHS |
| Sumber kebutuhan | SIA-R09 |
| Tujuan | Mahasiswa melihat nilai mata kuliah yang sudah dipublikasikan pada semester terpilih. |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih menu KHS dan menentukan semester. |
| Prasyarat | Mahasiswa telah terautentikasi; nilai pada semester terpilih sudah dipublikasikan. |
| Pascakondisi berhasil | KHS semester terpilih ditampilkan dan hanya memuat nilai berstatus Dipublikasikan; tidak ada data yang berubah. |
| Pascakondisi gagal | KHS tidak ditampilkan; sistem menampilkan pesan bahwa nilai semester tersebut belum dipublikasikan. |
| Collaboration | SIA-CO02: Lihat KHS |
| Aturan bisnis | Nilai yang belum dipublikasikan tidak boleh ditampilkan pada KHS. |

Alur utama ringkas:

1. Mahasiswa memilih menu KHS dan semester.
2. Sistem memeriksa status publikasi nilai pada semester tersebut.
3. Sistem menampilkan KHS yang hanya memuat nilai berstatus Dipublikasikan.
4. Mahasiswa melihat KHS.

Alur alternatif:

- **A1: Belum ada nilai yang dipublikasikan.** Sistem menampilkan keadaan kosong dan pesan bahwa nilai semester tersebut belum dipublikasikan; tidak ada nilai yang ditampilkan.
- **A2: Semester tidak valid atau tidak tersedia.** Sistem menolak permintaan dan menampilkan pesan kesalahan.

## 8. Spesifikasi hubungan diagram kumulatif SIA

| Sumber | Hubungan | Tujuan |
|--------|----------|--------|
| Civitas Akademika | Association | SIA-UC07 Lihat Kalender Akademik |
| Mahasiswa | Association (tetap dari Pertemuan 2) | SIA-UC01 Lihat Jadwal Kuliah |
| Mahasiswa | Association (tetap dari Pertemuan 3) | SIA-UC03 Ajukan KRS |
| Mahasiswa | Association (tetap dari Pertemuan 3) | SIA-UC05 Unduh Bukti Pengajuan KRS |
| Mahasiswa | Association | SIA-UC09 Lihat KHS |
| Dosen | Association | SIA-UC08 Input Nilai Mata Kuliah |
| Admin Akademik | Association (tetap dari Pertemuan 2) | SIA-UC02 Kelola Jadwal Kuliah |
| Admin Akademik | Association | SIA-UC10 Kelola Data Mahasiswa |
| Dosen Wali | Association (tetap dari Pertemuan 3) | SIA-UC06 Proses Keputusan KRS |
| Mahasiswa | Generalization → | Civitas Akademika |
| Dosen | Generalization → | Civitas Akademika |
| SIA-UC03 Ajukan KRS | `«include»` (tetap dari Pertemuan 3) | SIA-UC04 Validasi KRS |
| SIA-UC05 Unduh Bukti Pengajuan KRS | `«extend»` (tetap dari Pertemuan 3) | SIA-UC03 Ajukan KRS |
| SIA-UC01 Lihat Jadwal Kuliah | `«include»` (tetap dari Pertemuan 2) | SIA-UC02 Kelola Jadwal Kuliah |
| SIA-UC11 Tambah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| SIA-UC12 Ubah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| SIA-UC13 Hapus Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| SIA-CO01 (collaboration) | Realization → | SIA-UC08 Input Nilai Mata Kuliah |
| SIA-CO02 (collaboration) | Realization → | SIA-UC09 Lihat KHS |

Catatan pemeriksaan:

- SIA-UC07 hanya terhubung ke Civitas Akademika dan tidak mempunyai relasi `«include»`, `«extend»`, generalization, atau realization.
- SIA-UC08 dan SIA-UC09 masing-masing direalisasikan oleh satu collaboration.
- SIA-UC10 tidak dihubungkan langsung ke SIA-UC11, SIA-UC12, atau SIA-UC13 dengan asosiasi aktor; Admin Akademik cukup dihubungkan ke SIA-UC10, lalu use case khusus mewarisi aktor tersebut.
- Tidak ada garis dari aktor menuju collaboration.
- Nama dan ID pada diagram, katalog, dan deskripsi sama persis.

## 9. Riwayat versi

| Versi | Tanggal | Perubahan |
|-------|---------|-----------|
| v01 | 25-10-2026 | Aktor, katalog gabungan 13 use case, generalisasi aktor dan use case, dua collaboration, deskripsi SIA-UC08 dan SIA-UC09, serta spesifikasi hubungan disusun. |
