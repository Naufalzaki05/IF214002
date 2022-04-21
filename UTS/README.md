## UTS BASDAT
Naufal Zaki - 1207050089 - E

## No 1
Basis data relasional dapat langsung dibangun menggunakan perintah SQL di sistem basis data seperti MySQL, dsb tanpa ada perancangan terlebih dahulu. 
Jelaskan apa keuntungan melakukan perancangan basis data terlebih dahulu (menggunakan ERD ataupun Class Diagram) !
- keutungan nya data lebih sistematis dan tidak redundan
- bisa mengetahui alur bisnisnya

## No 2
cara mentransformasikan proses bisnis sebuah organisasi menjadi struktur data di basis data:
- Tentukan Deskripsi dari proses bisnis yang akan dibuat
- tentukan fitur-fitur yang akan ada di proses bisnis tersebut
- tentukan entitas serta atributnya
- tentukan relasi pada setiap entitas
- tentukan key pada setiap entitas.
- tentukan tipe datanya
- buat ERD notasi Chen dan notasi Crow Foot

## No 3
## Deskripsi-Project
Membuat sistem ruang baca komik, sehingga pengelola ruang baca mudah dalam mengurus administrasi.
## Fitur-fitur
1. Admin dapat mengelola komik.
2. Admin dapat mengelola peminjaman serta pengembalian komik member.

# Entitas dan Atribut
## Admin
1. id_admin(PK)
2. nama_admin
3. username_admin
4. pass_admin
5. alamat_admin
6. no_telp_admin

## komik
1. id_komik(PK)
2. judul_komik
3. tahun_rilis
4. id_genre(FK)
5. id_pengarang(FK)
6. id_penerbit(FK)
7. jumlah

## Genre
1. id_genre(PK)
2. nama_genre

## Pengarang
1. id_pengarang(PK)
2. nama_pengarang

## Penerbit
1. id_penerbit(PK)
2. nama_penerbit

## member
1. id_member(PK)
2. nama_member
3. alamat_member
4. no_telp_member

## peminjaman
1. id_peminjaman(PK)
2. id_member(FK)
3. waktu_peminjaman
4. jatuh_tempo

## pengembalian
1. id_pengembalian
2. id_peminjaman
3. waktu_prngembalian
4. status_pengembalian
5. kondisi
6. denda

## RELASI
Admin 1 1 --- 0-n Peminjaman
Admin 1 1 --- 1 1 Gudang
Komik 1-n --- 1 1
Admin 1 1 --- 0-n Pengembalian
Peminjaman 0-n --- 1 1 Member
Peminjaman 0-n --- 0-n Komik
Pengembalian 0-n --- 1 1 Member
Genre 1-n --- 1-n Komik
Pengarang 1 1 --- 1-n Komik
penerbit 1 1 --- 1-n Komik

## Erd Chen
![Diagram ERD drawio](https://user-images.githubusercontent.com/100655325/164358897-8c1a7027-793c-4bac-bbb9-29047f16b178.png)

## Erd Crow foot
(![erd crow foot drawio](https://user-images.githubusercontent.com/100655325/164357167-002a021d-9e36-4b30-b084-39448db82424.png)
)
#### Tabel Admin
|🔑id_admin|nama_admin|username_admin|pass_admin|alamat_admin|no_telepon|
|---|---|---|---|---|---|
|1|Pharaoh|pharaoh05|phara005|mesir|087745671111|
|2|Ozymandias|ozyman00|ozyy12|mesir|087899881212|
|3|Nero|neroc09|neronero0|roma|088827271313|

#### Tabel Gudang
|🔑id_rak|id_admin|id_buku|
|---|---|---|
|1|1|1|
|1|2|2|
|1|3|3|

#### Tabel Komik
|🔑id_komik|id_genre|id_pengarang|id_penerbit|judul_komik|tahun_rilis|jumlah|
|---|---|---|---|---|---|---|
|1|1|1|1|nisekoi|2011|10|
|2|1|2|2|Kanojo  Okarishimasu|2017|15|
|3|1|3|3|Yahari Ore no Seishun Love Comedy wa Machigatteiru|2011|11|

#### Tabel genre
|🔑id_genre|nama_genre|
|---|---|
|1|Romantis|
|2|Aksi|
|3|Fantasi|

#### Tabel Pengarang
|🔑id_pengarang|nama_pengarang|
|---|---|
|1|Komi Naoshi|
|2|Miyajima Reiji|
|3|Watari Wataru|


#### Tabel Penerbit
|🔑id_pengarang|nama_pengarang|
|---|---|
|1|Shueisha |
|2|Kondansha|
|3|Shogakukan|

#### Tabel Member
|🔑id_member|nama_member|alamat_member|no_telepon_member|
|---|---|---|---|
|1|rira|cileunyi|084511223467|
|2|rara|cipadung|087722445362|
|3|rora|manisi|089700998739|

#### Tabel Peminjaman
|🔑id_peminjaman|id_admin|id_komik|id_member|waktu_peminjaman|jatuh_tempo|
|---|---|---|---|---|---|
|1|1|1|1|2022-04-01 13:40:42|2022-05-01 13:40:42|
|2|1|2|2|2022-04-01 14:00:00|2022-05-01 14:00:00|
|3|1|3|3|2022-04-02 08:00:00|2022-05-02 08:00:00|

#### Tabel Pengembalian
|🔑id_pengembalian|id_peminjaman|waktu_pengembalian|status_pengembalian|kondisi_komik|Denda|
|---|---|---|---|---|---|
|1|1|2022-05-01 13:40:42|Sudah|baik|0|
|2|2|-|Belum|-|-|
|3|3|-|Belum|-|-|
---
