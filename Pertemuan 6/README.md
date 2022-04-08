

#### Tabel Admin
|🔑IDadmin|nama_admin|username_admin|pass_admin|alamat_admin|no_telepon|
|---|---|---|---|---|---|
|1|Pharaoh|pharaoh05|phara005|mesir|087745671111|
|2|Ozymandias|ozyman00|ozyy12|mesir|087899881212|
|3|Nero|neroc09|neronero0|roma|088827271313|
#### Tabel Komik
|🔑IDkomik|IDGenre|IDPengarang|IDPenerbit|judul_komik|tahun_rilis|
|---|---|---|---|---|---|
|1|1|1|1|nisekoi|2011|
|2|1|2|2|Kanojo  Okarishimasu|2017|
|3|1|3|3|Yahari Ore no Seishun Love Comedy wa Machigatteiru|2011|
#### Tabel genre
|🔑IDGenre|nama_genre|
|---|---|
|1|Romantis|
|2|Aksi|
|3|Fantasi|

#### Tabel Pengarang
|🔑IDPengarang|nama_pengarang|
|---|---|
|1|Komi Naoshi|
|2|Miyajima Reiji|
|3|Watari Wataru|


#### Tabel Penerbit
|🔑IDPengarang|nama_pengarang|
|---|---|
|1|Shueisha |
|2|Kondansha|
|3|Shogakukan|

#### Tabel Member
|🔑IDMember|nama_member|alamat_member|no_telepon_member|
|---|---|---|---|
|1|rira|cileunyi|084511223467|
|2|rara|cipadung|087722445362|
|3|rora|manisi|089700998739|

#### Tabel Peminjaman
|🔑IDPeminjaman|IDadmin|IDkomik|IDMember|waktu_peminjaman|jatuh_tempo|
|---|---|---|---|---|---|
|1|1|1|1|2022-04-01 13:40:42|2022-05-01 13:40:42|
|2|1|2|2|2022-04-01 14:00:00|2022-05-01 14:00:00|
|3|1|3|3|2022-04-02 08:00:00|2022-05-02 08:00:00|

#### Tabel Pengembalian
|🔑IDPengembalian|IDPeminjaman|waktu_pengembalian|status_pengembalian|kondisi_komik|Denda|
|---|---|---|---|---|---|
|1|1|2022-05-01 13:40:42|Sudah|baik|0|
|2|2|-|Belum|-|-|
|3|3|-|Belum|-|-|
---
