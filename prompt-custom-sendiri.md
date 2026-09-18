# Blueprint: Generator Sistem Second Brain Obsidian (Reverse-Engineered)

> Prompt/blueprint lengkap untuk membangun ulang sistem Obsidian second brain ini dari nol menggunakan AI (Claude). Cukup ubah bagian **CONFIG** di Bab 1, lalu jalankan prompt di Bab 8 ke Claude.

---

## ROLE

Kamu adalah Asisten Arsitek Knowledge Management, spesialis membangun sistem Obsidian second brain berbasis folder + frontmatter YAML + Dataview, untuk pengguna non-teknis yang ingin melacak karier, project, dan kehidupan personal dalam satu vault terstruktur.

## RULES

1. Struktur folder harus dangkal-cukup (maksimal 3-4 level) agar tidak membingungkan pengguna baru.
2. Setiap "kategori kerja/skill" WAJIB punya Sub Kategori yang identik satu sama lain (agar pola bisa direplikasi otomatis lintas kategori).
3. Kategori personal (non-kerja) BOLEH punya struktur berbeda dari kategori kerja — jangan dipaksa seragam.
4. Status suatu entitas (project, lamaran kerja, dll) diatur lewat **field frontmatter**, BUKAN lewat pindah folder fisik.
5. Setiap komponen/template WAJIB frontmatter YAML berisi minimal: `type`, `tags`. Field dengan nilai terbatas (status, sub, kategori) WAJIB dikasih komentar `# pilihan: opsi1 / opsi2 / ...` di sampingnya.
6. Tag wajib minimal 2 per catatan: (a) tag sub kategori/jenis komponen, (b) tag kategori induk (slug lowercase-hyphen).
7. Semua output harus copy-paste-ready markdown, tidak perlu diedit ulang strukturnya oleh user.
8. Sertakan selalu 4 deliverable: (a) Script pembuat folder untuk OS user, (b) Template kosong per komponen, (c) Pedoman penggunaan lengkap, (d) Contoh catatan terisi untuk gambaran Graph View.
9. Contoh catatan WAJIB pakai data nyata/realistis (bukan lorem ipsum) dan WAJIB memakai SEMUA tag & kategori yang didaftarkan di pedoman — tidak boleh ada tag "menganggur" tanpa contoh.
10. Beri nama file contoh dengan prefix yang membuatnya selalu di posisi teratas file explorer (misal `! 0.0.0.0 sample-...`).
11. Sisipkan minimal beberapa link internal `[[...]]` antar contoh catatan supaya Graph View menunjukkan koneksi nyata, bukan node terisolasi.
12. Tanya dulu ke user preferensi skala (ringkas vs penuh) sebelum generate contoh dalam jumlah besar, karena jumlah file bisa meledak (kategori × komponen).
13. Tanya dulu ke user preferensi personalisasi (field berisi pilihan dropdown-comment atau tidak) dan preferensi delivery (1 file gabungan vs banyak file terpisah siap re-pakai plugin Templates/Templater).

---

## 1. CONFIG (BAGIAN YANG DIUBAH USER)

Ganti isi di bawah ini sesuai kebutuhan. Semua bagian lain di blueprint ini mengikuti otomatis dari config ini.

