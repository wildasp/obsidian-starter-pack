# Pedoman Penggunaan — Obsidian Second Brain Wilda

Dokumen ini menjelaskan fungsi tiap bagian, komponen di dalamnya, dan daftar tag/nilai yang boleh diisi. Simpan file ini di root vault sebagai referensi.

---

## 1. Gambaran Umum Struktur

```
Vault/
├── Programmer/
├── Teacher/
├── AI Engineer/
├── Marketer/
├── Gamer/
├── Founder/
├── Writer/
├── Keluarga/
├── Health & Self/
└── Templates/
```

**Prinsip dasar:**
- 7 kategori pertama (Programmer → Writer) = **kategori kerja/skill**, semuanya punya struktur Sub Kategori yang identik (lihat Bagian 2).
- **Keluarga** dan **Health & Self** = kategori personal, struktur beda karena bukan konteks karier.
- Status project **tidak** dipindah folder — cukup ubah field `status:` di frontmatter, lalu pantau lewat Dataview dashboard.
- Kalau satu catatan relevan ke lebih dari satu kategori, jangan digandakan filenya — cukup tambahkan tag tambahan di frontmatter (lintas-kategori).

---

## 2. Sub Kategori pada 7 Kategori Kerja

Fungsi tiap Sub Kategori:

| Sub Kategori | Fungsi |
|---|---|
| **Job** | Melacak proses lamaran kerja/freelance dari awal sampai selesai |
| **Learn** | Menyimpan proses belajar — course, buku, latihan, sertifikat |
| **Speaker-Guest** | Mencatat kegiatan jadi pembicara/narasumber di acara |
| **Link** | Menyimpan referensi eksternal (dokumentasi, tutorial, inspirasi) |
| **Project** | Melacak pekerjaan/proyek dari mulai sampai selesai atau batal |
| **Asset** | Menyimpan alat kerja siap pakai (template, snippet, preset) |
| **Network** | Mencatat relasi profesional (kontak, komunitas, mentor) |
| **Income** | Mencatat sisi finansial pekerjaan (invoice, rate, data klien) |

### 2.1 Job

| Komponen | Fungsi | Field Frontmatter | Tag Wajib |
|---|---|---|---|
| Lamaran | Catat lowongan yang dilamar | `perusahaan`, `posisi`, `tanggal-apply`, `status`, `sumber-info` | `job`, `lamaran` |
| Interview | Catat proses wawancara | `perusahaan`, `tahap`, `tanggal`, `status` | `job`, `interview` |
| Offer | Catat tawaran kerja yang diterima | `perusahaan`, `posisi`, `gaji-ditawarkan`, `deadline-keputusan`, `status` | `job`, `offer` |
| Riwayat Kerja | Arsip pekerjaan yang sudah dijalani | `perusahaan`, `posisi`, `periode` | `job`, `riwayat` |

**Nilai boleh diisi:**
- `status` (Lamaran): `dikirim` / `dibalas` / `interview` / `offer` / `ditolak` / `dibatalkan`
- `tahap` (Interview): `HR` / `Technical` / `User` / `Final`
- `status` (Interview): `dijadwalkan` / `selesai` / `lolos` / `gagal` / `dibatalkan`
- `status` (Offer): `dipertimbangkan` / `diterima` / `ditolak` / `negosiasi`
- `sumber-info`: `LinkedIn` / `Job Portal` / `Referral` / `Direct` / `Lainnya`

### 2.2 Learn

| Komponen | Fungsi | Field Frontmatter | Tag Wajib |
|---|---|---|---|
| Course | Catat progres kursus online/offline | `nama-course`, `platform`, `progress`, `tanggal-mulai`, `tanggal-selesai` | `learn`, `course` |
| Buku | Catat ringkasan & refleksi buku yang dibaca | `judul`, `penulis`, `status` | `learn`, `buku` |
| Practice | Catat sesi latihan mandiri | `topik`, `tanggal` | `learn`, `practice` |
| Sertifikat | Arsip sertifikasi yang diperoleh | `nama-sertifikat`, `penerbit`, `tanggal-terbit`, `berlaku-sampai` | `learn`, `sertifikat` |

**Nilai boleh diisi:**
- `platform` (Course): `Udemy` / `Coursera` / `YouTube` / `Bootcamp` / `Internal` / `Lainnya`
- `progress` (Course): `0%` / `25%` / `50%` / `75%` / `100%`
- `status` (Buku): `belum dibaca` / `dibaca sebagian` / `selesai`

### 2.3 Speaker-Guest

| Komponen | Fungsi | Field Frontmatter | Tag Wajib |
|---|---|---|---|
| Undangan | Catat tawaran jadi pembicara | `event`, `penyelenggara`, `tanggal-event`, `status` | `speaker`, `undangan` |
| Materi Presentasi | Simpan outline & file slide | `event`, `judul-materi`, `tanggal` | `speaker`, `materi` |
| Rekaman-Dokumentasi | Arsip rekaman & feedback sesi | `event`, `tanggal`, `link-rekaman` | `speaker`, `dokumentasi` |

