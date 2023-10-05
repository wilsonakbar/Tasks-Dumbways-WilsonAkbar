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

### install multipass pada pc untuk menjalankan lokal
[https://learn.microsoft.com/en-us/windows/wsl/install](https://multipass.run/install)

### install ansible pada local ubuntu
https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html#installing-ansible-on-ubuntu
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f45fd9aa-6ecc-4d75-b244-8d8258dc0fce)
```
ansible --version
```
### buat buat direktori ansible dan file seperti berikut
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d775a191-8afd-4949-88e5-c6d4909ed6fd)
ansible.cfg
```
[defaults]

inventory = Inventory
private_key_file = /home/ubuntu/.ssh/id_rsa
host_key_checking = False
interpreter_python = auto_silent
```
Inventory
```
[appserver]
103.127.97.68

[gateway]
103.127.97.70

[all:vars]
ansible_user="wilson"
```
### salin ssh private lokal ke authorized appserver dan gateway
buat kunci ssh pada lokal bila belum ada
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ec09d0f2-cbfc-4560-86c5-432a4e5bbfed)
```
ssh-keygen
```
```
cat id_rsa.pub
```
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/3ecd2c95-e6d5-4095-af10-c261e360f788)
lalu salin ke authorized_keys yang ada di appserver dan gateway
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/46f4798d-83b8-4baf-90c6-25fd8fd93893)
test ping
```
ansible all -m ping
```
