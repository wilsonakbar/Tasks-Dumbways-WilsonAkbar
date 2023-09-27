# Docker
## 1. Instalasi Docker
### 1.1 Instalasi Docker dengan perintah seperti berikut
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/7753ce33-0517-4524-b859-ffe857358933)
```
sudo apt-get update
```
![Screenshot_17](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b87edb7d-fb84-403f-b535-93999aab11cb)
```
sudo apt-get install ca-certificates curl gnupg
```
![Screenshot_18](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/36484796-8188-4a30-937b-154de40f9bad)
```
sudo install -m 0755 -d /etc/apt/keyrings
```
![Screenshot_19](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f686f8d3-da79-4712-96d4-48e897ec3d3d)
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
![Screenshot_20](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a101c2ba-511d-490a-98ee-1a03c55eed36)
```
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
### 1.2 install repository Docker
![Screenshot_21](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1054f9ae-5920-406d-95aa-0055f6d0caac)
```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
![Screenshot_22](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/229920f6-54a7-44a6-ac1d-0514d54cbc80)
```
sudo apt-get update
```
### 1.3 Install the Docker packages
![Screenshot_23](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/cec60ad2-beec-4350-b520-d24b3f6399d3)
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
### 1.4 buat user group dengan nama kita
![Screenshot_24](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/57db033f-54fc-4533-91f5-443366fdcfe4)
```
sudo usermod -aG docker wilson
```
### 1.5 test dengan membuat docker hello-world
![Screenshot_25](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9cb1ef87-d0ee-44af-b6c7-12a7e2306d83)
```
sudo docker run hello-world
```
### 1.6 cek versi docker
![Screenshot_26](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3365f00e-a417-44bd-b145-4b7c3191477c)
```
docker -v
```


## 2. Deploy Aplikasi - menggunakan database MySQL & berfungsi dengan baik, Jalankan on top Docker, gunakan docker-compose, Push image ke hub Docker menggunakan akun masing-masing
### 2.1 Clone repository Wayshub frontend dan backend
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1e4e9442-3308-40fc-8b28-d34748ca5586)
```
git clone https://github.com/dumbwaysdev/wayshub-frontend
```
![Screenshot_69](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/46e76b3e-ab2f-43df-9fec-2114d9b3ec44)
```
git clone https://github.com/dumbwaysdev/wayshub-backend
```
### 2.2 install base image node 10.24.1-alpen pada direktori wayshub-frontend dan backend
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/aae4adf6-8327-413e-8da1-d71f3cd8999a)
```
https://hub.docker.com/_/node/tags?page=1&name=10.24.1
```
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/468ea506-12ff-497f-b4d9-423d5b2fe05c)
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6b7b7160-308d-4de4-b27d-51b35a8d15c7)
```
docker pull node:10.24.1-alpine
```
### 2.3 buat file dockerfile pada direktori wayshub-frontend dan backend
```
nano Dockerfile
```
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b6460c82-a85e-4b3c-a1bd-dfff9cac3db1)
```
FROM node:10.24.1-alpine
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["npm","start"]
```
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d4999c83-7a25-486c-a964-a4adfbaece16)
```
FROM node:10.24.1-alpine
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 5000
CMD ["npm","start"]
```
### 2.4 buat image lokal pada masing - masing direktori wayshub-frontend dan backend
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d06d83fe-225d-4f15-8544-4bfd93628311)
```
docker build -t wilson/wayshub-frontend .
```
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9506ac12-c330-4d0f-a0cc-00a87497a525)
```
docker build -t wilson/wayshub-backend .
```
### 2.5 jalankan aplikasi dengan docker kompos
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/dbb650cc-b7ab-42b3-bd8a-6794ada39508)
```
nano docker-compose.yml
```
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/62fd5289-f050-489b-813f-c4e61ac15272)
```
---
version: "3.8"
services:
  frontend:
    container_name: wayshub-frontend
    image: wilson/wayshub-frontend:latest
    stdin_open: true
    ports:
      - 13000:3000

  database:
    container_name: wayshub-db
    image: mysql:latest
    volumes:
      - ~/mysql-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: Wilson123
      MYSQL_USER: wilson
      MYSQL_PASSWORD: Wilson123
      MYSQL_DATABASE: db-wayshub
    
    ports:
      - 13306:3306
  backend:
    container_name: wayshub-backend
    image: wilson/wayshub-backend:latest
    stdin_open: true
    ports:
      - 15000:5000
```
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6fa991f6-e46a-4db6-91c1-3c91f559bcd1)
```
docker compose up
```



```
nano Dockerfile
```
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/8e31ee57-a3fc-4482-b95e-030a570ce023)

### 2.4 jalankan build doker untuk direktori wayshub-frontend
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/df497f89-a82a-4b8e-9079-d05ccce885d2)
```
docker build -t wayshub-frontend .
```



```

### 1.
```
```