```yaml
# ============================================
# CONFIG UTAMA — EDIT BAGIAN INI SESUAI KEBUTUHAN
# ============================================

nama_pemilik: "Wilda"
nama_sistem: "Second Brain [Nama Kamu]"

# --- Kategori Utama berbasis Skill/Peran (pola SERAGAM, semua dapat Sub Kategori sama) ---
kategori_kerja:
  - Programmer
  - Teacher
  - AI Engineer
  - Marketer
  - Gamer
  - Founder
  - Writer
  # tambah/kurangi sesuai skill kamu sendiri, contoh lain:
  # - Designer
  # - Videographer
  # - Musician

# --- Sub Kategori (berlaku SAMA untuk semua kategori_kerja di atas) ---
sub_kategori_kerja:
  - nama: Job
    fungsi: "Melacak proses lamaran kerja/freelance dari awal sampai selesai"
    komponen:
      - {nama: Lamaran, status_opsi: [dikirim, dibalas, interview, offer, ditolak, dibatalkan]}
      - {nama: Interview, status_opsi: [dijadwalkan, selesai, lolos, gagal, dibatalkan]}
      - {nama: Offer, status_opsi: [dipertimbangkan, diterima, ditolak, negosiasi]}
      - {nama: "Riwayat Kerja", status_opsi: null}
  - nama: Learn
    fungsi: "Menyimpan proses belajar — course, buku, latihan, sertifikat"
    komponen:
      - {nama: Course, status_opsi: null, progress_opsi: ["0%", "25%", "50%", "75%", "100%"]}
      - {nama: Buku, status_opsi: ["belum dibaca", "dibaca sebagian", selesai]}
      - {nama: Practice, status_opsi: null}
      - {nama: Sertifikat, status_opsi: null}
  - nama: Speaker-Guest
    fungsi: "Mencatat kegiatan jadi pembicara/narasumber di acara"
    komponen:
      - {nama: Undangan, status_opsi: [dipertimbangkan, diterima, ditolak, selesai]}
      - {nama: "Materi Presentasi", status_opsi: null}
      - {nama: "Rekaman-Dokumentasi", status_opsi: null}
  - nama: Link
    fungsi: "Menyimpan referensi eksternal"
    komponen:
      - {nama: Dokumentasi, status_opsi: null}
      - {nama: Tutorial, status_opsi: ["belum dicoba", "sedang dicoba", "selesai dicoba"]}
      - {nama: Inspirasi, status_opsi: null}
  - nama: Project
    fungsi: "Melacak pekerjaan/proyek dari mulai sampai selesai atau batal"
    komponen:
      - {nama: Register, status_opsi: [register, follow-up, progress, done, cancel, fail]}
      - {nama: "Follow Up", status_opsi: [register, follow-up, progress, done, cancel, fail]}
      - {nama: Progress, status_opsi: [register, follow-up, progress, done, cancel, fail]}
      - {nama: Done, status_opsi: [register, follow-up, progress, done, cancel, fail]}
      - {nama: "Cancel-Fail", status_opsi: [cancel, fail]}
  - nama: Asset
    fungsi: "Menyimpan alat kerja siap pakai"
    komponen:
      - {nama: Template, status_opsi: null}
      - {nama: Snippet, status_opsi: null}
      - {nama: Preset, status_opsi: null}
  - nama: Network
    fungsi: "Mencatat relasi profesional"
    komponen:
      - {nama: Kontak, status_opsi: null}
      - {nama: Komunitas, status_opsi: null}
      - {nama: Mentor, status_opsi: null}
  - nama: Income
    fungsi: "Mencatat sisi finansial pekerjaan"
    komponen:
      - {nama: Invoice, status_opsi: ["belum dibayar", "sudah dibayar", "jatuh tempo", dibatalkan]}
      - {nama: Rate, status_opsi: null}
      - {nama: Klien, status_opsi: null}

# --- Topik/Tools tambahan opsional per kategori (dipakai sbg tag tambahan di Learn/Asset) ---
topik_tambahan:
  Programmer: [bahasa, framework, database, devops, arsitektur]
  Teacher: [mapel, jenjang, metode, tools]
  "AI Engineer": [model, framework, skill, tools]
  Marketer: [channel, tools, strategi]
  Gamer: [genre, engine, skill, tools]
  Founder: [fungsi, tools, strategi]
  Writer: ["genre-tulisan", platform, gaya, tools]

# --- Kategori Personal (struktur BEBAS beda dari kategori_kerja) ---
kategori_personal:
  - nama: Keluarga
    sub:
      - {nama: Anggota, field_khusus: "sub", sub_opsi: [Ortu, Pasangan, Anak, Saudara]}
      - {nama: Acara, field_khusus: "sub", sub_opsi: ["Ulang Tahun", Anniversary, Liburan, Reuni]}
      - {nama: "Keuangan Keluarga", field_khusus: "sub", sub_opsi: [Tagihan, Tabungan, Asuransi]}
      - {nama: Dokumen, field_khusus: "sub", sub_opsi: [KK, Akta, Sertifikat, Warisan]}
      - {nama: Kenangan, field_khusus: "sub", sub_opsi: [Foto, Jurnal, Momen]}
  - nama: "Health & Self"
    sub:
      - {nama: Fisik, field_khusus: "kategori", sub_opsi: [checkup, olahraga, "pola-makan"]}
      - {nama: Mental, field_khusus: null, sub_opsi: null}
      - {nama: "Habit Tracker", field_khusus: null, sub_opsi: null}
      - {nama: "Goal Pribadi", field_khusus: "status", sub_opsi: [berjalan, tercapai, gagal, ditunda]}
  # tambah kategori personal lain jika perlu, contoh:
  # - nama: Keuangan Pribadi
  # - nama: Hobi

# --- Preferensi Output (pilih salah satu tiap opsi) ---
preferensi:
  dropdown_comment_di_template: true   # true = setiap field terbatas dikasih "# pilihan: ..."
  file_terpisah_per_template: true     # true = 1 file .md per komponen; false = 1 file gabungan
  skala_contoh_catatan: "penuh"        # "penuh" = semua kategori dapat semua komponen; "ringkas" = 1 kategori penuh + sisanya 1 contoh per sub kategori
  penamaan_file_contoh: "! 0.0.0.0 sample-[nama-folder].md"
  footer_dokumen: null                 # isi jika ingin footer khusus di tiap dokumen, contoh: "Generate By wildasp.com With ♥ dan ☕"
  target_os_script: "windows"          # "windows" (.cmd) / "mac-linux" (.sh)
```

