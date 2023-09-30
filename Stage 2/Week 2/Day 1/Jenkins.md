# Jenkins
## 1. Jalankan Jenkins on top Docker
### 1.1 buat file sudo nano docker-compose.yml dan jalankan docker compose nya
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d3003eb6-ba71-4742-9015-7268f5d602a2)
```
sudo nano docker-compose.yml
```
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c4b038f6-92ba-4fd1-8e99-83701b779c66)
```
version: '3.8'
services:
   jenkins:
      image: jenkins/jenkins:lts-jdk11
      container_name: jenkins
      restart: always
      privileged: true
      user: root
      ports:
         - 8080:8080
         - 50000:50000 
      volumes:
         - ~/jenkins:/var/jenkins_home
```
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/56b2992c-7c7c-4c43-9120-d68ddb091a12)
 ```
docker compose up
```
copy password yang ada dalam docker
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3fbf5d0b-bdec-4a6a-b15f-9b7ffe03b357)
```
docker logs jenkins
```
masukan password jenkins
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d4bbe6e8-1c08-4262-a7e1-fa7c88b2d18e)

```
http://103.127.97.68:8080/
```
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e60d33da-547b-4181-9330-b12926980f3c)
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/84ea1bcc-5650-4b26-baf6-b4091ee924f5)
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/dfef9c8d-5aee-4ed3-b086-61375553992c)
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/55308a2f-5989-4084-8c41-6fb3b99b3f76)
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/156b1d64-8237-40c0-a467-22c0fd63ee0b)
nah ini adalah tampilan awal jenkins setelah selesai di install
### 1.2 Sambungkan Jenkins ke Server
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d9d82d0d-4df2-4a2d-8f15-d0509db2e122)
pada managemen jenkins pilih credentials
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/172cdbf7-8eba-4b97-91ea-7b9556aa65dc)
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/74748bba-e40d-4416-934e-be44852d0c41)
![Screenshot_15](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/144a4b5f-cdd8-45c0-bd6c-79677cff4ce6)
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/df42963f-ddf3-458e-9e9c-d69d1be53e68)
pilih SSH Username with private key
![Screenshot_17](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d24544da-fd30-488f-867a-a544df062350)
isi semua kolom nya
![Screenshot_18](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ebf2b8fb-9790-4194-91f8-b7f61b23a45e)
masukan isi gembok pc kita lalu copy pada private key
![Screenshot_19](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b4bdf7af-991b-4b29-b909-5fd14824868a)
![Screenshot_20](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e7241d4c-7cf4-4aef-b6c7-9ca8e1d368d1)
## 2. Pipeline untuk frontend & b
ackend
### 2.1 Pull dari repository
