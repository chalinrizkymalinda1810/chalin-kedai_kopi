# Kedai Kopi — Minggu 2

## Jawaban langkah 6

### a. Data pada address bar setelah form dikirim

Setelah form dikirim, address bar berisi alamat `pesan.html` yang diikuti tanda tanya (`?`) dan pasangan nama-nilai dari setiap field, misalnya:

```
pesan.html?nama=Alya&whatsapp=08123456789&menu=cappuccino&jumlah=2&cara_ambil=ambil-di-tempat&catatan=Tanpa+gula
```

Data itu terlihat di address bar karena form memakai `method="get"`. Pada metode HTTP GET, browser mengirim data form sebagai query string di URL. Berbeda dengan POST, data tidak ditempatkan di bagian body request. Karena itu GET cocok untuk data yang aman ditampilkan dan dapat dibookmark, tetapi tidak cocok untuk kata sandi atau data rahasia.

### b. Contoh penggunaan element semantic

Bagian navigasi di setiap halaman menggunakan element `<nav>`, bukan `<div>`. Saya memilih `<nav>` karena bagian ini memang berisi kumpulan link untuk berpindah antarhalaman. Element semantic tersebut memberi makna yang jelas kepada browser, pembaca layar, dan orang yang membaca kode: ini adalah navigasi utama. `<div>` hanya menjadi wadah umum dan tidak menjelaskan fungsi isinya.

## Cara menjalankan

1. Buka folder ini di VS Code.
2. Jalankan `index.html` menggunakan Live Server.
3. Coba kirim form di `pesan.html` dalam keadaan nama atau nomor WhatsApp kosong untuk melihat validasi bawaan browser.
4. Isi form lengkap lalu kirim. Perhatikan query string yang muncul di address bar.
