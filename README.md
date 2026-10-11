# Tugas Mandiri 1 Information Retrieval: Cosine TF-IDF vs BM25

Perbandingan dua model perangkingan, **Cosine TF-IDF (skema ltc.ltc)** dan **BM25 (k1 = 1,2; b = 0,75)**, pada korpus 50 artikel berita berbahasa Indonesia (Antara News). Keduanya diimplementasikan sendiri tanpa library IR.

Mata kuliah Information Retrieval, Prodi Informatika UPN "Veteran" Jawa Timur.

## Isi repository
- `Tugas_Mandiri_1_IR_tfidf_vs_bm25.ipynb`: notebook lengkap (praproses, kedua model, evaluasi, uji k1 dan b, analisis)
- `berita_indonesia_50.csv`: korpus uji
- `hasil_ranking_tfidf_vs_bm25.csv`: peringkat dan skor kedua model untuk 14 query
- `hasil_evaluasi_baseline.csv`: AP, R-Precision, dan Kendall tau per query
- `hasil_grid_k1_b.csv`: hasil uji 20 kombinasi k1 dan b
- `fig_*.png`: grafik panjang dokumen, grid parameter, dan bentuk fungsi saturasi

## Cara menjalankan
1. Buka notebook di Google Colab.
2. Unggah `berita_indonesia_50.csv` saat diminta (atau letakkan di folder kerja).
3. Jalankan seluruh sel dari atas ke bawah (Runtime > Run all).

## Metode singkat
- Praproses: case folding, tokenisasi, stopword (Sastrawi + NLTK + stopword berita), stemming Sastrawi.
- Cosine TF-IDF: w = (1 + log10 tf) x log10(N/df), dinormalisasi cosine, dengan pencarian term-at-a-time.
- BM25: idf = ln(1 + (N - df + 0,5)/(df + 0,5)); skor = idf x tf(k1+1)/(tf+K); K = k1(1 - b + b x dl/avgdl).
- Evaluasi: 14 query dengan penilaian relevansi manual; metrik AP, R-Precision, dan Kendall tau.
- Validasi: kedua implementasi cocok dengan latihan di slide Pertemuan 4 dan 5.

## Ringkasan hasil baseline
| Model | MAP | R-Precision |
|---|---|---|
| Cosine TF-IDF (ltc.ltc) | 0,9355 | 0,8845 |
| BM25 (k1 = 1,2; b = 0,75) | 0,9948 | 0,9857 |

Top-5 kedua model berbeda pada 13 dari 14 query. Rincian dan analisisnya ada di laporan.
