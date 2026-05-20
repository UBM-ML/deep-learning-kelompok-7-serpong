# Experiment Log

Catat setiap percobaan hyperparameter di sini. **Minimal 5 eksperimen.**

> Tips: ubah **satu hyperparameter pada satu waktu** agar bisa mengisolasi efeknya. Setelah memahami efek tiap variabel, baru gabungkan untuk hasil terbaik.

---

## 📋 Tabel Ringkasan

Isi tabel ini setelah selesai semua eksperimen.

| # | Hidden | Neurons | Activation | Optimizer | LR     | Batch | Epochs | Dropout | Test Acc | Train Time |
|---|--------|---------|------------|-----------|--------|-------|--------|---------|----------|------------|
| 0 | 1      | 64      | relu       | sgd       | 0.01   | 32    | 10     | 0.0     | ~85%     | ~30s       |
| 1 | 5      | 512     | tanh       | adam      | 1.0    | 512   | 50     | 0.5     | ~10%     | ~683.5s    |
| 2 | 2      | 512     | relu       | adam      | 0.001  | 128   | 30     | 0.2     | ~88.95%  | ~208.9s    | 
| 3 | 2      | 256     | relu       | adam      | 0.001  | 64    | 50     | 0.3     | ~89.47%  | ~134.7s    |
| 4 |        |         |            |           |        |       |        |         |          |            |
| 5 |        |         |            |           |        |       |        |         |          |            |

> **Eksperimen #0** = baseline (jangan ubah, ini patokan kalian).

---

## 🧪 Detail Setiap Eksperimen

Gunakan template di bawah untuk SETIAP eksperimen.

---

### Eksperimen #1

**Apa yang diubah dari baseline:**
> - Menggunakan hidden layer sebanyak 5 layer  
> - Menggunakan 512 neuron pada setiap layer  
> - Menggunakan activation function `tanh`
> - Menggunakan optimizer `adam`
> - Menggunakan learning rate sebesar 1.0 
> - Menggunakan batch sebesar 512
> - Menggunakan epoch sebesar 50
> - Menggunakan dropout sebesar 0.5  


**Hipotesis sebelum run:**
> - Penggunaan hidden layer dan neuron dalam jumlah besar diharapkan mampu meningkatkan kemampuan model dalam mengenali pola data yang kompleks. Optimizer Adam diperkirakan dapat mempercepat proses konvergensi, sedangkan learning rate yang tinggi diharapkan mempercepat proses pembelajaran model. Penggunaan dropout bertujuan mengurangi overfitting, dan jumlah epoch yang besar diharapkan memberikan model kesempatan belajar lebih optimal sehingga akurasi model meningkat.
**Hasil:**
- Test accuracy: 10.00%
- Train accuracy: 10.11%
- Validation accuracy: 10.32%
- Train time: 683.5 detik
- underfit

**Observasi & Insight:**
> Model gagal mempelajari pola dataset dengan baik. Hal ini terlihat dari akurasi yang sangat rendah dan confusion matrix yang hanya memprediksi satu kelas. Penyebab utama diduga karena learning rate terlalu besar sehingga proses update bobot menjadi tidak stabil. Selain itu, penggunaan hidden layer dan neuron yang terlalu besar membuat model semakin sulit dilatih secara optimal.

**Rencana eksperimen berikutnya:**
> Menurunkan learning rate agar proses update bobot lebih stabil, mengurangi jumlah hidden layer untuk menyederhanakan arsitektur model, mengganti activation function menjadi `relu` agar proses pembelajaran lebih efektif, menurunkan batch size dan epoch supaya update bobot lebih responsif, serta mengurangi dropout agar model tidak kehilangan terlalu banyak informasi saat training.
---

### Eksperimen #2

**Apa yang diubah:**
> Kami melakukan penyesuaian pada beberapa hyperparameter utama dari model baseline. Jumlah hidden layer ditambah dari 1 menjadi 2, sedangkan jumlah neuron ditingkatkan dari 64 menjadi 512. Optimizer juga diganti dari sgd menjadi adam, dengan learning rate yang diturunkan dari 0,01 menjadi 0,001 agar proses pembelajaran lebih stabil. Selain itu, batch size dinaikkan dari 32 menjadi 128, jumlah epoch ditingkatkan dari 10 menjadi 30, dan dropout sebesar 0,2 ditambahkan untuk mengurangi risiko overfitting. Fungsi aktivasi tetap menggunakan relu.

**Hipotesis:**
> Kami memperkirakan bahwa kombinasi hyperparameter tersebut mampu meningkatkan akurasi model karena penambahan hidden layer dan jumlah neuron memberikan kapasitas belajar yang lebih besar. Optimizer Adam digunakan karena memiliki proses pembaruan bobot yang lebih adaptif dan stabil dibandingkan SGD. Learning rate sebesar 0,001 dipilih agar perubahan bobot berlangsung lebih terkontrol. Selain itu, dropout 0,2 diterapkan untuk menekan risiko overfitting yang dapat muncul akibat peningkatan kompleksitas model.

