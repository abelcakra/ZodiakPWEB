# Program Penentu Zodiak (Node.js CLI)

Program ini adalah aplikasi sederhana berbasis terminal menggunakan JavaScript (Node.js) untuk menentukan zodiak berdasarkan tanggal dan bulan lahir yang dimasukkan oleh pengguna.

---

## Cara Menjalankan Program

1. Pastikan Node.js sudah terinstall di komputer
2. Buka terminal pada folder project
3. Jalankan perintah:

```bash
node zodiak.js
```

4. Masukkan tanggal dan bulan lahir sesuai instruksi

---

## Penjelasan Kode Program

Berikut penjelasan setiap bagian pada file **zodiak.js**.

### 1. Import Modul readline
```js
const readline = require("readline");
```
Kode ini digunakan untuk mengambil modul bawaan Node.js bernama **readline**.  
Modul ini berfungsi untuk membaca input dari user melalui terminal.

---

### 2. Membuat Interface Terminal
```js
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});
```
Bagian ini membuat koneksi antara program dan terminal sehingga program bisa menerima input dari keyboard dan menampilkan teks ke layar.

---

### 3. Fungsi getZodiac
```js
function getZodiac(day, month) {
  if ((month === 3 && day >= 21) || (month === 4 && day <= 19)) return "Aries";
  if ((month === 4 && day >= 20) || (month === 5 && day <= 20)) return "Taurus";
  if ((month === 5 && day >= 21) || (month === 6 && day <= 20)) return "Gemini";
  if ((month === 6 && day >= 21) || (month === 7 && day <= 22)) return "Cancer";
  if ((month === 7 && day >= 23) || (month === 8 && day <= 22)) return "Leo";
  if ((month === 8 && day >= 23) || (month === 9 && day <= 22)) return "Virgo";
  if ((month === 9 && day >= 23) || (month === 10 && day <= 22)) return "Libra";
  if ((month === 10 && day >= 23) || (month === 11 && day <= 21)) return "Scorpio";
  if ((month === 11 && day >= 22) || (month === 12 && day <= 21)) return "Sagittarius";
  if ((month === 12 && day >= 22) || (month === 1 && day <= 19)) return "Capricorn";
  if ((month === 1 && day >= 20) || (month === 2 && day <= 18)) return "Aquarius";
  if ((month === 2 && day >= 19) || (month === 3 && day <= 20)) return "Pisces";
  return "Tanggal tidak valid";
}
```
Fungsi ini berfungsi untuk menentukan zodiak berdasarkan tanggal dan bulan lahir.  
Setiap kondisi `if` mewakili rentang tanggal suatu zodiak.

Contoh:
```
(month === 3 && day >= 21) || (month === 4 && day <= 19)
```
Artinya: Aries = 21 Maret – 19 April.

---

### 4. Input Tanggal dan Bulan Lahir
```js
rl.question("Masukkan tanggal lahir (1-31): ", (dayInput) => {
  rl.question("Masukkan bulan lahir (1-12): ", (monthInput) => {
```
Program meminta pengguna memasukkan tanggal dan bulan lahir melalui terminal.

---

### 5. Konversi Input ke Angka
```js
const day = parseInt(dayInput);
const month = parseInt(monthInput);
```
Input dari terminal berupa teks (string).  
`parseInt` digunakan untuk mengubahnya menjadi angka agar bisa diproses.

---

### 6. Validasi Input
```js
if (isNaN(day) || isNaN(month) || day < 1 || day > 31 || month < 1 || month > 12)
```
Kode ini mengecek apakah:
- input bukan angka
- tanggal di luar 1–31
- bulan di luar 1–12  

Jika tidak valid maka program menampilkan pesan kesalahan.

---

### 7. Menentukan Zodiak
```js
const zodiac = getZodiac(day, month);
```
Program memanggil fungsi `getZodiac` untuk mendapatkan zodiak berdasarkan tanggal dan bulan lahir.

---

### 8. Menampilkan Output
```js
console.log("\n=== HASIL ===");
console.log("Tanggal lahir :", day);
console.log("Zodiak        :", zodiac);
```
Bagian ini menampilkan hasil akhir berupa tanggal lahir dan zodiak pengguna.

---

### 9. Menutup Program
```js
rl.close();
```
Digunakan untuk menutup proses input terminal setelah program selesai dijalankan.

---

## Contoh Output Program

### Percobaan 1
```
Masukkan tanggal lahir (1-31): 09
Masukkan bulan lahir (1-12): 7

=== HASIL ===
Tanggal lahir : 09
Zodiak        : Cancer
```

### Percobaan 2
```
Masukkan tanggal lahir (1-31): 30
Masukkan bulan lahir (1-12): 12

=== HASIL ===
Tanggal lahir : 30
Zodiak        : Capricorn
```

### Percobaan 3
```
Masukkan tanggal lahir (1-31): 1
Masukkan bulan lahir (1-12): 3

=== HASIL ===
Tanggal lahir : 1
Zodiak        : Pisces
```

---

## Screenshot Percobaan

Tambahkan screenshot hasil terminal di bawah ini:

![Percobaan 1](ss1.png)
![Percobaan 2](ss2.png)
![Percobaan 3](ss3.png)

---

## Kesimpulan

Program berhasil menentukan zodiak berdasarkan tanggal dan bulan lahir yang dimasukkan pengguna melalui terminal menggunakan JavaScript (Node.js).  
Program juga melakukan validasi input sehingga hanya menerima tanggal dan bulan yang valid.
