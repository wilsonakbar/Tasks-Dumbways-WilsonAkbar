# Web Server & Reverse Proxy
## 1. Buat 1 VM tambahan untuk nginx saja (Ini opsional ya, tidak wajib)
Melakukan manipulasi pada sebuah file menggunakan terminal, tanpa menggunakan teks editor seperti nano.
### 1.1 membuat 1 VM ubuntu seperti minggu pertama (ssh baru "akbar")
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/31f1ef53-943f-4712-8e00-6841bda4b81b)
### 1.2 melakukan update dan upgrade, kalian bisa menggunakan perintah di bawah ini.
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f684bbdd-8c71-41f2-947a-71793c7528d9)
```
sudo apt update; sudo apt upgrade
```
### 1.3 Selanjutnya kita akan coba untuk menginstall aplikasi Nginx.
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3c21ef6d-0301-40d3-adf0-4b2eeb29c1b6)
```
sudo apt install nginx
```
### 1.4 cek dengan menggunakan perintah dibawah ini
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e3e23555-4c96-4937-a0c5-756137dd6974)
```
sudo systemctl status nginx
```
### 1.5 coba buka browser kalian, lalu masukkan IP dari server kalian
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e192cf36-649e-40ad-8c02-693851e3e886)
```
192.168.245.99
```
## 2. Jalankan aplikasi Dumbflix menggunakan PM2
### 2.1 install PM2 dengan perintah sebagai berikut
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/0deaf10d-5222-4089-a7b9-35cab9f09b81)
```
npm install pm2 -g
```
### 2.2 masuk pada direktori src pada Dumbflix lalu jalankan PM2
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/da1ca7b2-4f6d-401b-ab43-dcf16590eac3)
```
cd src/
```
```
pm2 start index.js
```
## 3. Buatlah reverse proxy dengan directory /etc/nginx/dumbways
## 4. Dengan nginx, pastikan dumbflix bisa diakses ke domain yang diinginkan