**Hasil:**
- Test accuracy: 88.95%
- Train accuracy: 93.30%
- Validation accuracy: 89.58%
- Train time: 208.9 detik
- Apakah overfit/underfit? Tidak ditemukan indikasi overfitting yang terlalu besar karena perbedaan antara train accuracy dan validation accuracy terlihat hanya sekitar 3,72%, sehingga performa model dapat dikategorikan masih tergolong stabil dan mampu melakukan generalisasi dengan cukup baik.

**Observasi:**
> Hasil eksperimen memperlihatkan bahwa penyesuaian hyperparameter berhasil meningkatkan performa pada model, dari baseline ~85% menjadi 88,95% pada data test. Grafik training menunjukkan bahwa model mampu mempelajari pola data dengan cukup baik, terlihat dari peningkatan accuracy dan penurunan loss. Namun, nilai train accuracy yang lebih tinggi dibandingkan validation accuracy mengindikasikan bahwa model mulai terlalu menyesuaikan diri terhadap data training. Penggunaan dropout sebesar 0,2 diterapkan untuk membantu mengurangi jarak performa antara data training dan validation agar tidak terlalu besar.

**Rencana eksperimen berikutnya:**
> Berdasarkan observasi, model sudah berada di jalur yang benar (akurasi melesat ke 88.95%), namun tanda-tanda overfitting mulai terlihat. Pada Eksperimen #3, kami akan mengisolasi variabel Dropout Rate dengan menaikkannya dari 0.2 menjadi 0.3 untuk menekan overfitting dan merapatkan jarak antara akurasi training dan validasi, sementara hyperparameter lainnya dibuat persis sama dengan Eksperimen #2.
---

### Eksperimen #3

**Apa yang diubah:**
- Menurunkan jumlah neuron per layer dari 512 menjadi 256.
- Memperkecil batch size dari 128 menjadi 64.
- Meningkatkan jumlah epoch dari 30 menjadi 50.
- Menaikkan sedikit dropout rate dari 0.2 menjadi 0.3.
- (Fungsi aktivasi relu, optimizer adam, dan learning rate 0.001 tetap dipertahankan).

**Hipotesis:**
> Dengan memotong jumlah neuron menjadi 256, kita menyederhanakan model agar tidak terlalu "gemuk" dan rawan overfit. Batch size yang lebih kecil (64) akan membuat transisi perbaikan bobot (weight updates) menjadi lebih sering dan dinamis di setiap epoch. Ditambah dengan kompensasi 50 epoch dan peningkatan dropout ke 0.3, model diharapkan punya waktu belajar yang lebih stabil dan menghasilkan akurasi yang lebih tinggi daripada Eksperimen #2

**Hasil:**
- Test accuracy: 89.47%
- Train accuracy: 92.29%
- Validation accuracy: 89.40%
- Train time: 134.7 detik
- Apakah overfit/underfit? Good Fit / Well-balanced. Jarak antara train accuracy (92.29%) dan validation accuracy (89.40%) menyusut menjadi hanya 2.89%. Ini adalah indikator bahwa model melakukan generalisasi dengan sangat sehat.
  
**Observasi:**
- Performa Terbaik: Eksperimen ini berhasil memecahkan rekor akurasi tertinggi sejauh ini (89.47%). Pengurangan neuron dan pengecilan batch size terbukti membuat model lebih lincah dan adaptif.
- Analisis Terperinci (Berdasarkan Gambar Confusion Matrix): Model sudah sangat master dalam mengenali barang-barang non-baju atas seperti Bag (975 benar), Trouser (971 benar), Sandal (970 benar), dan Sneaker (967 benar).
  - Masalah krusialnya ada pada area pakaian atas (upper-wear clusters). Kelas Shirt adalah titik terlemah (hanya 672 yang benar) karena sering sekali salah ditebak sebagai T-shirt/top (114 kali), Pullover (84 kali), dan Coat (77 kali). Kemiripan potongan lengan dan kerah pada resolusi gambar yang rendah membuat model kesulitan membedakannya secara detail.
---

### Eksperimen #4

**Apa yang diubah:**

**Hipotesis:**

**Hasil:**

**Observasi:**

---

### Eksperimen #5

**Apa yang diubah:**

**Hipotesis:**

**Hasil:**

**Observasi:**

---

## 🏆 Konfigurasi Terbaik

Setelah semua eksperimen, salin konfigurasi terbaik kalian ke sini:

```python
HIDDEN_LAYERS     = ?
NEURONS_PER_LAYER = ?
ACTIVATION        = ?
DROPOUT_RATE      = ?
OPTIMIZER         = ?
LEARNING_RATE     = ?
BATCH_SIZE        = ?
EPOCHS            = ?
```

**Test accuracy final: ___%**
