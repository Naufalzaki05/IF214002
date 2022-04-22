## Perintah SQL
1. Perintah SELECT
Perintah SELECT merupakan perintah dasar SQL yang di gunakan untuk memilih data dari database. Data yang di kembalikan di simpan dalam tabel yang di sebut result-set.
- SELECT kolom1, kolom2, ... FROM nama_tabel;
2. Perintah SELECT DISTINCT
Perintah SELECT DISTINCT merupakan perintah dasar SQL yang di gunakan untuk mengembalikan hanya nilai yang berbeda dari dalam sebuah tabel, dengan kata lain semua record duplikat (record dengan nilai yang sama) yang terdapat pada tabel akan di anggap sebagai satu record/nilai.
- SELECT DISTINCT kolom1, kolom2, ... FROM nama_tabel;
3. Perintah WHERE merupakan perintah dasar SQL yang di gunakan untuk mem-filter hasil SELECT dengan mengekstrak record yang memenuhi persyaratan tertentu.
- SELECT kolom1, kolom2, ... FROM nama_tabel WHERE kondisi;
4. Perintah (operator) AND, OR dan NOT
Operator AND, OR dan NOT merupakan perintah dasar SQL yang biasanya di kombinasikan dengan perintah WHERE. Ketiganya di gunakan untuk mem-filter record berdasarkan suatu kondisi, operator AND akan menampilkan record apabila semua kondisi bernilai TRUE, operator OR akan menampilkan record apabila salah satu kondisi bernilai TRUE, sedangkan operator NOT akan menampilkan record apabila semua kondisi bernilai FALSE.
- Sintaks AND
SELECT kolom1, kolom2, ... FROM nama_tabel WHERE kondisi1 AND kondisi2 AND kondisi3 ...;

- Sintaks OR
SELECT kolom1, kolom2, ... FROM nama_tabel WHERE kondisi1 OR kondisi2 OR kondisi3 ...;

- Sintaks NOT
SELECT kolom1, kolom2, ... FROM nama_tabel WHERE NOT kondisi;

5. Perintah ORDER BY
Perintah ORDER BY merupakan perintah dasar SQL yang di gunakan untuk mengurutkan result-set dalam pengurutan ‘ascending’ atau ‘descending’. Secara default perintah ORDER BY menampilkan record dalam pengurutan ‘ascending’ (‘ASC’). Untuk mengurutkan ‘descending’, gunakan kata kunci ‘DESC’.
- Sintaks
SELECT kolom1, kolom2, ... FROM nama_tabel ORDER BY column DESC;

6. Perintah INSERT INTO
Dalam SQL, perintah INSERT INTO merupakan perintah dasar SQL bagian dari perintah untuk DML (Data Manipulation Language) Saya asumsikan Anda telah faham perbedaan DDL, DCL, dan DML. Perintah INSERT INTO dapat di gunakan untuk menambahkan record baru ke dalam tabel.

- Sintaks
INSERT INTO nama_tabel VALUES (nilai1, nilai2, nilai3, ...);
7.  Perintah UPDATE
Perintah UPDATE merupakan perintah dasar SQL yang di gunakan untuk memperbarui atau mengubah nilai suatu record berdasarkan kriteria tertentu.

- Sintaks
UPDATE nama_tabel SET kolom1 = nilai1, kolom2 = nilai2, ... WHERE kondisi;
8. Perintah DELETE
Hampir sama dengan perintah UPDATE, perintah DELETE juga merupakan perintah dasar SQL yang di gunakan untuk menghapus nilai suatu record berdasarkan kriteria tertentu.

- Sintaks
DELETE FROM table_name WHERE condition;

9. Perintah (fungsi) MIN()
Fungsi MIN() merupakan perintah dasar SQL yang di gunakan untuk mendapatkan nilai terkecil dari suatu kolom, Anda dapat menerapkannya pada kolom ‘harga’, ‘nilai’, ‘qty’ atau kolom yang semisal dengan itu, berbeda dengan perintah ORDEY BY, fungsi MIN() hanya menampilkan satu record saja yang memenuhi kriteria yang Anda tentukan.

- Sintaks
SELECT MIN(nama_kolom) FROM nama_tabel WHERE kondisi;
10. Perintah (fungsi) MAX()
Fungsi MAX() merupakan perintah dasar SQL yang di gunakan untuk mendapatkan nilai terbesar dari suatu kolom, seperti halnya fungsi MIN() Anda dapat menerapkannya pada kolom ‘harga’, ‘nilai’, ‘qty’ atau kolom yang semisal dengan itu.

