# Kelompok
## Anggota
Anggota :
* Wilson - ()
* [Ihkam Audito] - (https://github.com/DitoIhkam/devops17-dumbways-ihkam-audito/blob/eb1a211354d6126e6ef722b8466a96a030391dc4/Stage%202/Week%202%20Kelompok%20Docker.md)
* [Jerry] - ()
"CICD - NEO Lite SS2.2

1. Jalankan Jenkins on top Docker
2. Pipeline untuk frontend & backend
     - Pull dari repository
     - Dockerize aplikasi kita
     - Deploy aplikasi on top Docker
     - Push ke Docker Hub
3. Reverse Proxy & SSL Certificate untuk domain aplikasi
4. Aplikasi hanya di appserver, dan hanya ada Jenkins di CICD
5. Auto-Trigger build pipeline setiap push di github

Challenge
- Repository Private
- Push Notification melalui discord, telegram atau app pilihan kalian
- Untuk Gitlab, tambahkan server CI/CD ke Gitlab-runner"						
## 1. Jalankan Jenkins on top Docker
### 1.1 buat file docker kompose
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/0ffd0719-8a69-47d9-8e66-d0f37e284685)
```
nano docker-compose.yml
```
buat perintah seperti ini
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e7c57a2f-b026-40f2-a1ad-623062f9a572)
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
jalankan docker kompose
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2b59120e-30d1-425a-8570-8e9449234902)
```
docker compose up -d
```
### 2.1 Reverse Proxy & SSL Certificate untuk domain aplikasi
pada server gateway kita setting proxy dan juga domain nya
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2a7bb83f-be8f-408d-a219-1249f3fec014)
```
cd /etc/nginx/sites-enabled/
```
```
sudo nano rproxy.conf
```
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c95f071b-f00a-452f-936e-bc2b19df222d)
```
server {
    server_name jen33.studentdumbways.my.id;

    location / {
             proxy_pass http://103.127.97.68:8080;
    }
}
```
buat dns pada cloudflare
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/59b9f1ef-ad2b-442a-bbda-0fa37fc56ad0)
```
https://dash.cloudflare.com/
```
kembali ke server gateway kita jalankan ulang nginx nya
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/84ceba2d-1606-437f-9d28-6467f3067c6d)
```
sudo nginx -t
```
```
sudo systemctl reload nginx
```
setelah itu kita setting http menjadi https
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ba560717-eff0-4ec2-b7a7-152f60115580)
```
sudo apt install snapd
```
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2b911db5-ff23-4a74-ad5d-9ba08716a35f)
```
sudo snap install --classic certbot
```
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/df5dba4f-9bb4-45d7-a8fb-0151c3eb42fd)
```
sudo ls -s /snap/bin/certbot /user/bin/certbot
```
pada bagian ini kita pilih domain mana yang mau di setting SSL Certificate
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1a06743a-855a-47a4-b729-6b1644703bbc)
```
sudo certbot --nginx
```
jika berhasil file rproxy.conf akan berubah seperti ini
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6e8176a4-3321-478f-8a5d-b7af9309ac8d)
```
server {
    server_name jen33.studentdumbways.my.id;

    location / {
             proxy_pass http://103.127.97.68:8080;
    }


    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/jen33.studentdumbways.my.id/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/jen33.studentdumbways.my.id/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}
server {
    if ($host = jen33.studentdumbways.my.id) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


    server_name jen33.studentdumbways.my.id;
    listen 80;
    return 404; # managed by Certbot
```
### 3.1 jalankan jenkins pada web dengan domain yang telah kita buat
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ea88a9b4-ba9a-4820-9e93-daeb5fd365e5)
```
https://jen33.studentdumbways.my.id/
```
masukan password yang kita dapat dari dalam file
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/55c31dde-8d5f-4655-afa3-043625c1b407)
```
/var/jenkins_home/secrets
```
pilih install suggested plugins
![Screenshot_15](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/92ee3ca8-01de-4d54-ad83-dc306e04c781)
tunggu hasil installasi
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f52eabcc-fe0f-490c-9716-2bc42161d419)
buat username dan password baru untuk login jenkins nya
![Screenshot_17](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ae8288b7-4e0f-4c9e-98b1-78185b26a188)
masukan url domain yang telah kita buat sebelum nya
![Screenshot_18](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/18bb7247-e7de-4f2c-a557-cb4ef74afa72)
```
https://jen33.studentdumbways.my.id/
```
jenkin sudah berhasil di install
![Screenshot_19](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/79359c11-a536-4811-85d6-6ced26fd4500)
### 4.1 sambungkan jenkins dengan appserver wayshub-frontend danwayshub-backend
pada manage jenkins pilih credentials
![Screenshot_20](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ef3583dc-b8e7-4c96-9df7-4570ad2f1c2a)
kemudian pilih system
![Screenshot_21](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f79ab359-3986-42b3-9f5f-a0f0601c4796)
pilih global credentials
![Screenshot_22](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a1848939-3a2b-40ce-89aa-09d92cb1aa5c)
add credentials
![Screenshot_23](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/10a8975d-d0e9-440b-a1b8-502e182132d7)
pilih SSH username with private key, isi username sesuai appserver yang ingin di sambungkan
![Screenshot_24](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/0515bafa-38a1-4d75-bbda-23b92fd71029)
salin private key yang ada pada pc kalian
![Screenshot_25](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1a6089d4-3b0e-4eac-8846-798fbf534802)
credentials berhasil di buat
![Screenshot_26](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/81597e7b-36fe-4043-b0d7-3443ff326c23)
jangan lupa tambahkan SSH Agent pada plugin dan install
![Screenshot_27](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/a6de6cb5-2732-46ba-a649-38579cec004a)
plugin SSH Agent berhasil ditambahkan
![Screenshot_28](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/db8a3ee5-ad8b-4ee2-a2eb-aecb46a1daaa)
### 5.1 Pipeline untuk frontend & backend
buat file jenkins pada frontend
![Screenshot_37](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2a127652-ca15-4732-a18b-f16f07f62a8c)
```
cd wayshub-frontend
```
```
nano Jenkinsfile
```
![Screenshot_38](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1aa159d2-6e94-4ecd-8ed7-2cdf04ab865b)
```
def branch = "main"
def repo = "https://github.com/wilsonakbar/wayshub-frontend.git"
def cred = "ditoihkam"
def dir = "~/wayshub-frontend"
def server = "ditoihkam@103.175.221.143"
def imagename = "wayshub-fe"
def dockerusername = "wilsonakbar"

pipeline {
    agent any

    stages {
        stage('Pull From Repository') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        git remote add origin ${repo} || git remote set-url origin ${repo}
                        git pull origin ${branch}
                        exit
                        EOF
                    """
                }
            }
        }

    stage('Dockerize') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        docker build -t ${imagename}:latest .
                        exit
                        EOF
                    """
                }
            }
        }

        stage('Deploy Docker') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        docker container stop ${imagename}
                        docker container rm ${imagename}
                        docker run -d -p 3000:3000 --name="${imagename}"  ${imagename}:latest
                        docker container stop ${imagename}
                        docker container rm ${imagename}
                        exit
                        EOF
                    """
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
               sshagent([cred]) {
                            sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                                    docker tag ${imagename}:latest ${dockerusername}/${imagename}:latest
                                    docker image push ${dockerusername}/${imagename}:latest
                                    docker image rm ${dockerusername}/${imagename}:latest
                                    docker image rm ${imagename}:latest
                                    exit
                    EOF
                        """
                        }
            }
        }
    }
}
```
buat Pipeline pada jenkins
![Screenshot_29](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/66a8f466-6d38-45b8-8733-e8bfacf5ef8e)
masukan nama frontend lalu pilih Pipeline
![Screenshot_30](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d0101351-c5c2-4194-864c-93fe3b109229)
ceklis github hook trigger
![Screenshot_31](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c258549c-04c0-4c1a-be9f-8e36aec5db6c)
isi file repositori dengan url github
![Screenshot_32_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f157d5f3-bbf2-494e-8479-9e313dd7a69a)
pilih branch main dan apply

