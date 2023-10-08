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
### buat direktori ansible dan file seperti berikut
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
### Membuat user baru, gunakan login ssh key pada appserver dan gateway
buat file nano user.yml pada direktori ansible lalu jalankan
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/4a9ef1a3-cd67-429c-9afb-3197159064cd)
```
- become: true
  gather_facts: false
  hosts: all
  vars:
   - username: "akbar"
   - password: ""

  tasks:
    - name: "Creating User"
      ansible.builtin.user:
        groups: sudo
        name: "{{username}}"
        password: "{{password}}"
```
```
ansible-playbook user.yml
```
cek user baru pada pada appserver dan gateway
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b3c6aec4-7b64-4b18-a44e-6346ad97c6c4)
```
su akbar
```
```
exec bash
```
### Instalasi Docker
buat file nano install-docker.yml pada direktori ansible lalu jalankan
![Screenshot_15](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/7ad915ab-023c-4f04-a32a-61d252a6a4af)
```
---
- become: true
  gather_facts: false
  hosts: all
  tasks:
    - name: Docker Dependencies
      apt:
        update_cache: true
        name:
          - ca-certificates
          - curl
          - gnupg
          - lsb-release
    - name: Docker GPG Key
      apt_key:
        url: https://download.docker.com/linux/ubuntu/gpg
    - name: Docker Repository
      apt_repository:
        repo: deb https://download.docker.com/linux/ubuntu focal stable
    - name: Docker Engine
      apt:
        update-cache: true
        name:
          - docker-ce
          - docker-ce-cli
          - containerd.io
          - docker-compose-plugin
    - name: Python Dependencies
      apt:
        name: python3-pip
        state: latest
        update_cache: true
      become: true
    - name: Docker SDK for Python
      pip:
        name: docker
    - name: add user docker group
      user:
        name: wilson
        groups: docker
        append: yes
```
```
ansible-playbook install-docker.yml
```
cek apa kah docker berhasil di instal pada appserver dan gateway
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/dea82b4f-3d99-448d-88b3-ea2d6276c468)
```
docker -v
```
```
sudo docker images
```
```
sudo docker ps -a
```
### Instalasi node-exporter
buat file nano install_node_exporter.yml pada direktori ansible lalu jalankan
![Screenshot_17](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d0d355f9-ab31-49a9-9785-6a303e74e2ae)
```
- name: Deploy Node Exporter with Docker
  hosts: appserver
  become: true
  tasks:
    - name: Pull the bitnami/node-exporter Docker image
      docker_image:
        name: bitnami/node-exporter
        source: pull

    - name: Run the Node Exporter container
      docker_container:
        name: node-exp
        image: bitnami/node-exporter
        state: started
        restart_policy: unless-stopped
        published_ports:
          - "9100:9100"
```
```
ansible-playbook install_node_exporter.yml
```
### Instalasi nginx pada gateway
buat file nano nginx.yml pada direktori ansible lalu jalankan
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1f3c9ec7-3282-4cca-affb-aa7f4ca15f90)
```
---
- become: true
  gather_facts: false
  hosts: gateway
  tasks:
    - name: "Installing nginx"
      apt:
        name: nginx
        state: latest
        update_cache: yes
    - name: start nginx
      service:
        name: nginx
        state: started
```
```
ansible-playbook nginx.yml
```
buka nginx dengan ip gateway pada browser
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c72b3997-0463-4ecd-9d5c-8f59090ae9f1)
