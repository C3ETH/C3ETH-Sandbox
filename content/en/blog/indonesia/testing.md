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

### **Apa itu Crypto Wallet?**

Crypto Wallet adalah sebuah alat, tool, atau software wajib bagi para pengguna crypto untuk mengakses atau mentransaksikan aset crypto yang dimiliki.

### **Apakah Crypto Wallet menyimpan aset crypto?**

Crypto Wallet tidak menyimpan aset - aset crypto yang dimiliki oleh para pengguna. Crypto wallet bukanlah sebuah dompet yang menyimpan uang secara harafiah. 

### **Jika tidak disimpan di Crypto Wallet, dimana aset crypto kita disimpan?**

Aset crypto ***tercatat*** di dalam entry ***public address*** yang ada di blockchain. Setiap address menunjukkan aset apa saja yang dimiliki, total nilai, beserta historisnya.

Walaupun crypto wallet sedang error, dengan public address, pengguna tetap dapat mengecek aset crypto yang dimiliki melalui blockchain explorer.

### **Apa itu non-custodial VS custodial wallet?**

* Non-custodial (tidak dalam penguasaan oleh suatu pihak / non-kustodial) wallet adalah wallet dimana pengguna memiliki dan menjaga sendiri seed phrase / recovery phrase / mnemonic dari wallet tersebut. Untuk transaksi jual beli aset crypto hanya bisa dilakukan melalui DEX (Decentralized Exchange)

* Custodial (dalam penguasaan suatu pihak / kustodial) wallet adalah wallet yang seed phrase / recovery phrase / mnemonic dimiliki dan dipegang oleh suatu pihak, pada umumnya CEX (Centralized Exchange) seperti Binance, Coinbase, Kraken, dan sejenisnya. Biasa digunakan oleh para pengguna crypto awal atau pengguna yang lebih memilih kemudahan ketika transaksi jual beli aset crypto

* Di non-custodial wallet, pengguna harus menjaga baik - baik seed phrase / recovery phrase / mnemonic dari wallet-nya sendiri. Sedangkan di custodial wallet, jika terjadi apa - apa dengan pihak lain itu misalnya CEX, maka semua aset crypto yang dimiliki pengguna terancam tidak bisa diakses lagi atau hilang

### **Kenapa kita harus simpan seed phrase / recovery phrase / mnemonic baik - baik walaupun crypto wallet-nya juga sudah di-password dengan super panjang dan rumit?**

Public address lahir atau muncul dari ***proses enkripsi*** dengan private keys yang berasal dari seed phrase / recovery phrase / mnemonic sesuai dengan blockchain masing - masing.

Dengan seed phrase / recovery phrase / mnemonic, setiap pengguna dapat mengakses aset crypto yang dimiliki di wallet manapun (tentunya sesuai blockchain masing - masing).

***Sedangkan password yang diterapkan ke crypto wallet hanya mengenkripsi wallet secara lokal di browser/PC/laptop yang bersangkutan, namun tidak di browser/PC/laptop di tempat lain atau milik orang lain.***

***Jika seed phrase dicuri, walaupun pencuri tidak tahu password-nya, pencuri tetap dapat mengakses aset crypto dengan wallet lain, karena seed phrase → private keys → public address sehingga aset - aset crypto dapat ketahuan semuanya dan selanjutnya dicuri.***

### **Terus, bagaimana cara menyimpan seed phrase / recovery phrase / mnemonic yang paling aman?**

Metode paling aman untuk menyimpan seed phrase / recovery phrase / mnemonic adalah dengan menuliskannya di atas kertas yang terpisah, kemudian menyimpannya di tempat - tempat yang terpisah juga.

Tidak disarankan menyimpan di PC, laptop, atau handphone, terlebih lagi jika memakai nama file yang mudah ditebak. Resikonya adalah, jika PC/laptop/handphone terkena exploit/hack/virus, maka hacker dapat dengan mudah menemukan file tersebut.

### **Kalau tidak salah, pernah dengar tentang Ledger, Trezor. Katanya lebih aman ya kalau pakai itu?**

Ledger, Trezor, Keepkey, Bitbox, dan sejenisnya disebut sebagai **hardware wallet**, atau sering disebut juga **cold wallet**.

Sedangkan wallet - wallet yang dapat diakses dengan mudah melalui web browser, browser extension, mobile apps, atau dalam bentuk instalasi software desktop disebut sebagai **software wallet**, atau sering disebut juga **hot wallet**.

### **Mengapa disebut cold wallet dan hot wallet?**

Dengan cold wallet, terdapat extra layer security bagi pengguna ketika ingin mengakses public address yang ada di setiap blockchain (misal BTC, ETH, ADA, dll), dimana **dibutuhkan interaksi fisik dari pengguna** dalam meng-input password, memilih blockchain yang ingin digunakan, serta menekan tombol - tombol yang ada di cold wallet ketika melakukan transaksi.

