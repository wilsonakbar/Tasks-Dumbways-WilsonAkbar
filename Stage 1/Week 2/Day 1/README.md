# Introduction to DevOps
## 1. Penjelasan Distributed Version Control
  Sistem kontrol versi terdistribusi (DVCS) membawa salinan lokal dari repositori lengkap ke komputer setiap anggota tim, sehingga mereka dapat melakukan, mencabangkan, dan menggabungkan secara lokal. Server tidak harus menyimpan file fisik untuk setiap cabang — server hanya memerlukan perbedaan antara setiap penerapan.
  
## 2. buat repository dengan nama makanan kesukaan kalian (diluar tugas) yang berisi 3 file dengan isi yang berbeda
### 2.1 membuat repositori di github dengan nama ayamgoreng
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2f865670-5006-47c2-91ee-44fadfdf9ef8)
### 2.2 membuat direktori ayamgoreng kemudian buat file didalam direktori ayamgoreng lalu pastikan file yang telah di buat
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/61584389-2068-4801-82f9-5a9015e6fa53)
```
git init ayamgoreng
```
```
cd ayamgoreng
```
```
touch ayamgeprek ayamrica ayamkecap
```
```
git status
```
### 2.3 tambahkan 3 file yang tadi kita buat ke github
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/cdaac5f4-27df-45ea-bda9-9f1818c4c256)
```
git add ayamgeprek ayamrica ayamkecap
```
```
git status
```
```
git commit -m "first commit"
```
```
git remote add origin git@github.com:wilsonakbar/ayamgoreng.git
```
### 2.4 buat branch lalu upload file yang sudah di tambah ke github
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a8273b4b-bc7a-4025-a9f4-30643397d8b6)
```
git branch -m main
```
```
git push origin main
```

## 3. Buat 2 branch Staging dan Production
disini saya membuat branch sesuai dengan tugas dengan nama Staging dan Production
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b90e355d-dd93-4864-a8ce-618bf2592e29)
```
git branch Staging
```
```
git branch Production
```
```
git branch -a
```

## 4. Cari 3 command git yang belum dijelaskan dan praktekkan
### 4.1 git clone
berfungsi untuk mengclone file repositori online agar kita dapat memodifikasi secara offline
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e5fb5565-e272-4432-a21d-64534c5fd46c)
```
git clone git@github.com:wilsonakbar/ayamgoreng.git
```
### 4.2 git restore
berfungsi untuk mengembalikan file yang add / tambahkan dari server lokal ke github
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/cdc88bba-1119-40c5-9ce7-3c9b33cced3d)
```
git restore --stage ayamgorengbaru
```
### 4.3 git pull
berfungsi untuk menyamakan version file repositori dari database online ke database lokal
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c525ca1e-45f7-4d5d-9394-33e15a066744)
```
git pull git@github.com:wilsonakbar/ayamgoreng.git
```
