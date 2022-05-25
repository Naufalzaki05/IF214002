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

ALTER TABLE IF EXISTS public.gudang
    OWNER to postgres;
-- Index: fki_id_komik

-- DROP INDEX IF EXISTS public.fki_id_komik;
CREATE INDEX IF NOT EXISTS fki_id_komik
    ON public.gudang USING btree

CREATE TABLE IF NOT EXISTS public.genre
(
    id_genre integer NOT NULL,
    nama_genre character(20) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT genre_pkey PRIMARY KEY (id_genre)
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
    
CREATE TABLE IF NOT EXISTS public.pengembalian
(
    id_pengembalian integer NOT NULL,
    id_peminjaman integer NOT NULL,
    waktu_pengembalian date NOT NULL,
    denda integer NOT NULL,
    status_pengembalian pengembalian_status NOT NULL,
    kondisi kondisi_status NOT NULL,
    CONSTRAINT pengembalian_pkey PRIMARY KEY (id_pengembalian),
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
INSERT INTO ADMIN (id_admin,nama_admin,username_admin,pass_admin,alamat_admin,no_telepon) VALUES (
  '1',
  'pixelle',
  'pixelle05',
  '12345',
  'aka05',
  '085412341111'
); 
```
![Screenshot (654)](https://user-images.githubusercontent.com/100655325/170275946-db9a8921-de63-47de-8ca3-b5e45de104c7.png)

```sql
INSERT INTO gudang (id_rak,id_admin,id_komik) VALUES (
  '1',
  '1',
  '1'
); 
```
![Screenshot (653)](https://user-images.githubusercontent.com/100655325/170275750-e6275556-7d09-4fae-ac39-c5270698ecd2.png)

```sql
INSERT INTO genre (id_genre,nama_genre) VALUES (
  '1',
  'fantasy'
); 
```
![Screenshot (652)](https://user-images.githubusercontent.com/100655325/170275394-d64e28c5-c06c-4dd0-a3f5-b3bc9a6ef7c6.png)

```sql
INSERT INTO penerbit (id_penerbit,nama_penerbit) VALUES (
  '1',
  'KakaoPage'
); 
```
![Screenshot (651)](https://user-images.githubusercontent.com/100655325/170275126-bcce8f47-0bee-4e82-aa38-62f428a0cb1f.png)

```sql
INSERT INTO pengarang (id_pengarang,nama_pengarang) VALUES (
  '',
  'Chugong'
);
```
![Screenshot (650)](https://user-images.githubusercontent.com/100655325/170274867-939a9a5e-ec76-4662-aeda-c2daa851f8a3.png)

```sql
INSERT INTO komik (id_komik,id_genre,id_pengarang,id_penerbit,judul_komik,tahun_rilis,jumlah) VALUES (
  '1',
  '1',
  '1',
  '1',
  'Solo Levelling',
  '2016',
  '10'
); 
```
![Screenshot (649)](https://user-images.githubusercontent.com/100655325/170274668-75759426-56f0-4189-be4c-e2bc143802a7.png)

```sql
INSERT INTO MEMBER (id_member,nama_member,alamat_member,no_telepon_member) VALUES (
  '1',
  'zaki',
  'cibiru',
  '085218907635'
); 
```
![Screenshot (648)](https://user-images.githubusercontent.com/100655325/170274395-11378059-3827-4515-9e74-d6b509170124.png)

```sql
INSERT INTO peminjaman (id_peminjaman,id_admin,id_komik,id_member,waktu_peminjaman,jatuh_tempo) VALUES (
  '1',
  '1',
  '1',
  '1',
  '2022-05-25',
  '2022-06-25'
); 
```
![Screenshot (647)](https://user-images.githubusercontent.com/100655325/170273940-505391cd-5208-48f8-bf93-80073f8cafef.png)

```sql
INSERT INTO pengembalian (id_pengembalian,id_peminjaman,waktu_pengembalian,denda,status_pengembalian,kondisi) VALUES (
  '1',
  '1',
  '2022-06-25',
  '0',
  'sudah',
  'baik'
);
```
![Screenshot (646)](https://user-images.githubusercontent.com/100655325/170273622-dee2459c-b8b1-4548-ab9e-36994f509f6b.png)

## DQL
### data gudang
```sql
SELECT
	g.id_rak id_rak,
	a.nama_admin nama_admin,
    c.judul_komik judul_komik,
    jumlah
FROM
	gudang g
INNER JOIN admin a
    ON a.id_admin = g.id_rak
INNER JOIN komik c
```
![Screenshot (645)](https://user-images.githubusercontent.com/100655325/170273236-65a3c3b0-6fe6-4dcb-8e9d-a7bd33fea820.png)

### data komik
```sql
SELECT
	c.id_komik id_komik,
	c.judul_komik judul_komik,
    tahun_rilis,
	g.nama_genre nama_genre,
	p.nama_pengarang nama_pengarang,
    q.nama_penerbit nama_penerbit
FROM
	komik c
INNER JOIN genre g
    ON g.id_genre = c.id_komik
INNER JOIN pengarang p 
    ON p.id_pengarang = c.id_komik
INNER JOIN penerbit q
    on q.id_penerbit = c.id_komik
```
![Screenshot (644)](https://user-images.githubusercontent.com/100655325/170272549-db45fbe2-b6f7-479e-bcc2-d6574a8e845e.png)

### data peminjaman
```sql
SELECT
	p.id_peminjaman id_peminjaman,
	a.nama_admin nama_admin,
	c.judul_komik judul_komik,
	m.nama_member nama_member,
    waktu_peminjaman,
    jatuh_tempo
FROM
	peminjaman p
INNER JOIN admin a
    ON a.id_admin = p.id_peminjaman
INNER JOIN komik c
    ON c.id_komik = p.id_peminjaman
INNER JOIN member m
    on m.id_member = p.id_peminjaman
```
![Screenshot (642)](https://user-images.githubusercontent.com/100655325/170272013-e0be0b01-b9c3-4596-a1e8-7f18af9cf2f9.png)

### data pengembalian
```sql
SELECT
	p.id_pengembalian id_pengembalian,
	m.nama_member nama_member,
    a.nama_admin nama_admin,
	c.judul_komik judul_komik,
	waktu_pengembalian,
    status_pengembalian,
    kondisi,
    p.denda denda
FROM
	pengembalian p
INNER JOIN member m
    on m.id_member = p.id_pengembalian
INNER JOIN admin a
    on a.id_admin = p.id_pengembalian
INNER JOIN komik c
    ON c.id_komik = p.id_pengembalian
```
![Screenshot (655)](https://user-images.githubusercontent.com/100655325/170279090-3fca883e-e775-484b-bbb3-9672c02524a4.png)

### Create data type
```sql
CREATE TYPE public.kondisi_status AS ENUM
    ('baik', 'rusak', 'hilang');
```
```sql
CREATE TYPE public.pengembalian_status AS ENUM
    ('sudah', 'belum');
```
