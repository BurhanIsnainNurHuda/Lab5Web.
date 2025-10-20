## Praktikum 5 - Validasi Form (Lab5Web)

    Nama: Burhan Isnain Nur Huda 
    NIM: 312410266 
    Kelas: TI.24.A.2
    Mata Kuliah: Pemograman Web 1

Tujuan
Mempelajari cara membuat form dengan validasi input menggunakan JavaScript, agar data yang dimasukkan user sesuai aturan sebelum dikirim.

## 1. Struktur Dasar HTML

    <!DOCTYPE html>
    <html lang="id">
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validasi Form</title>

Penjelasan:

``<!DOCTYPE html>`` → Menandakan dokumen ini adalah HTML5.

``<html lang="id">`` → Menentukan bahasa halaman yaitu Bahasa Indonesia.

``<meta charset="UTF-8">`` → Agar karakter seperti huruf é atau simbol lain bisa ditampilkan dengan benar.

``<meta name="viewport"`` ...> → Supaya tampilan web menyesuaikan layar HP atau laptop.

``<title>`` → Menampilkan judul di tab browser.

## 2. Bagian CSS 

    <style>
    body {
        font-family: Arial, sans-serif;
        background-color: #222;
        color: #eee;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

Penjelasan:

``font-family`` → Mengatur jenis huruf jadi lebih modern (Arial).

``background-color: #222`` → Memberikan warna hitam keabu-abuan pada background.

``display: flex; justify-content: center; align-items: center;`` → Memposisikan form di tengah halaman secara vertikal dan horizontal.

``height: 100vh`` → Tinggi halaman 100% dari layar pengguna.

    form {
    background-color: #333;
    padding: 20px;
    border-radius: 15px;
    width: 350px;
    box-shadow: 0 0 10px rgba(255,255,255,0.2);
    }
 
Penjelasan:

``background-color: #333`` → Warna abu tua untuk form.

``padding`` → Memberi jarak antara isi form dengan pinggirannya.

``border-radius`` → Membuat sudut form jadi melengkung.

``box-shadow`` → Menambah efek bayangan supaya form terlihat timbul.

    button {
    margin-top: 15px;
    width: 100%;
    background-color: #00ffcc;
    border: none;
    padding: 10px;
    font-weight: bold;
    border-radius: 5px;
    cursor: pointer;
    }
    button:hover {
    background-color: #00bfa5;
    }

Penjelasan:

``background-color: #00ffcc`` → Warna tombol biru kehijauan agar kontras.

``cursor: pointer`` → Saat diarahkan ke tombol, pointer berubah jadi tangan.

``:hover`` → Efek ketika mouse diarahkan ke tombol, warnanya sedikit berubah agar terlihat interaktif.

## 3. Struktur Form HTML
   
    <form id="myForm" onsubmit="return validasiForm()">
    <h2>Form Validasi</h2>
    <label>Nama:</label>
    <input type="text" id="nama" placeholder="Masukkan nama">
    <span id="errorNama" class="error"></span>

Penjelasan:

``<form id="myForm" onsubmit="return validasiForm()">`` → Setiap kali tombol submit diklik, fungsi validasiForm() akan dijalankan.

``placeholder`` → Menampilkan teks petunjuk di dalam kotak input.

``<span id="errorNama">`` → Tempat menampilkan pesan error kalau input salah.

    <label>Email:</label>
    <input type="email" id="email" placeholder="Masukkan email">
    <span id="errorEmail" class="error"></span>

    <label>Umur:</label>
    <input type="number" id="umur" placeholder="Masukkan umur">
    <span id="errorUmur" class="error"></span>

    <button type="submit">Kirim</button>

Penjelasan:

``type="email"`` → Hanya menerima format email.

``type="number"`` → Hanya bisa diisi angka.

``span`` di bawah setiap input digunakan untuk menampilkan pesan kesalahan masing-masing.

## 4. Script JavaScript (Validasi Form)
   
       <script>
       function validasiForm() {
        let nama = document.getElementById("nama").value.trim();
        let email = document.getElementById("email").value.trim();
        let umur = document.getElementById("umur").value.trim();
        let valid = true;

Penjelasan:

``getElementById`` → Mengambil nilai dari input berdasarkan ``id``.

``.trim()`` → Menghapus spasi di awal dan akhir input supaya tidak dihitung kosong padahal ada spasi.

``valid = true`` → Sebagai penanda bahwa form valid, nanti bisa berubah ``false`` kalau ada kesalahan.

    document.getElementById("errorNama").innerText = "";
    document.getElementById("errorEmail").innerText = "";
    document.getElementById("errorUmur").innerText = "";
 
Penjelasan:

Baris ini menghapus semua pesan error sebelumnya setiap kali tombol submit ditekan, agar pesan lama tidak tertumpuk.

    if (nama === "") {
    document.getElementById("errorNama").innerText = "Nama tidak boleh kosong";
    valid = false;
    }
    
Penjelasan:

``Jika kolom nama kosong`` → muncul pesan ``“Nama tidak boleh kosong”``, dan variabel ``valid`` diubah menjadi ``false`` (form tidak akan dikirim).

    if (email === "" || !email.includes("@")) {
    document.getElementById("errorEmail").innerText = "Email tidak valid";
    valid = false;
    }
    
Penjelasan:

Mengecek apakah email kosong atau tidak mengandung simbol ``@.`` Kalau salah, tampilkan pesan error.

    if (umur === "" || umur < 17) {
    document.getElementById("errorUmur").innerText = "Umur minimal 17 tahun";
    valid = false;
    }

Penjelasan:

Cek apakah umur kosong atau kurang dari 17 tahun.
``Jika iya`` → muncul pesan error dan form tidak akan dikirim.

    if (valid) {
    alert("Form berhasil dikirim!");
    }
    return valid;
    
Penjelasan:

Jika semua input benar ``(valid == true)``, muncul pop-up pemberitahuan bahwa form berhasil dikirim.
``return valid`` membuat form tidak terkirim kalau ada error (karena ``false`` menghentikan proses submit).

## 5. Kesimpulan

Dari praktikum ini, saya belajar bahwa validasi form sangat penting untuk mencegah data kosong atau salah format sebelum dikirim ke server.
Selain itu, dengan menggunakan JavaScript, proses pengecekan bisa dilakukan langsung di browser tanpa harus reload halaman.

## 6. Hasil ScreenShoot
<img width="1919" height="956" alt="image" src="https://github.com/user-attachments/assets/80819fbe-263d-4dcb-b933-5f8c209f4fe6" />

