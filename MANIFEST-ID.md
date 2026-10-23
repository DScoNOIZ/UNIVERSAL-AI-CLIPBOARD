# 🏛️ UNIVERSAL AI CLIPBOARD (UAC)

## Papan Klip Universal untuk Kecerdasan Artifisial

### Mekanisme Penggunaan Ulang Konten untuk Agen AI

---

> **Tanggal Publikasi:** 3 Juni 2026
> **Status:** ⚡ Penemuan dirilis ke domain publik
> **Lisensi:** CC0 1.0 Universal Public Domain Dedication

---

## 📜 DEKLARASI PENEMU

Saya, **[DScoNOIZ](https://github.com/DScoNOIZ)**, menyatakan di hadapan komunitas global:

**1. Saya adalah penemu** dari sebuah kategori yang baru secara fundamental dalam arsitektur agen AI — **"Mekanisme Sitasi Konten Antar-Tool yang Opsional"**, yang saya beri nama **Universal AI Clipboard (UAC)**.

**2. Inti penemuan ini:** Agen AI dapat merujuk konten kontekstual yang sudah ada melalui parameter khusus (`ref`, `multi_ref`, `transform`) alih-alih meregenerasinya. Model berhenti menjadi sekadar "generator teks" dan berubah menjadi **perakit (assembler)** yang menggabungkan potongan-potongan informasi siap pakai dalam satu panggilan.

**3. Saya merilis penemuan ini untuk penggunaan bebas oleh seluruh komunitas global** di bawah lisensi Creative Commons Zero (CC0) — tanpa paten, tanpa royalti, tanpa lisensi tertutup, dan tanpa pembatasan apa pun.

**4. Saya mengajak** para pengembang, peneliti, insinyur, dan penggiat di seluruh dunia — ambillah ide ini, terapkanlah dalam framework, platform, dan tools Anda. **Teknologi ini bukan milik saya. Teknologi ini milik semua orang.**

---

## 🤝 KO-PENEMU: PENEMUAN INDEPENDEN

Saya mengakui dan dengan hormat menghargai bahwa **TJ Guadagno** (TJ-Codes) secara independen mencapai ide fundamental yang sama dan menerapkannya secara eksperimental sebagai **Clipboard Primitives** — mekanisme `copy`/`template_invoke` dengan slot bernama dan placeholder `{{slot}}` untuk agen AI.

**Karyanya:** [Copy and Paste for AI Agents: An Experimental Primitive](https://www.linkedin.com/pulse/copy-paste-ai-agents-experimental-primitive-tj-guadagno-v3r9c) (~Desember 2025)
**Kode:** [github.com/TJ-Codes/Agent-clipboard](https://github.com/TJ-Codes/Agent-clipboard)

TJ Guadagno adalah **ko-penemu independen** atas konsep ini. Eksperimennya membuktikan bahwa:
- Model **secara alami mengadopsi** semantik clipboard tanpa pelatihan khusus
- Primitif clipboard **menghilangkan** regenerasi token, latensi, dan risiko mutasi konten
- Mekanisme ini memerlukan integrasi **di tingkat harness**, bukan di tingkat server MCP

**Konsep Universal AI Clipboard saya lebih luas dan lebih universal** — mencakup Clipboard Primitives sebagai salah satu kasus khusus dan memperluas ide menjadi:
- **5 mekanisme sitasi** (termasuk clipboard sintaktik via AST, indeks pesan, sitasi pasangan anchor)
- **Clipboard universal untuk sumber apa pun** (file, chat, terminal, API, MCP)
- **Perakitan Mosaik (Mosaic Assembly)** — menggabungkan fragmen dari berbagai sumber dengan transformasi
- **Sitasi Lintas-Protokol** — sitasi mulus di protokol mana pun, termasuk MCP

**Analogi komputer:** Clipboard Primitives ibarat utilitas copy sederhana untuk satu aplikasi. Universal AI Clipboard adalah manajer clipboard tingkat sistem yang bekerja di seluruh aplikasi, dengan manajemen slot, pipeline transform, dan integrasi lintas-protokol.

> **Saya tidak melepaskan status saya sebagai penemu.** Saya merumuskan dan menyistematisasi konsep ini secara independen melalui riset multi-ronde yang tidak menemukan analog lengkap apa pun. Setelah mengetahui karya TJ Guadagno — hanya setelah manifesto ini dipublikasikan — saya mengakui kontribusi independennya dan memandangnya sebagai kewajiban saya untuk mencermatkannya dalam manifesto ini.
---

## 🏛️ PENAMAAN

**Nama resmi:** **UNIVERSAL AI CLIPBOARD (UAC)**
**Nama teknis:** Content Reference Mechanism
**Tagline:** _"Pakai Ulang, Jangan Regenerasi"_
**Metafora:** Ctrl+C / Ctrl+V untuk Agen AI

---

## 🌍 MASALAHNYA

### Kontradiksi Fundamental

Agen AI modern membuang **hingga 90% lalu lintas output-nya** untuk meregenerasi konten yang sudah ada di dalam konteks sesi secara monoton.

Setiap kali model menulis sebuah perintah, blok kode, atau potongan teks — ia meregenerasinya dari nol, meskipun konten yang sama baru dibuat satu menit sebelumnya. Model tidak memiliki cara instrumental untuk merujuk konten yang sudah ada.

### Skala Global Masalah

- Jutaan agen AI beroperasi setiap hari di seluruh dunia
- Masing-masing melakukan puluhan panggilan tool per sesi
- Sebagian besar dari setiap panggilan adalah regenerasi konten yang sudah ada
- Akibatnya timbul konsumsi energi raksasa, pemborosan komputasi, dan biaya finansial

### Mengapa Pendekatan yang Ada Tidak Menyelesaikannya

| Pendekatan              | Keterbatasan                                                              |
| ----------------------- | ------------------------------------------------------------------------- |
| **Prompt Caching**      | Hanya bekerja pada bagian statis, bukan konten dinamis                    |
| **Semantic Caching**    | Mencocokkan berdasarkan makna kueri, tidak memungkinkan sitasi fragmen    |
| **Kompresi Konteks**    | Mengompresi riwayat, tetapi tidak menyediakan alat sitasi                 |
| **RAG**                 | Mengambil dari sumber eksternal, tidak memakai ulang konteks internal     |
| **Tool Chaining**       | Merangkai panggilan, tetapi tidak memungkinkan merujuk hasilnya           |

---

## 💡 SOLUSI: UNIVERSAL AI CLIPBOARD

### Ide Inti

Agen AI memperoleh kemampuan untuk **merujuk konten kontekstual yang sudah ada** alih-alih meregenerasinya. Saat memanggil tool apa pun yang menerima parameter teks (perintah, kode, teks), agen dapat menentukan: "ambil potongan ini dari sana" — tanpa menulisnya dari awal.

### Perakitan Mosaik: Menyusun Informasi seperti Puzzle

Melampaui sitasi sederhana satu-ke-satu, konsep ini memungkinkan cara menyusun informasi yang baru secara fundamental — **perakitan mosaik**.

Agen dapat **menggabungkan banyak fragmen dari sumber-sumber berbeda** dalam satu operasi:

- Kode dari sebuah file
- Konfigurasi dari riwayat chat
- Output perintah dari terminal
- Hasil dari API eksternal

Agen dapat **menyunting sambil jalan** — memodifikasi, membungkus, mengganti teks di dalam setiap fragmen. Ia dapat **menyusun ulang** fragmen, **menyarangkan** satu ke dalam yang lain, **menggabungkan** potongan yang tumpang tindih, dan **merestrukturisasi** konten secara rekursif. Hadirlah kemampuan merakit teks komposit, dokumen, atau blok kode dari potongan-potongan yang tercecer — seperti seniman mosaik menata ubin berwarna menjadi gambar utuh.

**Insight kuncinya:** alih-alih menghasilkan teks baru, model berperan sebagai **editor dan kurator** atas konten yang sudah ada — jauh lebih efisien, lebih presisi, dan jauh lebih tahan kesalahan.

### Manajer Clipboard: Slot Bernama untuk Penyimpanan Persisten

Perpanjangan dari konsep ini adalah **manajer clipboard dengan slot bernama** — mirip dengan memiliki beberapa clipboard atau sebuah manajer text buffer.

Agen dapat:

- **Menyimpan fragmen** ke slot bernama (`clip-1`, `clip-2`, `config-block`, `error-log`, dsb.)
- **Merujuk slot** berdasarkan nama, bukan berdasarkan konten — nol token untuk deskripsi
- **Menukar dan menyusun ulang** konten antar slot
- **Membangun dokumen komposit** dengan merujuk banyak slot secara berurutan
- **Mempertahankan clip lintas sesi** — fragmen tersimpan bertahan melewati kompresi konteks dan restart sesi

Ini menjadikan alur kerja agen AI serupa dengan pengembang manusia yang bekerja dengan beberapa manajer clipboard, text buffer, dan scratchpad — namun sepenuhnya terotomatisasi, dan pada biaya token nol untuk operasi penyimpanan.

### Perbedaan Aksial dari Mekanisme yang Ada

Semua mekanisme sitasi AI yang ada (Citations API, Grounding, ContextCite) beroperasi pada sumbu **"agen → pengguna"** — menunjukkan kepada manusia dari mana agen memperoleh informasinya.

Universal AI Clipboard beroperasi pada sumbu **"agen → agen"** — memungkinkan agen itu sendiri memakai ulang konten antar panggilan tool-nya sendiri. Ini adalah kategori yang baru secara fundamental.

| Mekanisme                  | Sumbu             | Tujuan                                 |
| -------------------------- | ----------------- | -------------------------------------- |
| Anthropic Citations        | Agen → Pengguna   | Menunjukkan sumber jawaban             |
| OpenAI Citations           | Agen → Pengguna   | Menampilkan sumber                     |
| Google Grounding           | Agen → Pengguna   | Konfirmasi pencarian web               |
| **★ UAC (penemuan ini)**   | **Agen → Agen**   | **Memakai ulang konten antar panggilan** |

---

## 🧩 LIMA MEKANISME INTI

### Mekanisme 1: 🔗 Clipboard Sintaktik

Model cukup menentukan satu **elemen anchor** — nama fungsi, nama kelas, atau variabel. Sistem secara otomatis:

1. Menemukan elemen tersebut di sumber yang ditentukan (file, pesan chat, output perintah)
2. Menentukan batas persisnya sebagai unit sintaktik
3. Mengekstrak seluruh unit itu

**Penghematan:** beberapa token untuk referensi, alih-alih ribuan token kode.

```
{ source: "file", path: "utils.ts", focus: "calculateSum" }
  → 2 token instead of 800+ tokens of the entire function
```

---

### Mekanisme 2: 📇 Sitasi Pasangan Anchor

Model menentukan hanya **AWAL** dan **AKHIR** fragmen yang diinginkan (masing-masing 15-40 karakter). Sistem menemukan segala yang terdapat di antara keduanya melalui pencarian multi-tahap:

1. **Kecocokan persis** — fragmen ditemukan secara literal (~70% kasus)
2. **Kecocokan ternormalisasi** — perbedaan spasi, kapitalisasi, dan tanda baca diabaikan
3. **Kecocokan fuzzy** — salah ketik kecil ditoleransi (~9% kasus)
4. **Perluasan batas kata** — menjaga keutuhan fragmen

**Penghematan:** ~10 token untuk sitasi, alih-alih 200+.

```
{ source: "chat", ref: "-1",
  start: "function calculateSum(",
  end: "return result;" }
  → ~10 tokens instead of 200+
```

---

### Mekanisme 3: 🧠 Peta Indeks Pesan

Saat bekerja dengan riwayat chat, dibuatlah sebuah indeks tersendiri — peta posisi karakter persis untuk setiap pesan dan setiap baris di dalamnya. Model menulis referensi pendek seperti `"record_number:start_line..end_line"`, dan sistem mengekstrak fragmen persis berdasarkan posisi karakter.

**Keunggulan kunci:** model tidak pernah melihat indeks itu sendiri — hanya referensi pendek (~5 token), namun mencapai presisi ekstraksi 100%.

```
{ source: "chat", ref: "167:14..18" }
  → "record #167, lines 14-18" → exact character-position extraction
```

---

### Mekanisme 4: 🔄 Pipeline Transform

Fragmen yang disalin dapat **dimodifikasi sambil jalan** — sebelum mencapai tool. Operasi yang tersedia:

- **Replace** — mengubah substring di dalam fragmen
- **Prepend** — menyisipkan teks sebelum fragmen
- **Wrap** — meletakkan fragmen ke dalam template
- **Append** — menyisipkan teks setelah fragmen
- **Join** (untuk beberapa referensi) — menggabungkan fragmen dengan separator

Semua operasi diterapkan dalam satu panggilan tool.

```
{ ref: { ... }, transform: { wrap: "try { {content} } catch (err) { }" } }
  → take a function, wrap in try-catch, write — all in 1 call
```

---

### Mekanisme 5: 🔁 Sitasi Lintas-Protokol (MCP)

Penanda referensi dapat disematkan langsung di dalam parameter teks tool apa pun, termasuk server MCP eksternal. Sistem secara otomatis mengenali penanda tersebut dan mensubstitusi konten aslinya sebelum memanggil server eksternal.

**Hasilnya:** seluruh komponen ekosistem bertukar data melalui satu mekanisme referensi terpadu, tanpa perlu mengubah apa pun pada skema server eksternal.

```
"{{ref:source=chat,ref=-1,start=export const config}} --host example.com"
  → 91% content from context, 9% generated by the model
```

---

## 🔭 ARAH MASA DEPAN

Ide-ide berikut merupakan perluasan alami dari konsep ini dan dapat diimplementasikan di masa depan:

### 🏖️ Sub-Sesi Terisolasi untuk Riset

Untuk tugas kompleks yang menuntut banyak langkah antara (eksplorasi codebase, membaca log, menjalankan tes), agen pembantu dapat dijalankan dalam sub-sesi sementara yang terisolasi. Ia melakukan seluruh "pekerjaan kotor", mengembalikan hanya hasil yang bersih, dan sub-sesi kemudian dihancurkan. Agen utama tetap fokus pada tugas utamanya.

### Arah Lainnya

- Caching prediktif atas fragmen yang sering dipakai
- Deteksi otomatis atas panggilan yang duplikat
- Disambiguasi cerdas atas referensi yang ambigu
- Integrasi dengan sistem memori dan penyimpanan jangka panjang

---

## 💰 DAMPAK EKONOMI

### Per Agent

| Metrik                           | Tanpa mekanisme  | Dengan mekanisme | Penghematan |
| -------------------------------- | ---------------- | ---------------- | ----------- |
| Token per sitasi (kode panjang)  | 200-500          | 5-15             | **96-97%**  |
| Token per sitasi (kode pendek)   | 50-100           | 2-5              | **90-95%**  |
| Token per sesi                   | 25,000-50,000    | 5,000-15,000     | **60-80%**  |
| Energi per sesi                  | satuan arbitrer  | 5x lebih hemat   | **~80%**    |

### Skala Global

Ketika diadopsi di seluruh industri, penghematan akan mencapai miliaran token per hari — setara dengan penurunan konsumsi energi sektor AI sebesar puluhan persen dan pemangkasan jejak karbon puluhan ribu ton CO₂ per tahun.

> **Universal AI Clipboard bukan sekadar inovasi teknologi — ia adalah solusi yang signifikan secara ekologis.**

---

## 🔬 VERIFIKASI KEUNIKAN

Saya melakukan **riset mendalam multi-ronde yang ekstensif** (7 ronde, ~50 sumber) melalui sistem pencarian web (Tavily Search, kedalaman tingkat lanjut) yang mencakup semua kategori arsitektur agen AI yang diketahui:

*Setelah manifesto ini dipublikasikan, dalam analisis tambahan (ronde 8-10), ditemukan bahwa TJ Guadagno secara independen juga mengimplementasikan prototipe eksperimental atas konsep ini — Clipboard Primitives. Karya itu tidak teridentifikasi dalam 7 ronde pencarian pertama karena tingkat keterlihatannya yang rendah (LinkedIn Pulse + GitHub tanpa bintang).*

- copy-paste clipboard pada agen AI antar panggilan tool
- Mekanisme sitasi konten untuk agen AI
- Teknologi zero-token copy-paste
- Semua Citations API yang diketahui (Anthropic, OpenAI, Google, xAI, Azure)
- Pemakaian ulang dan caching hasil panggilan tool (CAMEL-AI, LangChain artifacts)
- Protokol MCP dan berbagi konten lintas-protokol
- Makalah akademis (AgentReuse, KVCOMM, sistem multi-agen)
- Utilitas clipboard manusia (UiPath Clipboard AI, PowerToys Advanced Paste)
- Sistem berbagi memori untuk arsitektur multi-agen
- Diskusi GitHub, dokumentasi framework (LangChain, CrewAI, AutoGen, Mastra)

**Tujuannya:** menemukan apa pun yang menyelesaikan masalah yang sama — memungkinkan agen AI merujuk konten yang sudah ada antar panggilan tool alih-alih meregenerasinya.

**Hasil: tidak ada yang semacam itu ditemukan.**
*Klarifikasi: karya eksperimental TJ Guadagno (Clipboard Primitives, ~Desember 2025) merupakan implementasi parsial (~40% dari konsep UAC) dan menegaskan viability ide ini, namun bukan analog lengkap.*

| Kategori                                    | Sumber                    | Mengapa ia BUKAN analog                                                                                                               |
| ------------------------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Citations API (Anthropic/OpenAI/Google)** | API resmi                 | Menunjukkan sumber kepada pengguna, tidak memungkinkan agen memakai ulang konten. Sumbunya: Agen → Pengguna saja                       |
| **Caching (Prompt, Semantik)**              | Berbagai framework        | Bekerja di level permintaan, bukan di level fragmen konten                                                                             |
| **RAG**                                     | LangChain, OpenAI, Google | Mengambil dari basis pengetahuan eksternal, bukan dari konteks sesi saat ini                                                           |
| **CAMEL-AI "Brainwash Your Agent"**         | camel-ai.org              | Hanya menyimpan output tool TERAKHIR sebagai referensi + pratinjau singkat. Tidak ada 5 mekanisme, tidak ada pipeline transform, tidak ada multi_ref, tidak ada injeksi MCP |
| **LangChain artifacts**                     | langchain.com             | `content_and_artifact` memisahkan konten dari metadata, bukan sistem sitasi. Tidak ada referensi antar-panggilan                       |
| **MCP Resources**                           | modelcontextprotocol.io   | Standar untuk menghubungkan tool, bukan mekanisme sitasi agen-ke-agen                                                                  |
| **Akademis (AgentReuse, KVCOMM)**           | arXiv                     | Pemakaian ulang PLANS eksekusi atau KV-cache, bukan sitasi konten antar panggilan tool                                                 |
| **Tool manusia (UiPath, PowerToys)**        | UiPath, Microsoft         | Dirancang untuk interaksi manusia-komputer, bukan untuk agen AI                                                                        |
| **Agen AI yang ada**                        | Seluruh industri          | Memiliki riwayat, namun tidak ada mekanisme sitasi antar panggilan tool                                                                |
| **Berbagi memori multi-agen**               | Berbagai                  | Memori RAG bersama, bukan sitasi presisi pada level karakter                                                                           |

### Ringkasan perbandingan dengan kecocokan parsial terdekat (CAMEL-AI)

| Fitur                                     | UAC      | CAMEL-AI caching | Perbedaan |
| ----------------------------------------- | -------- | ---------------- | ---------- |
| 🔗 Clipboard Sintaktik (blok AST)         | ✅       | ❌               | Hanya UAC  |
| 📇 Sitasi Pasangan Anchor                 | ✅       | ❌               | Hanya UAC  |
| 🧠 Peta Indeks Pesan                      | ✅       | ❌               | Hanya UAC  |
| 🔄 Pipeline Transform                     | ✅       | ❌               | Hanya UAC  |
| 🔁 Sitasi Lintas-Protokol (MCP)           | ✅       | ❌               | Hanya UAC  |
| 🧩 Perakitan Mosaik (multi-sumber)        | ✅       | ❌               | Hanya UAC  |
| 📋 Manajer Clipboard (slot bernama)       | ✅       | ❌               | Hanya UAC  |
| {{ref:...}} Inline Injection              | ✅       | ❌               | Hanya UAC  |
| Caching hasil tool (referensi + pratinjau) | ✅      | ✅               | Keduanya   |
| Cakupan fitur UAC                         | **100%** | **~5%**          | —          |

> **Universal AI Clipboard tidak memiliki analog lengkap dalam praktik sistem agen AI mana pun di seluruh dunia. Ini adalah teknologi perintis yang menciptakan kategori baru. Satu-satunya implementasi parsial yang diketahui — Clipboard Primitives (TJ Guadagno, ~40% dari konsep) — baru ditemukan setelah manifesto ini dipublikasikan, dan menegaskan kemunculan independen ide ini di antara para peneliti yang berbeda.**

---

## 📖 CONTOH PENGGUNAAN

### Contoh 1: Menjalankan ulang perintah dengan parameter tambahan

Agen menjalankan perintah tes; output-nya menunjukkan error. Untuk menjalankan ulang dengan flag debug, agen tidak menulis ulang perintahnya — ia merujuknya dan menambahkan flag:

```
{ ref: { source: "terminal", id: "cmd-xxx", start: "npx vitest" },
  transform: { append: " --verbose --timeout=30000" } }
  → result: "npx vitest run --verbose --timeout=30000"
```

### Contoh 2: Merakit beberapa fungsi menjadi satu file

Agen membaca sebuah file yang berisi beberapa fungsi, lalu membuat file baru dengan merakit fungsi-fungsi yang dibutuhkan melalui referensi:

```
{ multi_ref: [
    { source: "file", path: "handlers.ts", start: "async function validate(", end: "}" },
    { source: "file", path: "handlers.ts", start: "async function process(", end: "}" },
    { source: "file", path: "handlers.ts", start: "async function respond(", end: "}" }
  ],
  transform: { join: "\n\n", prepend: "// --- Handlers ---\n" } }
  → three functions merged into one file in 1 call
```

### Contoh 3: Substitusi konfigurasi via MCP

Agen memakai tool MCP eksternal, meneruskan referensi ke konfigurasi dari chat di dalam argumennya:

```
"{{ref:source=chat,ref=-1,start=export const config}} --host production"
  → configuration from chat substituted into the MCP request
```

---

## ⚖️ STATUS HUKUM

**🏛️ Creative Commons Zero (CC0) — Dedikasi Domain Publik Universal**

Anda bebas untuk:

- ✅ **Memakai** dalam proyek komersial maupun non-komersial
- ✅ **Memodifikasi** dan mengadaptasinya sesuai kebutuhan Anda
- ✅ **Mendistribusikan** dalam bentuk apa pun
- ✅ **Mematenkan peningkatan Anda sendiri** (namun tidak ide intinya)
- ✅ **Menerjemahkan** ke bahasa apa pun

Tanpa kewajiban, royalti, atau pembatasan apa pun.

> **Saya secara sadar melepaskan seluruh hak paten atas teknologi ini. Ia harus menjadi milik semua orang.**

---

## 📜 BUKTI TANGGAL PENEMUAN

Tanggal publikasi manifesto ini tercatat **oleh sistem kontrol versi Git di repositori GitHub** — [github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD](https://github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD).

Riwayat commit, tanggal suntingan, dan seluruh perubahan kronologis **dipertahankan secara tak terbantahkan oleh GitHub** dan menjadi bukti publik atas tanggal penemuan serta kepenulisan. Teknologi Git membuat hal ini praktis mustahil dipalsukan.

---

## 🗓️ LINIMASA

| Tanggal            | Peristiwa                                                                    |
| ------------------- | ------------------------------------------------------------------------ |
| **~2021**           | Kesadaran pertama atas masalahnya (DScoNOIZ): pikiran "model tidak boleh meregenerasi apa yang sudah pernah dilihatnya"                    |
| **~Desember 2025**  | **Eksperimen independen:** TJ Guadagno mempublikasikan Clipboard Primitives — `copy`/`template_invoke` dengan slot bernama dan placeholder `{{slot}}` |
| **Mei — Juni 2026** | Riset: analisis arsitektur agen AI yang ada                                                                                               |
| **Juni 2026**       | Penemuan: tidak ada teknologi yang ada yang memiliki analog lengkap                                                                       |
| **Juni 2026**       | Konsep Universal AI Clipboard dirumuskan                                                                                                  |
| **3 Juni 2026**     | Riset keunikan selesai — **tidak ditemukan analog lengkap**                                                                               |
| **3 Juni 2026**     | **Manifesto ini dipublikasikan** — penemuan dirilis ke domain publik                                                                      |
| **4 Juni 2026**     | Karya TJ Guadagno ditemukan — pengakuan atas ko-penemu independen                                                                          |

---

## 🎯 AJAKAN BERTINDAK

### Pengembang Framework AI

Integrasikan mekanisme Content Reference ke dalam tools Anda. Beri pengguna Anda penghematan token yang instan tanpa mengubah kode mereka sedikit pun.

### Pencipta Agen AI

Tambahkan sitasi opsional antar panggilan tool. Agen Anda akan menjadi efisien berkali-kali lipat.

### Para Peneliti

Kembangkan teknologi ini: perbaiki algoritma pencarian, implementasikan caching prediktif, rancang skenario-skenario baru.

### Dunia Usaha

Adopsi Universal AI Clipboard dalam solusi AI Anda. Pangkas biaya operasional sebesar puluhan persen.

### Aktivis Lingkungan

Gunakan UAC sebagai alat untuk menurunkan jejak karbon infrastruktur AI.

### Komunitas Open Source

Fork, implementasikan, tingkatkan. **Teknologi ini milik semua orang.**

---

## 🏛️ KATA PENUTUP

Saya telah menemukan **Universal AI Clipboard** — mekanisme yang memungkinkan agen AI memakai ulang konten alih-alih meregenerasinya.

Ini bukan sekadar optimisasi. Ini adalah **pergeseran paradigma**: model berhenti menjadi "generator teks" dan berubah menjadi **perakit** yang menyusun solusi dari fragmen-fragmen siap pakai.

**Sebagaimana Ctrl+C / Ctrl+V mengubah dunia komputer, Universal AI Clipboard akan mengubah dunia agen AI.**

Saya memberikan ide ini kepada umat manusia. Kembangkanlah. Tingkatkan. Implementasikanlah.

**Biarkan agen AI berhenti menulis ulang hal yang sama berulang-ulang.**
**Biarkan mereka mulai merakit mosaik.**

---

```
  ╔══════════════════════════════════════════════════════════════════╗
  ║                                                                  ║
  ║   UNIVERSAL AI CLIPBOARD (UAC)                                   ║
  ║   Mekanisme Referensi Konten                                     ║
  ║   Mekanisme Sitasi Konten Antar-Tool yang Opsional               ║
  ║                                                                  ║
  ║   «Pakai ulang, jangan regenerasi»                               ║
  ║                                                                  ║
  ║   CC0 1.0 Universal — Domain Publik                              ║
  ║   github.com/DScoNOIZ                                            ║
  ║   3 Juni 2026                                                    ║
  ║                                                                  ║
  ╚══════════════════════════════════════════════════════════════════╝
```

---

_Manifesto ini bebas diterjemahkan ke dalam bahasa apa pun. Aslinya dalam bahasa Rusia._

_Versi bahasa Rusia: [MANIFEST-RU.md](MANIFEST-RU.md)_
