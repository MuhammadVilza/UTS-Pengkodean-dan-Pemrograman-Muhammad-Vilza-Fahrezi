# DOKUMENTASI PROMPT AI SISTEM AKUNTANSI KAS KELUAR

Dokumen ini berisi kumpulan prompt terstruktur yang ditujukan untuk model kecerdasan buatan (AI) untuk Modul Voucher Kas Keluar (*Cash Disbursement Voucher*).

---

## 1. PROMPT GEMINI CANVAS / KODE GENERATOR

Gunakan prompt berikut untuk menghasilkan purwarupa antarmuka web interaktif beserta skema basis data secara utuh:

> **Prompt:**
> Tolong kembangkan purwarupa antarmuka web interaktif untuk modul Pencatatan Kas Keluar (*Cash Disbursement Voucher Entry*) dalam sistem akuntansi perusahaan, yang dikemas dalam satu file utuh berisi HTML, CSS, dan JavaScript.
> 
> **Spesifikasi Teknis & Fungsional:**
> 1. **Formulir Transaksi:** Menyediakan input tanggal transaksi, nomor voucher, deskripsi ringkas, serta tabel jurnal yang bersifat dinamis.
> 2. **Baris Jurnal Interaktif:** Tabel mencakup kolom pilihan akun (dari *Chart of Accounts*), nominal debit, nominal kredit, serta tombol untuk menambah maupun menghapus baris.
> 3. **Kalkulasi Otomatis:** Menghitung total debit, total kredit, serta selisih nilai secara *real-time* setiap kali ada perubahan pada angka nominal.
> 4. **Indikator Keseimbangan (*Balance Indicator*):** Menampilkan status visual "Balanced" jika selisih bernilai nol, atau "Unbalanced" jika sebaliknya.
> 5. **Aturan Tombol Submit:** Tombol kirim hanya akan aktif jika memenuhi seluruh kondisi berikut: minimal ada 2 baris valid, setiap baris hanya terisi nilai positif di salah satu sisi (debit atau kredit saja), seluruh akun sudah terpilih, dan total debit sama persis dengan total kredit.
> 6. **Lapisan Validasi:** Validasi sisi klien (*frontend*) dirancang untuk kenyamanan pengguna, sementara validasi ketat wajib diterapkan kembali di sisi *backend*/database sebelum data disimpan atau diposting.
> 7. **Rancangan Skema & Integrasi Supabase PostgreSQL:** Menggunakan tabel `chart_of_accounts`, `journal_headers`, `journal_lines`, serta `audit_logs`, dengan mekanisme penyimpanan dan posting yang dieksekusi melalui fungsi RPC `create_voucher` dan `post_voucher`.
> 8. **Jejak Audit & Integritas Data:** Setiap transaksi mencatat `created_by`, `created_at`, jenis aksi pengguna, identitas transaksi, serta *hash checksum* berbasis SHA-256.
> 9. **Kepatuhan Status Jurnal:** Jurnal yang sudah berstatus `POSTED` bersifat permanen (tidak boleh diubah atau dihapus); koreksi wajib dilakukan melalui mekanisme *reversing entry* (jurnal pembalik).
> 10. **Desain & Dokumentasi:** Tampilan antarmuka harus responsif, dilengkapi pesan kesalahan yang informatif, serta panduan konfigurasi Supabase yang ringkas.
> 
> *Sertakan kode implementasi lengkap, rancangan skema SQL, alur validasi, serta dokumentasi skenario pengujian yang mencakup: kondisi jurnal seimbang, jurnal tidak seimbang, input nominal negatif, dan simulasi upaya modifikasi pada jurnal berstatus `POSTED`. (Catatan: Jangan pernah menyatakan aplikasi telah terhubung atau teruji apabila proses pengujian tersebut belum benar-benar dijalankan).*

---

## 2. PROMPT UJI KEPATUHAN (NOTEBOOKLM / RAG)

Gunakan prompt berikut untuk menguji sumber dokumen (*source grounding*) pada basis pengetahuan seperti NotebookLM:

> **Prompt:**
> Berdasarkan sumber yang tersedia, mengenai file `dokumentasi_code_voucher_kas_keluar.txt`, apakah:
> (a) pencatatan kas keluar mendebit akun lawan dan mengkredit Kas atau Bank?
> (b) kas dan setara kas dikelompokkan sesuai definisi standar akuntansi yang berlaku?
> (c) pencatatan jurnal dipisahkan dari klasifikasi arus kas operasi, investasi, dan pendanaan?
> (d) total debit sama dengan total kredit sebelum posting?
> (e) jurnal `POSTED` dilindungi dan dikoreksi lewat jurnal pembalik?