# Dokumentasi Dataset TKI UAS

## Deskripsi

Dataset TKI UAS adalah koleksi data putusan pengadilan terkait kasus Tenaga Kerja Indonesia (TKI). Dataset ini dikumpulkan untuk keperluan penelitian akademik dalam pengembangan sistem retrieval berbasis vektor (vector-based retrieval system) yang dapat mencari putusan pengadilan serupa berdasarkan fakta-fakta kasus.

Dataset berisi 5 kolom utama yang telah difilter dari data asli untuk fokus pada informasi hukum dan fakta kasus.

## Sumber Data

Data diperoleh dari sistem informasi pengadilan resmi Republik Indonesia. Data telah diproses untuk menghilangkan informasi sensitif dan difokuskan pada aspek hukum dan fakta kasus.

## Struktur Data

Dataset tersimpan dalam format Excel (.xlsx) dengan nama file `TKI UAS.xlsx` di folder `dataset/`.

### Kolom-Kolom dalam Dataset

Dataset menggunakan 5 kolom utama:

| Kolom | Deskripsi | Tipe Data |
|-------|-----------|-----------|
| No | Nomor urut record | integer |
| nomor | Nomor putusan pengadilan | string |
| nama pengadilan negeri | Nama lembaga peradilan | string |
| petunjuk bb | Barang bukti dalam format JSON array | string |
| putusan | Teks amar putusan | string |

## Tipe Data

- **Integer**: Kolom `No`
- **String**: Kolom `nomor`, `nama pengadilan negeri`, `petunjuk bb`, `putusan`

## Contoh Data

Berikut adalah 5 baris pertama dari dataset:

| No | nomor | nama pengadilan negeri | petunjuk bb | putusan |
| --- | --- | --- | --- | --- |
| 1 | Nomor 227/Pid.Sus/2024/PN Jkt.Brt | Pengadilan Negeri Jakarta Barat | ["1 (satu) unit Handphone merk Samsung S22 warna putih.","1 (satu) unit Kartu ATM BCA Nomor Reken... | MENGADILI:<br>1. Menyatakan Terdakwa ANDREAN JUSTIN bin TJIOE KOK KHIONG telah terbukti secara sah d... |
| 2 | Nomor: 75/Pid.Sus/2016/PN.Jkt.Brt. | Pengadilan Negeri Jakarta Barat | ["1 (satu) paket plastic kecil shabu dengan berat bruto 0,2 gram, setelah dilakukan pemeriksaan l... | MENGADILI<br>1. Menyatakan Terdakwa ARIF BIJAKSONO BIN HEMAT telah terbukti secara sah dan meyakinka... |
| 3 | Nomor: 728/Pid.Sus/2024/PN.Jkt.Brt. | Pengadilan Negeri Jakarta Barat | ["1 (satu) bungkus plastik klip ukuran sedang berisikan serbuk warna putih dengan berat netto 14,... | MENGADILI:<br>1. Menyatakan Terdakwa OKTAVIANUS WIJAYA Als OKTA Bin JIN KIUN telah terbukti secara s... |
| 4 | Nomor 770/Pid.Sus/2024/PN Jkt.Brt | Pengadilan Negeri Jakarta Barat | ["2 (dua) bungkus plastik klip ukuran sedang masing-masing berisikan kristal warna putih dengan b... | MENGADILI:<br>1. Menyatakan Terdakwa Rachmat Alias Tepos Bin H. Saaman tersebut diatas, telah terbuk... |
| 5 | Nomor 889/Pid.Sus/2024/PN Jkt.Brt | Pengadilan Negeri Jakarta Barat | ["1 bungkus plastik klip (kode A) berisikan Metamfetamina dengan berat netto 4,7865 gram (sisa)."... | M E N G A D I L I<br>1. Menyatakan Terdakwa Muhammad Taufik Alias Abang Bin Abdul Malik tersebut dia... |

## Statistik Dataset

- **Jumlah Record**: 50
- **Jumlah Kolom**: 5
- **Rentang Tanggal**: 2024

## Penggunaan Dataset

Dataset ini dapat digunakan untuk:

1. **Pengembangan Sistem Retrieval**: Mencari putusan serupa berdasarkan fakta kasus menggunakan teknik embedding dan vector search
2. **Analisis Hukum**: Menganalisis pola putusan dalam kasus TKI
3. **Penelitian Akademik**: Studi tentang sistem peradilan terkait TKI
4. **Machine Learning**: Training model untuk klasifikasi atau retrieval otomatis

### Contoh Penggunaan dalam Kode

```python
import pandas as pd

# Load dataset
df = pd.read_excel('dataset/Overview.xlsx')

# Filter kolom utama
filtered_df = df[['nomor', 'nama pengadilan negeri', 'petunjuk bb', 'putusan']]

# Parsing petunjuk bb
import json
def parse_bb(value):
    if pd.isna(value):
        return value
    try:
        items = json.loads(value)
        return '\n'.join(f"{i+1}. {item}" for i, item in enumerate(items))
    except:
        return str(value)

filtered_df['petunjuk bb'] = filtered_df['petunjuk bb'].apply(parse_bb)
```

## Lisensi

Dataset ini untuk keperluan akademik dan penelitian. Penggunaan komersial memerlukan izin dari sumber data asli.

## Kontak

Untuk pertanyaan lebih lanjut tentang dataset ini, hubungi:
- Nama: Muhammad Hariz Faizul Anwar
- Email: muh4mm4dh4r1z@gmail.com
- Institusi: Universitas Universitas Muhammadiyah Malang

## Riwayat Versi

- **v1.0** (November 2025): Versi awal dokumentasi dataset

## Catatan

- Beberapa kolom mungkin mengandung nilai kosong (NaN) yang perlu ditangani dalam preprocessing
- Kolom `petunjuk bb` memerlukan parsing JSON untuk mendapatkan list barang bukti
- Data telah dianonimkan untuk melindungi privasi individu yang terlibat</content>
<parameter name="filePath">d:\Side\UTS TKI\readme.md
