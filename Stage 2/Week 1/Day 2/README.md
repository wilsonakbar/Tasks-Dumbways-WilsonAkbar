# Deploy Wayshub
## 1. Buat 2 VM di IDCloudHost
### 1.1 pada profil di idcloudhost pilih user dumbways.dev@gmail.com yang sudah di share
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f3bc6686-e3cb-4fa9-9182-bdffc2710550)

### 1.2 kemudian pilih virtual machine
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/7e1ea100-384a-4913-8e5c-8decfad3089d)

### 1.3 kemudian pilih type, os, location, dan size sesuai gambar lalu scroll kebawah
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/84714b4f-6833-4d53-9fe9-b8e399c479b4)

### 1.4 kemudian ceklis public ip, vpc sesuai ip komputer kita, isi username password dan resource name wilson-appserver seperti gambar lalu klik create
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1ca847a1-b48f-4d35-8a14-7896fa042a2d)

### 1.5 lakukan hal yang sama untuk membuat vm kedua dan yang membedakan resource name wilson-gateway
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/76bf7a6d-d46c-45af-9b90-8e8102e1c23e)

## 2. Appserver
### 2.1 Clone repository Wayshub frontend & backend
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/5df0edce-4b85-4571-9b03-257ae8e24887)
```
git clone https://github.com/dumbwaysdev/wayshub-frontend
```
```
git clone https://github.com/dumbwaysdev/wayshub-backend
```
### 2.2 install nodejs versi 14.x
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/13fa1228-d199-4a09-b5b3-1dc64073e66f)
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/5e96818b-96ec-417b-ae7f-99df1bc4a237)
```
exec bash
```
```
nvm install 16
```
### 2.3 install PM2
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e014fc54-681c-4eb6-be05-3468599739cc)
```
npm install -g pm2
```
### 2.4 deploy aplikasinya menggunakan PM2
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/5f2d63e6-ff7e-4726-89c1-9e8409dd8f0f)
```
cd wayshub-frontend/
```
```
npm install
```
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/79adb24d-bba7-4c41-9619-0d71c1b0fa4a)
```
pm2 ecosystem simple
```
```
nano ecosystem.config.js
```
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/71386a7f-702c-4746-9e14-fd4be27dac87)
```
module.exports = {
  apps : [{
    name   : "frontend",
    script : "npm start"
  }]
}
```
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/bab61aaa-534c-453e-aa8d-80d649a8d4ae)
```
pm2 start
```
![Screenshot_15](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/4b5315c2-c69f-4240-ba64-9ef7dc23bdbc)
lalukan hal yang sama pada direktori wayshub-backend
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b16aa1d4-b0b9-43b3-a85b-5415fb19f84c)
```
module.exports = {
  apps : [{
    name   : "backend",
    script : "npm start"
  }]
}
```
![Screenshot_17](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/12bfde8e-989f-4e90-bef1-f2174a93b0d7)
```
pm2 start
```
## 3. Install dan konfigurasi database MySQL 
### 3.1 sebelum konfigurasi apt update terlebih dahulu
![Screenshot_18](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/dbf9cf0d-5d31-4006-ac61-7eb7aa07a932)
```
exec bash
```
```
sudo apt update
```
### 3.2 masuk pada sources.list lalu ganti mirrors.idcloudhost.com menjadi archive.ubuntu.com
![Screenshot_19](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/363fe602-5079-4088-b563-598b54f30844)
```
sudo nano /etc/apt/sources.list
```
replace dengan menekan ctrl + \
![Screenshot_20](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/623be78f-2ab8-4564-83b7-6bf7f31a68a2)
```
mirrors.idcloudhost.com
```
![Screenshot_21](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/bea60a71-e579-4649-93f6-a92d24fc3805)
```
archive.ubuntu.com
```
lalu enter dan replace all dengan menekan a
![Screenshot_22](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f161cf8f-19bf-4287-9a5f-1bb75d20969f)
### 3.3 kemudian Install database MySQL dan cek status MySQL
![Screenshot_23](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/672e0bfd-def4-4aa1-a18e-9609b4d82829)
```
sudo apt install mysql-server
```
![Screenshot_24](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3bd438b9-663b-4369-867a-cc3304d0c6ce)
```
sudo systemctl mysql.service
```
### 3.4 kemudian buat password untuk user root dan tambah user baru sesuai nama
![Screenshot_25](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/de350f79-4d81-4aef-be69-68502106643e)
```
sudo mysql -u root
```
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'Wilson123';
```
```
CREATE USER 'wilson'@'%' IDENTIFIED WITH mysql_native_password BY 'Wilson123';
```
### 3.5 setting mysql_secure_installation dan berikan hak akses pada user yang kita buat
jalankan sekuritas mysql sesuai step by step
![Screenshot_26](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6406bddb-6301-45e9-baf0-e733aec684cf)
```
sudo mysql_secure_installation
```
![Screenshot_27](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/893ff124-9ac2-41ee-93fd-ecfc4ef42620)
```
sudo mysql -u root -p
```
```
GRANT ALL PRIVILEGES ON *.* TO 'wilson'@'%';
```
### 3.6 kemudian konfigurasi config.json pada direktori wayshub-backend
![Screenshot_28](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/8766e05d-61af-440f-81ec-7249fd93dac5)
```
cd wayshub-backend/
```
```
cd config/
```
```
nano config.json
```
![Screenshot_29](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b5b38e94-bd81-4f49-ae5c-3c4aad812063)
pada bagian ini ganti username password sesuai user yang sudah kita buat dan berikan nama database nya
### 3.7 kemudian konfigurasi api.js pada direktori wayshub-frontend
![Screenshot_30](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/245cccfe-32f1-440a-a12f-fc16cc965780)
```
cd wayshub-frontend/
```
```
cd src/
```
```
cd config/
```
```
nano api.js
```
![Screenshot_37](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9152135b-d7cc-4acb-8a6c-70046401e748)
pada bagiaon ini ganti baseURL dengan ip kita masing-masing
### 3.8 menggabungkan konfigurasi database yang kita buat
![Screenshot_32](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b94281a3-a409-4674-8092-12530d37d3d4)
```
cd wayshub-backend/
```
```
npm install -g sequelize-cli
```
```
sequelize db:create
```
```
sequelize db:migrate
```
### 3.9 jalankan ulang aplikasinya menggunakan PM2
![Screenshot_33](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9cfe980e-fe2f-4c22-b5a7-841d903ac5c8)
```
pm2 start
```
![Screenshot_34](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/54f6097b-3b6c-463f-9f6b-4cc5c6babf31)
registrasi user pada fontend wayshub
![Screenshot_35](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/03929f6e-e54b-4e5b-9230-78b46962e326)
kemudian login user yang telah kita buat
![Screenshot_36](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a1210506-4f3e-407c-85f0-30ca1d38ac02)
selesai buat akun wayshub


