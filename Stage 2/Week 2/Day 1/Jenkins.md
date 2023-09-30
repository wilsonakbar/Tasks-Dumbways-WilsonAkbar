# Jenkins
## 1. Jalankan Jenkins on top Docker
### 1.1 install Jenkins
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
![Screenshot_21](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6c0e7aaa-d62e-4923-9401-4de96bcd2cf6)
install ssh agent pada jenkins
## 2. Pipeline untuk frontend & backend
### 2.1 hubungkan jenkins dengan aplikasi frontend dan sambungkan frontend pada github dengan ssh
buat nama Pipeline
![Screenshot_25](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9a172e56-4885-4435-9f79-b494ca70f90b)
ceklist github hook trigger
![Screenshot_26](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/82da8e97-5d68-439e-98fd-31757077dcfa)
pada pilihan Definition pilih pipe SCM
![Screenshot_27](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/981a252d-5348-4629-97dd-0cd265034a82)
pilih main untuk branch nya
![Screenshot_28](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f94bdc19-7592-4e8e-910c-45994f2ddbff)
![Screenshot_29](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/47569f22-02c8-42d1-94fc-507d7f4f638a)
pada bagian security pilih accept first connection
![Screenshot_30](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/0c0732d3-e157-4e73-a589-6aa14da92451)
pada bagian setting github
![Screenshot_31](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/eb6e2cb2-8313-48bf-8063-678455eebbdb)
```
cat .\.ssh\id_rsa.pub
```
![Screenshot_32](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/28ab91e1-3378-46f6-af59-2bdaee228766)
masukan kunci ssh yang sudah kita salin kedalam github
![Screenshot_33](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/12da49e6-8795-44b8-9a6c-e02571c6d500)
kemudian salin ssh direktori pada github
![Screenshot_34](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/431e4749-4c7e-4bda-90c4-edef7aca6e4e)
pada direktori frontend kita remote ssh yang sudah di salin dari github
![Screenshot_35](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6b8e4e26-17cf-447f-8aca-db00f5c1eadb)
```
git config --list
```
```
cd wayshub-frontend/
```
```
git config --list
```
```
git remote -v
```
```
git remote set-url origin git@github.com:wilsonakbar/wayshub-frontend.git
```
![Screenshot_36](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/da8d189a-87e7-4ee3-bce8-7b6a6657ffa0)
```
git add .
```
```
git status
```
```
git commit -m "test"
```
![Screenshot_37](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ffa4200c-fe83-4326-a904-c83cbf5c55ab)
```
git config --global user.name "wilsonakbar"
```
```
git config --global user.name "wilsonakbar2@gmail.com"
```
```
ssh git@github.com -T
```
![Screenshot_38](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a1ecc307-2c62-4100-ae70-c9102b40eb9e)
salin gembok ssh dari komputer kita
![Screenshot_39](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3ecd5e26-2f05-4794-a256-9cf6a8d9c884)
buat file id_rsa pada ssh di server kita lalu salin isi gembok nya
```
cd. ssh
```
```
nano id_rsa
```
![Screenshot_40](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/412bd3c1-9ef7-4657-ac88-15d7070c163b)
kemudian masuk pada direktori frontend dan lalukan push
![Screenshot_41](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ccf3487b-89a1-4485-8f58-59b3c97151c6)
```
cd wayshub-frontend/
```
```
git push
```
![Screenshot_42](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/de006f74-7a32-4810-b078-e0d671787ca0)
direktory server frontend berhasil tersambung dengan direktory github
![Screenshot_43](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e7d40289-62b2-4cef-9ad9-2a6e3d041e60)


![Screenshot_45](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f1986136-0dfe-41ae-81d3-4a0bdd37bd6c)
![Screenshot_46](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/4e3c54af-9151-4847-b688-5876041705af)
![Screenshot_47](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/8a02411b-035a-4b74-808e-250dec1a7d6a)


buat file Jenkins pada direktori frontend dengan script seperti ini
![Screenshot_48](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/5297fbc7-94b0-48d8-b0d8-d82fc48a461e)
kemudian push file script Jenkins
![Screenshot_44](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d4d71970-d58e-4e1e-9b00-41a129ccd3b8)
git add
```
```
git commit -m "test"
```
```
git push
```
pada halaman jenkins kemudian kita trigger build
![Screenshot_49](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3f7690de-d29c-4ebd-bbd6-3c71c04c8ab5)
terakhir upload file pada dockerhub
![Screenshot_50](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/36aac4e1-d784-494c-9c76-27b522f0e9d4)












