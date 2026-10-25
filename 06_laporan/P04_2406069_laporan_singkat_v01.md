<!-- P04_2406111_laporan_singkat_v01 — Laporan Singkat Pertemuan 4 -->

<!-- Tujuan -->

Mendalami use case diagram dengan tiga unsur baru: generalization aktor, generalization use case, serta collaboration dengan relasi realization. Diagram bersifat kumulatif, yaitu diagram Pertemuan 3 dipertahankan lalu ditambah elemen baru.

<!-- Kasus yang dikerjakan -->

| Kasus | Jenis | Ringkasan |
|-------|-------|-----------|
| Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium (LAB) | Studi kasus terbimbing | Peminjam sebagai aktor umum bagi Mahasiswa dan Dosen; Kelola Data Peralatan dengan tiga bentuk khusus; pencatatan pengembalian dengan pemeriksaan kondisi |
| Sistem Informasi Akademik, Layanan Hasil Studi (SIA) | Tugas praktik | Civitas Akademika sebagai aktor umum bagi Mahasiswa dan Dosen; Kelola Data Mahasiswa dengan tiga bentuk khusus; Input Nilai Mata Kuliah dan Lihat KHS |

 <!-- Generalization aktor -->
- LAB: Mahasiswa dan Dosen adalah bentuk khusus dari Peminjam. Asosiasi ke Lihat Ketersediaan Peralatan dan Ajukan Peminjaman digambar satu kali dari Peminjam. Asosiasi Mahasiswa ke Cetak Bukti Pengajuan tetap langsung.
- SIA: Mahasiswa dan Dosen adalah bentuk khusus dari Civitas Akademika. Asosiasi ke Lihat Kalender Akademik digambar satu kali dari Civitas Akademika.

<!-- Generalization use case -->
- LAB: Tambah, Ubah, dan Hapus Data Peralatan adalah bentuk khusus dari Kelola Data Peralatan.
- SIA: Tambah, Ubah, dan Hapus Data Mahasiswa adalah bentuk khusus dari Kelola Data Mahasiswa.

<!-- Collaboration dan realization -->
- LAB: LAB-CO01 Ajukan Peminjaman dan LAB-CO02 Catat Pengembalian Peralatan.
- SIA: SIA-CO01 Input Nilai Mata Kuliah dan SIA-CO02 Lihat KHS.
- Keduanya digambar sebagai elips garis putus-putus dengan relasi realization dari collaboration ke use case, dan tidak terhubung ke aktor.

 <!-- Use case description -->
- LAB-UC11 Catat Pengembalian Peralatan (lengkap) _(pastikan sudah ada di berkas skenario LAB)_.
- SIA-UC08 Input Nilai Mata Kuliah (lengkap) dan SIA-UC09 Lihat KHS (ringkas).

<!-- Artefak yang dihasilkan -->

| Artefak | Lokasi |
|---------|--------|
| Kebutuhan dan skenario LAB | `01_skenario/P04_LAB_kebutuhan_v01.md`, `P04_LAB_skenario_v01.md` |
| Kebutuhan dan skenario SIA | `01_skenario/P04_SIA_kebutuhan_v01.md`, `P04_SIA_skenario_v01.md` |
| Diagram LAB | `04_model_analisis/P04/LAB/P04_2406111_LAB_usecase_v02.drawio` dan PNG |
| Diagram SIA | `04_model_analisis/P04/SIA/P04_2406111_SIA_usecase_v01.drawio` dan PNG |
| Metadata | `02_template/P04_metadata_artefak_v01.md` |
| Logbook | `00_administrasi/P04_2406111_logbook_v01.md` |

<!-- Review dan perbaikan -->

Diagram LAB v01 direview terhadap Tabel 4.5 (17 hubungan) dan checklist. Semua hubungan sudah ada dengan arah yang benar. Perbaikan pada v02:
1. Menambahkan catatan condition dan extension point pada relasi extend LAB-UC05 ke LAB-UC03.
2. Memperbaiki rute garis include LAB-UC11 ke LAB-UC12 agar tidak melewati elips collaboration.