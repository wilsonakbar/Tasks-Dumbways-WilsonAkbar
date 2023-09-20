# Gateway
## 1. Installasi nginx di server gateway
### 1.1 pada ssh wilson-gateway sebelum install nginx terlebih dahulu update apt
![Screenshot_44](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9bb26ae5-17a0-408f-a2d3-5c98c8a446f8)
```
sudo apt update
```
### 1.2 kemudian install nginx dengan perintah
![Screenshot_45](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b5436997-f248-4acb-a038-c54f7ab855ce)
```
sudo apt install nginx
```
### 1.3 cek status nginx dengan perintah
![Screenshot_46](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/df39224e-3f77-45bd-ae45-b7df9a26ae34)
```
sudo systemctl status nginx
```
## 2. Installasi nginx di server gateway
### 2.1 buat file config pada direktori
![Screenshot_51](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e65d09b3-2989-42be-9814-131d68523589)
```
cd /etc/nginx/sites-enabled/
```
```
sudo nano rproxy.conf
```
## 3. Gunakan domain sesuai dengan nama kalian
### 3.1 isi domain sesuai tugas
- <nama>.studentdumbways.my.id (front-end)
- api.<nama>.studentdumbways.my.id (back-end)
![Screenshot_47](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/4a3b437e-bada-418b-bf79-1ac01facca95)
```
server {
    server_name wilson.studentdumbways.my.id;

    location / {
             proxy_pass http://103.187.146.221:3000;
    }
}

server {
    server_name api.wilson.studentdumbways.my.id;

    location / {
             proxy_pass http://103.187.146.221:5000;
    }
}
```
### 1.6 konfirmasi file config yang telah kita buat lalu reload nginx
![Screenshot_48](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/17c47c45-1d45-474f-b759-9ef2c6bb225b)
```
sudo nginx -t
```
```
sudo systemctl reload nginx
```
### 1.7 buka domain yang tadi kita telah buat di browser
![Screenshot_49](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/46a6dabb-f5f5-4090-bb2f-c3e3e3e8fa7f)
```
http://wilson.studentdumbways.my.id/login
```
![Screenshot_50](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e2d30561-4120-4c76-9b70-45154dd3c1f3)
```
http://api.wilson.studentdumbways.my.id/login
```
















