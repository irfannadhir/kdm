# GoDM — Download Manager untuk Windows

GoDM mengambil alih download dari Chrome dan Edge, lalu mengunduh dengan banyak koneksi sekaligus supaya lebih cepat. Download bisa di-pause dan dilanjutkan kapan saja, termasuk setelah aplikasi ditutup atau PC restart.

- Download multi-koneksi (default 8 koneksi per file) yang lanjut sendiri setelah internet putus
- Pause/resume yang bertahan walau PC dimatikan
- Antrean: 1–20 download berjalan sekaligus
- Scheduler: mulai dan berhenti pada jam tertentu, lalu shutdown/sleep/hibernate setelah semua selesai
- Kategori otomatis ke subfolder (Video, Musik, Dokumen, Program, Arsip)
- Tema gelap/terang, bahasa Indonesia/Inggris

## Unduh

Ambil **`godm-<versi>-windows-amd64.zip`** dari [Releases](https://github.com/irfannadhir/kdm/releases/latest).

Kebutuhan: Windows 10 (21H2+) atau Windows 11 64-bit, WebView2 Runtime (sudah ada di Windows yang diperbarui), serta Chrome dan/atau Edge versi terbaru.

## Pasang

1. Ekstrak zip, buka foldernya, klik kanan di ruang kosong → **Open in Terminal**, lalu jalankan:

   ```powershell
   powershell -ExecutionPolicy Bypass -File .\install.ps1
   ```

   Tidak perlu hak admin. Skrip ini menyalin GoDM ke `%LOCALAPPDATA%\GoDM`, mendaftarkannya ke Chrome dan Edge, dan membuat shortcut di Start Menu.

2. Pindahkan folder `extension` dari zip ke tempat permanen (misalnya `%LOCALAPPDATA%\GoDM\extension`). Lalu buka `chrome://extensions` atau `edge://extensions`, aktifkan **Developer mode**, klik **Load unpacked**, dan pilih folder tersebut.

3. Buka **GoDM** dari Start Menu, lalu klik link download apa saja di browser. Dialog **Download baru** akan muncul di GoDM.

Panduan lengkap, termasuk cara memperbarui, menghapus, dan mengatasi masalah, ada di `INSTALL.md` di dalam zip.

## Keamanan

- `godm.exe` belum ditandatangani secara digital, jadi Windows SmartScreen mungkin memperingatkan. Pilih **More info → Run anyway** hanya bila zip diunduh dari halaman Releases ini.
- Cocokkan checksum zip dengan `SHA256SUMS.txt` di halaman rilis:

  ```powershell
  Get-FileHash .\godm-1.0.0-windows-amd64.zip -Algorithm SHA256
  ```

## Menghapus

```powershell
powershell -ExecutionPolicy Bypass -File .\install.ps1 -Uninstall
```

Lalu hapus ekstensi dari halaman ekstensi browser. Database dan log tetap ada di `%LOCALAPPDATA%\GoDM` sampai folder itu dihapus.
