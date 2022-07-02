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

## Gudang
1. id_rak(PK)
2. rak
3. id_admin(FK)
4. id_komik(FK)

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
3. id_komik(FK)
4. waktu_peminjaman
5. jatuh_tempo

## pengembalian
1. id_pengembalian(PK)
2. id_peminjaman(FK)
3. waktu_pengembalian
4. status_pengembalian
5. kondisi
6. denda
7. id_member(FK)
8. id_admin(FK)
9. id_komik(FK)

## ERD
![Untitled](https://user-images.githubusercontent.com/100655325/176494114-e5896729-4569-46d2-ada2-c8205f00bf35.png)

## DDL DML DQL
[DDL DML DQL](https://github.com/Naufalzaki05/IF214002/tree/main/Pertemuan%2011)

## Tabel-tabel
[tabel](https://github.com/Naufalzaki05/IF214002/blob/main/Pertemuan%206/README.md)

## Aplikasi
[Aplikasi](https://github.com/Naufalzaki05/komiku-app/tree/main)

## Video Presentasi
[youtube](https://youtu.be/-siuXVbLROk)
