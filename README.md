# Program Penentu Zodiak (Node.js CLI)

Program ini merupakan program sederhana menggunakan JavaScript yang dijalankan melalui terminal (Node.js).  
Program akan meminta pengguna memasukkan tanggal dan bulan lahir, kemudian menentukan zodiak berdasarkan input tersebut.

## Cara Menjalankan Program

1. Pastikan Node.js sudah terinstall di komputer
2. Buka terminal pada folder project
3. Jalankan perintah berikut:
   ```bash
   node zodiak.js
   ```
4. Masukkan tanggal dan bulan lahir sesuai yang diminta program

## Penjelasan Kode

Program ini menggunakan modul bawaan Node.js yaitu `readline` untuk membaca input dari terminal.

```js
const readline = require("readline");
```

Kode berikut digunakan untuk membuat koneksi antara program dan terminal, sehingga program bisa menerima input dari keyboard dan menampilkan hasil ke layar.

```js
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});
```

Selanjutnya terdapat fungsi `getZodiac` yang berisi logika penentuan zodiak berdasarkan tanggal dan bulan lahir.  
Setiap kondisi `if` mewakili rentang tanggal dari masing-masing zodiak.

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

Program kemudian meminta pengguna memasukkan tanggal dan bulan lahir melalui terminal.

```js
rl.question("Masukkan tanggal lahir (1-31): ", (dayInput) => {
  rl.question("Masukkan bulan lahir (1-12): ", (monthInput) => {
```

Karena input dari terminal berupa teks, maka diubah menjadi angka menggunakan `parseInt`.

```js
const day = parseInt(dayInput);
const month = parseInt(monthInput);
```

Setelah itu program mengecek apakah input yang dimasukkan valid (angka dan dalam rentang yang benar).

```js
if (isNaN(day) || isNaN(month) || day < 1 || day > 31 || month < 1 || month > 12)
```

Jika valid, program memanggil fungsi penentu zodiak lalu menampilkan hasilnya di terminal.

```js
const zodiac = getZodiac(day, month);
console.log("Tanggal lahir :", day);
console.log("Zodiak        :", zodiac);
```

Terakhir, proses input ditutup dengan `rl.close()` agar program selesai dijalankan.

## Contoh Output

Percobaan 1
```
Masukkan tanggal lahir (1-31): 09
Masukkan bulan lahir (1-12): 7

Tanggal lahir : 09
Zodiak        : Cancer
```

Percobaan 2
```
Masukkan tanggal lahir (1-31): 30
Masukkan bulan lahir (1-12): 12

Tanggal lahir : 30
Zodiak        : Capricorn
```

Percobaan 3
```
Masukkan tanggal lahir (1-31): 1
Masukkan bulan lahir (1-12): 3

Tanggal lahir : 1
Zodiak        : Pisces
```

## Screenshot

![Percobaan 1](ss1.png)  
![Percobaan 2](ss2.png)  
![Percobaan 3](ss3.png)

## Kesimpulan

Program ini dapat menentukan zodiak berdasarkan tanggal dan bulan lahir yang dimasukkan melalui terminal menggunakan Node.js.  
Selain itu, program juga melakukan pengecekan input sehingga hanya menerima tanggal dan bulan yang valid.
