<div align="center">

# 🔎 Searche — Pencarian Hybrid (Teks + Suara)

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Repo Size](https://img.shields.io/github/repo-size/useripx/10-Searche?style=for-the-badge&color=blue)
![Version](https://img.shields.io/badge/Version-1.0-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-Free-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Selesai-brightgreen?style=for-the-badge)
![Speech Recognition](https://img.shields.io/badge/Feature-Speech_Recognition-FF6F00?style=for-the-badge&logo=google&logoColor=white)
![Text to Speech](https://img.shields.io/badge/Feature-Text_to_Speech-4285F4?style=for-the-badge&logo=google&logoColor=white)
![PyInstaller](https://img.shields.io/badge/Build-PyInstaller-orange?style=for-the-badge&logo=pyinstaller&logoColor=white)
![Semester](https://img.shields.io/badge/Semester-1-blueviolet?style=for-the-badge)

**Mesin pencari CLI yang menggabungkan input teks dan suara, dengan output teks dan audio.**

*Dibuat oleh Yogi Ario — Proyek Semester 1*

---

</div>

## 📖 Deskripsi

**Searche** adalah aplikasi pencarian Google berbasis CLI yang menggabungkan **dua metode input** dalam satu program — pencarian via **teks (ketik)** dan via **suara (mikrofon)**. Hasil pencarian diambil langsung dari halaman web (web scraping), ditampilkan di terminal, dan **dibacakan** menggunakan Google Text-to-Speech (gTTS) dalam Bahasa Indonesia.

Program ini merupakan penyempurnaan dari proyek sebelumnya dengan menambahkan **menu pilihan** untuk memilih metode pencarian.

## ✨ Fitur

- ⌨️ **Pencarian Teks** — Ketik kata kunci langsung dari keyboard
- 🎤 **Pencarian Suara** — Input melalui mikrofon (Bahasa Indonesia)
- 🌐 **Web Scraping** — Ambil 5 paragraf pertama dari halaman hasil pencarian #1
- 🔊 **Text-to-Speech** — Bacakan hasil pencarian (disimpan ke `result.mp3`)
- 📋 **Menu Pilihan** — Pilih metode pencarian (teks/suara) setiap iterasi
- 🛡️ **Auto Admin Privilege** — UAC elevation otomatis
- ♻️ Loop pencarian berulang tanpa restart
- 🐍 **Virtual Environment** — Sudah include `myenv` untuk isolasi dependensi

## 📁 Struktur Proyek

```
10 searche/
├── searche.py             # Source code utama
├── searche.spec           # Konfigurasi PyInstaller
├── img.ico                # Icon aplikasi
├── myenv/                 # Python virtual environment
├── build/                 # File build PyInstaller
└── dist/
    ├── searche.exe        # Executable standalone
    ├── result.mp3         # Output audio hasil pencarian terakhir
    ├── query.mp3          # Audio query
    ├── setup x64.msi      # Installer MSI 64-bit
    └── setup x86.msi      # Installer MSI 32-bit
```

## 🚀 Cara Menjalankan

### Prasyarat

```bash
pip install SpeechRecognition googlesearch-python gTTS requests beautifulsoup4 PyAudio
```

Atau gunakan virtual environment yang sudah disediakan:

```bash
myenv\Scripts\activate
python searche.py
```

### Opsi 1: Jalankan file Python

```bash
python searche.py
```

### Opsi 2: Jalankan Executable

Buka `dist/searche.exe` langsung.

### Opsi 3: Install via MSI

| Installer | Lokasi |
|-----------|--------|
| MSI 64-bit | `dist/setup x64.msi` |
| MSI 32-bit | `dist/setup x86.msi` |

### Opsi 4: Build ulang executable

```bash
pip install pyinstaller
pyinstaller searche.spec
```

## 📸 Contoh Penggunaan

```
Projek Pencarian Suara v1.0
by Yogi Ario

Pencarian ini memberikan hasil secara langsung dari Google.

Pilih metode pencarian:
1. Pencarian berdasarkan teks
2. Pencarian berdasarkan suara
Masukkan pilihan Anda (1 atau 2, tekan enter untuk keluar): 1
Masukkan teks pencarian: Universitas Negeri Padang

Mengambil informasi dari: https://www.unp.ac.id/
Hasil pencarian:

Universitas Negeri Padang merupakan salah satu universitas negeri
terkemuka di Sumatera Barat yang berlokasi di Kota Padang...

🔊 (Hasil dibacakan melalui speaker → disimpan ke result.mp3)

Pilih metode pencarian:
1. Pencarian berdasarkan teks
2. Pencarian berdasarkan suara
Masukkan pilihan Anda (1 atau 2, tekan enter untuk keluar): 2
Silakan berbicara...
Mengenali suara...
Anda berkata: Apa itu Python
...
```

## 🧠 Alur Kerja

```
         ┌──────────────────────┐
         │     Menu Pilihan     │
         │  1. Teks  2. Suara   │
         └──────────┬───────────┘
                    │
        ┌───────────┴───────────┐
        ▼                       ▼
 ┌─────────────┐        ┌─────────────┐
 │ ⌨️ Input    │        │ 🎤 Input    │
 │   Teks      │        │   Suara     │
 └──────┬──────┘        └──────┬──────┘
        │                      │
        └──────────┬───────────┘
                   ▼
            ┌─────────────┐
            │ 🔍 Google   │
            │   Search    │
            └──────┬──────┘
                   ▼
            ┌─────────────┐
            │ 🌐 Web      │  → 5 paragraf pertama
            │  Scraping   │
            └──────┬──────┘
                   ▼
          ┌────────┴────────┐
          ▼                 ▼
   ┌────────────┐    ┌────────────┐
   │ 📺 Print   │    │ 🔊 gTTS   │
   │ di Terminal│    │ result.mp3 │
   └────────────┘    └────────────┘
```

## 🛠️ Teknologi

| Komponen | Detail |
|----------|--------|
| Bahasa | Python 3.x |
| Speech Recognition | `SpeechRecognition` + Google API |
| Text-to-Speech | `gTTS` (Google TTS) |
| Web Scraping | `requests` + `BeautifulSoup4` |
| Search Engine | `googlesearch-python` |
| Build Tool | PyInstaller |
| Environment | Virtual Environment (`myenv`) |
| Platform | Windows |

## 👤 Author

**Yogi Ario**

---

<div align="center">

*Proyek Mata Kuliah — Semester 1 — Teknik Informatika UNP*

</div>