**Nilai boleh diisi:**
- `status` (Undangan): `dipertimbangkan` / `diterima` / `ditolak` / `selesai`

### 2.4 Link

| Komponen | Fungsi | Field Frontmatter | Tag Wajib |
|---|---|---|---|
| Dokumentasi | Simpan link dokumentasi resmi/tools | `judul`, `url` | `link`, `dokumentasi` |
| Tutorial | Simpan link tutorial untuk dipraktikkan | `judul`, `url`, `status` | `link`, `tutorial` |
| Inspirasi | Simpan referensi ide/inspirasi | `judul`, `url` | `link`, `inspirasi` |

**Nilai boleh diisi:**
- `status` (Tutorial): `belum dicoba` / `sedang dicoba` / `selesai dicoba`

### 2.5 Project

| Komponen | Fungsi | Field Frontmatter | Tag Wajib |
|---|---|---|---|
| Register | Proyek baru masuk, belum deal | `client`, `project-name`, `tanggal-register`, `status` | `project`, `register` |
| Follow Up | Tahap negosiasi sebelum deal | `client`, `project-name`, `status` | `project`, `follow-up` |
| Progress | Proyek sedang dikerjakan | `client`, `project-name`, `sprint`, `status` | `project`, `progress` |
| Done | Proyek selesai & dibayar | `client`, `project-name`, `tanggal-selesai`, `status` | `project`, `done` |
| Cancel/Fail | Proyek batal atau gagal | `client`, `project-name`, `status` | `project`, `cancel` |

**Nilai boleh diisi:**
- `status`: `register` / `follow-up` / `progress` / `done` / `cancel` / `fail`

> Catatan: field `status` inilah yang jadi kunci Dataview dashboard (lihat Bagian 5) — bukan lokasi foldernya.

### 2.6 Asset

| Komponen | Fungsi | Field Frontmatter | Tag Wajib |
|---|---|---|---|
| Template | Simpan template dokumen/file siap pakai | `nama` | `asset`, `template` |
| Snippet | Simpan potongan kode/prompt yang sering dipakai ulang | `nama`, `bahasa-tools` | `asset`, `snippet` |
| Preset | Simpan konfigurasi/preset siap pakai | `nama` | `asset`, `preset` |

### 2.7 Network

| Komponen | Fungsi | Field Frontmatter | Tag Wajib |
|---|---|---|---|
| Kontak | Catat individu profesional yang dikenal | `nama`, `peran`, `kontak` | `network`, `kontak` |
| Komunitas | Catat komunitas yang diikuti | `nama-komunitas`, `platform` | `network`, `komunitas` |
| Mentor | Catat mentor & insight dari bimbingan | `nama`, `bidang` | `network`, `mentor` |

### 2.8 Income

| Komponen | Fungsi | Field Frontmatter | Tag Wajib |
|---|---|---|---|
| Invoice | Catat tagihan yang dikirim ke klien | `client`, `nomor-invoice`, `jumlah`, `tanggal-terbit`, `status` | `income`, `invoice` |
| Rate | Catat tarif layanan yang berlaku | `jenis-layanan`, `rate`, `berlaku-sejak` | `income`, `rate` |
| Klien | Arsip profil & riwayat kerja sama klien | `nama-klien`, `kontak`, `total-project` | `income`, `klien` |

**Nilai boleh diisi:**
- `status` (Invoice): `belum dibayar` / `sudah dibayar` / `jatuh tempo` / `dibatalkan`

---

## 3. Topik/Tools Tambahan (opsional, di dalam Learn atau Asset)

Kalau ingin klasifikasi lebih spesifik per kategori, tambahkan sub-tag berikut di field `tags` catatan Learn/Asset terkait:

| Kategori | Sub-topik yang bisa dipakai sebagai tag tambahan |
|---|---|
| Programmer | `bahasa`, `framework`, `database`, `devops`, `arsitektur` |
| Teacher | `mapel`, `jenjang`, `metode`, `tools` |
| AI Engineer | `model`, `framework`, `skill`, `tools` |
| Marketer | `channel`, `tools`, `strategi` |
| Gamer | `genre`, `engine`, `skill`, `tools` |
| Founder | `fungsi`, `tools`, `strategi` |
| Writer | `genre-tulisan`, `platform`, `gaya`, `tools` |

Contoh: catatan Learn/Course tentang React → `tags: [learn, course, framework]`.

---

## 4. Kategori Personal

### 4.1 Keluarga

