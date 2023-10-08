# Monitoring
## Tasks :
- Setup node-exporter, prometheus dan Grafana menggunakan docker
- install node-exporter di appserver & gateway
- Dengan Grafana, buatlah :
    -  Dashboard untuk monitor resource server (CPU, RAM & Disk Usage)
    -  Buat alerting dengan Contact Point pilihan kalian (discord, telegram, slack dkk)
    -  Untuk alert :
         - CPU Usage over 20%
         - RAM Usage over 75%

Docker Images :
[node-exporter](https://hub.docker.com/r/prom/node-exporter)
[Prometheus](https://hub.docker.com/r/prom/prometheus)
[Grafana Dashboard](https://hub.docker.com/r/grafana/grafana)

## Setup node-exporter, prometheus dan Grafana menggunakan docker
### install node-exporter dengan perintah seperti berikut
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/969903b9-9213-4c7f-b7f1-c741bda36fe0)
docker run -d -p 9100:9100 --name node-exporter bitnami/node-exporter:latest
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b22686c2-1010-4253-ae22-84aa3e7d341a)
jalankan node pada browser dengan ip http://103.127.97.70:9100/

### install prometheus dengan perintah seperti berikut
pertama buat direktori monitoring lalu buat file prometheus.yml
```
---
global:
  scrape_interval: 15s
scrape_configs:
  - job_name: appserver
    static_configs:
      - targets:
          - 103.127.97.68:9100
        labels:
          instance: appserver
  - job_name: gateway
    static_configs:
      - targets:
          - 103.127.97.70:9100
        labels:
          instance: gateway
```
lalu jalankan dengan perintah
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/54ce0fee-0648-4f70-b36e-7e2bc0edd1ec)
```
docker run -d -p 9090:9090 --name prometheus \
    -v ~/monitoring/prometheus.yml:/opt/bitnami/prometheus/conf/prometheus.yml \
    bitnami/prometheus:latest
```
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/da152cde-5628-44c1-ad3e-894425af222d)
buka prometheus pada browser dengan ip http://103.127.97.68:9090/

### install grafana dengan perintah seperti berikut
```
docker run -d --name=grafana -p 5000:3000 grafana/grafana
```
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2982d677-a3a5-4de6-accf-acbdf3cb6d4d)
buka prometheus pada browser dengan ip http://103.127.97.70:5000/

### Dashboard untuk monitor resource server (CPU, RAM & Disk Usage)
pertama kita buat data sources nya untuk menghubungkan prometheus dengan grafana
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/8c1ad3ef-1bef-4328-98ca-19a7cdf5344d)
pilih prometheus
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/f9a1713f-8b0b-4677-8c69-90afbbd42a9b)
pada HTTP masukan ip prometheus http://103.127.97.70:9090/
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/b6175a78-b512-4bed-8a97-11da400f8445)
kemudian save & test
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/4fd500c6-0ac7-4ac2-a207-f4925623c5db)

buat panel untuk menampilkan CPU Usage dengan query lalu run query kemudian ini nama panel dan apply agar diagram muncul pada dasboard
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/36be93ec-96fb-403f-b45d-8874aba83b3f)
```
100 - (avg by (instance) (irate(node_cpu_seconds_total{job="gateway",mode="idle"}[5m])) * 100)
```
buat panel untuk menampilkan RAM Usage dengan query lalu run query kemudian ini nama panel dan apply agar diagram muncul pada dasboard
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/554a6545-d93f-4d50-aebb-78c4b229e38c)
```
100 * (1 - ((avg_over_time(node_memory_MemFree_bytes{job="gateway"}[10m]) + avg_over_time(node_memory_Cached_bytes{job="gateway"}[10m]) + avg_over_time(node_memory_Buffers_bytes{job="gateway"}[10m])) / avg_over_time(node_memory_MemTotal_bytes{job="gateway"}[10m])))
```
buat panel untuk menampilkan DISK Usage dengan query lalu run query kemudian ini nama panel dan apply agar diagram muncul pada dasboard
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/ddaf95d8-7d47-4a63-8a38-8d35bc6c9a88)
```
100 - (node_filesystem_avail_bytes{job="gateway"} / node_filesystem_size_bytes{job="gateway"} * 100)
```