- Sintaks
SELECT MAX(nama_kolom) FROM nama_tabel WHERE kondisi;

11. Perintah (fungsi) COUNT()
Fungsi COUNT() merupakan perintah dasar SQL yang di gunakan untuk mendapatkan jumlah hitungan record yang memenuhi suatu kriteria.

- Sintaks
SELECT COUNT(nama_kolom) FROM nama_tabel WHERE kondisi;

12. Perintah (fungsi) AVG()
Fungsi AVG() merupakan perintah dasar SQL yang di gunakan untuk mendapatkan rata-rata record yang memenuhi suatu kriteria, tentunya nilai pada kolom harus numerik.

- Sintaks
SELECT AVG(nama_kolom) FROM nama_tabel WHERE kondisi;

13. Perintah (fungsi) SUM()
Fungsi SUM() merupakan perintah dasar SQL yang di gunakan untuk mendapatkan jumlah record yang memenuhi suatu kriteria, tentunya nilai pada kolom harus numerik.

- Sintaks
SELECT SUM(nama_kolom) FROM nama_tabel WHERE kondisi;

14. Perintah INNER JOI
INNER JOIN merupakan perintah dasar SQL yang di gunakan untuk menggabungkan beberapa tabel dan mengambil nilai yang cocok (identik) di antara kedua tabel tersebut.

- Sintaks
SELECT nama_kolom1, nama_kolom2, ... FROM tabel1 INNER JOIN tabel2 ON tabel1.nama_kolom = tabel2.nama_kolom;

15. Perintah LEFT JOIN

LEFT JOIN merupakan perintah dasar SQL yang di gunakan untuk menggabungkan beberapa tabel dan mengambil nilai yang cocok (identik) di antara kedua tabel tersebut dan nilai lain dari tabel pada ruas kiri meskipun tak ada nilai yang cocok dengan tabel pada ruas kanan.

- Sintaks
SELECT nama_kolom1, nama_kolom2, ... FROM tabel1 LEFT JOIN tabel2 ON tabel1.nama_kolom = tabel2.nama_kolom;

## Tabel Normalisasi
#### Tabel Admin
|🔑id_admin|nama_admin|username_admin|pass_admin|alamat_admin|no_telepon|
|---|---|---|---|---|---|
|1|Pharaoh|pharaoh05|phara005|mesir|087745671111|
|2|Ozymandias|ozyman00|ozyy12|mesir|087899881212|
|3|Nero|neroc09|neronero0|roma|088827271313|

#### Tabel Gudang
|🔑id_rak|id_admin|id_komik|
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
|🔑id_pengembalian|id_peminjaman|waktu_pengembalian|status_pengembalian|kondisi|Denda|
|---|---|---|---|---|---|
|1|1|2022-05-01 13:40:42|Sudah|baik|0|
|2|2|-|Belum|-|-|
|3|3|-|Belum|-|-|
---

