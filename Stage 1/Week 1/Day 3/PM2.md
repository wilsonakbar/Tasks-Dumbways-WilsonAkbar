# PM2
## 1. Instalasi PM2 secara global
### 1.1 Install PM2
![Screenshot_28](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/227fa5eb-5e0b-4f6b-bda2-0990285a92d9)
```
npm install pm2 -g
```
## 2. Jalankan aplikasi NodeJS dan Python menggunakan PM2
### 2.1 Menjalankan NodeJS dengan PM2 (masuk direktori wayshub-frontend/src)
![Screenshot_29](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/63dbb18b-0590-48c4-a9b1-8cb095b4b5fb)
```
pm2 start index.js
```
### 2.2 Menjalankan Python dengan PM2
![Screenshot_30](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/62f0ece3-5930-423b-9e95-3b8a5c5a9357)
```
pm2 start index --interpreter=python
```
