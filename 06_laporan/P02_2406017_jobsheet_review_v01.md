1 Temuan : Aktor Mahasiswa diletakkan di dalam batas sistem.  
Perbaikan yang diperlukan: Pindahkan aktor ke luar batas sistem.  
Alasan: Aktor merupakan representasi entitas eksternal yang berinteraksi dengan sistem, sehingga dalam UML Use Case selalu diletakkan di luar kotak system boundary.  
2 Temuan: Fungsi Lihat jadwal kuliah digambar sebagai kotak biasa.  
Perbaikan yang diperlukan: Ubah representasi fungsi menjadi bentuk elips.  
Alasan: Standar notasi UML untuk sebuah fungsi atau Use Case adalah elips/oval, sedangkan kotak biasanya untuk class atau batas sistem.  
3 Temuan: Aktor Mahasiswa dihubungkan dengan Kelola jadwal kuliah.  
Perbaikan yang diperlukan: Sesuaikan hubungan peran-fungsi dengan menghapus garis yang menghubungkan Mahasiswa ke Kelola jadwal kuliah.  
Alasan: Berdasarkan skenario, mahasiswa tidak memiliki kewenangan untuk mengelola jadwal, sehingga tidak boleh dihubungkan ke fungsi tersebut.  
4 Temuan: Identitas diagram menggunakan judul sistem laboratorium.  
Perbaikan yang diperlukan: Perbaiki judul batas sistem (identitas diagram) menjadi "Sistem Informasi Akademik".  
Alasan: Sistem yang sedang dimodelkan pada skenario ini adalah Sistem Informasi Akademik, bukan sistem laboratorium.
