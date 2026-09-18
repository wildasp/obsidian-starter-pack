# 🧠 Obsidian Second Brain — Struktur Karier & Personal

Sistem manajemen catatan berbasis [Obsidian](https://obsidian.md) untuk melacak karier di berbagai bidang skill (Programmer, Teacher, AI Engineer, Marketer, Gamer, Founder, Writer) sekaligus kehidupan personal (Keluarga, Health & Self) — dalam satu vault terstruktur, berbasis folder + frontmatter YAML + [Dataview](https://github.com/blacksmithgu/obsidian-dataview).

---

## ✨ Fitur

- **7 kategori skill kerja** dengan struktur Sub Kategori yang seragam (Job, Learn, Speaker-Guest, Link, Project, Asset, Network, Income) — mudah direplikasi untuk skill baru.
- **2 kategori personal** (Keluarga, Health & Self) dengan struktur khusus sesuai kebutuhan masing-masing.
- **37 template markdown siap pakai**, tiap field terbatas (status, sub-kategori) sudah dikasih opsi pilihan (`# pilihan: ...`) supaya pemula tidak bingung.
- **205 contoh catatan terisi** dengan data realistis, saling terhubung lewat wikilink `[[...]]` untuk melihat gambaran Graph View sejak awal.
- **Status project/job dilacak lewat frontmatter**, bukan lewat pindah folder — kompatibel dengan dashboard Dataview.
- **Blueprint reverse-engineer** — panduan lengkap untuk membangun ulang atau memodifikasi sistem ini dari nol pakai AI (Claude), tinggal ubah bagian CONFIG.

---

## 📁 Struktur Folder

```
Vault/
├── Programmer/
├── Teacher/
├── AI Engineer/
├── Marketer/
├── Gamer/
├── Founder/
├── Writer/
│   └── (tiap kategori di atas punya 8 Sub Kategori berikut)
│       ├── Job/{Lamaran, Interview, Offer, Riwayat Kerja}
│       ├── Learn/{Course, Buku, Practice, Sertifikat}
│       ├── Speaker-Guest/{Undangan, Materi Presentasi, Rekaman-Dokumentasi}
│       ├── Link/{Dokumentasi, Tutorial, Inspirasi}
│       ├── Project/{Register, Follow Up, Progress, Done, Cancel, Fail}
│       ├── Asset/{Template, Snippet, Preset}
│       ├── Network/{Kontak, Komunitas, Mentor}
│       └── Income/{Invoice, Rate, Klien}
├── Keluarga/
│   ├── Anggota/{Ortu, Pasangan, Anak, Saudara}
│   ├── Acara/{Ulang Tahun, Anniversary, Liburan, Reuni}
│   ├── Keuangan Keluarga/{Tagihan, Tabungan, Asuransi}
│   ├── Dokumen/{KK, Akta, Sertifikat, Warisan}
│   └── Kenangan/{Foto, Jurnal, Momen}
├── Health & Self/
│   ├── Fisik/
│   ├── Mental/
│   ├── Habit Tracker/
│   └── Goal Pribadi/
└── Templates/
    ├── Kategori-Kerja/   (28 file)
    ├── Keluarga/         (5 file)
    └── Health-Self/      (4 file)
```

---

## 📂 Isi Repository

| File/Folder | Deskripsi |
|---|---|
| `All Folder (Kecuali Templates)` | 205 contoh catatan terisi data realistis, untuk referensi & demo Graph View |
| `Templates` | 37 template markdown kosong, siap pakai plugin Templates/Templater |
| `pedoman-penggunaan-obsidian.md` | Dokumentasi lengkap: fungsi tiap komponen, field, tag, contoh query Dataview |
| `panduan-sintaks-markdown.md` | Panduan cepat sintaks markdown untuk pemula |
| `prompt-custom-sendiri.md` | Blueprint AI-ready untuk membangun ulang/memodifikasi sistem ini dari nol |

---

## 🚀 Cara Mulai Pakai

1. **Buat vault Obsidian baru** (atau pakai vault yang sudah ada).
2. **Jalankan script folder** — taruh `buat-struktur-obsidian.cmd` di root vault, lalu double-click (Windows). Semua folder & subfolder otomatis terbentuk.
3. **Extract Templates** — taruh isi `Templates-Obsidian-v2.zip` ke folder `Templates/` di vault. Aktifkan plugin **Templates** (bawaan Obsidian) atau **Templater** (community plugin).
4. **Extract Sample** (opsional, untuk belajar) — taruh isi `Sample-Catatan-Obsidian.zip` ke folder yang sesuai untuk melihat contoh nyata dan Graph View yang saling terhubung.
5. **Baca pedoman** — buka `pedoman-penggunaan-obsidian.md` untuk memahami field, tag, dan cara pakai tiap komponen.
6. **Install plugin Dataview** — untuk memakai dashboard query (contoh query ada di pedoman).
7. Mulai isi catatan asli dari Templates. Jangan edit sample langsung — sample hanya referensi.

---

## 🏷️ Aturan Tag & Frontmatter (Ringkas)

Setiap catatan wajib frontmatter YAML dengan minimal:

```yaml
---
type: [kategori-sub]-[komponen]   # contoh: job-lamaran, project-register
status: [nilai]                    # jika komponen punya status
tags: [tag-komponen, tag-kategori]
---
```

Field dengan nilai terbatas (status, sub) selalu diberi komentar opsi, contoh:

```yaml
status: dikirim # pilihan: dikirim / dibalas / interview / offer / ditolak / dibatalkan
```

Detail lengkap semua field & opsi per komponen ada di `pedoman-penggunaan-obsidian.md`.

---

## 🔧 Kustomisasi / Membangun Ulang dari Nol

Ingin menambah kategori skill baru atau mengubah struktur? Gunakan `blueprint-reverse-engineer-second-brain.md` — edit bagian **CONFIG** di dalamnya (format YAML), lalu jalankan prompt yang sudah disiapkan ke Claude atau AI lain untuk generate ulang seluruh sistem secara konsisten.

---

## 🛠️ Plugin Obsidian yang Direkomendasikan

- [Dataview](https://github.com/blacksmithgu/obsidian-dataview) — dashboard & query berbasis frontmatter
- [Templater](https://github.com/SilentVoid13/Templater) — otomasi pengisian template
- Graph View (bawaan) — visualisasi koneksi antar catatan lewat wikilink

---

## 📄 Lisensi

Gunakan dan modifikasi bebas sesuai kebutuhan pribadi.

---

*Develop By wildasp.com With ♥ dan ☕ @ 18 September 2026*