## Database
```sql
CREATE TABLE IF NOT EXISTS public.admin
(
    id_admin integer NOT NULL,
    nama_admin character(50) COLLATE pg_catalog."default" NOT NULL,
    username_admin character varying(50) COLLATE pg_catalog."default" NOT NULL,
    pass_admin character varying(12) COLLATE pg_catalog."default" NOT NULL,
    alamat_admin character varying(50) COLLATE pg_catalog."default" NOT NULL,
    no_telepon character(12) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT admin_pkey PRIMARY KEY (id_admin)
)

TABLESPACE pg_default;
CREATE TABLE IF NOT EXISTS public.genre
(
    id_genre integer NOT NULL,
    nama_genre character(20) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT genre_pkey PRIMARY KEY (id_genre)
)

TABLESPACE pg_default;
CREATE TABLE IF NOT EXISTS public.gudang
(
    id_rak integer NOT NULL,
    id_admin integer,
    id_komik integer,
    CONSTRAINT gudang_pkey PRIMARY KEY (id_rak),
    CONSTRAINT id_admin FOREIGN KEY (id_admin)
        REFERENCES public.admin (id_admin) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION,
    CONSTRAINT id_komik FOREIGN KEY (id_komik)
        REFERENCES public.komik (id_komik) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

TABLESPACE pg_default;
CREATE TABLE IF NOT EXISTS public.komik
(
    id_komik integer NOT NULL,
    id_genre integer NOT NULL,
    id_pengarang integer NOT NULL,
    id_penerbit integer NOT NULL,
    judul_komik character varying(100) COLLATE pg_catalog."default" NOT NULL,
    tahun_rilis character(4) COLLATE pg_catalog."default" NOT NULL,
    jumlah integer NOT NULL,
    CONSTRAINT id_komik UNIQUE (id_komik)
        INCLUDE(judul_komik),
    CONSTRAINT id_genre FOREIGN KEY (id_genre)
        REFERENCES public.genre (id_genre) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION,
    CONSTRAINT id_penerbit FOREIGN KEY (id_penerbit)
        REFERENCES public.penerbit (id_penerbit) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION,
    CONSTRAINT id_pengarang FOREIGN KEY (id_pengarang)
        REFERENCES public.pengarang (id_pengarang) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

TABLESPACE pg_default;
CREATE TABLE IF NOT EXISTS public.member
(
    id_member integer NOT NULL,
    nama_member character(50) COLLATE pg_catalog."default" NOT NULL,
    alamat_member character varying(100) COLLATE pg_catalog."default" NOT NULL,
    no_telepon_member character(12) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT member_pkey PRIMARY KEY (id_member)
)

TABLESPACE pg_default;
CREATE TABLE IF NOT EXISTS public.peminjaman
(
    id_peminjaman integer NOT NULL,
    id_admin integer NOT NULL,
    id_komik integer NOT NULL,
    id_member integer NOT NULL,
    waktu_peminjaman date NOT NULL,
    jatuh_tempo date NOT NULL,
    CONSTRAINT peminjaman_pkey PRIMARY KEY (id_peminjaman),
    CONSTRAINT id_admin FOREIGN KEY (id_admin)
        REFERENCES public.admin (id_admin) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION,
    CONSTRAINT id_komik FOREIGN KEY (id_komik)
        REFERENCES public.komik (id_komik) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION,
    CONSTRAINT id_member FOREIGN KEY (id_member)
        REFERENCES public.member (id_member) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

TABLESPACE pg_default;
CREATE TABLE IF NOT EXISTS public.penerbit
(
    id_penerbit integer NOT NULL,
    nama_penerbit character(25) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT penerbit_pkey PRIMARY KEY (id_penerbit)
)

TABLESPACE pg_default;
CREATE TABLE IF NOT EXISTS public.pengarang
(
    id_pengarang integer NOT NULL,
    nama_pengarang character(20) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT pengarang_pkey PRIMARY KEY (id_pengarang)
)

TABLESPACE pg_default;
CREATE TABLE IF NOT EXISTS public.pengembalian
(
    id_pengembalian integer NOT NULL,
    id_peminjaman integer NOT NULL,
    waktu_pengembalian date NOT NULL,
    status_pengembalian character(10) COLLATE pg_catalog."default" NOT NULL,
    kondisi character(10) COLLATE pg_catalog."default" NOT NULL,
    denda integer NOT NULL,
    CONSTRAINT pengembalian_pkey PRIMARY KEY (id_pengembalian),
    CONSTRAINT id_peminjaman FOREIGN KEY (id_peminjaman)
        REFERENCES public.peminjaman (id_peminjaman) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

TABLESPACE pg_default;

```python
print("PostgreSql")
```
![Screenshot (425)](https://user-images.githubusercontent.com/100655325/164622471-05ad9e96-4032-4707-924a-9ff5f5857b88.png)
![Screenshot (426)](https://user-images.githubusercontent.com/100655325/164623084-ff3963b5-d32f-428b-9024-7dc2ba5c49d3.png)
![Screenshot (588)](https://user-images.githubusercontent.com/100655325/164623211-164ad361-c1ae-4661-9c80-3cafc688ebdb.png)
![Screenshot (589)](https://user-images.githubusercontent.com/100655325/164623308-e28dba2f-90aa-4cc0-9b94-d36a52054804.png)
![Screenshot (590)](https://user-images.githubusercontent.com/100655325/164623412-f46646ac-cd45-41d0-936f-7401355c5a15.png)
![Screenshot (591)](https://user-images.githubusercontent.com/100655325/164623640-b0edc659-210f-4ae0-9874-b3dcd56f3b85.png)
![Screenshot (592)](https://user-images.githubusercontent.com/100655325/164623725-2a440bcc-c510-4e12-ad7d-83fea23b2a78.png)
![Screenshot (593)](https://user-images.githubusercontent.com/100655325/164623925-9d121340-c63a-49c7-a285-e513f769304d.png)
![Screenshot (594)](https://user-images.githubusercontent.com/100655325/164624024-a9dd6048-6df9-4efd-9b86-d97a94318e3d.png)



