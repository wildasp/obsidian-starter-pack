# Panduan Cepat Sintaks Markdown (untuk Obsidian)

Dokumen ini kumpulan seluruh simbol markdown yang akan sering kamu temui saat menulis catatan di Obsidian, dijelaskan singkat supaya langsung paham cara pakainya.

---

## 1. Heading (Judul & Sub-judul)

Dipakai untuk membuat struktur bertingkat pada catatan — semakin banyak tanda `#`, semakin kecil levelnya.

```md
# Heading 1   → judul utama halaman
## Heading 2  → sub-judul besar
### Heading 3 → sub-bagian
#### Heading 4
##### Heading 5
###### Heading 6 → level terkecil
```

**Kegunaan praktis:** di template kamu (Job, Learn, Project, dll), heading `##` dipakai untuk bagian seperti `## Detail Lowongan`, `## Catatan`, dst. Heading juga otomatis muncul di panel **Outline** Obsidian (sebelah kanan) sehingga catatan panjang mudah dinavigasi.

---

## 2. Teks Tebal, Miring, dan Gabungan

| Simbol | Hasil | Contoh |
|---|---|---|
| `*teks*` atau `_teks_` | *miring* | `*penting*` → *penting* |
| `**teks**` atau `__teks__` | **tebal** | `**deadline**` → **deadline** |
| `***teks***` | ***tebal+miring*** | `***urgent***` → ***urgent*** |
| `~~teks~~` | ~~coret~~ | `~~batal~~` → ~~batal~~ |

**Kegunaan praktis:** menandai kata kunci penting dalam catatan, misalnya **status: interview** atau ~~project dibatalkan~~.

---

## 3. Garis Pembatas (Horizontal Rule)

```md
---
```

Tiga tanda hubung (atau lebih) di baris sendiri membuat garis horizontal pemisah antar bagian.

⚠️ **Penting:** simbol `---` di bagian paling atas file (sebelum dan sesudah frontmatter) **bukan** garis pembatas biasa — itu adalah pembatas **frontmatter** (metadata YAML seperti `type:`, `status:`, `tags:`). Lihat Bagian 8.

---

## 4. Daftar (List)

### List tidak berurutan
```md
- Item pertama
- Item kedua
  - Sub-item (indentasi 2 spasi/tab)
```
atau bisa juga pakai `*` atau `+` sebagai pengganti `-`.

### List berurutan
```md
1. Langkah pertama
2. Langkah kedua
3. Langkah ketiga
```

### Checklist (checkbox) — paling sering dipakai di template
```md
- [ ] Belum selesai
- [x] Sudah selesai
```
Contoh nyata di template Job/Lamaran kamu:
```md
- [x] CV
- [x] Cover Letter
- [ ] Portfolio
```

---

## 5. Link

### Link ke halaman web
```md
[Teks yang tampil](https://url-nya.com)
```

### Link internal antar catatan Obsidian (Wikilink)
```md
[[Nama Catatan]]
```
Ini yang membuat **Graph View** Obsidian terhubung! Setiap kali kamu menulis `[[nama catatan lain]]`, Obsidian otomatis membuat garis penghubung di peta visual.

Contoh dari sample yang sudah dibuat:
```md
## Invoice
- Terkait: [[! 0.0.0.0 sample-invoice]]
```

---

## 6. Kode (Code)

### Kode inline (dalam satu baris)
```md
Gunakan perintah `npm install` untuk memasang paket.
```
Hasil: Gunakan perintah `npm install` untuk memasang paket.

### Blok kode (multi-baris)
````md
```
kode panjang
bisa banyak baris
```
````
Bisa juga ditambah nama bahasa supaya ada pewarnaan syntax, contoh:
````md
```javascript
console.log("halo dunia");
```
````

**Kegunaan praktis:** dipakai di template `Asset/Snippet` untuk menyimpan potongan kode.

---

## 7. Kutipan (Blockquote)

```md
> Ini adalah kutipan atau catatan penting yang ingin ditonjolkan.
```
Hasil tampil sebagai blok dengan garis vertikal di kiri teks.

---

## 8. Frontmatter (Metadata YAML)

Blok di **paling atas** file, diapit dua baris `---`. Ini bukan konten yang dibaca sebagai artikel, tapi **data** yang dipakai plugin seperti Dataview untuk query/filter.

```md
---
type: job-lamaran
status: dikirim
tags: [job, lamaran]
---
```

Semua template yang sudah dibuat pakai bagian ini di baris paling atas — jangan dihapus tanda `---`-nya, karena Obsidian akan gagal membaca metadata kalau strukturnya rusak.

---

## 9. Tabel

```md
| Kolom 1 | Kolom 2 |
|---|---|
| Isi A | Isi B |
| Isi C | Isi D |
```

Hasil:

| Kolom 1 | Kolom 2 |
|---|---|
| Isi A | Isi B |
| Isi C | Isi D |

Baris kedua (`|---|---|`) wajib ada — itu yang memberitahu Obsidian "ini tabel", bukan teks biasa.

---

## 10. Tag

```md
#tag-langsung-di-teks
```
Bisa ditulis langsung di badan catatan (bukan cuma di frontmatter). Tag dengan tanda pagar `#` ini juga bisa diklik dan dicari, sama fungsinya dengan `tags:` di frontmatter.

> Di sistem catatan kamu, tag sebaiknya konsisten ditaruh di frontmatter (`tags: [job, lamaran]`) bukan tersebar di badan teks, supaya query Dataview tetap rapi.

---

## 11. Gambar

```md
![Teks alternatif](nama-file-gambar.png)
```
Sama seperti link, tapi diawali tanda seru `!`. Untuk gambar yang disimpan lokal di vault, cukup tulis nama filenya (atau drag-drop gambar langsung ke catatan, Obsidian otomatis membuat sintaksnya).

---

## 12. Escape Karakter (menampilkan simbol markdown apa adanya)

Kalau ingin menampilkan tanda `*` atau `#` tanpa diformat, tambahkan backslash `\` di depannya:

```md
\*teks ini tidak jadi miring\*
```

---

## Ringkasan Simbol Sekali Lihat

| Simbol | Fungsi |
|---|---|
| `#` `##` `###` ... | Heading level 1–6 |
| `*teks*` / `**teks**` / `***teks***` | Miring / Tebal / Tebal-miring |
| `~~teks~~` | Coret |
| `---` | Garis pembatas (atau pembungkus frontmatter di posisi awal file) |
| `-` / `*` / `+` | List tidak berurutan |
| `1.` `2.` `3.` | List berurutan |
| `- [ ]` / `- [x]` | Checklist |
| `[teks](url)` | Link eksternal |
| `[[Nama Catatan]]` | Link internal Obsidian (untuk Graph View) |
| `` `kode` `` | Kode inline |
| ` ``` ` | Blok kode |
| `>` | Kutipan |
| `\| kolom \|` | Tabel |
| `#tagnama` | Tag |
| `![alt](gambar.png)` | Gambar |
| `\` | Escape simbol |

Simpan dokumen ini di root vault sebagai referensi cepat kapan pun lupa sintaks.
