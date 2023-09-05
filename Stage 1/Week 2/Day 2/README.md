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
```
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
## 2. Penjelasan tool htop atau nmon
## 3. buatlah BASH Script untuk instalasi nginx

