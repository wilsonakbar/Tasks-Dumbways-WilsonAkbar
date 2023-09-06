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
### 3.1
Pertama-tama masuk ke folder nginx setelah itu buat suatu directory baru telebih dahulu
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/70f4ef35-dba7-4777-ab01-f6715096dd75)
```
cd /etc/nginx
```
```
sudo mkdir dumbways
```
### 3.2
Selanjutnya keluar dari directory dumbways, setelah itu masuk ke dalam file nginx.conf
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d699ef23-1f01-481e-ae1e-3eccc8a2e7a4)
```
sudo nano nginx.conf
```
### 3.1
Selanjutnya pergi ke-bagian include, setelah itu masukan lokasi dari directory yang bersi konfigutasi yang sudah kalian buat tadi
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/02d2afba-52ac-44b7-8b43-f1f01807e27f)
```
include /etc/nginx/dumbways/*;
```
## 4. Dengan nginx, pastikan dumbflix bisa diakses ke domain yang diinginkan
### 4.1 Setelah itu masuk ke directory yang sudah kalian buat, setelah itu buat suatu file dengan nama dumbflix.conf
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/0dc64f85-0d59-4015-a88b-488b09fe90c1)
```
cd dumbways/
```
```
sudo nano dumbflix.conf
```
### 4.2 Setelah itu masukkan konfigurasi berikut
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6e469621-5bcb-46b5-8436-1fb0d86a45fe)
```
server { 
    server_name dumbflix.xyz; 
  
    location / { 
             proxy_pass http://127.0.0.1:3000;
    }
}
```
### 4.3 setting host pada windows
pertama buka file explorer
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ffb08317-e595-4ed1-89aa-ac710c27e560)
```
C:\Windows\System32\drivers\etc
```
### 4.4 buka file host menggunakan administrator notepad
lalu pada bagian paling bawah tambahkan ip address dan domain yang sudah di configurasi pada server
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/8b7f89c1-9de3-4594-ba25-8f1a5983b02e)
```
192.168.245.100 dumbflix.xyz
```
### 4.5 pastikan untuk melakukan pengecekan konfigurasi dengan menjalankan perintah :
![Screenshot_15](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/538c08b2-5c7e-4dae-9553-624d48118aed)
```
sudo nginx -t
```
### 4.6 Jika sudah sekarang kita tinggal melakukan reload dan mengecek status Nginx
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/492c443e-cbd7-4a45-840c-102acc99be75)
```
sudo systemctl reload nginx
```
```
sudo systemctl status nginx
```
### 4.7 Jika sudah sekarang coba buka web browser kalian setelah itu coba akses nama domain kalian
![Screenshot_17](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/eaebea9a-97be-455c-8728-5ae57ce8eeb4)

kemudian jalankan npm start pada direktori dumbflix-frontend
![Screenshot_18](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/493b5933-dbf2-4893-afbe-71791baf417a)
