# Jarkom-Modul-4-ITA06-2022

## <b> Anggota Kelompok: </b>
1. Anisah Farah Fadhilah - 5027201023
2. Banabil Fawazaim Muhammad - 5027201055
3. Shafira Khaerunnisa - 5027201072
---
## Topologi CPT

![image](https://user-images.githubusercontent.com/76768695/204092344-2c3f3da0-822a-43c8-8ee6-4e5bae5b42f4.png)

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

 
 
