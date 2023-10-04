# Ansible
## 1. Buatlah terraform untuk mendeploy docker image wayshub-fe
## 2. Praktekkan penggunaan terraform dari pembuatan hingga resource di hancurkan

### install terraform pada ubuntu server
https://developer.hashicorp.com/terraform/tutorials/docker-get-started/install-cli

### install docker pada ubuntu server
https://docs.docker.com/engine/install/ubuntu/

### buat file main.tf pada direktori ./terraform/docker untuk install docker
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/cef7f143-afe1-4bbb-b70b-ba94effe74df)
```
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 2.13.0"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "docker pull aimingds/wayshub-fe"
  keep_locally = false
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.latest
  name  = "frontend"
  ports {
    internal = 3000
    external = 8080
  }
}
```
### lalu didalam direktori ./terraform/docker kita terraform 
```
init -upgrade
```
dan 
```
terraform apply
```

### cek image docker yang sudah kita buat
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/988a0794-fb95-4e86-89ce-0db79bedf742)
```
docker images
```
```
docker ps -a
```

### buka aplikasi wayshub fe di browser pada ip
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9f65c771-2578-4000-b232-e35ec5c6c7c2)
```
http://103.127.97.68:8080/login
```
### masuk pada direktori ./terraform/docker untuk menghapus wayshub fe
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ea8b3b2b-470e-45a3-a4a2-37222299f414)
```
terraform destroy
```



















