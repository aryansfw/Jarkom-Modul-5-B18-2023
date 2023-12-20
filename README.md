# Jarkom-Modul-5-B18-2023
## Kelompok B18

|          Nama          |    NRP     |
| :--------------------: | :--------: |
|  Aryan Shafa Wardana   | 5025211031 |
| Shazia Ingeyla Naveeda | 5025211203 |

## Topologi

Berikut adalah gambar topologi yang digunakan.

![image](https://github.com/aryansfw/Jarkom-Modul-5-B18-2023/assets/114483889/e0448dcd-6731-4db4-b98b-d7c1f0c89d47)

[Sheets Perhitungan](https://docs.google.com/spreadsheets/d/17HEXDpGCzPmVEg1rM2y2JPe2_mbWf-D7G7KvcbQHRxE/edit#gid=671499381)

## Rute

Berikut adalah pembagian subnet dan rutenya untuk topologi yang kami gunakan

![image](https://github.com/aryansfw/Jarkom-Modul-5-B18-2023/assets/114483889/07d85743-c26a-405f-8917-4ac8b21a5acc)


### Pohon VLSM

Dari subnet-subnet tersebut, kita bisa membuat pohon VLSM yang digunakan untuk menentukan pembagian IP pada node-node dalam topologi seperti berikut.

![TREE - VLSM (3)](https://github.com/aryansfw/Jarkom-Modul-5-B18-2023/assets/114483889/5c93e432-34d5-449c-b0af-5e3c3371b340)


### Pembagian IP CIDR

Pembagian NID, netmask, dan broadcast dapat ditabelkan seperti pada tabel berikut.

![image](https://github.com/aryansfw/Jarkom-Modul-5-B18-2023/assets/114483889/5732b1f0-a4d1-42f6-90d1-db4371b79603)

- **Konfigurasi dan Routing**

Setelah mendapatan NID, Netmask dan Broadcast lakukan konfigurasi dan juga routing. Berikut Konfigurasi dan Routing pada setiap node.

**ROUTER**
- AURA

```sh
auto eth0
iface eth0 inet dhcp

#A1
auto eth1
iface eth1 inet static
	address 192.187.0.1
	netmask 255.255.255.252

#A4
auto eth2
iface eth2 inet static
	address 192.187.0.5
	netmask 255.255.255.252

# Lewat Heiter
up route add -net 192.187.4.0 netmask 255.255.252.0 gw 192.187.0.2
up route add -net 192.187.8.0 netmask 255.255.248.0 gw 192.187.0.2

# Lewat Frieren
up route add -net 192.187.0.16 netmask 255.255.255.252 gw 192.187.0.6
up route add -net 192.187.0.20 netmask 255.255.255.252 gw 192.187.0.6
up route add -net 192.187.2.0 netmask 255.255.254.0 gw 192.187.0.6
up route add -net 192.187.0.128 netmask 255.255.255.128 gw 192.187.0.6
up route add -net 192.187.0.24 netmask 255.255.255.252 gw 192.187.0.6
up route add -net 192.187.0.28 netmask 255.255.255.252 gw 192.187.0.6
```

- HEITER
```sh
#A1
auto eth0
iface eth0 inet static
	address 192.187.0.2
	netmask 255.255.255.252
	gateway 192.187.0.1

#A2
auto eth1
iface eth1 inet static
	address 192.187.8.1
	netmask 255.255.248.0

#A3
auto eth2
iface eth2 inet static
	address 192.187.4.1
	netmask 255.255.252.0
```

- FRIEREN
```sh
#A4
auto eth0
iface eth0 inet static
	address 192.187.0.6
	netmask 255.255.255.252
	gateway 192.187.0.5

#A5
auto eth1
iface eth1 inet static
	address 192.187.0.17
	netmask 255.255.255.252

#A6
auto eth2
iface eth2 inet static
	address 192.187.0.21
	netmask 255.255.255.252

# Lewat Himmel
up route add -net 192.187.2.0 netmask 255.255.254.0 gw 192.187.0.22
up route add -net 192.187.0.128 netmask 255.255.255.128 gw 192.187.0.22
up route add -net 192.187.0.24 netmask 255.255.255.252 gw 192.187.0.22
up route add -net 192.187.0.28 netmask 255.255.255.252 gw 192.187.0.22
```

- HIMMEL
```sh
#A6
auto eth0
iface eth0 inet static
	address 192.187.0.22
	netmask 255.255.255.252
	gateway 192.187.0.21

#A7
auto eth1
iface eth1 inet static
	address 192.187.2.1
	netmask 255.255.254.0

#A8
auto eth2
iface eth2 inet static
	address 192.187.0.129
	netmask 255.255.255.128

# Lewat Fern
up route add -net 192.187.0.24 netmask 255.255.255.252 gw 192.187.0.131
up route add -net 192.187.0.28 netmask 255.255.255.252 gw 192.187.0.131
```

- FERN
```sh 
#A8
auto eth0
iface eth0 inet static
	address 192.187.0.131
	netmask 255.255.255.128
	gateway 192.187.0.129

#A9
auto eth1
iface eth1 inet static
	address 192.187.0.25
	netmask 255.255.255.252

#A10
auto eth2
iface eth2 inet static
	address 192.187.0.29
	netmask 255.255.255.252
```
**DNS SERVER**
- Ritcher 
```sh
auto eth0
iface eth0 inet static
	address 192.187.0.26
	netmask 255.255.255.252
	gateway 192.187.0.25
```
**DHCP SERVER**
- Revolte
```sh
auto eth0
iface eth0 inet static
	address 192.187.0.30
	netmask 255.255.255.252
	gateway 192.187.0.29
```

**WEB SERVER**
- Sein
```sh
#A3
auto eth0
iface eth0 inet static
	address 192.187.4.2
	netmask 255.255.252.0
	gateway 192.187.4.1
```

- Stark
```sh 
#A5
auto eth0
iface eth0 inet static
	address 192.187.0.18
	netmask 255.255.255.252
	gateway 192.187.0.17
```

**CLIENT**
- TurkRegion
```sh
auto eth0
iface eth0 inet dhcp
```

- GrobeForest
```sh
auto eth0
iface eth0 inet dhcp
```

- LaubHills 
```sh
auto eth0
iface eth0 inet dhcp
```

- SchwerMountain
```sh
auto eth0
iface eth0 inet dhcp
```

Kemudian, client memperoleh IP dari DHCP server yaitu node Revolte. DHCP server perlu install isc-dhcp-server menggunakan

```bash
apt-get update
apt-get install isc-dhcp-server -y
```

Lalu pada file `/etc/default/isc-dhcp-server` seperti berikut.

```bash
INTERFACESv4="eth0"
INTERFACESv6=""
```

serta file `/etc/dhcp/dhcpd.conf` seperti berikut.

```bash
subnet 192.187.0.0 netmask 255.255.255.252 {
}

subnet 192.187.8.0 netmask 255.255.248.0 {
        range 192.187.8.2 192.187.15.254;
        option routers 192.187.8.1;
        option broadcast-address 192.187.15.255;
}

subnet 192.187.4.0 netmask 255.255.252.0 {
        range 192.187.4.2 192.187.7.254;
        option routers 192.187.4.1;
        option broadcast-address 192.187.7.255;
}

subnet 192.187.0.4 netmask 255.255.255.252 {
}

subnet 192.187.0.16 netmask 255.255.255.252 {
}

subnet 192.187.0.20 netmask 255.255.255.252 {
}

subnet 192.187.2.0 netmask 255.255.254.0 {
        range 192.187.2.2 192.187.3.254;
        option routers 192.187.2.1;
        option broadcast-address 192.187.3.255;
}

subnet 192.187.0.128 netmask 255.255.255.128 {
        range 192.187.0.132 192.187.0.254;
        option routers 192.187.0.131;
        option routers 192.187.0.129;
        option broadcast-address 192.187.0.255;
}

subnet 192.187.0.24 netmask 255.255.255.252 {
}

subnet 192.187.0.28 netmask 255.255.255.252 {
}
```

Kemudian kita bisa restart service `isc-dhcp-server` menggunakan

```bash
service isc-dhcp-server restart
```

Lalu pada router-router selain DHCP server dikonfigurasi menjadi DHCP relay. Router tersebut yaitu Fern, Himmel, Frieren, Aura, dan Heiter.	Contohnya pada node Fern, kita bisa install DHCP relay menggunakan

```bash
apt-get update
apt-get install isc-dhcp-relay -y
```

Lalu edit file `/etc/default/isc-dhcp-relay` seperti berikut.

```bash
SERVERS="192.187.0.30"
INTERFACES="eth0 eth1 eth2"
OPTIONS=
```

- `SERVERS` diisi dengan IP DHCP server
- `INTERFACES` diisi dengan interface ethernet yang terhubung dengan router tersebut

Selain itu, kita juga edit file `/etc/sysctl.conf` seperti berikut.

```conf
net.ipv4.ip_forward=1
```

Lalu kita restart service menggunakan

```bash
service isc-dhcp-relay restart
```

Konfigurasi dilakukan untuk setiap DHCP relay. Contoh hasil DHCP adalah sebagai berikut. Bisa dilihat node SchwerMountains memperoleh IP lease 192.187.0.132. Ini berarti DHCP sudah jalan.

![schwer mountain ip](https://github.com/aryansfw/Jarkom-Modul-5-B18-2023/assets/115603634/73cac070-ffaf-435a-a876-466658c05604)

## **Soal Nomor 1**
Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE.

### **Penyelesaian Nomor 1**



## **Soal Nomor 2**
Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.

### **Penyelesaian Nomor 2**


## **Soal Nomor 3**
Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.

### **Penyelesaian Nomor 3**


## **Soal Nomor 4**
Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.

### **Penyelesaian Nomor 4**


## **Soal Nomor 5**
Selain itu, akses menuju WebServer hanya diperbolehkan saat jam kerja yaitu Senin-Jumat pada pukul 08.00-16.00.

### **Penyelesaian Nomor 5**


## **Soal Nomor 6**
Lalu, karena ternyata terdapat beberapa waktu di mana network administrator dari WebServer tidak bisa stand by, sehingga perlu ditambahkan rule bahwa akses pada hari Senin - Kamis pada jam 12.00 - 13.00 dilarang (istirahat maksi cuy) dan akses di hari Jumat pada jam 11.00 - 13.00 juga dilarang (maklum, Jumatan rek).

### **Penyelesaian Nomor 6**


## **Soal Nomor 7**
Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.

### **Penyelesaian Nomor 7**


## **Soal Nomor 8**
Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.

### **Penyelesaian Nomor 8**

## **Soal Nomor 9**
Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir  alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit (clue: test dengan nmap).

### **Penyelesaian Nomor 9**

## **Soal Nomor 10**
Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level. 

### **Penyelesaian Soal Nomor 10**
