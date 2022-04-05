## Deskripsi-Project
Membuat sistem ruang baca komik, sehingga pengelola ruang baca mudah dalam mengurus administrasi.
## Fitur-fitur
1. Admin dapat mengelola komik.
2. Admin dapat mengelola peminjaman serta pengembalian komik member.

# Entitas dan Atribut
## Admin
1. id_admin
2. nama_admin
3. username_admin
4. pass_admin
5. alamat_admin
6. no_telp_admin

## komik
1. id_komik
2. judul_komik
3. tahun_rilis

## Genre
1. id_genre
2. nama_genre

## Pengarang
1. id_pengarang
2. nama_pengarang

## Penerbit
1. id_penerbit
2. nama_penerbit

## member
1. id_member
2. nama_member
3. alamat_member
4. no_telp_member

## peminjaman
1. id_peminjaman
2. id_member
3. tanggal_peminjaman
4. tanggal_pengembalian

## pengembalian
1. id_pengembalian
2. id_member
3. status_pengembalian
4. denda