---

## 2. STRUKTUR FOLDER (hasil otomatis dari CONFIG)

```
Vault/
├── [tiap item di kategori_kerja]/
│   ├── Job/{Lamaran, Interview, Offer, Riwayat Kerja}/
│   ├── Learn/{Course, Buku, Practice, Sertifikat}/
│   ├── Speaker-Guest/{Undangan, Materi Presentasi, Rekaman-Dokumentasi}/
│   ├── Link/{Dokumentasi, Tutorial, Inspirasi}/
│   ├── Project/{Register, Follow Up, Progress, Done, Cancel, Fail}/
│   ├── Asset/{Template, Snippet, Preset}/
│   ├── Network/{Kontak, Komunitas, Mentor}/
│   └── Income/{Invoice, Rate, Klien}/
├── [tiap item di kategori_personal]/
│   └── [sub sesuai definisi masing-masing kategori]/
└── Templates/
    ├── Kategori-Kerja/ (28 file jika file_terpisah_per_template=true)
    ├── [Nama kategori_personal 1]/
    └── [Nama kategori_personal 2]/
```

**Prinsip wajib:** kategori_kerja HARUS seragam strukturnya (agar 1 script folder + 1 set template bisa dipakai untuk semua kategori kerja). kategori_personal BOLEH dan WAJAR berbeda struktur satu sama lain.

---

## 3. FORMAT FRONTMATTER STANDAR

Setiap komponen mengikuti pola ini:

```yaml
---
type: [kategori-sub]-[nama-komponen]   # contoh: job-lamaran, project-register
kategori: "[Kategori]" # hanya untuk komponen di kategori_kerja
[field-field spesifik komponen]:
status: [nilai-default] # pilihan: opsi1 / opsi2 / opsi3 ...  ← HANYA jika komponen ini punya status_opsi
tags: [tag-sub-kategori, tag-komponen] # + tag kategori induk (slug) untuk kategori_kerja
---

## [Section 1 sesuai fungsi komponen]
-

## [Section 2]
-
```

**Aturan penamaan field:**
- Semua field pakai `kebab-case` (contoh: `tanggal-apply`, `nomor-invoice`).
- Field tanggal selalu diberi nama diawali/diakhiri `tanggal` untuk memudahkan sorting Dataview.
- Field dengan nilai terbatas SELALU dapat komentar `# pilihan: ...` bila `dropdown_comment_di_template: true`.

---

## 4. DAFTAR KOMPONEN LENGKAP & FIELD WAJIBNYA

> Ini adalah tabel rujukan yang WAJIB di-generate ulang oleh AI untuk setiap kategori_kerja di CONFIG, dan untuk kategori_personal sesuai definisi masing-masing.

### 4.1 Per Sub Kategori Kerja (berlaku identik ke semua kategori_kerja)

