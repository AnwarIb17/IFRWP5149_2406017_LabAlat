# P05 — Skenario Tugas Sistem Informasi Akademik: Layanan Hasil Studi

Tugas ini MELANJUTKAN kasus SIA Pertemuan 4, bukan kasus baru. Diagram acuannya adalah
diagram SIA Pertemuan 4, dan kebutuhan acuannya adalah SIA-R07 sampai SIA-R12 (lihat
Jobsheet Pertemuan 4, Tabel 4.6). Keterampilan baru pada tugas ini adalah penulisan skenario,
bukan perancangan kasus baru, sehingga tidak ada use case, aktor, atau kebutuhan baru di luar
diagram SIA Pertemuan 4.

Deliverable: 7 tabel skenario untuk SIA-UC07 sampai SIA-UC13, ditulis dengan struktur yang
sama persis dengan Tabel 5.1 (baris Nama use case, Aktor, Tujuan, Deskripsi; kolom Kegiatan
dan Respon sistem; Skenario Normal; Skenario Alternative dengan penomoran berlanjut; dan
Skenario Akhir).

---

## SIA-UC07 Lihat Kalender Akademik

| Field | Isi |
|-------|-----|
| Nama use case | SIA-UC07 Lihat Kalender Akademik |
| Aktor | Civitas Akademika (berlaku untuk Mahasiswa dan Dosen) |
| Tujuan | Kalender akademik dapat dilihat oleh civitas akademika pada periode yang dipilih |
| Deskripsi | Civitas Akademika membuka fungsi kalender akademik dan melihat jadwal akademik pada periode yang dipilih |

| Kegiatan | Respon sistem |
|----------|---------------|
| **Skenario Normal** | |
| 1. Civitas Akademika membuka fungsi Lihat Kalender Akademik | 2. Sistem menampilkan daftar periode kalender akademik |
| 3. Civitas Akademika memilih periode | 4. Sistem menampilkan kalender akademik periode tersebut |
| **Skenario Alternative** | |
| 5. Tidak ada data kalender pada periode yang dipilih (cabang dari langkah 4) | 6. Sistem menampilkan pesan tidak ada data kalender pada periode tersebut |
| **Skenario Akhir** | Use case selesai jika kalender akademik periode yang dipilih ditampilkan; jika tidak ada data kalender pada periode tersebut, use case selesai dengan pesan tersebut. |

Keterangan: use case ini direalisasikan oleh generalization aktor, sehingga skenario ditulis
satu kali atas nama Civitas Akademika dan berlaku untuk Mahasiswa dan Dosen. Asosiasi ke
SIA-UC07 digambar satu kali dari Civitas Akademika; Mahasiswa dan Dosen mewarisinya tanpa
garis tambahan. SIA-UC07 tidak mempunyai relasi include, extend, atau realization.

---

## SIA-UC08 Input Nilai Mata Kuliah

| Field | Isi |
|-------|-----|
| Nama use case | SIA-UC08 Input Nilai Mata Kuliah |
| Aktor | Dosen (prasyarat: dosen pengampu mata kuliah yang diampu) |
| Tujuan | Nilai mata kuliah yang diampu tersimpan untuk mahasiswa peserta dan siap dipublikasikan |
| Deskripsi | Dosen memilih mata kuliah yang diampu, mengisi nilai mahasiswa peserta, dan menyimpan nilai; sistem memeriksa hak pengampu, kelengkapan isian, dan rentang nilai 0–100 |

| Kegiatan | Respon sistem |
|----------|---------------|
| **Skenario Normal** | |
| 1. Dosen memilih mata kuliah yang diampu | 2. Sistem menampilkan daftar mahasiswa peserta dan nilai yang sudah ada |
| 3. Dosen mengisi nilai mahasiswa peserta | 4. Sistem menampung isian nilai |
| 5. Dosen memilih simpan | 6. Sistem memeriksa hak pengampu, kelengkapan isian, dan rentang nilai 0–100 |
| 7. Sistem menyimpan nilai berstatus Belum Dipublikasikan dan menampilkan konfirmasi | |
| **Skenario Alternative** | |
| 8. Nilai di luar rentang 0–100 (cabang dari langkah 6) | 9. Sistem menolak penyimpanan, menandai isian yang tidak sah, dan meminta Dosen memperbaiki nilai |
| 10. Dosen bukan pengampu mata kuliah tersebut (cabang dari langkah 1) | 11. Sistem menampilkan pesan Dosen tidak berhak menginput nilai dan tidak menampilkan daftar nilai |
| **Skenario Akhir** | Use case selesai jika nilai tersimpan per mahasiswa dengan status Belum Dipublikasikan; jika nilai di luar rentang atau Dosen bukan pengampu, tidak ada nilai baru yang tersimpan dan nilai yang sudah ada tidak berubah. |

