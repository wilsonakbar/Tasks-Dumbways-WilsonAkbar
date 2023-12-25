# Kubernetes
## Install K3S
https://docs.k3s.io/installation
### pertama update ubuntu
![Screenshot_1](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/6e5aef6c-0a77-4831-a79f-613790ce8b60)
```
sudo apt update
```
### kemudian install docker
![Screenshot_2](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/742b0410-f12a-4535-be9a-f4ed167e5615)
```
sudo apt install docker.io
```
### lalu install k3s untuk menggunakan kubernetes
![Screenshot_3](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/9e4ccfa7-dab5-40e8-ab84-71e254fa6b90)
```
curl -sfL https://get.k3s.io | sh -
```
![Screenshot_4](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/ddd86379-c9c9-45bc-9985-7d77de5bdfa3)
```
sudo chown $USER:$GROUP /etc/rancher/k3s/k3s.yaml
```
```
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```
untuk mengecek kubernetes yang sudah terinstall
```
kubectl get node
```
### buat direktori baru untuk menyimpan skript yaml
![Screenshot_55](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/50c19052-57f7-46cf-b166-fb330a3bce81)
```
mkdir master
```
```
cd master/
```
```
nano deployment.yaml
```
![Screenshot_7](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/ad344152-4bf2-4296-8815-e2062362a9f6)
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: fe-dumbmerch
spec:
  revisionHistoryLimit: 2
  selector:
    matchLabels:
      app: fe-dumbmerch
  template:
    metadata:
      labels:
        app: fe-dumbmerch
    spec:
      containers:
      - name: fe-dumbmerch
        image: wilsonakbar/fe-dumbmerch-production
        resources:
          limits:
            memory: "10Mi"
            cpu: "10m"
        ports:
        - containerPort: 3000

---

apiVersion: v1
kind: Service
metadata:
  name: service-fe-dumbmerch
spec:
  type: NodePort
  selector:
    app: fe-dumbmerch
  ports:
  - port: 3000
    targetPort: 80
    nodePort: 30001
```
### jalankan skrip yaml yang sudah di buat
![Screenshot_5](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/4ff7fa40-5e08-4f60-9de2-a46468116eb6)
```
kubectl apply -f deployment.yaml
```
![Screenshot_6](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/e49e7598-e303-41c3-b796-ec733fc7aaf9)
cek proses pembuatan dengan perintah
```
kubectl get pod
```
```
kubectl describe pod fe-dumbmerch-f9577985f-5z5zh
```
