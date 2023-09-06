# Load Balancing
## 1. Menggunakan 2 server, jalankan Load Balancing yang berfungsi dengan baik
### 1.1 pertama saya mau menjelaskan
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/fa876c4d-77c1-44e5-a3a4-415c1e334783)
disini saya sudah memiliki 2 server dimana
server utama ssh wilson@192.168.245.100
server kedua ssh akbar@192.168.245.99
### 1.2 Selanjutnya kita akan buat konfigurasi ke dalam file Load_Balancing.conf
![Screenshot_19](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/5be2d0aa-fcfd-43c6-919d-9f10ada65197)
```
sudo nano Load_Balancing.conf
```
### 1.3 Sekarang kita akan coba tambahkan beberapa konfigurasi
dimana pada bagian upstream domain di isi ip dari masing-masing server
lalu pada bagian server name di isi domain kita dumbflix.xyz
![Screenshot_20](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/647b23e0-c70b-492b-a8b9-0cff813eab83)
```
upstream domain {
    server 192.168.245.100:3000;
    server 192.168.245.99:3000;
}
server {
    server_name dumbflix.xyz;

    location / {
             proxy_pass http://domain;
    }
}
```
### 1.4 tahap selanjut nya reload dan cek status nginx
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/29826408-58c3-4475-8830-949f55063a63)
```
sudo systemctl reload nginx
```
```
sudo systemctl status nginx
```
### 1.5 menjalankan Load Balancing yang berfungsi dengan baik
ini adalah contoh saya menjalankan domain di browser yang terhubung dengan server kedua ssh akbar@192.168.245.99
![image](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ce796bea-19fb-46d1-abae-3db3a1b137ff)

ini
