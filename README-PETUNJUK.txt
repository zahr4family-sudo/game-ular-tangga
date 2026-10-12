# Game Ular Tangga Islami — KKG PAI Kabupaten Bandung

## Menjalankan offline
1. Ekstrak seluruh isi ZIP ke satu folder.
2. Buka `ular-tangga-islami-leaderboard.html` di Chrome/Edge.
3. Klik **Mulai Bermain** pada sampul.
4. File papan, gambar pion, logo dan audio harus tetap berada di folder yang sama.

## Fitur yang ditambahkan
- Sampul dengan logo KKG PAI Kabupaten Bandung.
- Kuis saat mendarat di pangkal tangga atau ekor ular.
- Batas waktu kuis dapat diubah (default 15 detik).
- Jika jawaban benar: naik tangga atau maju satu kotak untuk menghindari ular.
- Jika jawaban salah/waktu habis: batal naik tangga (mundur satu kotak) atau turun oleh ular.
- Jika pion mendarat pada kotak yang ditempati pion lain (selain START/FINISH), pion yang lebih dulu berada di kotak itu kembali ke START dan audio Astaghfirullah diputar.
- Impor soal CSV dengan pemisah kolom berupa satu karakter backslash (`\`); untuk pilihan gunakan pemisah `|`.
- Prompt AI pembuat soal tersedia di panel pengaturan.
- Tombol buat link online menggunakan Firebase Realtime Database.

## Format CSV
Kolom wajib `soal` dan `jawaban`; `jenis` opsional. Format yang disarankan:
`jenis\soal\opsi\jawaban`

Nilai `jenis`: `pg`, `bs`, atau `anagram`.
- `pg`: opsi dipisahkan `|`, jawaban harus sama persis dengan teks opsi yang benar.
- `bs`: opsi `Benar|Salah`, jawaban `Benar` atau `Salah`.
- `anagram`: jawaban adalah kata hasil susunan huruf.

## Mengaktifkan tautan online Firebase
Konfigurasi proyek Firebase sudah ditambahkan ke HTML. Fitur link online memakai REST API Realtime Database pada jalur `/sharedGames`.
Agar fitur bekerja, Firebase Realtime Database harus mengizinkan pembacaan dan penulisan pada jalur tersebut. **Jangan membuka akses baca/tulis publik secara permanen untuk penggunaan nyata**, karena siapa pun dapat membaca, mengubah, atau menghapus data. Untuk pemakaian publik yang aman, tambahkan Firebase Authentication dan aturan keamanan yang membatasi akses; aplikasi saat ini belum menerapkan login Firebase. Jika aturan database menolak permintaan, game offline tetap dapat dimainkan.

Catatan: link unik online menyimpan konfigurasi soal dan waktu kuis, bukan sesi permainan multiplayer real-time.
