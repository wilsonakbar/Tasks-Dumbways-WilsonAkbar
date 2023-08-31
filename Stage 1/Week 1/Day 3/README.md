# Application in Server
## 1. Deploy Aplikasi wayshub-frontend (NodeJS)
### 1.1 Instalasi NVM dengan perintah
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f8e77ccc-43b0-4132-af4c-1f88c8f19210)
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```
### 1.2 Eksekusi NVM dan Instalasi NodeJS v14 dan v16 serta gunakan v16 dengan perintah
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/31c361d2-d1c6-4dbc-8b82-c3d9fbd91da6)
```
exec bash
```
```
nvm install 14
```
```
nvm install 16
```
```
nvm use 16
```
### 1.3 Clone direktori yang telah disediakan dengan perintah
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b36d45f2-1dfc-46b0-b57d-9956d4be1c89)
```
git clone https://github.com/dumbwaysdew/wayshub-frontend.git
```
### 1.4 Masuk direktori wayshub-frontend dan install npm
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c5c03cde-6995-403e-9503-ecb8a8e1b5f4)
```
cd wayshub-frontend/
```
```
npm install -y
```
### 1.5 Menjalankan aplikasi pada Directory wayshub-frontend
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1f5543b1-b4ef-497f-b498-8409108a4faf)
```
npm start
```
### 1.6 Membuka aplikasi yang telah berjalan dengan ip address dan port 3000

![Screenshot_66](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/44c575a5-cf61-4f79-9c83-a5da6b1cbb85)
```
ifconfig
```
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/75b640f1-4b49-430f-a781-7f0150038bab)
```
192.168.145.200:3000
```
## 2. Deploy Golang dengan menampilkan nama masing-masing
### 2.1 Buat direktori golang dan masuk dengan perintah
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c1877de0-ea83-4eb3-9777-eaaf0ce00006)
```
mkdir golang
```
```
cd golang/
```
### 2.2 Instalasi GO
![Screenshot_77](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3d78f3a6-373e-4ce8-99eb-02b13bcd3937)
```
wget https://golang.org/dl/go1.16.5.linux-amd64.tar.gz && sudo su
```
### 2.3 Menghapus file temporary GO
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b0f82933-e9e0-447b-b178-030056f34caf)
```
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.16.5.linux-amd64.tar.gz && exit
```
### 2.4 Memasukan PATH Go
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/cc723b56-0e4a-4428-8fb8-018fb7c46d31)
```
sudo nano .bashrc
```
### 2.5 Masukan script berikut pada line paling terakhir
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/854774ae-1169-49b5-bf82-6362644ef271)
```
export PATH=$PATH:/usr/local/go/bin
```
### 2.6 Verifikasi GO yang telah kita install dengan perintah
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c6eb7012-9b89-4c54-bee2-fb7c7d5a8a55)
```
go version
```
### 2.7 Buat direktori untuk index golang dan masuk dengan perintah
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a4b8e80f-ae80-4a04-91dd-dcfe7eded3b9)
```
mkdir hari3go
```
```
cd hari3go/
```
```
nano index.go
```
### 2.8 Membuat project index sederhana menggunakan GO
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f4368d43-6a6e-46b8-ac98-c30a1e92a263)
```
package main  
import "fmt"  
func main() {  
    fmt.Println("Wilson Akbar")
}
```
### 2.9 Menjalankan project index yang telah dibuat dan membuat build agar mudah di jalankan dalam direktori index go yang kita buat
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9319acd6-20bc-47ae-b49f-92fa9dd5bc66)
```
go run index.go
```
```
go build index.go
```
```
./index.go
```
## 3. Deploy Python dengan menampilkan nama masing-masing
### 3.1 Membuat direktori python dan verifikasi python karna sudah terinstall pada ubuntu jadi kita install package manager saja
![Screenshot_15](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e071180b-db15-4749-ae3c-2132f1a73ea3)
```
mkdir python
```
```
cd /python
```
```
python3 -V
```
```
sudo apt-get install python3-pip
```
### 3.2 Instalasi library machine Python dan membuat index sederhana dengan Python
![Screenshot_17](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/68218659-3561-4071-8a33-359126c636bb)
```
pip install flask
```
```
nano index.py
```
![Screenshot_177](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e6b05fe2-eb58-4466-a744-b45e42cef64c)
```
from flask import Flask
app = Flask(__name__)
@app.route("/")
def helloworld():
    return "Calvin Novryan Rahaditya"
if __name__ == "__main__":
    app.run(host='0.0.0.0,port='5000')
```
### 3.3 Menjalankan aplikasi Python kemudian jalankan pada browser dengan ip masing2 dan port 5000
![Screenshot_188](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/8c1333f1-14b5-43f4-b5ac-23f886625a65)
```
python3 index.py
```
![Screenshot_18](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6edeafff-249e-4e50-a417-4b84f7b03f1c)
```
192.168.145.200:5000
```
![Screenshot_66](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c613fc84-1cf0-4d1d-91aa-0a183a4ece1c)
