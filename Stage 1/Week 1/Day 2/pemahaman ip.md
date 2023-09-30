# Basic Shell & Computer Networking
 ## 1. Perbedaan antara IP Private & Public, serta IP Dynamic & Static
     
     IP Private
         Diberikan oleh ISP 
         Ruang lingkup global 
         Tidak gratis 
         Bisa terhubung ke internet secara keseluruhan 
         Setiap nomor IP unik dan tak bisa digunakan oleh pihak lain
         Kurang aman karena dapat dilihat secara online
         Tidak membutuhkan network translation apapun untuk terhubung ke internet

     IP Public
         Diberikan oleh lokal administrator IT
         Ruang lingkup lokal
         Didapatkan secara gratis
         Tidak bisa terhubung ke internet secara keseluruhan
         Setiap nomor IP tidak unik dan bisa digunakan berulang dengan jaringan lokal lain
         Lebih aman karena hanya tersedia pada jaringan lokal
         Untuk terhubung ke internet/public membutuhkan NAT

     IP Static
         Ditetapkan manual pada sebuah perangkat untuk durasi yang lama
         IP yang di dedicated ke sebuah PC/Server, atau perangkat networking lainnya (misal router) sehingga IP nya tidak berubah ubah
         Biasa di gunakan untuk bisnis
         Penggunakan ip nya berbayar
     
      IP Dynamic
         Memiliki durasi yang singkat karena berubah setiap kali perangkat dimatikan ulang atau dikonfigurasi
         IP yang didapatkan oleh computer/router lain dari system DHCP, IP dynamic biasanya berubah-ubah
         Biasa di gunakan untuk kantor atau rumahan
         Penggunakan ip nya gratis

##  2. Buat rancangan sebuah jaringan dengan spesifikasi sebagai berikut!
        - CIDR Block : 192.168.1.xxx/24
        - Subnet : 255.255.255.0
        - Gateway : 192.168.1.1

        Rancangan Jaringan
          Subnet 1 : 192.168.1.0
              IP Network : 192.168.1.1
              Host pertama : 192.168.1.2
              Host terakhir : 192.168.1.62
              IP Broadcast : 192.168.1.63
          Subnet 2 : 192.168.1.64
              IP Network : 192.168.1.65
              Host pertama : 192.168.1.66
              Host terakhir : 192.168.1.126
              IP Broadcast : 192.168.1.127
          Subnet 3 : 192.168.1.128
              IP Network : 192.168.1.129
              Host pertama : 192.168.1.130
              Host terakhir : 192.168.1.191
              IP Broadcast : 192.168.1.192
          Subnet 4 : 192.168.1.192
              IP Network : 192.168.1.193
              Host pertama : 192.168.1.194
              Host terakhir : 192.168.1.254
              IP Broadcast : 192.168.1.255

##  3. Gunakan app.diagrams.net untuk membuat diagramnya, Referensi gambar sudah disertakan
   ![Diagram Tanpa Judul (1)](https://github.com/wilsonakbar/devops18-dumbways-WilsonAkbar/assets/132327628/4f679c34-c888-41a2-bcb5-9c653aa3288d)

