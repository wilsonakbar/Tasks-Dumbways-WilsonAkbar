# Ansible
## Local
buat konfigurasi Ansible & dan lakukan semua setup melalui local sebanyak mungkin.
## appserver
gunakan ansible-playbook
- Membuat user baru, gunakan login ssh key
- Instalasi Docker & node-exporter
- **buat konfigurasi prometheus (Monitoring)**
  - On top docker menjalankan Grafana & Prometheus
## gateway
gunakan ansible-playbook
- Membuat user baru, gunakan login ssh key
- Instalasi nginx
- Buat konfigurasi proxy lalu masukkan kedalam gateway
- Gunakan docker-compose untuk deploy aplikasi wayshub-frontend

## Local
 install ubuntu pada WSL
https://learn.microsoft.com/en-us/windows/wsl/install
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/139be8b2-466b-45c8-859b-854682bc1d2b)
```
wsl --install
```
### install terraform pada ubuntu server
https://developer.hashicorp.com/terraform/tutorials/docker-get-started/install-cli

### install docker pada ubuntu server
https://docs.docker.com/engine/install/ubuntu/
