---
title: "Cara Ikut Serta di Project Catalyst"
linkTitle: "Cara Ikut Serta di Project Catalyst"
hide_feedback: true
weight: 4
description: "Bagaimana cara menjadi Proposer, Voter, atau Community Advisor?" 
---

### **1. Pengantar**
* ADA tidak dikunci dan tetap dapat ditransaksikan kapan saja.
* ADA tetap berada di dompet dan tidak akan hilang selama staking.
* Tidak ada resiko slashing (holding ADA terkena pemotongan (slashed) oleh protokol sebagai hukuman karena tindakan merugikan yang dilakukan oleh SPO).
* Rewards staking otomatis ditambahkan ke akun staking (compounded).
* Biaya tetap (fixed cost) sebesar 340 ADA sesuai yang ditentukan oleh protokol dan margin (biaya di luar fixed cost yang diatur oleh SPO sendiri) diambil terlebih dahulu dari total rewards epoch untuk SPO. Selanjutnya, rewards didistribusikan ke semua delegator di SPO tersebut.

### **2. Informasi Epoch & Rewards**
* Durasi sebuah Epoch adalah 5 hari.
* Jadwal penghitungan Rewards (dengan contoh):

a. **Epoch 1 (sedang berjalan)** → Mulai staking di SPO

Biaya - biaya yang dikenakan saat pertama kali staking:
* Biaya jaringan: ± 0.17 ADA
* Biaya deposit Staking Key (Refundable): 2 ADA

b. **Epoch 2 (Hari 1-5)** → Proses stake snapshot, teregistrasi ke SPO.

c. **Epoch 3 (Hari 6-10)** → Proses pemilihan slot leaders dan block production. 

Stake ADA sudah aktif dan berkontribusi di SPO.

d. **Epoch 4 (Hari 11-15)** → Proses penghitungan rewards dari Epoch sebelumnya berdasarkan block production.

e. **Epoch 5 (Hari 16-20)** → Menerima rewards pertama dari Epoch 3.

f. **Epoch 6 (Hari 21-25)** → Menerima rewards dari Epoch 4.

g. **Epoch 7 (Hari 26-30)** → Menerima rewards dari Epoch 5. 

Rewards akan terus diterima di setiap Epoch selama SPO terus memproduksi block di 2 Epoch sebelumnya.

### **3. Mengubah Jumlah Staking (menambah/mengurangi)**
> *melanjutkan contoh di atas*

a. **Epoch 7 (sedang berjalan)**

Awal staking 100 ADA, kemudian menambahkan 50 ADA, menjadi 150 ADA.

b. **Epoch 8** → Masih terima rewards dari staking 100 ADA (Epoch 6)

Proses stake snapshot yang terbaru 150 ADA

c. **Epoch 9** → Masih terima rewards dari staking 100 ADA (Epoch 7)

Proses pemilihan slot leaders dan block production, stake ADA terbaru 150 ADA sudah aktif.

d. **Epoch 10** → Masih terima rewards dari staking 100 ADA (Epoch 8)

Proses penghitungan rewards dari Epoch sebelumnya berdasarkan block production.

e. **Epoch 11** → Sudah terima rewards dari staking 150 ADA (Epoch 9)

### **4. Mengubah SPO**
> *melanjutkan contoh di atas*

a. **Epoch 7 (sedang berjalan)**

Awal staking ke SPO ABC, kemudian pindah ke SPO XYZ.

b. **Epoch 8** → Masih terima rewards dari SPO ABC (Epoch 6)

Proses stake snapshot yang terbaru di SPO XYZ.

c. **Epoch 9** → Masih terima rewards dari SPO ABC (Epoch 7)

Proses pemilihan slot leaders dan block production, stake ADA sudah aktif di SPO XYZ.

d. **Epoch 10** → Masih terima rewards dari SPO ABC (Epoch 8)

Proses penghitungan rewards dari Epoch sebelumnya berdasarkan block production.

e. **Epoch 11** → Sudah terima rewards dari SPO XYZ (Epoch 9)

### **5. Withdraw Rewards & Stop Staking**

Ada 2 opsi yang dapat dilakukan ketika withdraw rewards:
* **Hanya Withdraw Rewards**

Akun staking tetap berhak mendapatkan rewards di Epoch berikutnya.
Rewards balance dipindah ke staking balance.

* **Stop Staking**

Deposit 2 ADA dikembalikan, akun staking ditarik registrasinya dan tidak berhak mendapatkan rewards lagi, termasuk dari Epoch terakhir ketika stop staking.
Rewards balance dan staking balance dipindah seluruhnya ke available balance.

### **6. Diagram Staking**

