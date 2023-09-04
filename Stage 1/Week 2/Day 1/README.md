# Introduction to DevOps
## 1. Penjelasan Distributed Version Control
  Sistem kontrol versi terdistribusi (DVCS) membawa salinan lokal dari repositori lengkap ke komputer setiap anggota tim, sehingga mereka dapat melakukan, mencabangkan, dan menggabungkan secara lokal. Server tidak harus menyimpan file fisik untuk setiap cabang — server hanya memerlukan perbedaan antara setiap penerapan.
  
## 2. buat repository dengan nama makanan kesukaan kalian (diluar tugas) yang berisi 3 file dengan isi yang berbeda
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ca97d244-c448-4bbd-9c30-1d4c69c75bd5)
disini saya membuat repository dengan nama ayamgoreng dengan masing-masing file ayamgorenggeprek, ayamgorengkecap, dan ayamgorengrica

## 3. Buat 2 branch Staging dan Production
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/7434e96c-8fc7-451c-bd22-f2d792c6cc43)
disini saya membuat branch sesuai dengan tugas dengan nama Staging dan Production

## 4. Cari 3 command git yang belum dijelaskan dan praktekkan
### 4.1 cara penggunaan git clone
berfungsi untuk mengclone file repositori online agar kita dapat memodifikasi secara offline
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e5fb5565-e272-4432-a21d-64534c5fd46c)
```
git clone git@github.com:wilsonakbar/ayamgoreng.git
```
### 4.2 cara penggunaan git restore
berfungsi untuk mengembalikan file yang add / tambahkan dari server lokal ke github
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/cdc88bba-1119-40c5-9ce7-3c9b33cced3d)
```
git restore --stage ayamgorengbaru
```
### 4.3 cara penggunaan git pull
berfungsi untuk menyamakan version file repositori dari database online ke database lokal
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c525ca1e-45f7-4d5d-9394-33e15a066744)
```
git pull git@github.com:wilsonakbar/ayamgoreng.git
```
