# Kalkulator Interaktif

Aplikasi kalkulator web interaktif yang dibangun menggunakan HTML5, CSS3, dan Vanilla JavaScript tanpa dependensi eksternal maupun library pihak ketiga. Aplikasi ini dirancang dengan antarmuka gelap (dark theme) yang ergonomis, mendukung navigasi keyboard penuh, serta menyediakan riwayat perhitungan lokal.

---

## Daftar Isi

- [Fitur Utama](#fitur-utama)
- [Struktur Proyek](#struktur-proyek)
- [Cara Menjalankan](#cara-menjalankan)
- [Panduan Pintasan Keyboard](#panduan-pintasan-keyboard)
- [Arsitektur dan Spesifikasi Teknis](#arsitektur-dan-spesifikasi-teknis)
- [Aksesibilitas (A11y)](#aksesibilitas-a11y)
- [Penyimpanan dan Riwayat](#penyimpanan-dan-riwayat)

---

## Fitur Utama

1. **Operasi Aritmatika Lengkap**
   - Penjumlahan (`+`), Pengurangan (`-`), Perkalian (`×`), dan Pembagian (`/`).
   - Kalkulasi persentase (`%`) untuk operasi diskon atau pembagian cepat.
   - Pergantian tanda positif dan negatif (`+/-`).
   - Penanganan pembagian dengan nol dengan indikator visual kesalahan (`Error`).

2. **Panel Riwayat Perhitungan**
   - Menyimpan hingga 20 kalkulasi terakhir secara otomatis di memori peramban (`localStorage`).
   - Panel riwayat dapat dibuka-tutup dengan animasi transisi yang mulus.
   - Hasil kalkulasi pada riwayat dapat diklik untuk dimuat kembali ke layar kalkulator.

3. **Input Fleksibel (Mouse, Touch, dan Keyboard)**
   - Mendukung klik mouse dan sentuhan layar perangkat seluler.
   - Dukungan keyboard penuh: mengetik langsung dari papan tuts angka (numpad) atau baris angka atas.

4. **Tampilan Responsif dan Tipografi Adaptif**
   - Ukuran font layar angka otomatis mengecil jika jumlah digit melebihi 10 karakter agar angka tidak terpotong.
   - Tombol memenuhi standar minimum target sentuh (44px) untuk kenyamanan pengguna perangkat ponsel.

---

## Struktur Proyek

Proyek ini menggunakan struktur berkas tunggal yang mandiri sehingga sangat ringan dan portabel:

```text
kalkulator-interaktif/
├── index.html       # Kode sumber utama (struktur markup, styling CSS, dan logika JavaScript)
└── README.md        # Dokumentasi lengkap proyek
```

---

## Cara Menjalankan

Aplikasi ini tidak membutuhkan server web, bundler, Node.js, atau proses kompilasi apa pun.

### Opsi 1: Buka Langsung (Rekomendasi)
1. Unduh atau clone repositori ini ke komputer Anda.
2. Klik ganda berkas `index.html` untuk langsung membukanya di peramban favorit Anda (Google Chrome, Microsoft Edge, Mozilla Firefox, Safari, atau Opera).

### Opsi 2: Menggunakan Ekstensi Live Server (VS Code)
1. Buka folder proyek di Visual Studio Code.
2. Klik kanan pada berkas `index.html`.
3. Pilih **Open with Live Server**.

### Opsi 3: Menggunakan Python HTTP Server
Jika Anda ingin menjalankannya melalui server lokal:
```bash
# Jalankan perintah berikut di dalam direktori proyek
python -m http.server 8000
```
Lalu buka alamat `http://localhost:8000` di peramban.

---

## Panduan Pintasan Keyboard

Anda dapat mengoperasikan seluruh fungsi kalkulator tanpa mouse menggunakan tombol berikut:

| Tombol Keyboard | Aksi |
|-----------------|------|
| `0` sampai `9` | Memasukkan angka digit |
| `.` atau `,` | Memasukkan tanda koma desimal |
| `+` | Operator Tambah |
| `-` | Operator Kurang |
| `*` | Operator Kali |
| `/` | Operator Bagi |
| `Enter` atau `=` | Menjalankan perhitungan (sama dengan) |
| `Backspace` | Menghapus satu karakter/digit terakhir |
| `Escape` atau `Delete` | Membersihkan semua nilai (All Clear / AC) |

---

## Arsitektur dan Spesifikasi Teknis

### 1. Desain dan Tampilan (CSS)
- **Sistem Warna CSS Variables:** Memudahkan pemeliharaan palet warna. Menggunakan warna dasar abu-abu gelap dengan aksen warna oranye hangat (`#e87c3a`) untuk operator aktif dan tombol utama.
- **CSS Grid dan Flexbox:** Penataan tombol menggunakan CSS Grid 4 kolom yang presisi dengan pemisah garis tipis 1px.
- **Dukungan prefers-reduced-motion:** Transisi animasi otomatis dinonaktifkan jika pengguna mengaktifkan preferensi pengurangan gerakan pada sistem operasi mereka.

### 2. Logika Matematika dan Presisi (JavaScript)
- **Format Presisi:** Menggunakan `toPrecision(10)` untuk membatasi angka desimal berulang dan mencegah floating point error umum di JavaScript (contohnya `0.1 + 0.2`).
- **Batas Digit:** Dibatasi maksimal 12 digit input untuk menjaga kejelasan angka pada tampilan.
- **Notasi Eksponensial:** Angka yang terlalu besar secara otomatis diformat menggunakan notasi eksponensial (`toExponential(4)`).

---

## Aksesibilitas (A11y)

Proyek ini mematuhi prinsip aksesibilitas web:
- **Atribut ARIA:** Elemen display menggunakan `aria-live="polite"` dan `aria-atomic="true"` agar pembaca layar (screen reader) dapat mengumumkan hasil kalkulasi secara akurat.
- **Indikator Fokus Jelas:** Tombol memiliki `outline` berwarna aksen saat dinavigasi menggunakan tombol `Tab`.
- **Target Sentuh yang Ergonomis:** Seluruh tombol memenuhi ukuran standar interaksi tangan manusia agar nyaman ditekan di smartphone maupun tablet.

---

## Penyimpanan dan Riwayat

- Riwayat kalkulasi disimpan pada antarmuka penyimpanan web peramban (`localStorage`) dengan kunci `calc-history`.
- Data riwayat tetap tersimpan meskipun peramban ditutup atau halaman dimuat ulang.
- Riwayat dibatasi hingga 20 kalkulasi terbaru secara otomatis untuk menjaga performa dan kerapian antarmuka.
