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

## ER DIAGRAM
![Untitled](https://user-images.githubusercontent.com/100655325/176494114-e5896729-4569-46d2-ada2-c8205f00bf35.png)

## query SQL
## DDL
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

ALTER TABLE IF EXISTS public.admin
    OWNER to postgres;

CREATE TABLE IF NOT EXISTS public.genre
(
    id_genre integer NOT NULL,
    nama_genre character(20) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT genre_pkey PRIMARY KEY (id_genre)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.genre
    OWNER to postgres;

CREATE TABLE IF NOT EXISTS public.penerbit
(
    id_penerbit integer NOT NULL,
    nama_penerbit character(25) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT penerbit_pkey PRIMARY KEY (id_penerbit)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.penerbit
    OWNER to postgres;

CREATE TABLE IF NOT EXISTS public.pengarang
(
    id_pengarang integer NOT NULL,
    nama_pengarang character(20) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT pengarang_pkey PRIMARY KEY (id_pengarang)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.pengarang
    OWNER to postgres;

CREATE TABLE IF NOT EXISTS public.komik
(
    id_komik integer NOT NULL,
    id_genre integer NOT NULL,
    id_pengarang integer NOT NULL,
    id_penerbit integer NOT NULL,
    judul_komik character varying(100) COLLATE pg_catalog."default" NOT NULL,
    tahun_rilis character(4) COLLATE pg_catalog."default" NOT NULL,
    jumlah integer NOT NULL,
    CONSTRAINT komik_pkey PRIMARY KEY (id_komik),
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

ALTER TABLE IF EXISTS public.komik
    OWNER to postgres;
-- Index: fki_id_genre

-- DROP INDEX IF EXISTS public.fki_id_genre;

CREATE INDEX IF NOT EXISTS fki_id_genre
    ON public.komik USING btree
    (id_genre ASC NULLS LAST)
    TABLESPACE pg_default;
-- Index: fki_id_penerbit

-- DROP INDEX IF EXISTS public.fki_id_penerbit;

CREATE INDEX IF NOT EXISTS fki_id_penerbit
    ON public.komik USING btree
    (id_penerbit ASC NULLS LAST)
    TABLESPACE pg_default;
-- Index: fki_id_pengarang

-- DROP INDEX IF EXISTS public.fki_id_pengarang;

CREATE INDEX IF NOT EXISTS fki_id_pengarang
    ON public.komik USING btree
    (id_pengarang ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE TABLE IF NOT EXISTS public.gudang
(
    id integer NOT NULL,
    id_admin integer,
    id_komik integer,
    rak character varying(2) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT gudang_pkey PRIMARY KEY (id),
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

ALTER TABLE IF EXISTS public.gudang
    OWNER to postgres;
-- Index: fki_id_komik

-- DROP INDEX IF EXISTS public.fki_id_komik;

CREATE INDEX IF NOT EXISTS fki_id_komik
    ON public.gudang USING btree
    (id_komik ASC NULLS LAST)
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

ALTER TABLE IF EXISTS public.member
    OWNER to postgres;

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

ALTER TABLE IF EXISTS public.peminjaman
    OWNER to postgres;
-- Index: fki_id_admin

-- DROP INDEX IF EXISTS public.fki_id_admin;

CREATE INDEX IF NOT EXISTS fki_id_admin
    ON public.peminjaman USING btree
    (id_admin ASC NULLS LAST)
    TABLESPACE pg_default;
-- Index: fki_id_member

-- DROP INDEX IF EXISTS public.fki_id_member;

CREATE INDEX IF NOT EXISTS fki_id_member
    ON public.peminjaman USING btree
    (id_member ASC NULLS LAST)
    TABLESPACE pg_default;

-- Table: public.pengembalian

-- DROP TABLE IF EXISTS public.pengembalian;

CREATE TABLE IF NOT EXISTS public.pengembalian
(
    id_pengembalian integer NOT NULL,
    id_peminjaman integer NOT NULL,
    waktu_pengembalian date NOT NULL,
    denda integer NOT NULL,
    status_pengembalian pengembalian_status NOT NULL,
    kondisi kondisi_status NOT NULL,
    id_member integer,
    id_admin integer,
    id_komik integer,
    CONSTRAINT pengembalian_pkey PRIMARY KEY (id_pengembalian),
    CONSTRAINT id_admin FOREIGN KEY (id_admin)
        REFERENCES public.admin (id_admin) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
        NOT VALID,
    CONSTRAINT id_komik FOREIGN KEY (id_komik)
        REFERENCES public.komik (id_komik) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
        NOT VALID,
    CONSTRAINT id_member FOREIGN KEY (id_member)
        REFERENCES public.member (id_member) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
        NOT VALID,
    CONSTRAINT id_peminjaman FOREIGN KEY (id_peminjaman)
        REFERENCES public.peminjaman (id_peminjaman) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.pengembalian
    OWNER to postgres;
-- Index: fki_id_peminjaman

-- DROP INDEX IF EXISTS public.fki_id_peminjaman;

CREATE INDEX IF NOT EXISTS fki_id_peminjaman
    ON public.pengembalian USING btree
    (id_peminjaman ASC NULLS LAST)
    TABLESPACE pg_default;

```

## DML
```sql
INSERT INTO public."admin" (id_admin,nama_admin,username_admin,pass_admin,alamat_admin,no_telepon) VALUES
	 (1,'Pixelle Zaaki','pixellezaak05','ilymywaifu05','cibiru','087722441001');
```

```sql
INSERT INTO public.gudang (id,id_admin,id_komik,rak) VALUES
	 (1,1,1,'1A'),
	 (2,1,2,'1A'),
	 (3,1,3,'1B'),
	 (4,1,4,'1C'),
	 (5,1,5,'1C'),
	 (6,1,6,'1D'),
	 (7,1,6,'1D'),
	 (8,1,6,'1E'),
	 (9,1,6,'1F'),
	 (10,1,6,'1F'); 
```

```sql
INSERT INTO public.genre (id_genre,nama_genre) VALUES
	 (1,'Romance             '),
	 (2,'Drama               '),
	 (3,'Comedy              '),
	 (4,'Slice of life       '),
	 (5,'Music               '),
	 (6,'Sport               '),
	 (7,'Sci-fi              '),
	 (8,'Fantasy             '),
	 (9,'Harem               '),
	 (10,'Echi                '),
	 (11,'Horror              '),
	 (12,'Thriller            ');

```

```sql
INSERT INTO public.penerbit (id_penerbit,nama_penerbit) VALUES
	 (1,'Square Enix              '),
	 (2,'Shueisha                 '),
	 (3,'Bessatsu Margaret        '),
	 (4,'Kodansha                 '),
	 (5,'Naver Corporation        '),
	 (6,'Hakusensha               ');
```

```sql
INSERT INTO public.pengarang (id_pengarang,nama_pengarang) VALUES
	 (1,'Daisuke Hagiwara    '),
	 (2,'Naoshi Komi         '),
	 (3,'Io Sakisaka         '),
	 (4,'Takeshi Obata       '),
	 (5,'Negi Haruba         '),
	 (6,'Sou Yayoi           '),
	 (7,'Ichigo Takano       '),
	 (8,'Natsuki Tayaka      '),
	 (9,'Mizuho Kusanagi     '),
	 (10,'Miki Yoshikawa      ');
```
```sql
INSERT INTO public.komik (id_komik,id_genre,id_pengarang,id_penerbit,judul_komik,tahun_rilis,jumlah) VALUES
	 (1,1,1,1,'Horimiya','2011',10),
	 (2,1,2,2,'Nisekoi','2011',9),
	 (3,1,3,2,'Ao Haru Ride','2011',10),
	 (4,1,4,2,'Bakuman','2008',8),
	 (5,1,5,4,'Gotoubun no Hanayome','2017',15),
	 (6,1,6,5,'ReLife','2013',13),
	 (7,1,7,2,'Orange','2012',12),
	 (8,1,8,6,'Fruits Basket','1998',10),
	 (9,1,9,6,'Akatsuki no Yona','2009',9),
	 (10,1,10,4,'Yamada-kun to 7-nin no Majo','2012',7);
```


```sql
INSERT INTO public."member" (id_member,nama_member,alamat_member,no_telepon_member) VALUES
	 (1,'Zaki','Cipadung','085623451100'),
	 (2,'Naufal','Cibiru','08900887766 '),
	 (3,'Anastasia','Manisi','085577663421');
```

```sql
INSERT INTO public.peminjaman (id_peminjaman,id_admin,id_komik,id_member,waktu_peminjaman,jatuh_tempo) VALUES
	 (1,1,1,1,'2022-06-23','2022-07-23'),
	 (2,1,1,2,'2022-06-24','2022-07-24'); 
```

```sql
INSERT INTO public.pengembalian(
	id_pengembalian, id_peminjaman, waktu_pengembalian, denda, status_pengembalian, kondisi, id_member, id_admin, id_komik)
	VALUES (1, 1, '2022-07-23', 0, 'sudah', 'baik', 1, 1, 1),(2, 2, '2022-07-24', 0, 'sudah', 'baik', 2, 1, 1);
```
## DQL
### data gudang
```sql
select g.rak,count(*) as jumlah_Komik from komik k  inner join gudang g on g.id_komik = k.id_komik group by g.rak order by g.rak;
```

### data komik
```sql
SELECT
	komik.id_komik,
	judul_komik,
	genre.nama_genre,
    pengarang.nama_pengarang,
    penerbit.nama_penerbit,
	komik.tahun_rilis,
    komik.jumlah
FROM
	komik
INNER JOIN genre 
    ON komik.id_genre = genre.id_genre
INNER JOIN pengarang
    on komik.id_pengarang = pengarang.id_pengarang
inner JOIN penerbit
    on komik.id_penerbit = penerbit.id_penerbit
ORDER BY judul_komik
```
```sql
SELECT p.nama_penerbit,count(*) as jumlah_Komik FROM komik k  inner join penerbit p on p.id_penerbit = k.id_penerbit group by k.id_penerbit, p.nama_penerbit;
```

### data peminjaman
```sql
SELECT
	peminjaman.id_peminjaman,
	admin.nama_admin,
	komik.judul_komik,
	member.nama_member,
    peminjaman.waktu_peminjaman,
    peminjaman.jatuh_tempo
FROM
	peminjaman
INNER JOIN admin
    ON peminjaman.id_admin = admin.id_admin
INNER JOIN komik
    ON peminjaman.id_komik = komik.id_komik
INNER JOIN member
    on peminjaman.id_member = member.id_member
```
### data pengembalian
```sql
SELECT
	pengembalian.id_pengembalian,
	member.nama_member,
    admin.nama_admin,
	komik.judul_komik,
	pengembalian.waktu_pengembalian,
    pengembalian.status_pengembalian,
    pengembalian.kondisi,
    pengembalian.denda
FROM
    pengembalian
INNER JOIN member
    on member.id_member = pengembalian.id_member
INNER JOIN admin
    on admin.id_admin = pengembalian.id_admin
INNER JOIN komik
    ON komik.id_komik = pengembalian.id_komik
ORDER BY id_pengembalian

```

### Create data type
```sql
CREATE TYPE public.kondisi_status AS ENUM
    ('baik', 'rusak', 'hilang');
```
```sql
CREATE TYPE public.pengembalian_status AS ENUM
    ('sudah', 'belum');
```
