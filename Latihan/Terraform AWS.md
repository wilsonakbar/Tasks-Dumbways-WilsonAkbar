# Membuat 2 Instansi ubuntu menggunakan terraform untuk AWS pada lokal windows
## Install terraform pada lokal windows
https://developer.hashicorp.com/terraform/install?product_intent=terraform
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/329a1d32-c270-40aa-a05d-6c0a99ef9849)

kemudian ekstrak file yang telah di download
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/d18e11f3-e3c4-4cc8-aea8-5018a25bb349)

pada "Advanced system settings" bagian "Environment Variables" edit path pada User variables" dan "System variables" sesuai dengan direktori file terraform
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/d8fa6242-eea3-4a64-911c-a22dd70bd3ad)

kemudian pada terminal masuk ke direktori file terraform untuk versi terraform nya
```
cd .\Downloads\terraform_1.6.6_windows_386\
```
```
terraform --version
```
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/55821565-fa58-469d-8cc3-80b7539fcbc8)

## Install aws cli pada lokal windows
https://aws.amazon.com/cli/
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/67ad32d6-5e11-46bf-92ce-a6500f257b16)

setelah file di download lalu install file exe dan jalankan perintah pada terminal
```
aws --version
```
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/6c377288-f0b5-4895-8dff-daa0f21c54f7)

```
aws configure
```
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/bb05d597-85fa-49cb-a410-84851e896e24)

masukan Access Key ID, Secret Access Key yang di dapat dari user aws yang telah di buat
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/9b4a4478-00ed-43fe-b87f-b51d1a6393fc)

sesuaikan Default region name yang biasa kita pakai
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/562691e4-0f82-4179-83f2-2c7cdd3b036c)

```
aws sts get-caller-identity
```
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/14ec202c-a0c3-4e60-9e7e-b351cc8f1d69)

cek informasi config aws yang telah dibuat di lokal windows

## baut server instansi menggunakan terraform
buat file main.tf di direktori file terraform
```
provider "aws" {
    region  = "us-east-1" # AWS region
}

resource "aws_vpc" "main" { 
  cidr_block = "10.0.1.0/24" # For Private IP assignment
  tags = {
      Name = "tuts vpc" # tags are optional
  }
}

resource "aws_subnet" "web" {
    vpc_id = aws_vpc.main.id
    cidr_block = "10.0.1.0/24" # For Private IP assignment
    tags = {
        Name = "web-subnet"
    }
}

# Instansi 1 di Subnet
resource "aws_instance" "instance1" {
  ami           = "ami-09e67e426f25ce0d7" # AMI ID Ubuntu 20.04
  instance_type = "t2.micro"
  subnet_id     = aws_subnet.web.id
}

# Instansi 2 di Subnet
resource "aws_instance" "instance2" {
  ami           = "ami-09e67e426f25ce0d7" # AMI ID Ubuntu 20.04
  instance_type = "t2.micro"
  subnet_id     = aws_subnet.web.id
}
```
masih pada terminal direktori terraform jalankan perintah
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/4f996498-f76d-49d9-8d53-08e6236dafb2)
```
.\terraform init
```
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/ea2da956-c8e2-4cc7-87b1-f972018046cc)
```
.\terraform plan
```
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/6866b687-f795-4f1a-b469-7e49834071dc)

```
.\terraform apply
```
![image](https://github.com/wilsonakbar/Tasks-Dumbways-WilsonAkbar/assets/132327628/67f66fa2-31b4-49ac-9262-2d47be334e68)
2 server instansi sukses di buat
```
```
