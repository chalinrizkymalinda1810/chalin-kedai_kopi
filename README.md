Link GitHub Pages: https://chalinrizkymalinda1810.github.io/chalin-kedai_kopi/

# Kedai Kopi — Coding 2 (CSS & Publikasi GitHub Pages)

Website **Kedai Kopi** (*Rasa yang Tak Terlupakan*) yang terdiri dari tiga halaman (`index.html`, `menu.html`, dan `pesan.html`) dan ditata dengan satu stylesheet eksternal (`css/style.css`) menggunakan konsep *Modern Cozy Coffee Shop*, pendekatan *mobile-first*, serta dipublikasikan melalui GitHub Pages.

## Jawaban Pertanyaan Refleksi (Langkah 8)

### a. Bagian yang disusun dengan Flexbox dan Grid, serta alasannya

- **Flexbox — Header / Navigasi (`.nav-inner` dan `.nav-links`)**  
  Bagian header pada ketiga halaman disusun menggunakan `display: flex`. Dengan pendekatan *mobile-first*, aturan dasarnya memakai `flex-direction: column` dan `align-items: center` agar logo Kedai Kopi dan link navigasi (`Beranda`, `Menu`, `Pesan`) tersusun ke bawah di layar ponsel. Mulai lebar `600px` (`@media (min-width: 600px)`), susunannya berubah menjadi `flex-direction: row` dengan `justify-content: space-between` sehingga logo berada di sisi kiri dan link navigasi berjajar di kanan.  
  **Mengapa Flexbox cocok:** Tata letak header bersifat **satu dimensi** (hanya satu sumbu: vertikal ke bawah di ponsel atau satu baris mendatar di tablet/desktop) dan membutuhkan distribusi ruang fleksibel kiri-kanan (`justify-content: space-between` dan `align-items: center`) tanpa perlu menentukan jumlah kolom tetap.

- **CSS Grid — Daftar Card Menu (`.menu-grid`)**  
  Pada halaman `menu.html`, card produk di kategori **Kopi** dan **Non-Kopi** disusun menggunakan `display: grid`. Aturan dasar untuk ponsel memakai `grid-template-columns: 1fr` (1 kolom), lalu di `@media (min-width: 600px)` berubah menjadi `repeat(2, 1fr)` (2 kolom), dan di `@media (min-width: 960px)` menjadi `repeat(3, 1fr)` (3 kolom) dengan jarak antarkartu yang konsisten (`gap: 1.35rem`–`1.5rem`).  
  **Mengapa CSS Grid cocok:** Daftar menu tersusun secara **dua dimensi** (baris dan kolom sekaligus) dan membutuhkan lebar kolom yang sama rata serta tinggi baris yang sejajar rapi pada setiap *breakpoint* (`375px`, `600px`, dan `960px`).

### b. Satu aturan CSS yang awalnya tidak berlaku, tampilan di panel Styles, dan cara memperbaikinya

- **Aturan yang bermasalah:** Warna latar link navigasi halaman yang sedang aktif (`aria-current="page"`) ketika diarahkan kursor (`:hover`). Awalnya, saat tombol halaman aktif (misalnya `Beranda` di `index.html`) di-hover, warna latarnya ikut berubah menjadi Caramel (`#A46C3C`) mengikuti aturan `.nav-links a:hover`, bukannya tetap Dark Coffee (`#4B2818`) seperti penanda halaman aktif.
- **Yang terlihat di panel Styles (Chrome DevTools):** Saat elemen `<a href="index.html" aria-current="page">` diinspeksi dengan state `:hover` diaktifkan di panel **Styles**, aturan `background-color: var(--dark-coffee)` pada `.nav-links a[aria-current="page"]` terlihat **tercoret (strikethrough)**. Penyebabnya, selector `.nav-links a[aria-current="page"]` dan `.nav-links a:hover` memiliki tingkat *specificity* yang setara (sama-sama 1 class, 1 elemen, dan 1 atribut/pseudo-class), sehingga aturan `.nav-links a:hover` yang menang saat state hover aktif.
- **Cara memperbaikinya:** Menambahkan selector yang lebih spesifik dengan menggabungkan penanda halaman aktif dan pseudo-class hover, yaitu `.nav-links a[aria-current="page"]:hover { background-color: var(--dark-coffee); }` pada `css/style.css`. Setelah halaman dimuat ulang, di panel **Styles** aturan tersebut muncul paling atas tanpa tercoret dan tombol halaman aktif tetap mempertahankan warna Dark Coffee saat di-hover.

---

# Kedai Kopi — Minggu 2 (Coding 1)

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
2. Jalankan `index.html` menggunakan Live Server, atau buka versi online di `https://chalinrizkymalinda1810.github.io/chalin-kedai_kopi/`.
3. Periksa tampilan responsif menggunakan Chrome DevTools **Device Toolbar** pada lebar `375px`, `600px`, `960px`, dan `1280px`.
4. Coba kirim form di `pesan.html` dalam keadaan nama atau nomor WhatsApp kosong untuk melihat validasi bawaan browser, atau isi form lengkap lalu kirim untuk melihat query string di address bar.
