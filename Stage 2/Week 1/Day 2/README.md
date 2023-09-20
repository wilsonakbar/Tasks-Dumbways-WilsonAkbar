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
### 2.2 install PM2
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e014fc54-681c-4eb6-be05-3468599739cc)
```
npm install -g pm2
```
### 2.3 deploy aplikasinya menggunakan PM2
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
### 3.1 Clone repository Wayshub frontend & backend
