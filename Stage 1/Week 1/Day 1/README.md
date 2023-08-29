# Introduction to DevOps
## 1. Definisi DevOps
          DevOps merupakan singkatan dari dua kata yaitu Development dan Operation. Di mana kedua kata tersebut bermakna “operasional pengembang”. Seperti yang disebutkan sebelumnya, DevOps adalah sebuah prinsip developer untuk mengkoordinasikan antar tim yaitu tim development dengan tim operations dengan efektif dan efisien

## 2. Sebutkan lifecycle DevOps (Continuous) dan jelaskan definisi-definisinya!
          Plan : Proses perencanaan untuk seluruh alur kerja yang dibutuhkan sebelum developers mulai menulis kode program.
          Code : Proses ini merupakan tahap dimana developers mulai menulis kode yang dibutuhkan untuk membuat suatu produk.
          Build : Aplikasi yang sudah siap untuk masuk ke tahap pengujian, akan langsung di build supaya dapat mengetahui apakah kode tersebut masih terdapat error atau sudah layak masuk ke divisi tester.
          Test : Merupakan tahap pengujian fungsional aplikasi secara internal. Jika pada proses tersebut terdapat masalah fungsionalitas, maka akan dilaporkan ke tim developer untuk diperbaiki.
          Realese : Setiap perubahan kode yang telah melewati serangkaian pengujian dan dinyatakan lolos, maka developers akan membuat sebuah release versi dari produk tersebut.
          Deploy : Release versi pada tahap sebelumnya akan digunakan untuk dijalankan ke server, sehingga dapat digunakan oleh orang lain (publik).
          Operate : Aplikasi yang sudah selesai dijalankan pada server, maka dapat digunakan secara publik. Dan memastikan bahwa tidak ada masalah ketika di akses baik dari HP ataupun komputer.
          Monitor : Tim Operations akan melakukan pemantauan infrastruktur, sistem, dan aplikasi. Hal ini dilakukan untuk memastikan bahwa produk atau aplikasi yang dikembangkan dapat berjalan dengan lancar.
          
## 3. Instalasi Ubuntu 20.04.6 LTS Live Server menggunakan VM UTM
1. pilih bahasa
![Screenshot_1](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/5e79f520-4745-472f-a9f2-fb72a900b0ff)
2. pilih bahasa untuk layout keyboard
![Screenshot_2](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c084b1c2-264b-404a-806d-53ad74588fda)
3. setting ip statis sesuai pada ipconfig di komputer lalu samakan dengan virtual ubuntu
![Screenshot_3](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/fa225e4c-5001-481f-8d7b-49ac0d0eea5e)
4. setelah selesai pilih done
![Screenshot_4](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/515b26bb-edd6-4407-8c83-1d4a7f71dc0d)
5. skip pada bagian setting proxy address
![Screenshot_5](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/6429ffef-861d-4ce2-8557-4026f50677c6)
6. skip pada bagian mirror address
![Screenshot_6](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c23c1b4a-b1d2-4dc0-a698-8d6a290f3378)
7. kemudian pilih continue without updating
![Screenshot_7](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/c822bcdd-2767-45c8-90b1-611716613e60)
8. kemudian kita kostum partisi untuk ubuntu
![Screenshot_8](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/d632eab6-7b20-4572-b3cc-3356bd5f07d7)
9. pilih size 15G untuk partisi utama “/”
![Screenshot_9](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/2959f174-9301-4706-9fcd-7a9a38958942)
10. kemudian pilih 4G untuk partisi berikutnya dengan format SWAP
![Screenshot_10](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/66cec731-47b8-479e-b914-a6697f5c195e)
11. kemudian lanjut tahap selanjut nya dengan klik done
![Screenshot_11](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/163db4fd-63d8-408e-b724-44a342b592ab)
12. kemudian buat server name dan password sesuai kolom
![Screenshot_12](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/94bc9916-5f76-4e49-9154-52ceea527bc9)
13. kemudian ceklis pada bagian install openSSH server
![Screenshot_13](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/097ba2bc-421a-4e34-95f0-cd358ddc720b)
14. kemudian tunggu proses install ubuntu sampai selesai
![Screenshot_14](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/e635e2c2-1b37-49bd-bd7f-66791b109ff1)
15. setelah install selesai pilih restart kemudian login dengan username dan password yang sudah di buat
![Screenshot_15](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/698623a0-34c4-4ca8-a28a-da2f331edd6b)
16. ini adalah tampilan awal setelah login “wilson@server:~$
![Screenshot_16](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/1cf814c6-14ea-422c-af01-47c1379d5b03)
17. kemudian test ping 8.8.8.8 pada google untuk mengecek apakah ubuntu tersambung dengan koneksi internet
![Screenshot_17](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/677d81f9-1e95-415f-a338-56bf589a27b6)
