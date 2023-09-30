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
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d4bbe6e8-1c08-4262-a7e1-fa7c88b2d18e)

```http://103.127.97.68:8080/```
## 2. Pipeline untuk frontend & backend
### 2.1 Pull dari repository