lakukan hal yang sama pada direktori backend seperti cara di atas
dengan file jenkins backend
```
def branch = "main"
def repo = "https://github.com/wilsonakbar/wayshub-backend.git"
def cred = "ditoihkam"
def dir = "~/wayshub-backend"
def server = "ditoihkam@103.175.221.143"
def imagename = "wayshub-be"
def dockerusername = "wilsonakbar"

pipeline {
    agent any

    stages {
        stage('Pull From Repository') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        git remote add origin ${repo} || git remote set-url origin ${repo}
                        git pull origin ${branch}
                        exit
                        EOF
                    """
                }
            }
        }

    stage('Dockerize') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        docker build -t ${imagename}:latest .
                        exit
                        EOF
                    """
                }
            }
        }

        stage('Deploy Docker') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        docker container stop ${imagename}
                        docker container rm ${imagename}
                        docker run -d -p 5000:5000 --name="${imagename}"  ${imagename}:latest
                        docker container stop ${imagename}
                        docker container rm ${imagename}
                        exit
                        EOF
                    """
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
               sshagent([cred]) {
			    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
				    docker tag ${imagename}:latest ${dockerusername}/${imagename}:latest
				    docker image push ${dockerusername}/${imagename}:latest
				    docker image rm ${dockerusername}/${imagename}:latest
				    docker image rm ${imagename}:latest
				    exit
                    EOF
			"""
		        }
            }
        }
    }
}
```
kemudian buat Pipeline sama seperti setingan di atas dengan nama backend
jalankan buiild now pada masing masing pipe
![Screenshot_39](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9a24598c-82e8-40a5-b01f-1bd2ecbd7b0e)
![Screenshot_40](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/fd6fa2a4-f0b7-4af9-87fa-705cbaba6540)
jika sukses stage view akan berwarna hijau
![Screenshot_41](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/9de4fc20-cba5-4ac8-92e3-cff1e13cef51)
file berhasil di upload ke dockerhub





## 1. Challenge
### 1.1 Repository Private
![Screenshot_32](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b6ed3d3d-b5ee-4f58-a429-fc498f9c2661)
pada repository url salin SSH Github
![Screenshot_33](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/5e47e337-432a-4580-9a1d-515a4f899171)
bagian setting security
![Screenshot_34](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/af574039-c8c9-47bf-a7de-afc6958d3c4a)
host key nya pilih accept first connection
![Screenshot_35](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/4433f448-8745-49e6-aa56-d94bdd8c52ef)
kemudian pada bagian ssh keys kita masukan kuci ssh server kita
![Screenshot_36](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d888ffdd-35f6-476a-b0ec-a1ba64947caa)
















