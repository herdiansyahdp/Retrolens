# RetroLens 🖐️✨

Portal filter real-time pakai gerakan tangan, dibuat dengan Python, OpenCV, dan MediaPipe.

Bentangkan dua tangan untuk membuka portal. Area di dalamnya akan terkena filter (dual-tone, thermal, sketch, glitch, dan lainnya). Ganti filter dengan pinch jempol dan kelingking.

> Proyek ini adalah turunan dari [Retrolens oleh syahdanfx](https://github.com/syahdanfx/Retrolens) (MIT License), diperbarui agar jalan di Python 3.13+.

## Perubahan dari versi asli

- Deteksi tangan dipindah dari `mp.solutions` (API lama yang sudah tidak ada di MediaPipe terbaru) ke **MediaPipe Tasks API** (`HandLandmarker`).
- Gambar landmark tangan sekarang digambar manual dengan OpenCV.
- Dependensi dikunci ke `mediapipe==1.2.3`.
- Filter, logika portal, mode 2D/3D, dan kontrol tetap sama.

## Persyaratan

- Python **3.13 atau lebih baru**
- Webcam
- Sudah diuji di Windows dengan Python 3.13. Di macOS/Linux belum diuji.

## Instalasi

```bash
python -m venv venv
```

Aktifkan venv:

```bash
# Windows (PowerShell)
.\venv\Scripts\Activate.ps1

# macOS / Linux
source venv/bin/activate
```

Install dependensi:

```bash
python -m pip install -r requirements.txt
```

> Jangan install `opencv-python` bersamaan dengan `opencv-contrib-python`, karena modul `cv2` bisa bentrok.

## Download model

Aplikasi butuh file model `hand_landmarker.task` di folder yang sama dengan `Retrolens.py`. File ini tidak disertakan di repo, jadi unduh dulu:

```bash
curl -L -o hand_landmarker.task "https://storage.googleapis.com/mediapipe-models/hand_landmarker/hand_landmarker/float16/latest/hand_landmarker.task"
```

Di Windows PowerShell, pakai `curl.exe` (bukan `curl`):

```powershell
curl.exe -L -o hand_landmarker.task "https://storage.googleapis.com/mediapipe-models/hand_landmarker/hand_landmarker/float16/latest/hand_landmarker.task"
```

Atau buka URL itu di browser, lalu pindahkan file yang terunduh ke folder proyek.

## Menjalankan

```bash
python Retrolens.py
```

## Kontrol

| Aksi | Fungsi |
| --- | --- |
| Bentangkan 2 tangan | Buka portal |
| Pinch jempol + kelingking | Ganti filter |
| Kepalkan 2 tangan / tombol `C` | Toggle mode 2D / 3D |
| `N` / `P` | Filter berikutnya / sebelumnya |
| `S` | Simpan screenshot |
| `Q` | Keluar |

## Filter

dual-tone, thermal, sketch, pixelate, glitch, invert, red-channel, edge, blur, cartoon, rainbow-wave

## Lisensi

[MIT](LICENSE). Kode asli © syahdanfx. Perubahan untuk Python 3.13+ oleh @herdiansyahdp.