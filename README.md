# UTS Pengkodean dan Pemrograman

| | |
| --- | --- |
| **Nama** | Muhammad Vilza Fahrezi |
| **NIM / Kelas** | 12030124140232 / D |
| **Mata Kuliah** | Pengkodean dan Pemrograman |
| **Dosen Pengampu** | Dr. Totok Dewayanto, S.E., M.Si., Akt. |

## Tujuan UTS

Ujian Tengah Semester ini bertujuan untuk:

1. Merancang arsitektur data sistem akuntansi (General Ledger) yang ternormalisasi dan menjaga integritas jurnal melalui skema relasional dan database constraints.
2. Mengotomasi proses bisnis di sisi database, seperti pembaruan persediaan dengan trigger dan stored procedure, serta menangani concurrency dan race condition.
3. Mengintegrasikan purwarupa web full-stack dengan basis data (Supabase/PostgreSQL), lengkap dengan validasi berlapis, jejak audit (audit trail), dan perlindungan jurnal yang sudah diposting.
4. Mengorkestrasi AI tools secara terdokumentasi dan bertanggung jawab: Gemini Canvas untuk menghasilkan purwarupa, dan NotebookLM untuk memverifikasi aturan bisnis terhadap standar akuntansi (PSAK).

## Isi Repositori

| Berkas | Keterangan |
| --- | --- |
| `voucher_entri_transaksi_kas_keluar.html` | Purwarupa aplikasi web **Voucher Entri Transaksi Kas Keluar** dalam satu berkas (HTML, Tailwind CSS, JavaScript). Memuat formulir voucher dengan tabel jurnal dinamis, simulator skenario pengujian, serta panduan konfigurasi Supabase dan skema PostgreSQL. Rancangannya mencakup RPC `create_voucher` dan `post_voucher`, tabel `audit_logs`, checksum SHA-256, dan reversing entry untuk koreksi jurnal POSTED. |
| `prompt_erd_documentation.md` | Dokumentasi prompt AI: (1) prompt untuk Gemini Canvas guna menghasilkan purwarupa web dan skema basis data, dan (2) prompt uji kepatuhan untuk NotebookLM guna memeriksa aturan bisnis kas keluar terhadap sumber dokumen. |

## Cara Menjalankan

1. Unduh seluruh berkas ke satu folder.
2. Buka `voucher_entri_transaksi_kas_keluar.html` di peramban (Chrome, Edge, atau Firefox). Koneksi internet diperlukan karena Tailwind CSS dimuat dari CDN.
3. Gunakan tab simulator pada halaman untuk mencoba skenario: jurnal seimbang, jurnal tidak seimbang, nominal negatif, dan upaya mengubah jurnal yang sudah diposting.
4. Untuk integrasi database, ikuti panduan konfigurasi Supabase di dalam halaman tersebut.

## Catatan

- Validasi di antarmuka hanya untuk kenyamanan pengguna. Penegakan aturan yang sebenarnya dirancang berada di database (constraint, trigger, dan fungsi RPC).
- Koneksi ke Supabase tidak boleh dinyatakan berhasil sebelum benar-benar diuji pada project Supabase yang dikonfigurasi sendiri.
- Seluruh penggunaan AI (Gemini Canvas dan NotebookLM) didokumentasikan pada `prompt_erd_documentation.md`.
