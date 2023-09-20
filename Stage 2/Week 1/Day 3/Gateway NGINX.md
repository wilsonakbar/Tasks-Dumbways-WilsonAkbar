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
### 3.2 konfirmasi file config yang telah kita buat lalu reload nginx
![Screenshot_48](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/17c47c45-1d45-474f-b759-9ef2c6bb225b)
```
sudo nginx -t
```
```
sudo systemctl reload nginx
```
### 3.3 buka domain yang tadi kita telah buat di browser
![Screenshot_49](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/46a6dabb-f5f5-4090-bb2f-c3e3e3e8fa7f)
```
http://wilson.studentdumbways.my.id/login
```
![Screenshot_50](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e2d30561-4120-4c76-9b70-45154dd3c1f3)
```
http://api.wilson.studentdumbways.my.id/login
```
## 4. SSL menggunakan certbot (http:// menjadi https://)
### 4.1 sebelum install certbot kita install snapd
![Screenshot_53](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/607c37dd-f5e3-4eb5-b812-72cd378e8ee2)
```
sudo apt install snapd
```
### 4.2 kemudian install certbot
![Screenshot_54](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/073caeaf-7050-41f0-952b-e2ecfb24a04b)
```
sudo snap install --classic certbot
```
### 4.3 buat direktori untuk certbot
![Screenshot_55](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/374c0ad9-87eb-41e2-b5a8-489d238bcedc)
```
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
### 4.4 sertifikasi domain yang telah kita buat sesuai perintah
![Screenshot_56](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f441df21-db8c-49d4-84aa-4d4011c3c5b5)
```
sudo certbot --nginx
```
### 4.5 jalankan certbot yang telah kita buat
![Screenshot_57](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/209622f4-c1d1-4bee-8802-f789585cd278)
```
sudo certbot renew --dry-run
```
### 4.6 jalankan kembali domain dengan https
![Screenshot_58](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/bc56b56a-70ee-4fce-aa69-e53e95811f75)
https://wilson.studentdumbways.my.id/login
![Screenshot_59](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c8cbd890-3604-4519-a291-09dd8343ed48)
https://api.wilson.studentdumbways.my.id/login
