Keterangan: use case ini direalisasikan oleh collaboration SIA-CO01 Input Nilai Mata Kuliah.
Collaboration tersebut tidak mempunyai langkah kegiatan pada tabel ini. Nilai yang belum
dipublikasikan tidak tampil pada KHS (SIA-UC09).

---

## SIA-UC09 Lihat KHS

| Field | Isi |
|-------|-----|
| Nama use case | SIA-UC09 Lihat KHS |
| Aktor | Mahasiswa |
| Tujuan | Mahasiswa melihat nilai mata kuliah yang sudah dipublikasikan pada semester yang dipilih |
| Deskripsi | Mahasiswa membuka fungsi KHS, memilih semester, dan melihat KHS yang hanya memuat nilai berstatus Dipublikasikan |

| Kegiatan | Respon sistem |
|----------|---------------|
| **Skenario Normal** | |
| 1. Mahasiswa membuka fungsi Lihat KHS dan memilih semester | 2. Sistem memeriksa status publikasi nilai pada semester tersebut |
| 3. Mahasiswa melihat KHS | 4. Sistem menampilkan KHS yang hanya memuat nilai berstatus Dipublikasikan |
| **Skenario Alternative** | |
| 5. Belum ada nilai yang dipublikasikan pada semester tersebut (cabang dari langkah 2) | 6. Sistem menampilkan pesan nilai semester tersebut belum dipublikasikan dan tidak menampilkan KHS |
| 7. Semester yang dipilih tidak tersedia pada daftar (cabang dari langkah 1) | 8. Sistem menampilkan pesan semester tidak tersedia |
| **Skenario Akhir** | Use case selesai jika KHS semester yang dipilih ditampilkan dengan nilai berstatus Dipublikasikan; jika nilai belum dipublikasikan atau semester tidak tersedia, KHS tidak ditampilkan dan pesan tersebut ditampilkan. |

Keterangan: use case ini direalisasikan oleh collaboration SIA-CO02 Lihat KHS. Collaboration
tersebut tidak mempunyai langkah kegiatan pada tabel ini. Nilai yang belum dipublikasikan
tidak boleh ditampilkan pada KHS.

---

## SIA-UC10 Kelola Data Mahasiswa

| Field | Isi |
|-------|-----|
| Nama use case | SIA-UC10 Kelola Data Mahasiswa |
| Aktor | Admin Akademik |
| Tujuan | Data mahasiswa terkelola melalui satu fungsi pengelolaan bersama |
| Deskripsi | Admin Akademik membuka fungsi pengelolaan data mahasiswa, memilih bentuk pengelolaan, dan menyimpan perubahan. Bentuk tambah, ubah, dan hapus dijabarkan pada tabel khusus masing-masing |

| Kegiatan | Respon sistem |
|----------|---------------|
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Kelola Data Mahasiswa | 2. Sistem menampilkan daftar data mahasiswa |
| 3. Admin Akademik memilih bentuk pengelolaan, yaitu tambah, ubah, atau hapus | 4. Sistem menampilkan formulir sesuai bentuk pengelolaan yang dipilih |
| 5. Admin Akademik mengisi atau mengonfirmasi data | 6. Sistem memeriksa kelengkapan dan keabsahan data |
| 7. Admin Akademik menyimpan perubahan | 8. Sistem menyimpan perubahan data mahasiswa dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 9. Data tidak lengkap atau tidak sah (cabang dari langkah 6) | 10. Sistem menolak penyimpanan dan menampilkan pesan kesalahan data |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa tersimpan; jika data tidak lengkap atau tidak sah, perubahan tidak tersimpan. |

Keterangan: use case umum. SIA-UC11, SIA-UC12, dan SIA-UC13 adalah bentuk khusus dari
SIA-UC10. Tabel khusus masing-masing memuat perilaku pembeda dan merujuk ke skenario umum
ini untuk langkah bersama.

---

## SIA-UC11 Tambah Data Mahasiswa

| Field | Isi |
|-------|-----|
| Nama use case | SIA-UC11 Tambah Data Mahasiswa |
| Aktor | Admin Akademik |
| Tujuan | Data mahasiswa baru tersimpan sebagai bentuk khusus dari pengelolaan data mahasiswa |
| Deskripsi | Admin Akademik mengisi data mahasiswa baru dan menyimpan data tersebut; langkah bersama mengikuti Tabel skenario SIA-UC10 |

