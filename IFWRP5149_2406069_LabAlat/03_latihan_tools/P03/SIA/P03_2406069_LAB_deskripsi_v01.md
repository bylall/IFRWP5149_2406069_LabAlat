Bagian	                Isi
ID dan nama	            SIA-UC01 Ajukan KRS
Sumber kebutuhan	    SIA-R03, SIA-R04, SIA-R05
Tujuan	                Menghasilkan pengajuan KRS yang tersimpan
Aktor utama     	    Mahasiswa
Aktor pendukung 	    –
Pemicu	                Mahasiswa memilih fungsi pengajuan KRS
Prasyarat	            Mahasiswa telah terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia
Include	                SIA-UC02 — Validasi KRS (dipanggil pada langkah 4)
Extension point  	    Bukti pengajuan tersedia, pada langkah 6
Extend	                SIA-UC03 jika [mahasiswa memilih unduh bukti]
Pascakondisi berhasil	Pengajuan tersimpan dengan nomor dan status Menunggu persetujuan dosen wali
Pascakondisi gagal	    Tidak ada pengajuan baru yang berhasil tersimpan
Aturan bisnis/asumsi	Validasi gagal berarti pengajuan tidak tersimpan; unduh bukti bukan syarat keberhasilan; KRS tersimpanbelum berarti    disetujui


Alur utama

|Langkah| Tindakan | mahasiswa |  Respons  |                                          sistem                                          |
|-------|----------|-----------|-----------|------------------------------------------------------------------------------------------|
|   1   | Membuka  | pengajuan |    KRS    | Menampilkan daftar mata kuliah yang dapat dipilih                     |
|   2   | Memilih  |   mata    |  kuliah   |                                    Menampung pilihan                                     |
|   3   | Mengirim | pengajuan | Memeriksa |                            ada tidaknya mata kuliah terpilih                             |
|   4   |    —     |Menjalankan| SIA-UC02  |                                      (Validasi KRS)                                      |
|   5   |    —     |   Jika    | validasi  |berhasil, menyimpan pengajuan berstatus Menunggu persetujuan dosen wali dan memberi nomor |
|   6   | Melihat  |konfirmasi |Menampilkan|                        nomor dan status; mencapai extension point                        |
|   7   |Mengakhiri| pengajuan |  Menutup  |                                     proses pengajuan                                     |

<!-- Alur alternatif/pengecualian -->
|                                                                                  Rujukan Kondisi Tindakan dan hasil                                                                                   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                        3a Tidak ada mata kuliah dipilih Sistem meminta mahasiswa memilih; kembali ke langkah 2                                                        |
|5a Validasi gagal (hasil dari SIA-UC02) Sistem menampilkan alasan kegagalan dan tidak menyimpan. Mahasiswa memperbaiki pilihan (kembali ke langkah 2) atau membatalkan. Jika batal: pascakondisi gagal |
|                                                                                                                                                                                                       |
|                                           6a [Mahasiswa memilih unduh bukti] di extension point Menjalankan SIA-UC03. Setelah selesai, lanjut ke langkah 7                                            |
|                                                            6b Mahasiswa tidak memilih unduh Lanjut ke langkah 7; pengajuan tetap tersimpan                                                            |


|   Bagian   |                                                         Isi                                                         |
|------------|---------------------------------------------------------------------------------------------------------------------|
|     ID     |                                          dan nama SIA-UC02 — Validasi KRS                                           |
|   Sumber   |                                                  kebutuhan SIA-R04                                                  |
|   Tujuan   |                               Menentukan apakah KRS layak disimpan sebagai pengajuan                                |
|   Aktor    |                                         utama Mahasiswa (melalui SIA-UC01)                                          |
|   Aktor    |                                                     pendukung –                                                     |
|   Pemicu   |                                       SIA-UC01 langkah 4 (pengajuan dikirim)                                        |
| Prasyarat  |                      Ada pilihan mata kuliah; data mata kuliah, prasyarat, dan jadwal tersedia                      |
|    Alur    |                                             utama lihat tabel di bawah                                              |
|Pascakondisi|                                   berhasil Hasil “valid” dikembalikan ke SIA-UC01                                   |
|Pascakondisi|             gagal Hasil “tidak valid” beserta alasan dikembalikan ke SIA-UC01; tidak ada data tersimpan             |
|   Aturan   |bisnis/asumsi Ketiga pemeriksaan selalu dijalankan pada setiap pengajuan; tidak ada batas SKS atau aturan pembayaran |

|Langkah|Tindakan|   Respons   |              sistem              |
|-------|--------|-------------|----------------------------------|
|   1   |   —    |  Menerima   | daftar mata kuliah dari SIA-UC01 |
|   2   |   —    |  Memeriksa  |    kelengkapan data pengajuan    |
|   3   |   —    |  Memeriksa  |    prasyarat tiap mata kuliah    |
|   4   |   —    |  Memeriksa  |benturan jadwal antar mata kuliah |
|   5   |   —    |Mengembalikan|    hasil “valid” ke SIA-UC01     |




