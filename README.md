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
**Langkah 1 :** Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan melakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan

![Subnetting](https://user-images.githubusercontent.com/55240758/143178466-b706a524-3f4a-4814-b0d4-25ba65658b1e.png)

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

Berdasarkan total IP dan netmask yang dibutuhkan, maka kita dapat menggunakan **netmask length /19** untuk memberikan pengalamatan IP pada subnet.

**Langkah 2 :** Subnet besar yang dibentuk memiliki **NID 10.2.0.0** dengan **netmask length /19**. Hitung pembagian IP berdasarkan NID dan netmask tersebut menggunakan pohon seperti gambar di bawah

![pohon](https://user-images.githubusercontent.com/55240758/143178440-b038f1f4-df9a-4501-8cda-a782b37a7d42.jpg)

Pembagian tersebut didapatkan dengan cara membagi menjadi dua cabang dan sesuai netmask yang dibutuhkan dari penjumlahan sebelumnya dimulai dari netmask length total yaitu /19. Kemudian pada netmask length /20 dapat kita lihat bahwa tidak ada subnet yang menggunakan netmask length tersebut, namun pada length /21....

## CIDR (Classless Inter Domain Routing) - GNS3


