# Kubernetes
## Install minikube
### pertama kita install minikube terlebih dahulu
https://minikube.sigs.k8s.io/docs/start/
disini saya install minikube di lokal windows menggunakan chocolatey
https://chocolatey.org/install
### jika sudah selesai kita lanjut install minikube dengan perintah
jalankan perintah menggunakan administrator shell pada windows
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1cdb58d8-ea66-4229-86bb-0402b7325988)
```
choco install minikube
```
### jalankan minikube dengan perintah
jalankan perintah menggunakan administrator command prompt pada windows 
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/840a9e89-518a-4805-97fe-efdefd8c3a90)
```
minikube start
```
### verifikasi minikube yang sudah di jalankan
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b04ed12f-d52c-438e-a2ce-5fe6860ae06d)
```
kubectl get all
```
```
minikube kubectl -- get po -A
```
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3fc3794b-f8df-4611-8e1a-cfb3a6dd9d12)
```
minikube dashboard
```
### deploy contoh hello minikube
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/841e3c10-2585-4f11-9a82-3c02eae2fe19)
```
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
```
```
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```
```
kubectl get all
```
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f398d2d9-65e8-4440-99b2-0c5c72792073)
```
minikube service hello-minikube
```
### persiapan deploy menggunakan file yml
pertama agar mempermudah dalam mendeploy kita buat folder baru untuk isi file yml pada windows
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/02d63653-b4da-4339-a5f5-b4a171915280)
```
C:\Users\Wilson\minikube
```
kemudian masuk file direktori yang kita buat pada administrator shell
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/8f1b27be-d296-479d-97e4-51349702c025)
```
cd .\minikube\
```
kemudian siapkan visual studio yang sudah terhubung ke folder yang baru dibuat
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/42d5669e-faff-4432-96a1-c01993dd6743)
### deploy nginx menggunakan file yml minikube
buat file yml dengan nama deploy-nginx
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f088849c-9673-415d-8a5c-5e2f8f58423b)
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:alpine
          ports:
            - containerPort: 80
```
buat file yml dengan nama expose-nginx
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f6324dab-6a9b-4a78-9297-a2c0e81ca30b)
```
apiVersion: v1
kind: Service

metadata:
  name: nginx-deployment
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - name: exposeport
      protocol: TCP
      port: 80
      targetPort: 80
```
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/05948924-33ce-4fcd-a2f6-c66f2e81225c)
apply file yang tadi kita buat
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d42f29f5-f585-45b2-b83a-4dafa8ae2306)
```
kubectl apply -f .\deploy-nginx.yml
```
```
kubectl apply -f .\expose-nginx.yml
```
kemudian cek hasil deploymen dan juga service nya
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/70a29f21-4e5f-4103-a22a-b3232bcf43ee)
```
kubectl get all
```
kemudian jalankan service yang sudah kita deploy
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/636235a0-0b0e-49be-9549-c3df30ca9110)
```
minikube service nginx-deployment
```
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/83d87b3a-725a-43ef-a108-4b371a0c6eb3)
### deploy wayshub-frontend menggunakan file yml minikube
buat file deploy-frontend
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/057a02db-86f3-4bf5-b796-0c442f50aebe)
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend-deployment
  labels:
    app: frontend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: frontend
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
        - name: wayshub-frontend
          image: aimingds/wayshub-fe
          ports:
            - containerPort: 3000
```
buat file expose-frontend
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a3741188-5f84-4adb-b65b-5b47f4ca3ac2)
```
apiVersion: v1
kind: Service

metadata:
  name: frontend-deployment
spec:
  type: NodePort
  selector:
    app: frontend
  ports:
    - name: exposeport
      protocol: TCP
      port: 3000
      targetPort: 3000
```
apply file yml yang telah kita buat
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/27c14b4e-2dc3-4b80-b844-a3cb65fede47)
```
kubectl apply -f .\deploy-frontend.yml
```
```
kubectl apply -f .\expose-frontend.yml
```
cek deploy dan service yang telah dibuat
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/72cfa046-9902-4f65-b2a1-bfbedfb7e4bc)
```
kubectl get all
```
jalankan service nya
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/534ef239-2e19-4b10-a539-ed0cbe07cd49)
```
minikube service frontend-deployment
```
![Screenshot_15](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/958add41-4048-44de-a575-a4cfec1daec6)
