# Jarkom-Modul-4-ITA06-2022

## <b> Anggota Kelompok: </b>
1. Anisah Farah Fadhilah - 5027201023
2. Banabil Fawazaim Muhammad - 5027201055
3. Shafira Khaerunnisa - 5027201072
---
## Topologi CPT

![image](https://user-images.githubusercontent.com/76768695/204092344-2c3f3da0-822a-43c8-8ee6-4e5bae5b42f4.png)

#### Catatan
1. Soal shift dikerjakan pada Cisco Packet Tracer dan GNS3 menggunakan metode perhitungan CLASSLESS yang berbeda.
2. Keterangan: Bila di CPT menggunakan VLSM, maka di GNS3 menggunakan CIDR atau Sebaliknya
3. Untuk di GNS3 CLOUD merupakan NAT1 jangan sampai salah agar bisa terkoneksi internet.
4. Pembagian IP menggunakan Prefix IP yang telah ditentukan pada modul pengenalan Pembagian IP dan routing harus SE-EFISIEN MUNGKIN.


## VLSM
Pertama-tama, kami membagi topologi kedalam beberapa bagian subnet

![vlsm_v2](https://user-images.githubusercontent.com/76768695/204092013-2669a7f4-e8ef-49af-811c-8ac13833baf8.png)

Dari hasil pembagian subnet diketahui terdapat sejumlah 18 Subnet

### Perhitungan VLSM
Selanjutnya menghitung jumlah host pada setiap subnet dan netmask yang akan digunakan

![image](https://user-images.githubusercontent.com/76768695/204092120-ec76d776-c364-4d00-9dd8-566bcf182321.png)

Major network nya berada pada netmask /20. Prefix IP kelompok kami adalah 192.212.X.X. Selanjutnya kami membuat pohon perhitungan VLSM

![vlsm_tree](https://user-images.githubusercontent.com/76768695/204092028-f83299fd-6974-482f-b027-4038d70c8cbc.png)

Untuk table perhitungannya sebagai berikut :

![image](https://user-images.githubusercontent.com/76768695/204092164-ffa42a76-dca2-415f-bf6b-121186a7fc47.png)

Selanjutnya memasukkan ip pada setiap node, misal pada subnet A1
```
Subnet A1 : 
    NID : 192.212.0.0
    Netmask : 255.255.252.0
    IP range : 192.212.0.1 - 192.212.3.254
 ```
 
- Kemudian mengatur router
misal pada The Minister terhubung dengan Guideau pada interface `Fa0/0`, maka ip pada interface `Fa0/0` diatur dengan IP range yang tersedia 

![the minister](https://user-images.githubusercontent.com/76768695/204091988-b9056cad-16c2-4257-bf3b-9ffc72033917.PNG)

- Setelah mengatur IP pada The Minister, lalu mengatur IP pada Guideau dengan IP range yang telah tersedia

![guideau](https://user-images.githubusercontent.com/76768695/204091986-21457f63-246e-4210-819e-350c18e0ce85.PNG)

- Setelah subnet A1 berhasil, selanjutnya mengatur IP setiap subnet sampai A18 sesuai hasil perhitungan sebelumnya. 
Karena terlalu banyak, kami hanya mencontohkan pada satu subnet saja. 
Untuk selengkapnya dapat di akses melalui link ini

- Setelah semua Node IP nya sudah diatur, selanjutnya melakukan routing agar semua node saling terhubung. 
Dengan cara masuk pada config ROUTING. kemudian mengisikan Network, Mask, dan Next Hop yang ditujukan. 
Sebagai contoh, pada Router The Order. The order terhubung dengan router The Minister, sehingga konfigurasi pada router The Order yaitu:

![the order](https://user-images.githubusercontent.com/76768695/204091981-5a005fbe-3e02-48c8-b933-c5fee2fac011.PNG)

- Selanjutnya memastikan semua node telah terhubung.

![sukses](https://user-images.githubusercontent.com/76768695/204091976-d32a654e-fcf0-4a7c-8d23-7d3f7190a2bb.PNG)

 
 ## CIDR
 Pertama-tama, kami membuat topologi CIDR menggunakan GNS3 sebagai berikut
 
![image](https://user-images.githubusercontent.com/76768695/204095124-5f6e104e-d228-4a94-8fc3-7235b1050251.png)
 
### Pembagian subnet
- Langkah 1

![SUBNETTIN-I-Gambar drawio - Copy](https://user-images.githubusercontent.com/76768695/204093759-863ceaa1-2ae1-4b85-8e40-bf55d2c755d5.png)

- Langkah 2

![SUBNETTIN-B drawio](https://user-images.githubusercontent.com/76768695/204093774-c2438664-54e1-456a-81a6-db8a8989d5af.png)

- Langkah 3

![SUBNETTIN-C drawio](https://user-images.githubusercontent.com/76768695/204093783-3b87c961-5ccd-499d-abdb-055eff1198ad.png)

- Langkah 4

![SUBNETTIN-D drawio](https://user-images.githubusercontent.com/76768695/204093788-bfe24846-10e1-4fe8-b707-a204706a8ae8.png)

- Langkah 5

![SUBNETTIN-E drawio](https://user-images.githubusercontent.com/76768695/204093790-b14c70f6-774a-47d5-927b-73f756e17ab2.png)

- Langkah 6

![SUBNETTIN-F drawio](https://user-images.githubusercontent.com/76768695/204093800-b13fb9c7-5bac-44f1-a376-b1c19c874d89.png)

- Langkah 7

![SUBNETTIN-G drawio](https://user-images.githubusercontent.com/76768695/204093803-cf056c21-f2e9-4198-b63f-4c72ce91890c.png)

- Langkah 8

![SUBNETTIN-H drawio](https://user-images.githubusercontent.com/76768695/204093806-5f8ca085-cfa7-4de4-9f7b-0ea6ef2925f3.png)

- Hasil subnetting

 ![SUBNETTIN-I drawio](https://user-images.githubusercontent.com/76768695/204093925-5bac7c70-bce6-411b-9549-ee1f66682a0f.png)
 
 ### CIDR Tree
 
![SUBNETTIN-I-Graph drawio](https://user-images.githubusercontent.com/76768695/204094606-2a6a6399-96cd-467e-b0c2-d2ac5c2a6186.png)
 
 ### Setting GNS3
 - The Minister
```
auto eth0
iface eth0 inet static
   address 192.212.8.2
   netmask 255.255.255.252
   brodcast 192.212.8.3
   gateway 192.212.8.1

auto eth1
iface eth1 inet static
   address 192.212.4.1
   netmask 255.255.252.0
   brodcast 192.212.7.255
   gateway 192.212.8.1

auto eth2
iface eth2 inet static
   address 192.212.1.1
   netmask 255.255.255.252
   brodcast 192.212.1.3
   gateway 192.212.8.1
```

 - The Order
```
auto eth0
iface eth0 inet static
   address 192.212.32.2
   netmask 255.255.255.252
   brodcast 192.212.32.3
   gateway 192.212.32.1

auto eth1
iface eth1 inet static
   address 192.212.16.1
   netmask 255.255.255.192
   brodcast 192.212.16.63
   gateway 192.212.32.1

auto eth2
iface eth2 inet static
   address 192.212.8.1
   netmask 255.255.255.252
   brodcast 192.212.8.3
   gateway 192.212.32.1
```
 - The Resonance
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
   address 192.212.32.1
   netmask 255.255.255.252
   brodcast 192.212.32.3

auto eth2
iface eth2 inet static
   address 192.212.98.1
   netmask 255.255.255.252
   brodcast 192.212.98.3

auto eth3
iface eth3 inet static
   address 192.212.80.1
   netmask 255.255.255.252
   brodcast 192.212.80.3

auto eth4
iface eth4 inet static
   address 192.212.100.1
   netmask 255.255.255.252
   brodcast 192.212.100.3
```
 - The Magical
```
auto eth0
iface eth0 inet static
   address 192.212.98.2
   netmask 255.255.255.252
   getaway 192.212.98.1

auto eth1
iface eth1 inet static
   address 192.212.96.1
   netmask 255.255.254.0
   brodcast 192.212.97.255
```
 - The Dauntiess
```
auto eth0
iface eth0 inet static
   address 192.212.1.2
   netmask 255.255.255.252
   brodcast 192.212.1.3
   gateway 192.212.1.1

auto eth1
iface eth1 inet static
   address 192.212.0.1
   netmask 255.255.255.0
   brodcast 192.212.0.255
   gateway 192.212.1.1
```
 - The Instrument
```
auto eth0
iface eth0 inet static
  address 192.212.80.2
  netmask 255.255.255.252
  brodcast 192.212.80.3
  gateway 192.212.80.1

auto eth1
iface eth1 inet static
  address 192.212.74.1
  netmask 255.255.255.128
  brodcast 192.212.74.127
  gateway 192.212.80.1

auto eth2
iface eth2 inet static
  address 192.212.73.1
  netmask 255.255.255.252
  brodcast 192.212.73.3
  gateway 192.212.80.1

auto eth3
iface eth3 inet static
  address 192.212.68.1
  netmask 255.255.255.252
  brodcast 192.212.68.3
  gateway 192.212.80.1
```
 - The Profound
```
auto eth0
iface eth0 inet static
  address 192.212.73.2
  netmask 255.255.255.252
  brodcast 192.212.73.3
  gateway 192.212.73.1

auto eth1
iface eth1 inet static
  address 192.212.72.1
  netmask 255.255.255.128
  brodcast 192.212.72.127
  gateway 192.212.73.1

auto eth2
iface eth2 inet static
  address 192.212.72.129
  netmask 255.255.255.127
  brodcast 192.212.72.255
  gateway 192.212.73.1
```

- Ashaf
```
auto eth0
iface eth0 inet static
   address 192.212.16.2
   netmask 255.255.255.192
   gateway 192.212.16.1
   
```
- The Beast
```
auto eth0
iface eth0 inet static
   address 192.212.100.2
   netmask 255.255.255.252
   gateway 192.212.100.1
 ```
 
 ### Routing
```
 route add -net <NID> netmask <netmask> gw <ip gateway>
```
- resonance (A1,A2,A3,A4,A5, A9, A11,A12,A13,A14,A15,A16,A17,A18)
```
route add -net 192.212.4.0 netmask 255.255.252.0 gw 192.212.32.1
route add -net 192.212.1.0 netmask 255.255.255.252 gw 192.212.32.1
route add -net 192.212.0.0 netmask 255.255.255.0 gw 192.212.32.1
route add -net 192.212.8.0 netmask 255.255.255.252 gw 192.212.32.1
route add -net 192.212.16.0 netmask 255.255.255.192 gw 192.212.32.1

route add -net 192.212.96.0 netmask 255.255.254.0 gw 192.212.98.1

route add -net 192.212.74.0 netmask 255.255.255.128 gw 192.212.80.1
route add -net 192.212.73.0 netmask 255.255.255.252 gw 192.212.80.1
route add -net 192.212.72.0 netmask 255.255.255.128 gw 192.212.80.1
route add -net 192.212.72.128 netmask 255.255.255.128 gw 192.212.80.1
route add -net 192.212.68.0 netmask 255.255.255.252 gw 192.212.80.1
route add -net 192.212.66.0 netmask 255.255.254.0 gw 192.212.80.1
route add -net 192.212.64.0 netmask 255.255.255.0 gw 192.212.80.1
route add -net 192.212.65.0 netmask 255.255.255.252 gw 192.212.80.1
```

- order (A1,A2,A3)
```
route add -net 192.212.4.0 netmask 255.255.252.0 gw 192.212.8.1
route add -net 192.212.1.0 netmask 255.255.255.252 gw 192.212.8.1
route add -net 192.212.0.0 netmask 255.255.255.0 gw 192.212.8.1
```

- minister (A3)
```
route add -net 192.212.0.0 netmask 255.255.255.0 gw 192.212.1.1
```

- instrument (A13,A14, A16,A17,A18)
```
route add -net 192.212.72.0 netmask 255.255.255.128 gw 192.212.73.1
route add -net 192.212.72.128 netmask 255.255.255.128 gw 192.212.73.1

route add -net 192.212.66.0 netmask 255.255.254.0 gw 192.212.68.1
route add -net 192.212.64.0 netmask 255.255.255.0 gw 192.212.68.1
route add -net 192.212.65.0 netmask 255.255.255.252 gw 192.212.68.1
```
- firefist (A18)
```
route add -net 192.212.65.0 netmask 255.255.255.252 gw 192.212.64.1
```


- Pada router The Resonance, jalankan:

`iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.212.0.0/16`

- Pada semua node (router dan client) selain The Resonancee, jalankan:

`echo nameserver 192.168.122.1 > /etc/resolv.conf`

### Kendala
- Error pada routing
 
 
