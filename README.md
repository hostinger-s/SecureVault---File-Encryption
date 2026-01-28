1. Deskripsi Umum (Apa ini?)
Nama Aplikasi: SecureVault - Client-Side File Encryptor Fungsi: Alat keamanan berbasis web untuk mengamankan (mengenkripsi) file pribadi agar tidak bisa dibuka oleh orang lain tanpa password yang tepat.

Latar Belakang Masalah: Pengiriman file sensitif (foto pribadi, dokumen kontrak, laporan keuangan) melalui internet seringkali berisiko disadap atau diretas. SecureVault hadir sebagai solusi untuk mengunci file tersebut sebelum dikirim, sehingga meskipun file tersebut dicuri, isinya tetap tidak terbaca.

2. Cara Kerja Sistem (User Flow)
Aplikasi ini memiliki dua mode utama:

Mode Enkripsi (Mengunci):

Pengguna memilih file (Gambar/PDF/Txt).

Sistem membaca file tersebut.

Pengguna memasukkan password.

Sistem mengubah file menjadi format acak (ciphertext) dan otomatis mengunduhnya dengan ekstensi .encrypted.

Mode Dekripsi (Membuka):

Pengguna mengunggah file .encrypted.

Pengguna memasukkan password yang sama.

Jika password benar, file kembali ke bentuk asli dan bisa dilihat/diunduh.

3. Bedah Teknis (Di Balik Layar)
Ini adalah bagian terpenting untuk menjelaskan aspek pemrograman dan kriptografi kepada dosen:

A. Pengolahan File (File Handling) Karena kriptografi bekerja pada teks/angka, sedangkan file yang diupload bisa berupa gambar (biner), maka website ini menggunakan FileReader API.

Teknik yang dipakai adalah konversi Base64.

File gambar diubah menjadi string teks panjang (contoh: data:image/png;base64,iVBORw0K...). String inilah yang kemudian dienkripsi.

B. Algoritma Kriptografi Website ini menggunakan library CryptoJS untuk menerapkan algoritma AES (Advanced Encryption Standard).

Jenis: Symmetric Key Encryption (Kunci Simetris). Artinya, kunci (password) untuk mengunci dan membuka adalah sama.

Keamanan: AES adalah standar enkripsi yang digunakan oleh pemerintah dan bank di seluruh dunia. Sangat sulit ditembus dengan metode brute force jika password cukup panjang.

C. Client-Side Processing (Sisi Klien) Keunggulan utama kodingan ini adalah Tanpa Server (Serverless).

Semua proses hitungan matematika enkripsi terjadi di browser (laptop pengguna) menggunakan JavaScript.

Privasi: File asli tidak pernah diunggah ke cloud atau database manapun, sehingga pembuat website pun tidak bisa mengintip isinya.

D. Download Handler Setelah file dienkripsi, JavaScript membungkus hasilnya ke dalam objek Blob (Binary Large Object) lalu membuat link download virtual agar browser memaksa file tersebut tersimpan ke komputer pengguna.

4. Ringkasan Fitur (Poin Plus)
Jika ditanya apa kelebihan website ini, jawablah:

Universal: Bisa mengunci jenis file apa saja (JPG, PNG, PDF, DOCX).

Privasi Tinggi: Data diproses lokal (Local processing).

Modern UI: Menggunakan Tailwind CSS sehingga tampilan responsif dan rapi.

Indikator Keamanan: Jika password salah saat dekripsi, file tidak akan terbuka (integritas data terjaga).
