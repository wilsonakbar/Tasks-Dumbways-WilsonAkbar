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