***Perlu diingat! Cold wallet sendiri memiliki seed phrase / recovery phrase / mnemonic ketika proses konfigurasi pertama kali. Metode penyimpanan dari seed phrase / recovery phrase / mnemonic tentunya mengacu ke penjelasan sebelumnya di atas.***

Untuk hot wallet, pengguna dapat dengan mudah meng-input seed phrase / recovery phrase / mnemonic atau wallet password kapanpun dan dimanapun. Pengguna **dapat bertransaksi secara cepat** tanpa perlu repot - repot interaksi fisik dengan sebuah alat.

### **Bagaimana jika cold wallet hilang atau rusak?**

Di setiap cold wallet sudah memiliki prosedur keamanan tersendiri, semisal jika password 3x salah, maka otomatis akan factory reset. Kembali lagi, asalkan keamanan seed phrase / recovery phrase / mnemonic dari cold wallet dapat dijaga, pencuri pun tidak dapat mengaksesnya atau pengguna dapat membeli cold wallet baru lalu mengaksesnya dengan seed phrase yang dimiliki dari cold wallet sebelumnya.

### **Saya pribadi tetap lebih prefer pake hot wallet, tidak repot, tidak buang biaya ekstra juga. Ada saran untuk menjaga keamanannya?**

Beberapa saran keamanan:
* Selalu delete wallet begitu selesai digunakan (jika menggunakan wallet berupa browser extension). Contoh: Yoroi, Nami, CCVault, Typhon, GeroWallet dll. 
***Browser extension tidak akan hilang otomatis jika hanya clean browser’s histories, cookies, and caches ketika mau close browser***

* Selalu clean browser’s histories, cookies, and caches ketika mau close browser (jika menggunakan wallet berupa web browser). Contoh: AdaLite, dll

* Pastikan jaringan handphone tidak terhubung sembarangan ke public network seperti public WiFi di tempat - tempat umum (cafe, restoran, hotel, bandara, mall, dll). Usahakan tetap menggunakan paket data milik pribadi (jika menggunakan wallet berupa mobile apps). Contoh: Yoroi, dll

* Pastikan PC/laptop yang digunakan memiliki security yang selalu terupdate (jika menggunakan wallet berupa instalasi software desktop). Contoh: Exodus, Guarda,dll
Security dapat berupa windows defender atau antivirus yang selalu terupdate. Dapat juga menggunakan PC/laptop dengan sistem operasi di luar Windows seperti Linux dan MacOS.

### **Jika saya mau pindah ke wallet lain, apakah saya harus unstaking ADA dulu di wallet saat ini?**

Kembali ke penjelasan di atas, semua historis transaksi tercatat di blockchain termasuk staking. Dengan seed phrase / recovery phrase / mnemonic, setiap pengguna dapat mengakses aset crypto yang dimiliki di wallet manapun.

Password wallet sendiri dapat dibuat, diubah, atau diganti - ganti sesuka hati, karena keamanan yang terutama tetap di seed phrase / recovery phrase / mnemonic.

Blockchain dengan mekanisme konsensus Proof of Stake adalah blockchain yang menggunakan aset crypto yang *di-staking* atau *di-depositkan* untuk memutuskan siapa yang akan memvalidasi transaksi – transaksi dan menambahkannya ke dalam block berikutnya, untuk kemudian di-input ke chain. Di dalam blockchain Proof of Work seperti Bitcoin, hal ini disebut sebagai ***Block Mining***. 

Ketika aset crypto sedang di-staking dan digunakan dalam ***Block Mining***, aset tersebut memperoleh rewards karena telah membantu prosesnya. Mirip seperti deposit uang ke rekening deposito bank dan memperoleh bunga dari situ. 

Apa kelebihan PoS dibanding metode konsensus lainnya seperti PoW?
* Cara mudah memperoleh rewards/interest dari aset crypto.
* Tidak perlu membeli perangkat atau pengetahuan spesifik untuk block mining di BTC
* Membantu menjaga keamanan dan efisiensi dari blockchain yang bersangkutan (dalam hal ini Cardano)
* Lebih ramah lingkungan daripada block mining di BTC

Sekilas tentang cara kerja PoW untuk perbandingan:

* Jaringan blockchain membutuhkan processing power yang sangat besar dimana masing - masing miner di seluruh dunia bersaing menyelesaikan mathematical problem untuk menemukan random code yang disebut *nonce*. 

* Oleh karena itu, muncul istilah jika banyak miner yang sedang online, difficulty problem makin susah. Jika banyak miner yang sedang offline, difficulty problem lebih mudah.

 * Pemenangnya kemudian berhak menambahkan block yang sudah berisi transaksi - transaksi tervalidasi ke dalam blockchain, lalu menerima crypto sebagai rewards-nya.
