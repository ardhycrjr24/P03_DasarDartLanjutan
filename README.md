# P03 - Dasar Dart Lanjutan

> **Nama:** Ardiansyah
> **Kelas:** Rekayasa Perangkat Lunak (RPL)
> **Mata Kuliah:** Pemrograman Multiplatform
> **Politeknik Negeri Bengkalis**

Praktikum 3: membuat aplikasi Dart berbasis console untuk mempelajari dasar-dasar pemrograman Dart lanjutan — operator (penugasan, aritmatika, relasional, logika, bitwise, string) dan struktur kontrol (if, switch, perulangan, kontrol alur).

## Alat & Bahan

- macOS (Apple Silicon)
- Dart SDK 3.13.2 (via Flutter SDK)
- Visual Studio Code + ekstensi Flutter & Dart

## Cara Menjalankan

Jalankan dari terminal di dalam folder ini:

```bash
dart run ex1_operator_penugasan.dart
```

Khusus file yang butuh input keyboard (`ex6`, `ex8`, `ex12`–`ex18`, `ex24`), jalankan lewat terminal lalu ketik nilainya.

Di VS Code: buka file `.dart` lalu tekan **F5** atau klik tombol **▶ Run** di pojok kanan atas editor.

## Daftar Program

| No | File | Materi |
|----|------|--------|
| 1 | `ex1_operator_penugasan.dart` | Operator penugasan (`+=`, `-=`, `*=`, `~/=`, `/=`) |
| 2 | `ex2_operator_aritmatika.dart` | Operator aritmatika (`+`, `-`, `*`, `/`, `~/`, `%`) |
| 3 | `ex3_operator_increament.dart` | Operator inkrement (`++a` vs `a++`) |
| 4 | `ex4_operator_decreament.dart` | Operator dekrement (`--a` vs `a--`) |
| 5 | `ex5_operator_relasional.dart` | Operator relasional (`==`, `!=`, `>`, `>=`, `<`, `<=`) |
| 6 | `ex6_operator_relasional_do.dart` | Penerapan relasional + `do-while` (tolak b = 0) |
| 7 | `ex7_operator_logika.dart` | Operator logika (`&&`, `\|\|`, `!`) |
| 8 | `ex8_operator_logika_imp.dart` | Implementasi logika (validasi nilai 0..9) |
| 9 | `ex9_operator_bitwise.dart` | Operator bitwise (`&`, `\|`, `^`, `~`, `<<`, `>>`) |
| 10 | `ex10_operator_string.dart` | Operator string (membalik string dengan loop) |
| 11 | `ex11_operator_lainnya.dart` | Operator lainnya (`is`, `as`, ternary, `??`) |
| 12 | `ex12_if_1.dart` | `if` satu kondisi |
| 13 | `ex13_if_2.dart` | `if` dua kondisi (`if-else`) |
| 14 | `ex14_if_3.dart` | `if` tiga kondisi (`if-else if-else`) |
| 15 | `ex15_if_3++.dart` | `if` lebih dari tiga kondisi (nama bulan) |
| 16 | `ex16_switch.dart` | Struktur pemilihan `switch-case` |
| 17 | `ex17_while.dart` | Perulangan `while` (rata-rata data) |
| 18 | `ex18_do_while.dart` | Perulangan `do-while` (login berulang) |
| 19 | `ex19_for.dart` | Perulangan `for` dan for-each list |
| 20 | `ex20_for_each.dart` | Perulangan `forEach` pada List dan Map |
| 21 | `ex21_break.dart` | Perintah `break` |
| 22 | `ex22_continue.dart` | Perintah `continue` |
| 23 | `ex23_return.dart` | Perintah `return` |
| 24 | `ex24_exit.dart` | Perintah `exit()` + `switch` nama hari |

## Catatan Perbaikan Kode

Kode pada modul ditulis untuk Dart versi lama, disesuaikan dengan null safety Dart 3:

- Semua `stdin.readLineSync()` ditambahkan `!` karena mengembalikan `String?`
- `ex11` — `num a` menjadi `num? a` agar bisa di-set `null`, `int maks` menjadi `int maks = ...toInt()` karena hasil ternary bertipe `num`
- `ex9` — typo modul `']nBitwise OR'` diperbaiki menjadi `'\nBitwise OR'`
- `ex2` — variabel `c` dibiarkan (sesuai modul) walau muncul warning *unused variable*
- Warning `dart analyze` lainnya (`unnecessary_type_check`, `dead_code`) disengaja ada pada kode modul untuk keperluan pembelajaran

## Pemahaman Program (Tugas Praktikum)

### 1. Operator (ex1–ex11)

