# KDM — Download Manager for Windows

KDM takes over downloads from Chrome and Edge and fetches them over many connections at once, so they finish faster. Downloads can be paused and resumed at any time, even after the app is closed or the PC restarts.

- Multi-connection downloads (8 connections per file by default) that resume by themselves after the internet drops
- Pause/resume that survives turning the PC off
- Queue: 1–20 downloads running at once
- Scheduler: start and stop at set times, then shut down, sleep, or hibernate when everything is done
- Automatic categories into subfolders (Video, Music, Documents, Programs, Archives)
- Streaming video (HLS) saved as a single MP4, from a button on the video in the browser
- Dark/light theme, Indonesian/English interface
- Updates from inside the app: the new version is downloaded and installed without a wizard

## Download

Get **`kdm-<version>-setup.exe`** from [Releases](https://github.com/irfannadhir/kdm/releases/latest).

There is also `kdm-<version>-windows-amd64.zip` for portable use or scripted installation.

Requirements: Windows 10 (21H2+) or Windows 11, 64-bit, the WebView2 Runtime (already on an updated Windows), and a current Chrome and/or Edge.

## Install

1. Double-click `kdm-<version>-setup.exe` and follow the wizard. No administrator rights and no UAC prompt are needed: KDM is installed for your own account in `%LOCALAPPDATA%\KDM`, registered with Chrome and Edge, and appears in the Start menu and in the Windows list of apps.

2. Install the browser extension once: open `chrome://extensions` or `edge://extensions`, turn on **Developer mode**, click **Load unpacked**, and pick `%LOCALAPPDATA%\KDM\extension` (the last page of the wizard has a button that opens that folder). The extension is not in the Chrome Web Store yet, so this step cannot be automated.

3. Open **KDM** from the Start menu, then click any download link in the browser. KDM shows its **New download** question.

The full guide, including updating, uninstalling, and troubleshooting, is in `INSTALL.md` inside the zip.

## Security

- `kdm.exe` is not digitally signed yet, so Windows SmartScreen may warn you. Choose **More info → Run anyway** only if you downloaded the file from this Releases page.
- Compare the checksum of the downloaded file with `SHA256SUMS.txt` on the release page:

  ```powershell
  Get-FileHash .\kdm-1.0.0-setup.exe -Algorithm SHA256
  ```

- Like browser downloads, files downloaded by KDM are marked as coming from the internet (Mark of the Web), so Windows SmartScreen still checks programs before they run and Office opens documents in Protected View.
- In-app updates only download the installer from this Releases page over HTTPS, and install it only when its checksum matches the `SHA256SUMS.txt` of the same release.

## Uninstall

**Settings → Apps → Installed apps → KDM → Uninstall** (or search for "KDM" in the Start menu and choose **Uninstall**). Then remove the extension from the browser's extensions page. The database and logs stay in `%LOCALAPPDATA%\KDM` until you delete that folder.

For a portable installation: `powershell -ExecutionPolicy Bypass -File .\install.ps1 -Uninstall`.
