# GoDM — Download Manager untuk Windows

GoDM mengambil alih download dari Chrome dan Edge, lalu mengunduh dengan banyak koneksi sekaligus supaya lebih cepat. Download bisa di-pause dan dilanjutkan kapan saja, termasuk setelah aplikasi ditutup atau PC restart.

- Download multi-koneksi (default 8 koneksi per file) yang lanjut sendiri setelah internet putus
- Pause/resume yang bertahan walau PC dimatikan
- Antrean: 1–20 download berjalan sekaligus
- Scheduler: mulai dan berhenti pada jam tertentu, lalu shutdown/sleep/hibernate setelah semua selesai
- Kategori otomatis ke subfolder (Video, Musik, Dokumen, Program, Arsip)
- Tema gelap/terang, bahasa Indonesia/Inggris

## Unduh

Ambil **`godm-<versi>-setup.exe`** dari [Releases](https://github.com/irfannadhir/kdm/releases/latest).

Ada juga `godm-<versi>-windows-amd64.zip` untuk pemakaian portable atau pemasangan lewat skrip.

Kebutuhan: Windows 10 (21H2+) atau Windows 11 64-bit, WebView2 Runtime (sudah ada di Windows yang diperbarui), serta Chrome dan/atau Edge versi terbaru.

## Pasang

1. Klik dua kali `godm-<versi>-setup.exe` dan ikuti wizard-nya. Tidak perlu hak admin dan tidak ada prompt UAC: GoDM dipasang untuk akun kamu sendiri di `%LOCALAPPDATA%\GoDM`, terdaftar ke Chrome dan Edge, dan muncul di Start Menu serta di daftar aplikasi Windows.

2. Pasang ekstensinya sekali: buka `chrome://extensions` atau `edge://extensions`, aktifkan **Developer mode**, klik **Load unpacked**, lalu pilih `%LOCALAPPDATA%\GoDM\extension` (halaman terakhir wizard punya tombol untuk membuka folder itu). Ekstensi belum ada di Chrome Web Store, jadi langkah ini belum bisa diotomatiskan.

3. Buka **GoDM** dari Start Menu, lalu klik link download apa saja di browser. Dialog **Download baru** akan muncul di GoDM.

Panduan lengkap, termasuk cara memperbarui, menghapus, dan mengatasi masalah, ada di `INSTALL.md` di dalam zip.

## Keamanan

- `godm.exe` belum ditandatangani secara digital, jadi Windows SmartScreen mungkin memperingatkan. Pilih **More info → Run anyway** hanya bila berkasnya diunduh dari halaman Releases ini.
- Cocokkan checksum berkas yang diunduh dengan `SHA256SUMS.txt` di halaman rilis:

  ```powershell
  Get-FileHash .\godm-1.0.0-setup.exe -Algorithm SHA256
  ```

## Menghapus

**Settings → Apps → Installed apps → GoDM → Uninstall** (atau cari "GoDM" di Start Menu lalu pilih **Uninstall**). Lalu hapus ekstensi dari halaman ekstensi browser. Database dan log tetap ada di `%LOCALAPPDATA%\GoDM` sampai folder itu dihapus.

Untuk pemasangan portable: `powershell -ExecutionPolicy Bypass -File .\install.ps1 -Uninstall`.
