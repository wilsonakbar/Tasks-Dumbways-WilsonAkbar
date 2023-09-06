# NodeJS BASH Script
## 1. Install nodeJS using BASH Script
### 1.1 pertama buat file script.sh
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2e5bba22-f0cc-48c2-a21f-0dfb10a968f1)
```
nano script.sh
```
### 1.2 kemudian buat perintah seperti berikut
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6f2abcbc-d7e3-4414-bcd2-646adaa3b7e7)
```
#!/usr/bin/env bash

sudo apt update
sudo apt install nodejs -y
node -v
sudo apt install npm -y
```
### 1.3 jalankan Script dengan perintah
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ba7cd414-a65c-4ba0-8f67-3ff02d6586ef)
```
sh script.sh
```
