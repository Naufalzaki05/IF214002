## quiz
## Pemanfaatan data historis
- untuk membantu menganalisis/mencari data
- untuk membantu mengelompokann data

## Relasi
karyawan 1 1 --- 1-n historisgaji
karyawan 1 1 --- 1-n historisalamat
karyawan 1 1 --- 1-n historisjabatan

#### Tabel karyawan
|PKIDkaryawan|nama_karyawan|gaji_bulanan|tanggal_mulai_gaji|tanggal_masuk|alamat_sekarang|jabatan_sekarang|
|---|---|---|---|---|---|---|


```sql
CREATE TABLE

databasekaryawan_ tbl(
   karyawan_id INT NOT NULL AUTO_INCREMENT,
   nama_karyawan VARCHAR(100) NOT NULL,
   gaji bulanan INT NOT NULL,
   tanggal_mulai_gaji_DATETIME,
   tanggal_masuk DATETIME,
   alamat_sekarang VARCHAR(100)
   Jabatan_sekarang CHAR(20)
   PRIMARY KEY ( karyawan_id )
);
datahistorigaji_ tbl(
   karyawan_id INT NOT NULL AUTO_INCREMENT,
   gaji bulanan INT NOT NULL,
   tanggal_mulai_gaji_DATETIME,
   PRIMARY KEY ( tanggal_mulai_gaji )
);
datahistorisalamat_ tbl(
   karyawan_id INT NOT NULL AUTO_INCREMENT,
   tanggal_masuk DATETIME,
   alamat_sekarang VARCHAR(100),
   PRIMARY KEY (  tanggal_masuk )
);
datahistorijabatan_ tbl(
   karyawan_id INT NOT NULL AUTO_INCREMENT,
   tanggal_masuk DATETIME,
   Jabatan_sekarang CHAR(20)
   PRIMARY KEY (  tanggal_masuk )
);

```python
print("Quiz Pertemuan 7")
```
