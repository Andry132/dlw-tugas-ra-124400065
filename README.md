# Studi Ablasi RNN, LSTM, GRU vs ANN untuk Prediksi Trafik Seluler Milan

Tugas Workshop Deep Learning — Teknik Telekomunikasi ITERA.

## Kelompok

| Peran | Nama | NIM |
|---|---|---|
| Ketua | Andryansyah Amir | 124400065 |

- **Kelas:** [RA]
- **Lokasi kelompok:** [5] — [Bandara Linate] (digit terakhir NIM terkecil)
- **Laporan:** [`laporan-latex/main.pdf`]

## Cara Menjalankan

```bash
uv sync
uv run jupyter lab
```

Buka `tugas_ablasi.ipynb`, isi `LOKASI_KELOMPOK`, lalu jalankan semua sel. Semua run tercatat di `hasil/ablasi.csv`.

Perangkat yang kami pakai: [laptop CPU AMD Ryzen5 5600H dan laptop CPU Intel i5], total waktu training: [71.3] menit.

## Ringkasan Hasil

Model rekuren lebih akurat dan lebih tahan terhadap perubahan hyperparameter dibanding ANN: saat jendela W diperpanjang dari 6 ke 168 jam, val MAE ANN memburuk dari 211,5 menjadi 298,2 dengan parameter naik dari 2.465 menjadi 38.753, sedangkan RNN dan GRU nyaris tidak berubah. Pada konfigurasi terbaik hasil val MAE, test MAE di Duomo adalah ANN 290,5 ± 23,9, RNN 233,9 ± 16,4, LSTM 263,3 ± 19,2, dan GRU 228,8 ± 10,6, jauh lebih baik dari baseline naif terbaik (467,6); hanya ANN, LSTM, dan GRU yang membaik terhadap acuan, dan selisih RNN dengan GRU tidak melebihi simpangan baku. Di Bandara Linate, konfigurasi terbaik Duomo tidak memberi perbaikan berarti (test MAE 7,6–8,3 vs 7,5–8,8 pada acuan), dan pada minggu Natal baseline “nilai terakhir” mengalahkan seluruh model di Linate (7,1 vs 10,8–12,8) serta ANN, LSTM, dan GRU di Duomo (431,2).

## Struktur

```
tugas_ablasi.ipynb      notebook eksperimen (di-commit beserta output)
data/                   data trafik per jam (Duomo + 10 lokasi tugas)
hasil/                  CSV seluruh run, tabel, dan grafik
laporan-latex/ atau laporan-typst/   sumber laporan + PDF
```

## Data

Telecom Italia Big Data Challenge (Barlacchi dkk., 2015, *Scientific Data*, lisensi ODbL), versi per jam dari Zhang dkk. (INFOCOM 2021). Disiapkan oleh pengajar di repo [mctosima/dl-workshop](https://github.com/mctosima/dl-workshop).