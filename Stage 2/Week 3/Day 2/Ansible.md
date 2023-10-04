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
### install ubuntu pada WSL
https://learn.microsoft.com/en-us/windows/wsl/install

### install ansible pada ubuntu
https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html#installing-ansible-on-ubuntu

### buat file ansible.cfg
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9e1ac28f-cf2c-4acc-bddf-20346291e224)

### buat file Inventory
saya membuat 3 server dan 3 gateway dimana semua user bernama wilson
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/eaa195a5-ef34-4a73-a5da-532820efcf9e)
```
[server]
172.21.201.11
172.21.201.12
172.21.201.13

[gateway]
172.21.201.21
172.21.201.22
172.21.201.23

[all:vars]
ansible_user="wilson"
```
### salin kunci publik yang ada di pc ke server lokal ubuntu
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/5a805bad-4a2b-4973-894e-e538dd81a632)
