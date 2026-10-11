# Indonesia Holidays Calendar Data

Data hari libur nasional, cuti bersama, dan hari peringatan (observances) Indonesia dalam format JSON.

## API Endpoint

```
https://[your-username].github.io/calendar-data/holidays-{year}.json
```

Contoh:
- `holidays-2026.json`
- `holidays-2027.json`

## Sumber Referensi Resmi

Data **hari libur nasional** dan **cuti bersama** diambil dari referensi resmi pemerintah Indonesia, yaitu **Surat Keputusan Bersama (SKB) 3 Menteri**:

1. **Menteri Agama** (Menag)
2. **Menteri Ketenagakerjaan** (Menaker)
3. **Menteri Pendayagunaan Aparatur Negara dan Reformasi Birokrasi** (PANRB)

### Contoh Referensi untuk Tahun 2026

- **Dokumen:** SKB 3 Menteri Nomor 1497 Tahun 2025, Nomor 2 Tahun 2025, dan Nomor 5 Tahun 2025
- **Tentang:** Hari Libur Nasional dan Cuti Bersama Tahun 2026
- **Tanggal ditetapkan:** 19 September 2025
- **Sumber berita resmi:** [Sekretariat Negara (setneg.go.id)](https://setneg.go.id/baca/index/inilah_skb_3_menteri_libur_nasional_dan_cuti_bersama_2026)
- **Jumlah libur nasional:** 17 hari
- **Jumlah cuti bersama:** 8 hari

### Referensi Tahun 2027

- **Dokumen:** SKB 3 Menteri Nomor 1205 Tahun 2026, Nomor 3 Tahun 2026, dan Nomor 2 Tahun 2026
- **Tentang:** Hari Libur Nasional dan Cuti Bersama Tahun 2027
- **Tanggal ditetapkan:** 15 September 2026
- **Sumber berita resmi:** [Sekretariat Negara (setneg.go.id)](https://www.setneg.go.id/baca/index/inilah_skb_3_menteri_libur_nasional_dan_cuti_bersama_2027)
- **Jumlah libur nasional:** 18 hari
- **Jumlah cuti bersama:** 8 hari

### Cara Mencari Referensi Tahun Berikutnya

Untuk membuat data tahun baru (misal: `holidays-2027.json`), cari pengumuman resmi dengan kata kunci:

```
SKB 3 menteri hari libur nasional dan cuti bersama [tahun]
```

Atau kunjungi langsung:
- [setneg.go.id](https://setneg.go.id)
- [kemenkopmk.go.id](https://www.kemenkopmk.go.id)

Pastikan data yang dimasukkan sesuai dengan tanggal, nama hari libur, dan jumlah hari yang tercantum dalam SKB resmi.

## Struktur Data

```json
{
  "year": 2026,
  "holidays": [...],
  "collective_leave": [...],
  "observances": [...]
}
```

### Field Description

| Field | Deskripsi |
|-------|-----------|
| `date` | Format ISO 8601 (`YYYY-MM-DD`) |
| `name` | Nama hari libur atau peringatan |
| `type` | Tipe: `national_holiday`, `collective_leave`, atau `observance` |
| `day` | Nama hari dalam bahasa Indonesia (Senin, Selasa, dst.) |

### Tipe Data

- **`holidays`**: Hari libur nasional resmi (17 hari per tahun, sesuai SKB 3 Menteri)
- **`collective_leave`**: Cuti bersama resmi (biasanya 6–8 hari per tahun, sesuai SKB 3 Menteri)
- **`observances`**: Hari peringatan/kenegaraan yang **tidak libur**

### Tentang Observances

Observances di Indonesia **tidak diatur dalam satu dokumen tunggal**. Masing-masing ditetapkan oleh berbagai peraturan perundang-undangan yang berbeda:

| Sumber Regulasi | Contoh Observances |
|-----------------|-------------------|
| **Keputusan Presiden (Keppres)** | Hari Pers Nasional (No. 5/1985), Hari Guru Nasional (No. 78/1994), Hari Anak Nasional (No. 44/1984), Hari Kesaktian Pancasila (No. 153/1967) |
| **Peraturan Presiden (Perpres)** | Perubahan/penambahan hari peringatan |
| **Undang-Undang (UU)** | Hari Anak Nasional (dasar: UU No. 4/1979 tentang Kesejahteraan Anak) |
| **Kebijakan Kementerian/Lembaga** | Hari peringatan sektoral (Hari Kesehatan, Hari Pendidikan, dll.) |

**Kebijakan di repositori ini:**
- Observances yang disimpan hanya yang berbasis **tanggal Masehi tetap** (tidak berubah tiap tahun).
- Observances berbasis kalender keagamaan/lunar (contoh: Siwaratri) **sengaja tidak dimasukkan** agar data konsisten dan bisa di-copy antar tahun tanpa penyesuaian.
- Jika ada observances baru yang ditetapkan pemerintah, bisa ditambahkan. Jika ada yang dicabut, bisa dihapus.

**Sumber observances yang digunakan:**
- **[Universitas Amikom Yogyakarta: Daftar Hari Besar Nasional dan Internasional 2026](https://blog.amikom.ac.id/hari-besar-nasional-dan-internasional-2026/)** — menjadi acuan praktis untuk menyusun daftar observances. Artikel ini merupakan rangkuman editorial, bukan keputusan resmi pemerintah.
- Dari daftar tersebut, repositori ini mengambil peringatan berlabel **nasional** yang memakai tanggal Masehi tetap. Peringatan internasional dan tanggal yang bergantung pada kalender lunar/agama tidak dimasukkan.
- Jika tersedia, dasar hukum atau pengumuman instansi terkait dapat dipakai sebagai verifikasi tambahan; namun cakupan daftar observances mengikuti acuan Amikom.

**Cara memverifikasi observances:**
1. Gunakan artikel Amikom untuk mengidentifikasi peringatan nasional dan tanggalnya.
2. Cek sumber resmi kementerian/lembaga atau naskah hukum bila perlu memastikan dasar penetapannya.
3. Hitung ulang nama hari berdasarkan tahun data; jangan menyalin nama hari dari artikel tahun lain.

## Checklist: Membuat Data Tahun Baru

Gunakan langkah-langkah berikut untuk membuat file `holidays-{tahun}.json` (contoh: `holidays-2027.json`):

### 1. Persiapan File
- [ ] Copy file tahun sebelumnya (contoh: `holidays-2026.json` → `holidays-2027.json`)
- [ ] Update nilai field `"year"` ke tahun baru

### 2. Holidays & Collective Leave (Wajib Ikuti SKB 3 Menteri)
- [ ] Cari SKB 3 Menteri untuk tahun baru dengan kata kunci: `SKB 3 menteri hari libur nasional dan cuti bersama {tahun}`
- [ ] Kunjungi [setneg.go.id](https://setneg.go.id) atau [kemenkopmk.go.id](https://www.kemenkopmk.go.id) jika perlu
- [ ] Hapus semua data lama di array `"holidays"` dan `"collective_leave"`
- [ ] Masukkan ulang data holidays sesuai daftar di SKB (biasanya 16–17 hari)
- [ ] Masukkan ulang data collective_leave sesuai daftar di SKB (biasanya 6–8 hari)
- [ ] Pastikan tanggal, nama hari libur, dan field `"day"` sudah benar
- [ ] **Perhatian:** Tanggal hari keagamaan (Idul Fitri, Idul Adha, Waisak, Imlek, Nyepi, dll.) **berganti tiap tahun**. Jangan asal copy dari tahun sebelumnya.

### 3. Observances (Copy & Cek)
- [ ] Copy seluruh data dari array `"observances"` tahun sebelumnya
- [ ] Gunakan artikel daftar hari besar nasional Amikom untuk tahun baru sebagai acuan utama
- [ ] Ambil peringatan berlabel nasional yang sesuai dengan kebijakan repositori; jangan masukkan peringatan internasional
- [ ] Cek pengumuman resmi atau dasar hukum bila tersedia dan hitung ulang nama hari
- [ ] **Jangan masukkan** observances berbasis kalender lunar/keagamaan non-Masehi

### 4. Validasi Akhir
- [ ] Pastikan tidak ada tanggal yang salah (contoh: 31 Februari)
- [ ] Pastikan field `"day"` cocok dengan tanggal (contoh: 1 Januari 2027 = Jumat)
- [ ] Pastikan format JSON valid (bisa dicek dengan JSON linter)
- [ ] Bandingkan jumlah holidays & collective_leave dengan jumlah di SKB
