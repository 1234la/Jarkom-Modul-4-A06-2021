```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
# Jarkom-Modul-3-A06-2021
Lapres Praktikum Jaringan Komputer 2021 - Modul 3
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

| Subnet | Length | Jumlah Usable IP (Jumlah Host)|
| --- | --- | --- | 
| A1 (elena) | /22 | 721 |  
|A2 (enieslobby)	| /24	| 252 |  
|A3 (guanho + oimo)	| /30 | 2 |  
|A4 (jabra)	| /22	| 521 |  
|A5 (foosha + guanho)	| /30 |	2 |
|A6 (maingate + guanho + alabasta)	| /23 |	502 |
|A7 (jorge)	| /28 |	13 |
|A8 (blueno)	|	/21 | 1001 |
|A9 (foosha + water7)	| /30	| 2 |
|A10 (water7 + pucci)	| /30 | 2 |
|A11 (cipher)	| /22 |	701 |
|A12 (jipangu)	| /25 | 101 |
|A13 (calmbelt + courtyard)	| /21 |	2021 |
|A14 (doriki)	| /30 |	2 |
|A15 (fukurou)	| /30 |	 2 |
|**Total** 				  |**/19**|**5845**|

Berdasarkan total jumlah IP yang telah didapat yakni sebesar **5845**. Jumlah IP tersebut, apabila dikonversikan ke dalam netmask didapatkan **netmask length /19** sesuai dengan tabel modul berikut :

![image](https://user-images.githubusercontent.com/55240758/143677389-021ad918-2bdd-4c6a-984c-43f166d257f1.png)

Dimana, dengan  **netmask length /19** diperoleh beberapa informasi penting yakni wildcard yang akan digunakan pada proses pembagian subnetting pada pohon subnet. 

**Langkah 3 :** Hitung pembagian IP berdasarkan jumlah IP yang telah didapat pada langkah sebelumnya. Adapun untuk mempermudah perhitungan dengan menggunakan visualisasi atau pohon subnetting.

Jumlah IP yang telah kami dapat memiliki **netmask length /19** , dimana netmask length tersebut memiliki **wildcard 0.0.31.255** berdasarkan tabel modul yang telah dilampirkan sebelumnya. Adapun berdasarkan wildcard tersebut kita dapat menyimpulkan berapa range IP pada digit tertentu yang disediakan untuk suatu netmask. Pada kasus ini digit ketiga wilcard yaitu **31**, atau dapat kita artikan range digit ketiga suatu IP pada netmask tersebut adalah 0-31, yang menandakan ada 32 macam kombinasi IP pada digit tersebut.

Sebelum melakukan pehitungan, perlu diketahui bahwa prefix IP yang kami gunakan adalah **10.2**. Kemudian berdasarkan prefix IP & netmask length yang telah didapat, IP permulaan yang akan dijadikan root pada pohon subnetting yaitu **10.2.0.0 /19**. 

Dari IP **10.2.0.0 /19** ini, kita membagi rangenya menjadi 2 sama rata. Di sisi kiri memiliki range IP **10.2.0.0 /20** hingga **10.2.15.0 /20**. Sedangkan di sisi kanan, rangenya adalah **10.2.16.0 /20** hingga **10.2.31.0 /20**. Karena pada hasil subnetting tidak ada yang membutuhkan netmask /20, maka kita meneruskan pembagian. Pada sisi kiri, kita membagi 2 sama rata lagi, sehingga menjadi range **10.2.0.0 /21** hingga **10.2.7.0 /21** dan **10.2.8.0 /21** hingga **10.2.15.0 /21**. Dan seterusnya hingga didapatkan pohon subnetting seagai berikut :

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

**Pada Router**
- Foosha
- Water7
- Pucci
- Guanhao
- Alabasta
- Oimo
- Seastone

**Pada PC**

**Pada Server**

**Langkah 5 :** Melakukan testing dengan mengirimkan paket antar PC ke PC, PC ke Router, maupun Router ke Router. Salah satu hasil testing sebagai berikut :
- PC ke PC
- PC ke Router
- Router ke Router

## CIDR (Classless Inter Domain Routing) - GNS3