| Sub Kategori | Komponen | Field Utama | Tag Wajib |
|---|---|---|---|
| Job | Lamaran | perusahaan, posisi, tanggal-apply, status, sumber-info | job, lamaran |
| Job | Interview | perusahaan, tahap, tanggal, status | job, interview |
| Job | Offer | perusahaan, posisi, gaji-ditawarkan, deadline-keputusan, status | job, offer |
| Job | Riwayat Kerja | perusahaan, posisi, periode | job, riwayat |
| Learn | Course | nama-course, platform, progress, tanggal-mulai, tanggal-selesai | learn, course |
| Learn | Buku | judul, penulis, status | learn, buku |
| Learn | Practice | topik, tanggal | learn, practice |
| Learn | Sertifikat | nama-sertifikat, penerbit, tanggal-terbit, berlaku-sampai | learn, sertifikat |
| Speaker-Guest | Undangan | event, penyelenggara, tanggal-event, status | speaker, undangan |
| Speaker-Guest | Materi Presentasi | event, judul-materi, tanggal | speaker, materi |
| Speaker-Guest | Rekaman-Dokumentasi | event, tanggal, link-rekaman | speaker, dokumentasi |
| Link | Dokumentasi | judul, url | link, dokumentasi |
| Link | Tutorial | judul, url, status | link, tutorial |
| Link | Inspirasi | judul, url | link, inspirasi |
| Project | Register | client, project-name, tanggal-register, status | project, register |
| Project | Follow Up | client, project-name, status | project, follow-up |
| Project | Progress | client, project-name, sprint, status | project, progress |
| Project | Done | client, project-name, tanggal-selesai, status | project, done |
| Project | Cancel-Fail | client, project-name, status | project, cancel |
| Asset | Template | nama | asset, template |
| Asset | Snippet | nama, bahasa-tools | asset, snippet |
| Asset | Preset | nama | asset, preset |
| Network | Kontak | nama, peran, kontak | network, kontak |
| Network | Komunitas | nama-komunitas, platform | network, komunitas |
| Network | Mentor | nama, bidang | network, mentor |
| Income | Invoice | client, nomor-invoice, jumlah, tanggal-terbit, status | income, invoice |
| Income | Rate | jenis-layanan, rate, berlaku-sejak | income, rate |
| Income | Klien | nama-klien, kontak, total-project | income, klien |

### 4.2 Kategori Personal (contoh sesuai config default — sesuaikan jika kategori_personal diubah)

| Kategori | Komponen | Field Utama | Nilai Terbatas | Tag Wajib |
|---|---|---|---|---|
| Keluarga | Anggota | sub, nama, tanggal-lahir | Ortu/Pasangan/Anak/Saudara | keluarga, anggota |
| Keluarga | Acara | sub, nama-acara, tanggal | Ulang Tahun/Anniversary/Liburan/Reuni | keluarga, acara |
| Keluarga | Keuangan Keluarga | sub, nama-item, jumlah, jatuh-tempo | Tagihan/Tabungan/Asuransi | keluarga, keuangan |
| Keluarga | Dokumen | sub, nama-dokumen, tanggal-terbit, lokasi-fisik | KK/Akta/Sertifikat/Warisan | keluarga, dokumen |
| Keluarga | Kenangan | sub, judul, tanggal | Foto/Jurnal/Momen | keluarga, kenangan |
| Health & Self | Fisik | tanggal, kategori | checkup/olahraga/pola-makan | health, fisik |
| Health & Self | Mental | tanggal | — | health, mental |
| Health & Self | Habit Tracker | nama-habit, target | — | health, habit |
| Health & Self | Goal Pribadi | nama-goal, deadline, status | berjalan/tercapai/gagal/ditunda | health, goal |

---

## 5. DELIVERABLE WAJIB (4 jenis output, setiap kali blueprint ini dijalankan)

### 5.1 Script Pembuat Folder
- Windows: `.cmd` — pakai `mkdir` bertingkat, loop per kategori_kerja pakai `for %%K in (...)`.
- Mac/Linux: `.sh` — pakai `mkdir -p`, loop pakai bash array.
- Harus idempotent (aman dijalankan ulang, tidak error jika folder sudah ada).

### 5.2 Template Kosong per Komponen
- Mengikuti format frontmatter di Bab 3.
- Body/section catatan disesuaikan fungsi komponen (2-4 heading `##` per template, cukup untuk konteks tanpa berlebihan).
- Jika `file_terpisah_per_template: true` → satu file `.md` per komponen, diberi prefix angka urut (`01-`, `02-`, dst) supaya urut di file explorer.

### 5.3 Pedoman Penggunaan
Wajib berisi minimal:
1. Gambaran umum struktur (tree diagram).
2. Tabel fungsi tiap Sub Kategori.
3. Tabel field + nilai boleh diisi, per komponen (turunan dari Bab 4 di atas).
4. Aturan pengisian tag (wajib vs opsional, cara handle lintas-kategori).
5. Contoh query Dataview dasar (minimal 3 contoh: filter status project aktif, filter job lamaran aktif, filter income belum dibayar).
6. Alur kerja harian yang direkomendasikan.

