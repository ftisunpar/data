# Dokumentasi Open Data FTIS
Laman ini digunakan untuk mendokumentasikan struktur data dari Open Data FTIS. Data yang terdapat pada repositori ini dapat dipergunakan secara bebas pakai, mengacu pada [lisensi yand diberikan](../LICENSE) pada repository ini.

## Daftar Isi
- [Akses Publik](#Akses-Publik)
- [Detil Endpoint](#Detil-Endpoint)
  - [Prasyarat](#Prasyarat)

## Akses Publik
Berdasarkan [isu ini](https://github.com/ftisunpar/data/issues/1), anda dapat mengkases open data tersebut pada[https://ftisunpar.github.io/data/prasyarat.json](https://ftisunpar.github.io/data/prasyarat.json).

## Detil Endpoint
Endpoint di definisikan sebagai url yang mengikuti setelah basis url `https://ftisunpar.github.io/data/`. 

Sebagai contoh endpoint `prasyarat.json` memiliki alamat url lengkap `https://ftisunpar.github.io/data/prasyarat.json`.

### `prasyarat.json`
`Prasyarat.json` memiliki informasi tentang seluruh matakuliah, jumlah SKS, posisi semester, serta prasyarat yang ada. Bentuk datanya adalah array dari matakuliah.

Setiap struktur matakuliah memiliki properties sebagai berikut:
- `kode` (String)
- `nama` (String)
- `prasyarat`
  - `tempuh` (String[])
  - `lulus` (String[])
  - `bersamaan` (String[])
  - `berlakuAngkatan` (Number|null)
- `sks` (Number)
- `wajib` (Boolean)
- `semester` (Number)

Untuk memperjelas bagian ini, berikut contoh dari objek tersebut:

```js
 {
    "kode": "AIF181100",
    "nama": "Dasar Pemrograman",
    "prasyarat": {
      "tempuh": [],
      "lulus": [
        "AIF181101"
      ],
      "bersamaan": [],
      "berlakuAngkatan" : 2018
    },
    "sks": 4,
    "wajib": true,
    "semester": 2
  }
```

Pada prasyarat lulus, diberikan sebuah string berupa kode mata kuliah yang menjadi prasyarat lulus untuk mata kuliah tersebut.

#### Definisi Prasyarat
##### Tempuh
Mahasiswa diharuskan sudah pernah menempuh mata kuliah yang disebutkan.
##### Lulus
Mahasiswa diharuskan untuk lulus mata kuliah yang disebutkan.
##### Bersamaan
Mata kuliah tersebut harus di ambil secara bersamaan dengan mata kuliah yang disebutkan (butuh informasi lagi).
##### Berlaku Angkatan
Property ini mulai berlaku karena pergantian kurikulum. Prasyarat ini memiliki maksud bahwa matakuliah ini mulai berlaku semenjak angkatan x.