| Kegiatan | Respon sistem |
|----------|---------------|
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Tambah Data Mahasiswa | 2. Sistem menampilkan formulir data mahasiswa baru |
| 3. Admin Akademik mengisi data mahasiswa baru | 4. Sistem memeriksa kelengkapan data |
| 5. Admin Akademik menyimpan data | 6. Sistem menyimpan data mahasiswa baru dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 7. Data mahasiswa baru tidak lengkap (cabang dari langkah 4) | 8. Sistem menolak penyimpanan dan meminta Admin Akademik melengkapi data |
| **Skenario Akhir** | Use case selesai jika data mahasiswa baru tersimpan; jika data tidak lengkap, data tidak tersimpan. |

Keterangan: use case khusus dari SIA-UC10 Kelola Data Mahasiswa. Perilaku pembeda: data
mahasiswa baru tersimpan. Langkah bersama mengikuti Tabel skenario SIA-UC10.

---

## SIA-UC12 Ubah Data Mahasiswa

| Field | Isi |
|-------|-----|
| Nama use case | SIA-UC12 Ubah Data Mahasiswa |
| Aktor | Admin Akademik |
| Tujuan | Data mahasiswa berubah sebagai bentuk khusus dari pengelolaan data mahasiswa |
| Deskripsi | Admin Akademik memilih data mahasiswa, mengubah datanya, dan menyimpan perubahan; langkah bersama mengikuti Tabel skenario SIA-UC10 |

| Kegiatan | Respon sistem |
|----------|---------------|
| **Skenario Normal** | |
| 1. Admin Akademik memilih data mahasiswa yang akan diubah | 2. Sistem menampilkan data mahasiswa saat ini |
| 3. Admin Akademik mengubah data mahasiswa | 4. Sistem memeriksa perubahan data |
| 5. Admin Akademik menyimpan perubahan | 6. Sistem menyimpan data mahasiswa yang diubah dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 7. Data mahasiswa tidak ditemukan (cabang dari langkah 2) | 8. Sistem menampilkan pesan data mahasiswa tidak ditemukan |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa tersimpan; jika data tidak ditemukan, perubahan tidak tersimpan. |

Keterangan: use case khusus dari SIA-UC10 Kelola Data Mahasiswa. Perilaku pembeda: data
mahasiswa berubah. Langkah bersama mengikuti Tabel skenario SIA-UC10.

---

## SIA-UC13 Hapus Data Mahasiswa

| Field | Isi |
|-------|-----|
| Nama use case | SIA-UC13 Hapus Data Mahasiswa |
| Aktor | Admin Akademik |
| Tujuan | Data mahasiswa terhapus sebagai bentuk khusus dari pengelolaan data mahasiswa |
| Deskripsi | Admin Akademik memilih data mahasiswa, mengonfirmasi penghapusan, dan sistem menghapus data tersebut; langkah bersama mengikuti Tabel skenario SIA-UC10. Syarat: mahasiswa tidak memiliki data akademik aktif |

| Kegiatan | Respon sistem |
|----------|---------------|
| **Skenario Normal** | |
| 1. Admin Akademik memilih data mahasiswa yang akan dihapus | 2. Sistem memeriksa mahasiswa tidak memiliki data akademik aktif |
| 3. Admin Akademik mengonfirmasi penghapusan | 4. Sistem menghapus data mahasiswa dan menampilkan konfirmasi penghapusan |
| **Skenario Alternative** | |
| 5. Mahasiswa memiliki data akademik aktif (cabang dari langkah 2) | 6. Sistem menolak penghapusan dan menampilkan pesan data tidak dapat dihapus karena masih memiliki data akademik aktif |
| **Skenario Akhir** | Use case selesai jika data mahasiswa terhapus; jika mahasiswa memiliki data akademik aktif, data tidak terhapus. |

Keterangan: use case khusus dari SIA-UC10 Kelola Data Mahasiswa. Perilaku pembeda: data
mahasiswa terhapus, dengan syarat mahasiswa tidak memiliki data akademik aktif. Langkah
bersama mengikuti Tabel skenario SIA-UC10.

---

## Riwayat versi

| Versi | Tanggal | Perubahan |
|-------|---------|-----------|
| v01 | 01-11-2026 | 7 tabel skenario SIA-UC07 sampai SIA-UC13 disusun dengan struktur Tabel 5.1: SIA-UC07 generalization aktor, SIA-UC08 dan SIA-UC09 direalisasikan collaboration, SIA-UC10 umum dan SIA-UC11/UC12/UC13 khusus. |