- **ex1 — Operator penugasan:** variabel `a` diinialisasi 3, lalu diubah bertahap dengan `+= 2` (5), `-= 1` (4), `*= 2` (8), `~/= 3` (2). Operator `~/` adalah bagi bulat, sehingga hasilnya int. `b = 7` kemudian `b /= a` menghasilkan `3.5` karena `/` selalu menghasilkan `double`.
- **ex2 — Operator aritmatika:** dengan `a = 10` dan `b = 3`: penjumlahan 13, pengurangan 7, perkalian 30, pembagian `3.333...` (double), bagi bulat `~/` = 3, sisa bagi `%` = 1. Pembagian `/` selalu double sedangkan `~/` membuang pecahannya.
- **ex3 — Inkrement:** `++a` (pre) menambah nilai **lebih dulu** sehingga cetakan hasil langsung 10, sedangkan `b++` (post) mengembalikan nilai **lama** dulu (9), baru variabel bertambah — nilai akhir tetap 10.
- **ex4 — Dekrement:** prinsipnya sama dengan inkrement, hanya arahnya kebalikan: `--a` → 8, `b--` → menampilkan 9 lalu nilai akhir 8.
- **ex5 — Relasional:** membandingkan `a = 9` dan `b = 10`. Semua perbandingan menghasilkan `bool` (`9 == 10` false, `9 < 10` true, dll.).
- **ex6 — Penerapan relasional:** `do-while` berulang selama `b == 0` sehingga pembagian `a / b` tidak pernah dibagi nol. Hasil `10 / 2 = 5.0`.
- **ex7 — Logika AND/OR/NOT:** AND hanya `true` jika kedua operand `true`; OR hanya `false` jika kedua operand `false`; NOT membalik nilai. Karena ekspresinya konstan, analyzer menandai *dead code* — tetapi tetap dipertahankan untuk pembelajaran.
- **ex8 — Implementasi logika:** kondisi `a >= 0 && a <= 9` memvalidasi rentang input; jika salah maka ditampilkan pesan kesalahan.
- **ex9 — Bitwise:** `120 & 127 = 120`, `120 | 127 = 127`, `120 ^ 127 = 7` (karena 120 = `1111000b`, 127 = `1111111b`). `~` membalik bit (komplemen dua's, hasil negatif), `<<` menggeser bit ke kiri (dikalikan 2), `>>` ke kanan (dibagi 2).
- **ex10 — String:** fungsi `reverseString` menyusun ulang string dari indeks terakhir ke awal, sehingga `'Rekayasa Perangkat Lunak'` menjadi `'kanuL takgnareP asayakeR'`.
- **ex11 — Operator lainnya:** `is`/`is!` mengecek tipe data, `as` melakukan casting (`isOdd`/`isEven`), ternary `a > b ? a : b` memilih nilai maksimum (10), dan `??` mengambil nilai pengganti saat `a = null` sehingga `c = 10`.

### 2. Struktur Pemilihan (ex12–ex16)

- **ex12** — hanya mencetak jika bilangan positif (tanpa `else`), input negatif/nol tidak menghasilkan output.
- **ex13** — `if-else` membuat dua kemungkinan: positif atau bukan positif.
- **ex14** — `if-else if-else` membedakan tiga kondisi: positif, nol (0), negatif.
- **ex15** — deret `else if` memetakan nomor bulan 1–12 ke nama bulan; di luar rentang memanggil `exit(1)` dan program berhenti dengan status error.
- **ex16** — `switch-case` melakukan hal yang sama seperti ex15 tetapi lebih ringkas dan rapi; `break` mencegah *fall-through* ke case berikutnya, `default` menangani input salah.

### 3. Perulangan (ex17–ex20)

- **ex17 — while:** mencetak Baris 0–4, lalu membaca `n` data dan menjumlahkannya. Dengan 3 data (10, 20, 30): Jumlah = 60.0, Rata-rata = 20.0. Loop berjalan selama kondisi `i < n` terpenuhi.
- **ex18 — do-while:** badan loop dijalankan **sekali dulu** baru dicek kondisinya — cocok untuk login: program tetap meminta username/password berulang sampai benar (`admin`/`demo123`).
- **ex19 — for:** loop klasik `for (int i = 0; i < 5; i++)` mencetak Baris 0–4; lalu `for-in` mengiterasi tiap elemen list `[10, 20, 30, 40, 50]`.
- **ex20 — forEach:** `list.forEach` mencetak tiap elemen, `map.forEach` mencetak pasangan key-value (mis. `'one' artinya 'satu'`).

### 4. Kontrol Alur (ex21–ex24)

- **ex21 — break:** menghentikan loop **total** saat `i == 3`, sehingga output hanya `0 1 2 3`.
- **ex22 — continue:** melewati iterasi yang ganjil-genap (`i.isEven`), loop tetap jalan sampai selesai — output hanya bilangan ganjil `1 3 5 7 9`.
- **ex23 — return:** mengembalikan hasil dari fungsi; jika salah satu faktor 0 langsung `return 0`, selain itu `8 * 9 = 72.0`.
- **ex24 — exit():** validasi input 1..7; jika salah mencetak pesan lalu `exit(1)` menghentikan program dengan kode error 1 (terbukti `exit=1` saat diuji input 9). Jika valid, `switch` menampilkan nama hari (5 → Kamis).

---
