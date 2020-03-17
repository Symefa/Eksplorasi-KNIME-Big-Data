# Eksplorasi KNIME Big Data

Oleh : Alifa Izzan


## Daftar Isi
- [Eksplorasi KNIME Big Data](#eksplorasi-knime-big-data)
  - [Daftar Isi](#daftar-isi)
  - [DB Exercise](#db-exercise)
    - [01_DB_Connect](#01dbconnect)
    - [02_DB_InDB_Processing](#02dbindbprocessing)
    - [03_DB_Modeling](#03dbmodeling)
    - [04_DB_WritingToDB](#04dbwritingtodb)
  - [Hadoop Exercise](#hadoop-exercise)
    - [00_Setup_Hive_Table](#00setuphivetable)
    - [01_Hive_Modelling](#01hivemodelling)
    - [02_Hive_WritingToDB](#02hivewritingtodb)


## DB Exercise

### 01_DB_Connect
- Merubah nama tabel dengan menggunakan software manajemen dbms navicat 
  ![rename](assets/Annotation%2C2020-03-17%2C181151.jpg "Rename Table")
- Pertama tambahkan node sqlite connector
![sqlite](assets/Annotation%2C2020-03-17%2C194817.jpg "Add")
- Selanjutnya menambahkan node tabel selector untuk memilih tabel yang ingin di proses
![sqliteselector](assets/Annotation%2C2020-03-17%2C195322.jpg)
- Setelah selesai ini hasil nodenya
![dbreader](assets/Annotation%2C2020-03-17%2C195839.jpg)
- Jika konfigurasi sudah benar maka saat view data table akan muncul
![dtable](assets/Annotation%2C2020-03-17%2C214324.jpg)

### 02_DB_InDB_Processing
- kali ini sudah disediakan sebagai berikut
![sedia](assets/Annotation%2C2020-03-17%2C215128.jpg)
- konfigurasikan sesuai arahan dari nama node
- Melakukan join tabel (serialno) dengan mengexclud pwgtp* dan puma*
![puma](assets/Annotation%2C2020-03-17%2C220249.jpg) 
- hasilnya sebagai berikut
![resjoin](assets/Annotation%2C2020-03-17%2C220447.jpg)
- selanjutnya mefilter cow is null dan cow is not null dari tabel s13pme
![filter](assets/Annotation%2C2020-03-17%2C220813.jpg)
- cow is null
![cownull](assets/Annotation%2C2020-03-17%2C220942.jpg)
- cow is not null
![cownotnull](assets/Annotation%2C2020-03-17%2C221014.jpg)
- selanjutnya mengaverage agep dan group by sex dengan node group by
![avgagep](assets/Annotation%2C2020-03-17%2C222125.jpg)
- berikut hasil avg agep nya
![hasilagep](assets/Annotation%2C2020-03-17%2C222305.jpg)
- dan ini hasil node nya
![node02indb](assets/Annotation%2C2020-03-17%2C222530.jpg)

### 03_DB_Modeling
- konfigurasikan db sesuai setting anda pada step sebelumnya
![dbmodel](assets/Annotation%2C2020-03-17%2C223919.jpg)
- selanjutnya untuk mencoba decission tree kita hapus dulu beberapa value dari cow menggunakan navicat
![remove](assets/Annotation%2C2020-03-17%2C224244.jpg)
- hasil pada knime akan seperti ini
![removeres](assets/Annotation%2C2020-03-17%2C224355.jpg)
- tambahkan decission tree learner
![decs](assets/Annotation%2C2020-03-17%2C224624.jpg)
- jika berhasil tambahkan node decision tree to img untuk menampilkan gambar decission tree
![desimg](assets/Annotation%2C2020-03-17%2C224953.jpg)
- selanjutnya tambahkan decission tree predictor
![descpre](assets/Annotation%2C2020-03-17%2C225337.jpg)
- berikut hasil final node knime
![hasdes](assets/Annotation%2C2020-03-17%2C225435.jpg)

### 04_DB_WritingToDB
- step awal konfigurasikan node sesuai konfigurasi pada step sebelumnya
![konfigDB](assets/Annotation%2C2020-03-17%2C225656.jpg)
- Tambahkan node DB update
![dbup](assets/Annotation%2C2020-03-17%2C230259.jpg)
- setelah dijalankan kita lihat data cow yang tadi telah kita hapus berhasil terupdate pada navicat
![naviuo](assets/Annotation%2C2020-03-17%2C230500.jpg)


## Hadoop Exercise

### 00_Setup_Hive_Table
- buka file exercisenya lalu akan muncul node seperti ini
![hivenode](assets/Annotation%2C2020-03-17%2C233318.jpg)
- setting table reader dan arahkan ke file .table
![hpeset](assets/Annotation%2C2020-03-17%2C233558.jpg)
- lakukan pada kedua tabel reader
- perbarui data tabel untuk menambahkan prefiks nrp dengan mengatur node DB Table Creator
![asdf](assets/Annotation%2C2020-03-17%2C233819.jpg)
- jalankan semua node dan ini hasilnya
![res1](assets/Annotation%2C2020-03-17%2C234935.jpg)

### 01_Hive_Modelling
- buka file exercise lalu ganti node awal dengan node hive connector
![nodebig](assets/Annotation%2C2020-03-17%2C235507.jpg)
- konfigurasi node hive connector
![setupnode](assets/Annotation%2C2020-03-17%2C235915.jpg)
- jangan lupa menambahkan prefix nrp pada db tabel selector
- jika tutorial sebelumnya berhasil dijalankan maka semua node akan berhasil di eksekusi
![asdkka](assets/Annotation%2C2020-03-18%2C000254.jpg)

### 02_Hive_WritingToDB
- untuk latihan selanjutnya buka file exercise lalu jalankan node pertama.
- setelah itu atur db tabel selector
![asdkas](assets/Annotation%2C2020-03-18%2C000945.jpg)
- setelah selesai mengatur jalankan semua node
![semua](assets/Annotation%2C2020-03-18%2C000965.jpg)
- lalu tambahkan db tabel creator
![creator](assets/Annotation%2C2020-03-18%2C001354.jpg)
- selanjutnya tambahkan node db loader dan atur seperti pada gambar berikut
![aturlah](assets/Annotation%2C2020-03-18%2C001841.jpg)
- jika semua step telah berhasil dijalankan maka saat kita query menggunakan hive gui akan muncul sebagai berikut
  ![hasual](assets/Annotation%2C2020-03-18%2C001957.jpg)