| Komponen | Fungsi | Field Frontmatter | Nilai `sub` yang boleh diisi | Tag Wajib |
|---|---|---|---|---|
| Anggota | Profil tiap anggota keluarga | `sub`, `nama`, `tanggal-lahir` | `Ortu` / `Pasangan` / `Anak` / `Saudara` | `keluarga`, `anggota` |
| Acara | Rencana & dokumentasi acara keluarga | `sub`, `nama-acara`, `tanggal` | `Ulang Tahun` / `Anniversary` / `Liburan` / `Reuni` | `keluarga`, `acara` |
| Keuangan Keluarga | Tagihan, tabungan, asuransi rumah tangga | `sub`, `nama-item`, `jumlah`, `jatuh-tempo` | `Tagihan` / `Tabungan` / `Asuransi` | `keluarga`, `keuangan` |
| Dokumen | Arsip dokumen legal keluarga | `sub`, `nama-dokumen`, `tanggal-terbit`, `lokasi-fisik` | `KK` / `Akta` / `Sertifikat` / `Warisan` | `keluarga`, `dokumen` |
| Kenangan | Jurnal momen & foto keluarga | `sub`, `judul`, `tanggal` | `Foto` / `Jurnal` / `Momen` | `keluarga`, `kenangan` |

> Perbedaan dengan Income (kategori kerja): Keuangan Keluarga khusus rumah tangga, bukan penghasilan dari pekerjaan.

### 4.2 Health & Self

| Komponen | Fungsi | Field Frontmatter | Nilai `kategori`/`status` | Tag Wajib |
|---|---|---|---|---|
| Fisik | Catatan kesehatan fisik | `tanggal`, `kategori` | `checkup` / `olahraga` / `pola-makan` | `health`, `fisik` |
| Mental | Jurnal refleksi & mood | `tanggal` | — (isi bebas di bagian Mood) | `health`, `mental` |
| Habit Tracker | Pelacak kebiasaan harian | `nama-habit`, `target` | — | `health`, `habit` |
| Goal Pribadi | Target personal & progresnya | `nama-goal`, `deadline`, `status` | `berjalan` / `tercapai` / `gagal` / `ditunda` | `health`, `goal` |

---

## 5. Field Umum yang Muncul di Semua Template

| Field | Fungsi | Wajib Diisi? |
|---|---|---|
| `type` | Identitas jenis catatan (untuk query Dataview) | Ya, jangan diubah |
| `kategori` | Kategori kerja induk (Programmer/Teacher/dst) | Ya, untuk 7 kategori kerja |
| `tags` | Klasifikasi untuk pencarian & filter | Ya, minimal 2 tag wajib sesuai tabel di atas |
| `status` | Status proses (job/project/dll) | Ya, jika komponen punya field ini |
| `tanggal*` | Tanggal terkait (apply, mulai, terbit, dll) | Sebaiknya diisi untuk sorting kronologis |

**Aturan pengisian tag:**
1. Dua tag wajib (kategori sub + jenis komponen) — contoh: `[job, lamaran]` — jangan dihapus.
2. Boleh tambah tag topik dari Bagian 3 kalau relevan.
3. Untuk catatan lintas-kategori, tambahkan tag kategori kedua secara manual, contoh: `[job, lamaran, ai-engineer]`.
4. Jangan buat tag baru yang belum ada di pedoman ini tanpa mendaftarkannya juga di sini — supaya dashboard tetap konsisten.

---

## 6. Cara Membuat Dashboard dengan Dataview

Install plugin **Dataview** dari Community Plugins. Contoh query dasar:

**Semua project yang sedang Progress:**
```dataview
table client, project-name, sprint
from "Programmer/Project" or "Teacher/Project" or "AI Engineer/Project" or "Marketer/Project" or "Gamer/Project" or "Founder/Project" or "Writer/Project"
where status = "progress"
```

**Semua lamaran kerja yang masih aktif (belum ditolak/dibatalkan):**
```dataview
table perusahaan, posisi, status
from "Job"
where status != "ditolak" and status != "dibatalkan"
```

**Invoice yang belum dibayar:**
```dataview
table client, jumlah, tanggal-terbit
from "Income/Invoice"
where status = "belum dibayar"
```

Taruh dashboard ini di catatan terpisah, misal `Dashboard.md` di root vault.

---

## 7. Alur Kerja Harian (Rekomendasi)

1. Buka Templates → pilih komponen sesuai aktivitas hari ini.
2. Isi frontmatter — pilih salah satu nilai dari opsi `# pilihan:` yang tersedia, hapus sisanya.
3. Simpan file di folder kategori & sub kategori yang sesuai (bukan di folder Templates).
4. Update `status` setiap kali ada perkembangan (jangan pindah folder).
5. Cek Dashboard.md secara berkala untuk melihat progres lintas kategori.

---

## 8. Catatan Tambahan

- Nama file bebas, tapi disarankan format: `[Tanggal] - [Nama Singkat]` agar mudah diurutkan, contoh: `2026-09-18 - Interview Startup XYZ.md`.
- Semua field frontmatter di template bisa ditambah manual jika perlu, tapi jangan hapus field yang dipakai Dataview (`type`, `status`, `tags`).
- Kalau ingin komponen baru yang belum ada di pedoman ini, tambahkan dulu ke bagian tabel terkait supaya konsisten dengan seluruh sistem.
