```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
# Jarkom-Modul-4-A06-2021
Lapres Praktikum Jaringan Komputer 2021 - Modul 4
- Muh. Nur Fajrin Amiruddin (05111940000005)
- Rihan Farih Bunyamin (05111940000165)
- Lathifa Itqonina Mardiyati (05111940000176)

## Soal Praktikum
Pada soal diberikan topologi berikut:

![image1](https://user-images.githubusercontent.com/55240758/143179203-7b09d7f0-7a75-47e5-93dd-13764192ec47.png)

Berdasarkan topologi tersebut, diminta untuk menerapkan subnetting pada Cisco Packet Tracer dan GNS3 menggunakan metode perhitungan CLASSLESS yang berbeda. Bila di CPT menggunakan VLSM, maka di GNS3 menggunakan CIDR atau Sebaliknya.

Kelompok kami mengerjakan teknik **VLSM pada CPT**, sedangkan teknik **CIDR pada GNS3**.  


## VLSM (Variable Length Subnet Masking) - CPT
Perhitungan IP dapat dilakukan dengan menggunakan metode VLSM, dimana kita mengelompokkan setiap PC yang terhubung ke router. Apabila jumlah PC yang terhubung dengan router pada switch yang sama, lebih dari satu maka PC-PC tersebut akan dijadikakan satu kelompok.

**Langkah 1 :** Membuat topologi sesuai soal

**Langkah 2 :** Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan melakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan. 

![Subnetting](https://user-images.githubusercontent.com/55240758/143178466-b706a524-3f4a-4814-b0d4-25ba65658b1e.png)

Dimana kita akan menjumlahkan usable IP atau host yang dimiliki oleh masing-masing PC, kemudian setiap PC yang terhubung dengan 1 router, maka jumlah hostnya akan ditambahkan dengan 1, dan apabila PC terhubung dengan 2 router, maka jumlah hostnya akan ditambahkan dengan 2, lalu untuk router yang berhubungan dengan router lain, jumlah hostnya adalah 2, karena dia terhubung dengan PC dan juga router lain.

Berdasarkan penjelasan diatas dan label yang telah diberikan pada topologi, maka dapat didapatkan data sebagai berikut :

| Subnet | Jumlah Usable IP (Jumlah Host)| Length | 
| --- | --- | --- | 
| A1 (elena) | 721 | /22 |
|A2 (enieslobby)	| 252 | /24	| 
|A3 (guanho + oimo)	| 2 | /30 |
|A4 (jabra)	| 521 | /22	|
|A5 (foosha + guanho)	|	2 | /30 |
|A6 (maingate + guanho + alabasta)	|	502 | /23 |
|A7 (jorge)	|	13 | /28 |
|A8 (blueno)	|	1001 | /21 | 
|A9 (foosha + water7)	| 2 | /30	|
|A10 (water7 + pucci)	| 2 | /30 |
|A11 (cipher)	|	701 | /22 |
|A12 (jipangu)	| 101 |  /25 | 
|A13 (calmbelt + courtyard)	|	2021 |  /21 |
|A14 (doriki)	|	2 | /30 |
|A15 (fukurou)	| 2 | /30 |
|**Total** 				  |**5845**|**/19**|

Berdasarkan total jumlah IP yang telah didapat yakni sebesar **5845**. Jumlah IP tersebut, apabila dikonversikan ke dalam netmask didapatkan **netmask length /19** sesuai dengan tabel modul berikut :

![image](https://user-images.githubusercontent.com/55240758/143677389-021ad918-2bdd-4c6a-984c-43f166d257f1.png)

Dimana, dengan  **netmask length /19** diperoleh beberapa informasi penting yakni wildcard yang akan digunakan pada proses pembagian subnetting pada pohon subnet. 

**Langkah 3 :** Hitung pembagian IP berdasarkan jumlah IP yang telah didapat pada langkah sebelumnya. Adapun untuk mempermudah perhitungan dengan menggunakan visualisasi atau pohon subnetting.

Jumlah IP yang telah kami dapat memiliki **netmask length /19** , dimana netmask length tersebut memiliki **wildcard 0.0.31.255** berdasarkan tabel modul yang telah dilampirkan sebelumnya. Adapun berdasarkan wildcard tersebut kita dapat menyimpulkan berapa range IP pada digit tertentu yang disediakan untuk suatu netmask. Pada kasus ini digit ketiga wilcard yaitu **31**, atau dapat kita artikan range digit ketiga suatu IP pada netmask tersebut adalah 0-31, yang menandakan ada 32 macam kombinasi IP pada digit tersebut.

Sebelum melakukan pehitungan, perlu diketahui bahwa prefix IP yang kami gunakan adalah **10.2**. Kemudian berdasarkan prefix IP & netmask length yang telah didapat, IP permulaan yang akan dijadikan root pada pohon subnetting yaitu **10.2.0.0 /19**. 

Dari IP **10.2.0.0 /19** ini, kita membagi rangenya menjadi 2 sama rata. Di sisi kiri memiliki range IP **10.2.0.0 /20** hingga **10.2.15.0 /20**. Sedangkan di sisi kanan, rangenya adalah **10.2.16.0 /20** hingga **10.2.31.0 /20**. Karena pada hasil subnetting tidak ada yang membutuhkan netmask /20, maka kita meneruskan pembagian. Pada sisi kiri, kita membagi 2 sama rata lagi, sehingga menjadi range **10.2.0.0 /21** hingga **10.2.7.0 /21** dan **10.2.8.0 /21** hingga **10.2.15.0 /21**. Dan seterusnya hingga didapatkan pohon subnetting sebagai berikut :

![pohon](https://user-images.githubusercontent.com/55240758/143178440-b038f1f4-df9a-4501-8cda-a782b37a7d42.jpg)

Maka berdasarkan perhitungan atau pembagian IP yang diperoleh dari pohon subnetting, didapatkan :

| Subnet | IP	| Subnet Mask	| Length | Jumlah IP |
| --- | --- | --- | --- | --- | 
| A1 (elena) | 10.2.20.0 | 255.255.252.0 | /22 | 721 |  
|A2 (enieslobby)	| 10.2.26.0	| 255.255.255.0	| /24	| 252 |  
|A3 (guanho + oimo)	| 10.2.27.144	| 255.255.255.252	| /30 | 2 |  
|A4 (jabra)	| 10.2.12.0	| 255.255.252.0	| /22	| 521 |  
|A5 (foosha + guanho)	| 10.2.27.148	| 255.255.255.252	| /30 |	2 |
|A6 (maingate + guanho + alabasta)	| 10.2.24.0	| 255.255.254.0	| /23 |	502 |
|A7 (jorge)	| 10.2.27.128	| 255.255.255.240	| /28 |	13 |
|A8 (blueno)	| 10.2.16.0	| 255.255.252.0	| /22 |	1001 |
|A9 (foosha + water7)	| 10.2.27.152	| 255.255.255.252	| /30	| 2 |
|A10 (water7 + pucci)	| 10.2.27.156	| 255.255.255.252	| /30 | 2 |
|A11 (cipher)	| 10.2.8.0	| 255.255.252.0	| /22 |	701 |
|A12 (jipangu)	| 10.2.27.0	| 255.255.252.128	| /25 | 101 |
|A13 (calmbelt + courtyard)	| 10.2.0.0	| 255.255.248.0	| /21 |	2021 |
|A14 (doriki)	| 10.2.27.160	| 255.255.255.252	| /30 |	2 |
|A15 (fukurou)	| 10.2.27.164	| 255.255.255.252	| /30 |	 2 |
|**Total** 				  |             |**255.255.224.0** |**/19**|**5845**|

**Langkah 4 :** Melakukan penyetingan IP dan netmask berdasarkan perhitungan pada router maupun PC sesuai dengan label yang telah diberikan sebelumnya pada interface yang sesuai. Adapun pada penyettingan pada cisco packet tracer, telah kami rangkum sebagai berikut.

![image](https://user-images.githubusercontent.com/55240758/143679297-462aa42d-264f-4024-a1ff-603c1b7ab5ce.png)

sehingga pada pengaturan sebagai berikut :

**Pada Router**
- Foosha  
![Foosha 1](https://user-images.githubusercontent.com/55240758/143680245-2c53a775-c32a-4e9b-9fa8-96b9e394d6bb.jpg)
![Foosha 2](https://user-images.githubusercontent.com/55240758/143680253-71a4d1d9-f0b0-4247-b218-6e7d6e414565.jpg)
![Foosha 3](https://user-images.githubusercontent.com/55240758/143680255-831e5df0-2941-4f1c-b3c4-80e113e72db5.jpg)
![Foosha 4](https://user-images.githubusercontent.com/55240758/143680264-44497502-a7fd-4410-a296-0fb0a83127d8.jpg)

- Water7  
![Water7 1](https://user-images.githubusercontent.com/55240758/143680641-2544a3c7-4a6b-4f61-a342-aba95dab3760.jpg)
![Water7 2](https://user-images.githubusercontent.com/55240758/143680645-0c8f7a25-13b8-4228-a4e0-231e2956957b.jpg)
![Water7 3](https://user-images.githubusercontent.com/55240758/143680650-f6a9f5b8-6fbc-4921-b22e-1c5766fbc4f7.jpg)

- Pucci    
![Pucci 1](https://user-images.githubusercontent.com/55240758/143680654-77db1b50-aa51-4c7c-abb4-610a613e889c.jpg)
![Pucci 2](https://user-images.githubusercontent.com/55240758/143680658-7f58cf60-f604-4310-bb87-46ef5d67399d.jpg)
![Pucci 3](https://user-images.githubusercontent.com/55240758/143680660-71a69593-f013-4b1b-9f28-f105f4746d23.jpg)

- Guanhao  
![Guanhao 1](https://user-images.githubusercontent.com/55240758/143680666-de72dafa-a0ab-4a28-8557-38defec444de.jpg)
![Guanhao 2](https://user-images.githubusercontent.com/55240758/143680671-a36d8c13-5b34-4f2c-ac42-51cd7ab3ccc3.jpg)
![Guanhao 3](https://user-images.githubusercontent.com/55240758/143680673-fe080d8b-695d-4c05-a466-69eba781900c.jpg)
![Guanhao 4](https://user-images.githubusercontent.com/55240758/143680677-c65a8ece-9136-4b62-84f8-21b4234c235e.jpg)

- Alabasta  
![Alabasta 1](https://user-images.githubusercontent.com/55240758/143680681-2424c7f7-7b27-4a3d-ae4f-3b34673f4dca.jpg)
![Alabasta 2](https://user-images.githubusercontent.com/55240758/143680688-1e608962-4575-4e29-b782-c890963e0667.jpg)

- Oimo    
![Oimo 1](https://user-images.githubusercontent.com/55240758/143680698-ae0b7a65-8668-4b20-9d55-1bc8a6052551.jpg)
![Oimo 2](https://user-images.githubusercontent.com/55240758/143680700-e1694d13-a876-45c2-8e66-23bfe1722635.jpg)
![Oimo 3](https://user-images.githubusercontent.com/55240758/143680709-66f039a6-64fe-45f4-bea7-12e9f08a3440.jpg)

- Seastone  
![Seastone1](https://user-images.githubusercontent.com/55240758/143680715-8e74187b-f641-4384-af92-b37ecef605b5.jpg)
![Seastone 2](https://user-images.githubusercontent.com/55240758/143680720-b322ffa4-3ae5-4ff7-afd9-0bb58965f4cf.jpg)

**Pada PC**
- Blueno  
![Blueno 1](https://user-images.githubusercontent.com/55240758/143681268-67b32a75-fa6f-4917-8e52-908ece1fc3a6.jpg)

- Cipher  
![Cipher 1](https://user-images.githubusercontent.com/55240758/143681289-8c2c8fc5-f5d5-4811-90b9-932bc3d218fa.jpg)

- Calmbelt  
![Calmbelt 1](https://user-images.githubusercontent.com/55240758/143681293-327981d3-cc60-4a6b-8552-0e5ed58a349e.jpg)


- Courtyard  
![Courtyard 1](https://user-images.githubusercontent.com/55240758/143681296-7661cded-1924-4442-a205-34b7b52e8851.jpg)

- Jipangu  
![Jipangu 1](https://user-images.githubusercontent.com/55240758/143681302-73d1f879-2352-4a3d-ac7a-d6d218aa602a.jpg)

- Jabra  
![Jabra 1](https://user-images.githubusercontent.com/55240758/143681307-068459df-6ef8-4a3c-83c8-70393437382e.jpg)


- Maingate  
![Maingate 1](https://user-images.githubusercontent.com/55240758/143681314-a7ef3fc6-1436-4d6f-b4be-96533e5b09b6.jpg)


- Enieslobby  
![Enieslobby 1](https://user-images.githubusercontent.com/55240758/143681318-95f02c96-c8a7-4195-bbcb-b0d58751a1b3.jpg)


- Elena  
![Elena 1](https://user-images.githubusercontent.com/55240758/143681319-7ed4214d-9450-4eeb-a923-9657bfa968bb.jpg)


- Jorge  
![Jorge 1](https://user-images.githubusercontent.com/55240758/143681327-a0350c80-5496-4bb7-9588-2635758ad50a.jpg)



**Pada Server**
- Doriki  
![Doriki](https://user-images.githubusercontent.com/55240758/143681364-5009d1ef-6e40-4077-9259-ed2a972f24a3.jpg)

- Fukurou  
![Fukurou](https://user-images.githubusercontent.com/55240758/143681368-24be19ed-aaee-41f8-91c8-cf0ce79af454.jpg)


**Langkah 5 :** Melakukan routing pada setiap router, Adapun pada penyettingan pada cisco packet tracer, telah kami rangkum sebagai berikut.

![image](https://user-images.githubusercontent.com/55240758/143681703-97d7104c-53b7-4ed5-8e86-d81b4fe7287f.png)

sehingga pengaturan sebagai berikut :

- Foosha  
![Foosha](https://user-images.githubusercontent.com/55240758/143681744-b604064f-de13-487d-8505-2a8dfff99e90.jpg)


- Water7  
![Water7](https://user-images.githubusercontent.com/55240758/143681748-9cd87330-6f5c-4863-bc79-d79378e858fb.jpg)


- Pucci    
![Pucci](https://user-images.githubusercontent.com/55240758/143681754-5fa0a920-cff1-4a17-b43c-0620723c9f12.jpg)


- Guanhao  
![Guanhao](https://user-images.githubusercontent.com/55240758/143681759-de73cb9e-d1df-4af7-9381-4ec9ac89140f.jpg)

- Alabasta  
![Alabasta](https://user-images.githubusercontent.com/55240758/143681766-bede4d14-cdb3-477f-8b75-ba7eb1099016.jpg)


- Oimo    
![Oimo](https://user-images.githubusercontent.com/55240758/143681769-c14d229a-f99c-4c7d-bbb4-e9cbee54d53f.jpg)


- Seastone  
![Seastone](https://user-images.githubusercontent.com/55240758/143681772-b7fe8d10-bf98-4e78-8d46-2a2359236e69.jpg)


**Langkah 6:** Melakukan testing dengan mengirimkan paket antar PC ke PC, PC ke Router, & Server ke server maupun Router ke Router. Salah satu hasil testing sebagai berikut :
- PC ke PC : Courtyard -> Elena  
![1](https://user-images.githubusercontent.com/55240758/143682797-6439c3f8-2e34-4587-9252-50ed19a7f7f7.jpg)

- PC ke Router : Chiper -> Fukurou  
![2](https://user-images.githubusercontent.com/55240758/143682812-112d2e53-f8df-47e9-9e0c-07b54c611c8b.jpg)

- Router ke Router : Seastone -> Foosha  
![3](https://user-images.githubusercontent.com/55240758/143682819-fe6a1eba-467d-4409-8e93-0e7bd8983c58.jpg)

- Server ke server : Doriki -> Fukurou  
![4](https://user-images.githubusercontent.com/55240758/143682849-607ceebc-291f-4a23-9518-21d9b6ce9c21.jpg)

## CIDR (Classless Inter Domain Routing) - GNS3
Selain menggunakan metode VSLM, perhitungan IP dapat menggunakan metode CIDR dimana kita mengelompokkan subnet A yang telah didapat pada saat menggunakan VSLM yakni dengan mengelompokkan antarsubnet yang terhubung dengan 1 router yang sama dan dimulai dari node terluar. 

**Langkah 1:** Melakukan pengelompokan dengan metode CIDR

1. Pengelompokan subnet B sebagai berikut :
- B1 /20 → A12 /25 + A13 /21
- B2 /21 → A1 /24 + A2 /22
- B3 /22 → A6 /23 + A17 /28

![1](https://user-images.githubusercontent.com/55240758/143684177-00483b67-cfc1-4844-bdc0-0f5e1bf285bd.png)

2. Pengelompokan subnet C sebegai berikut :
- C1 /19 → B1 /20 + A10 /30
- C2 /20 → B2 /21 + A15 /30
- C3 /21 → B3 /22 + A4 /22

![2](https://user-images.githubusercontent.com/55240758/143684162-87d685d7-2624-40f0-9d67-0e1c9961920c.png)

3. Pengelompokan subnet D sebagai berikut :
- D1 /18 → C1 /19 + A11 /22
- D2 /19 → C2 /20 + A3 /30

![3](https://user-images.githubusercontent.com/55240758/143684377-5957f5e8-9d97-4490-8c29-b707c266e383.png)

4. Pengelompokan subnet E sebagai berikut :
- E1 /17 → D1 /18 + A9 /30
- E2 /18 → D2 /19 + C3 /21

![4](https://user-images.githubusercontent.com/55240758/143684431-9679eb02-58f5-4d22-a816-386752a67556.png)


5. Pengelompokan subnet F sebagai berikut :
- F1 /16 → E1 /17 + A8 /22
- F2 /17 → E2 /18 + A5 /30

![5](https://user-images.githubusercontent.com/55240758/143684609-eeff8a65-f0f2-4a77-a914-e1e625b54d0b.png)


6. Pengelompokan subnet G sebagai berikut :
- G1 /16 → F2 /17 + A14 /30

![6](https://user-images.githubusercontent.com/55240758/143684626-93fc2d34-150d-4868-a1ca-9ce1eb3a55e7.png)


7. Pengelompokan subnet H sebagai berikut :
- H1 /15 → F1 /16 + G1 /16

![7](https://user-images.githubusercontent.com/55240758/143684638-563c98cd-b029-4b08-b7cc-1b180fc60b38.png)

**Langkah 2:** Melakukan perhitungan dan pembagian IP berdasarkan labelling atau pengelompokan yang telah dilakukan. Adapun untuk mempermudah perhitungan dengan menggunakan visualisasi atau pohon subnetting. 

Sama seperti VSLM pada perhitungan CIDR, berdasarkan netmask terbesar dari pengelompokan yang telah dilakukan yaitu **netmask length /15** , dimana netmask length tersebut memiliki **wildcard 0.1.255.255** berdasarkan tabel modul yang telah dilampirkan sebelumnya. Adapun berdasarkan wildcard tersebut kita dapat menyimpulkan berapa range IP pada digit tertentu yang disediakan untuk suatu netmask. Pada kasus ini digit kedua wilcard yaitu **1**, atau dapat kita artikan range digit ketiga suatu IP pada netmask tersebut adalah 0-1, yang menandakan ada 2 macam kombinasi IP pada digit tersebut.

Sebelum melakukan pehitungan, perlu diketahui bahwa prefix IP yang kami gunakan adalah **10.2**. Kemudian berdasarkan prefix IP & netmask length yang telah didapat, IP permulaan yang akan dijadikan root pada pohon subnetting yaitu **10.2.0.0 /15**. 

Dari IP **10.2.0.0 /15** ini, kita membagi rangenya menjadi 2 sama rata. Di sisi kiri IP-nya menjadi **10.2.0.0 /16** di mana diassign ke subnet G1 yang memiliki netmask /16. Lalu di sisi kanan, memiliki IP **10.3.0.0 /16**. Lalu kita membagi lagi hingga sama rata dan didapatkan seluruh subnet memiliki IP masing-masing. Dan seterusnya hingga didapatkan pohon subnetting sebagai berikut :

![Pohon](https://user-images.githubusercontent.com/55240758/143726602-bb3f87f5-b63d-4aea-8275-1b2c34fd189a.jpeg)

Maka berdasarkan perhitungan atau pembagian IP yang diperoleh dari pohon subnetting, didapatkan :

| Subnet | IP	| Subnet Mask	| Length |   
| --- | --- | --- | --- | 
| A1 (elena) | 10.2.0.0 | 255.255.252.0 | /22 |  
| A2 (enieslobby)	| 10.2.4.0	| 255.255.254.0	| /24	|   
| A3 (guanho + oimo)	| 10.2.16.0	| 255.255.255.252	| /30 | 
| A4 (jabra)	| 10.2.36.0	| 255.255.252.0	| /22	|   
|A5 (foosha + guanho)	| 10.2.64.0	| 255.255.255.252	| /30 |	
|A6 (maingate + guanho + alabasta)	| 10.2.32.0	| 255.255.254.0	| /23 |	
|A7 (jorge)	| 10.2.34.0	| 255.255.255.240	| /28 |
|A8 (blueno)	| 10.3.128.0	| 255.255.252.0	| /22 |	
|A9 (foosha + water7)	| 10.3.64.0	| 255.255.255.252	| /30	| 
|A10 (water7 + pucci)	| 10.3.16.0	| 255.255.255.252	| /30 | 
|A11 (cipher)	| 10.3.32.0	| 255.255.252.0	| /22 |	
|A12 (jipangu)| 10.3.8.0	| 255.255.128.0	| /25 |	
|A13 (calmbelt + courtyard) | 10.3.0.0	| 255.255.248.0	| /21 | 
|A14 (doriki)	| 10.2.128.0	| 255.255.255.252	| /30 |	
|A15 (fukurou)	| 10.2.8.0	| 255.255.255.252	| /30 |	