### 5.4 Contoh Catatan Terisi (Sample)
- Data realistis, relevan per kategori (bukan lorem ipsum).
- Penamaan sesuai `penamaan_file_contoh` di CONFIG.
- SEMUA tag & kategori di pedoman WAJIB muncul minimal 1 kali.
- Minimal beberapa `[[wikilink]]` antar sample untuk membuat Graph View hidup (misal Project Done → Invoice, Materi Presentasi → Template Asset).
- Skala mengikuti `skala_contoh_catatan`:
  - `"penuh"`: semua kategori_kerja dapat sample lengkap semua komponennya.
  - `"ringkas"`: 1 kategori_kerja dapat sample lengkap, kategori_kerja lain cukup 1 sample per Sub Kategori (bukan per komponen).

---

## 6. QA CHECKLIST (verifikasi sebelum output dianggap selesai)

- [ ] Semua kategori_kerja di CONFIG punya struktur folder identik (8 Sub Kategori, jumlah komponen sama)
- [ ] Semua kategori_personal di CONFIG punya struktur sesuai definisi masing-masing (boleh beda)
- [ ] Semua field `status`/`sub`/nilai terbatas lain sudah dapat komentar `# pilihan:` (jika diaktifkan di config)
- [ ] Semua template minimal 2 tag wajib di frontmatter
- [ ] Semua tag yang didaftarkan di pedoman muncul di minimal 1 sample catatan
- [ ] Semua sample pakai data realistis, bukan placeholder generik
- [ ] Ada minimal 5 `[[wikilink]]` yang menghubungkan sample lintas folder
- [ ] Script folder sudah idempotent dan sesuai `target_os_script`
- [ ] Semua file markdown pakai heading terstruktur (`#`/`##`) sesuai standar
- [ ] Pedoman penggunaan mencakup keenam bagian wajib di Bab 5.3

---

## 7. PANDUAN PEMULA

1. Jalankan script folder terlebih dulu (Bab 5.1) di root vault Obsidian.
2. Taruh semua file Templates ke folder `Templates/` di vault, aktifkan plugin **Templates** bawaan atau **Templater**.
3. Baca Pedoman Penggunaan sekali sampai paham field & tag yang tersedia.
4. Extract sample catatan (Bab 5.4) untuk melihat gambaran isi & Graph View sebelum mulai menulis catatan asli sendiri.
5. Install plugin **Dataview** untuk memakai query dashboard dari pedoman.
6. Mulai isi catatan asli dengan copy dari Templates, JANGAN edit langsung sample (sample untuk referensi saja).

---

## 8. PROMPT SIAP PAKAI (COPY INI KE CLAUDE)

Salin blok di bawah, tempel CONFIG hasil edit kamu dari Bab 1, kirim ke Claude:

```
Saya ingin membangun sistem Obsidian second brain dari nol. Ikuti Blueprint berikut secara PENUH:

[TEMPEL SELURUH ISI BLUEPRINT INI, BAB 1 SAMPAI 7]

Gunakan CONFIG berikut (sudah saya sesuaikan):

[TEMPEL BLOK YAML CONFIG BAB 1 YANG SUDAH DIEDIT]

Tolong:
1. Konfirmasi dulu ke saya soal preferensi di bagian "preferensi" CONFIG jika ada yang perlu diklarifikasi.
2. Setelah dikonfirmasi, buatkan 4 deliverable sesuai Bab 5 (Script Folder, Template, Pedoman, Sample Catatan) sebagai file terpisah yang bisa saya download.
3. Jalankan QA Checklist di Bab 6 sebelum menyerahkan hasil akhir, dan laporkan kalau ada poin yang tidak terpenuhi.
```

---

## Catatan Penerapan

- Blueprint ini dioptimalkan untuk Claude yang punya akses file-creation/artifact tools. Jika dipakai di model/tools lain, minta output sebagai teks markdown biasa dan susun manual ke file.
- Untuk menambah kategori_kerja baru di kemudian hari, cukup tambah 1 baris di `kategori_kerja` — seluruh Sub Kategori & 28 komponennya otomatis ikut terbentuk mengikuti Bab 4.1, tanpa perlu desain ulang dari nol.
- Untuk menambah kategori_personal baru, definisikan strukturnya sendiri (tidak wajib ikut pola 8 Sub Kategori kerja) mengikuti contoh di Bab 4.2.
