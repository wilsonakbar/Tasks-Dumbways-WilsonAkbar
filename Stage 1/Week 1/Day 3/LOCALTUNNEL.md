# Localtunnel
## 1. Dumbflix-frontend bisa diakses melalui localtunnel
### 1.1 Instalasi Localtunnel
![Screenshot_19](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/dd2041a9-8c30-4098-bbe1-8cfea6d65503)
```
npm install -g localtunnel
```
### 1.2 Instalasi service Nginx
![Screenshot_20](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2d3a1949-86b1-4e13-886d-764bb250fd65)
```
sudo apt install nginx
```
### 1.3 Jalankan service Nginx dengan ip address
![Screenshot_21](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/89cd9408-1a54-4306-bec3-e0347aa8297c)
```
192.168.145.201:5000
```
![Screenshot_66](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e9c4cf8d-69a6-4c25-94e5-7e47c797cddf)
### 1.4 Menjalankan Localtunnel diatas port 3000 NodeJS (NodeJS sudah harus di jalankan terlebih dahulu)
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9aaa3684-1e4f-41fc-90a1-798b637cefdd)
```
npm start
```
![Screenshot_22](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d84bd5d9-81e4-4754-85d1-323bb07899c5)
```
lt --port 3000
```
### 1.5 Membuka Localtunnel yang telah berjalan pada browser
![Screenshot_24](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/7566238b-2df9-491e-8aa9-6dfc78e6f396)
```
https://cool-planets-nail.loca.lt
```
### 1.6 masukan IP Public yang kita dapat lalu submit
![Screenshot_23](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/af6f86b4-202a-40fe-800b-db7bdd7db6ea)
```
https://ipv4.icanhazip.com/
```
![Screenshot_25](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f668572c-8440-4faa-b313-ea2b37a9eac0)
## 2. App python bisa diakses melalui localtunnel
### 2.1 Menjalankan Localtunnel diatas port 5000 Python (Python sudah harus di jalankan terlebih dahulu)
![Screenshot_188](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a481ff82-3650-4c31-95f8-1238de92c310)
```
python3 index.py
```
![Screenshot_26](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c32f9623-940f-4ab1-9d21-75299cfbf996)
```
lt --port 5000
```
### 2.2 Membuka Localtunnel yang telah berjalan pada browser
![Screenshot_266](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/7da633df-244b-4c84-add9-770fb68f4ae8)
```
https://cyan-doodles-shop.loco.lt/
```
### 2.3 masukan IP Public yang kita dapat lalu submit
![Screenshot_23](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/af6f86b4-202a-40fe-800b-db7bdd7db6ea)
```
https://ipv4.icanhazip.com/
```
![Screenshot_27](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/84716778-89ce-4db2-9250-ca0b169d26d6)
