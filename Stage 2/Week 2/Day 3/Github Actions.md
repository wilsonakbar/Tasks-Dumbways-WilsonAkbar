# CI/CD
## Using GitlabCI, create a pipeline running
buat repository fe dan be pada gitlab
![Screenshot_29](https://github.com/wilsonakbar/Final-Task-Dumbways-WilsonAkbar/assets/132327628/1989bbef-9214-4706-8fcb-070cee151fcf)
buat pipeline pada gitlab di masing-masing branch staging dan production
![Screenshot_30](https://github.com/wilsonakbar/Final-Task-Dumbways-WilsonAkbar/assets/132327628/3d556b5f-2aab-4bb7-a975-f98af20cc38e)

```
stages:
  - repository_pull
  - build_push
  - test
pull:
  stage: repository_pull
  before_script:
    - command -v ssh-agent >/dev/null || ( apk add --update openssh )
    - eval $(ssh-agent -s)
    - echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add -
    - mkdir -p ~/.ssh
    - chmod 700 ~/.ssh
    - ssh-keyscan $VM_ADDRESS >> ~/.ssh/known_hosts
    - chmod 644 ~/.ssh/known_hosts
  script:
    - ssh $SSH_USER@$VM_ADDRESS "cd ~/fe-dumbmerch && git checkout Production && git pull origin Production"
build_push:
  stage: build_push
  image: docker:1.11
  services:
    - docker:dind
  script:
    - export DOCKER_HOST=tcp://docker:2375/
    - docker version
    - docker build -t wilsonakbar/fe-dumbmerch-production:latest .
    - docker login -u wilsonakbar -p $PASS_DOCKER
    - docker push wilsonakbar/fe-dumbmerch-production:latest
test:
  stage: test
  before_script:
    - command -v ssh-agent >/dev/null || ( apk add --update openssh )
    - eval $(ssh-agent -s)
    - echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add -
    - mkdir -p ~/.ssh
    - chmod 700 ~/.ssh
    - ssh-keyscan $VM_ADDRESS >> ~/.ssh/known_hosts
    - chmod 644 ~/.ssh/known_hosts
  script:
    - ssh $SSH_USER@$VM_ADDRESS "cd ~/fe-dumbmerch && git checkout Production && docker compose up -d"
```
kemudian commite changes
![Screenshot_37](https://github.com/wilsonakbar/Final-Task-Dumbways-WilsonAkbar/assets/132327628/6619df97-5a0e-4af6-af2c-c81eec9f08fc)
kemudian jika hijau seperti ini pipelines berhasil
![Screenshot_31](https://github.com/wilsonakbar/Final-Task-Dumbways-WilsonAkbar/assets/132327628/a2f50f78-dd3f-4b83-99ec-7d5dec3c444f)
images berhasil di build dan push ke dockerhub
![Screenshot_40](https://github.com/wilsonakbar/Final-Task-Dumbways-WilsonAkbar/assets/132327628/fd37907f-1556-4f25-9542-b7f68dae9a7c)
![Screenshot_38](https://github.com/wilsonakbar/Final-Task-Dumbways-WilsonAkbar/assets/132327628/ca8bb325-42c3-4162-8e83-6a9047088f7a)
![Screenshot_39](https://github.com/wilsonakbar/Final-Task-Dumbways-WilsonAkbar/assets/132327628/1cc54f33-3a67-4c73-a05c-9696599c8bbe)
aplikasi berhasil dijalankan
