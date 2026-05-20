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
| 2 | 2      | 512     | relu       | adam      | 0.001  | 128   | 30     | 0.2     | 88.95%   | 208.9s     | 
| 3 |        |         |            |           |        |       |        |         |          |            |
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

---

### Eksperimen #3

**Apa yang diubah:**

**Hipotesis:**

**Hasil:**

**Observasi:**

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