![Delegation Cycle](https://aws1.discourse-cdn.com/business4/uploads/cardano/original/3X/6/2/6291c37441ab5cbaca7c188f81e00481e1cf1f36.jpeg)

### **Parameter - Parameter** 

### **1. Throughput (volume transfer data)** 
Ukuran block: 64 KB.

Ukuran untuk single Plutus script transaction di-limit di 16 KB.

Ukuran simple transaction biasanya hanya 200-300 Bytes.

Minimal sebuah block dapat menampung 4 jenis transaksi, single Plutus script transaction (smart contract); native tokens; metadata; dan simple transaction seperti payment. Namun, ukuran block dapat diperbesar untuk meningkatkan throughput.

### **2. Mempool**
Ukuran Mempool: 128 KB (2x ukuran block).

Semua transaksi yang terjadi ditampung terlebih dahulu secara temporary di mempool sampai mereka siap diproses dan di-input ke dalam block. 

Transaksi – transaksi yang pending akan dihapus dari mempool begitu block baru sudah terbentuk. Setelah itu, transaksi – transaksi yang baru bisa ditambahkan lagi ke dalam mempool.

Dengan ukuran mempool yang dibuat tetap seperti ini memungkinan node – node tidak overload ketika periode high demand. Walaupun itu berarti setiap transaksi yang dilakukan dari wallet maupun Dapps harus di-submit kembali.

Hal ini bukan berarti jaringan sedang bersusah payah (struggling), melainkan lebih tepatnya jaringan beroperasi seperti yang sudah direncanakan sebelumnya (graceful degradation).

### **3. Block Time Budget**
Waktu yang tersedia untuk memproses semua transaksi ke dalam sebuah block. Waktu ini dibagi untuk memproses Plutus script dan transaksi – transaksi lainnya. 

Block Time Budget di-set sebesar 1 detik.

Untuk Plutus script sendiri diberikan jatah waktu sebesar 50 millisecond.

### **4. Timeliness (waktu adopsi block)**
Jaringan harus dapat mendistribusikan (mempropagasi) transaksi dan block yang telah diproduksi ke setiap node yang tersebar di seluruh dunia, agar tercipta konsensus sehingga terverifikasi dan tervalidasi untuk di-input ke dalam blockchain. 

Hal ini disebut sebagai data diffusion.

Data diffusion time di-set sebesar 5 detik karena standard dari protokol Ouroboros untuk menjamin keamanan jaringan.

### **5. Plutus Script Memory Units**
Faktor penting bagi para developer DApps agar dapat merancang Plutus scripts yang sophisticated sehingga mampu memproses banyak input data, meningkatkan concurrency, atau memperluas kapabilitas aplikasinya.

Semakin besar ukuran memory units, semakin besar ukuran transaksi (Bytes), semakin besar pula sumber daya yang dibutuhkan untuk memverifikasi dan memvalidasi transaksinya sehingga biaya transaksi juga menjadi semakin besar.

### **Throughput VS Timeliness**

Selanjutnya, dari kelima faktor di atas, perlu diketahui bahwa Throughput dan Timeliness adalah 2 faktor yang saling tarik menarik. Berikut penjelasannya:
* Throughput ditingkatkan, ukuran block diperbesar agar block mampu menampung banyak transaksi.
* Banyak transaksi yang tertampung seolah – olah jaringan bekerja dengan cepat (network performance bagus).
* Namun, hal ini menjadi bumerang ketika jaringan sangat sibuk (saturated) yang menyebabkan timeliness delay, yaitu ukuran block yang besar – besar sehingga waktu propagasi menjadi lebih lama. Proses verifikasi dan validasi ke dalam blockchain pun menjadi terlambat sehingga terbuka celah keamanan disitu.
* Data diffusion time sebesar 5 detik menjadi sebuah batasan yang harus diperhatikan ketika akan meningkatkan ukuran block. 
* Oleh karena itu, untuk meningkatkan throughput, dapat dilakukan dengan efisiensi parameter jaringan lainnya agar ada ruang yang cukup untuk meningkatkan ukuran block sehingga data diffusion time dapat tetap terjaga.

### **Perubahan Parameter Jaringan (akan selalu di-update)**
> *Perubahan yang telah dilakukan sejak awal tahun 2022*

#### **Epoch 306**
* Ukuran block, dari 64 KB -> 72 KB
* Ukuran Plutus script memory units per transaksi, dari 10.000.000 -> 11.250.000

#### **Epoch 317**
* Ukuran Plutus script memory units per transaksi, dari 11.250.000 -> 12.500.000

#### **Epoch 319**
* Ukuran block, dari 72 KB -> 80 KB
* Ukuran Plutus script memory units per transaksi, dari 12.500.000 -> 14.000.000

#### **Epoch 321**
* Ukuran Plutus script memory unit per block, dari 50.000.000 -> 56.000.000, yang berarti secara optimal dapat menampung memory 4 Plutus script transaction yang berukuran 14.000.000

#### **Epoch 328**
* Ukuran Plutus script memory units per block, dari 56.000.000 → 62.000.000, yang berarti secara optimal dapat menampung memory 4 Plutus script transaction yang berukuran 14.000.000 dan transaksi Plutus script lainnya sampai maksimal 62.000.000.

#### **Epoch 333**
* Ukuran block, dari 80 KB → 88 KB
