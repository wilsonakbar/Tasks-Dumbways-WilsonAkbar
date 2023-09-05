# Manage Server in Terminal
## 1. Penjelasan text manipulation beserta step by step
Melakukan manipulasi pada sebuah file menggunakan terminal, tanpa menggunakan teks editor seperti nano.
### 1.1 cat
Cat adalah salah satu perintah yang berfungsi untuk membuat daftar konten atau isi file pada standard output (sdout). Yang kalian tahu pasti perintah cat hanya bisa untuk melihat isi dari suatu file, sebenarnya tidak hanya itu.
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/eccdfa22-2155-44e9-abc3-ff3fdbbf795a)
```
cat > filewilson
```
lalu ketik kata atau kalimat yang kalian inginkan
```
cat filewilson
```
membuat file kedua lalu gabungkan kedua file tersebut beserta isi nya
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/223e2e45-282f-4045-8a76-bae9999586b9)
```
cat > fileakbar
```
lalu ketik kata atau kalimat yang kalian inginkan
```
cat filewilson fileakbar > filewilsonakbar
```
```
cat filewilsonakbar
```
### 2.1 sed
Sed adalah singkatan dari stream editor. Gunanya untuk memanipulasi teks dasar pada file. Dengan sed kita dapat mengganti teks dengan cepat
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b613774f-41da-4b57-a94d-c6d175086b8b)
```
sed -i 's/hallo/hai/g' file3
```
### 3.1 grep
Grep merupakan perintah untuk melakukan pencarian sebuah text dalam sebuah file yang telah dibuat.
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a0c1fe90-836c-4539-9e66-f9f79291d6a0)

```
grep wilson filewilsonakbar
```
berfungsi mencari teks dalam file tertentu
```
grep -c wilson filewilsonakbar
```
berfungsi menghitung jumlah teks yang ada dalam file
```
grep wilson *
```
berfungsi mencari teks dalam semua file
### 4.1 sort
Sort untuk mengurutkan data, baik itu secara ascending atau descending.
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/11323d41-c7dc-46ae-954e-82139d0ddb0e)
```
cat > filehitung
```
membuat file yang berisi text acak
```
sort filehitung
```
mengurutkan text dari yang terkecil sampai terbesar
```
sort -r filehitung
```
mengurutkan text dari yang terbesar sampai terkecil
### 5.1 echo
Echo digunakan untuk mencetak string / pesan dari hasil perintah lain.
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f493a593-9e40-45df-ac54-4eb3403bbb53)
```
echo "wilson akbar"
```
berfungsi untuk mencetak kata
```
echo "wilson akbar" >> wilsonakbarfile
```
berfungsi untuk mencetak data wilson akbar pada file wilsonakbarfile
```
echo "hallo wilson" > wilsonakbarfile
```
berfungsi untuk mereplace semua data file wilsonakbarfile dengan hallo wilson
## 2. Penjelasan tool htop atau nmon
### 2.1 htop
htop merupakan perintah untuk memonitoring sistem, kita dapat melihat penggunaan memory, cpu, swap
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3bb07d27-ad00-4a91-aba5-396ff1666876)
```
sudo apt install htop -y
```
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/631d00f1-9af6-486d-98f6-ecad22f5e7cb)
```
htop
```
## 3. buatlah BASH Script untuk instalasi nginx
### 3.1 pertama buat file script.sh
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1709b894-bfbb-41e8-b915-1d8abbc1b3e6)
```
nano script.sh
```
### 3.2 kemudian buat perintah seperti berikut
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/72ab58b3-ab6a-4b2f-8e86-8c93098f651a)
```
#!/usr/bin/env bash

sudo apt install nginx
```
### 3.3 jalankan Script dengan perintah
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e47629ca-2371-46bf-ab3e-e505b620d1c6)
```
sh script.sh
```
kemudian buka nginx dengan ip masing-masing
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6b314645-1dff-459f-a553-75cbb29f9bef)
```
http://192.168.245.100/
```
