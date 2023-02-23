---
title: Analisis Data dengan R
date: 2023-02-22 13:30:00 +07:00
modified: 2023-02-23 08:00:00 +07:00
tags: [R, statistics]
description:
image: 
---
#### Membaca file di R
Sebelum mulai mengolah data dengan R, kita terlebih dahulu harus tahu cara membaca file dalam berbagai format menggunakan R. Jenis file yang umum digunakan untuk menyimpan data adalah excel dan csv. Selain itu kita juga harus paham cara R membaca `filepath` untuk masing-masing OS; Linux, Windows maupun macOs. 

Berikut adalah cara membaca file excel di windows:
```R
data_saya <- read.excel(filepath)
```
Berikut adalah cara membaca file excel di linux:
```R
data_saya <- read.excel(filepath)
```
Berikut adalah cara membaca file excel di linux:
```R
data_saya <- read.excel(filepath)
```

#### Menginstall R packages
Ketika mengolah data, tentu kita ingin mengerjakan data dengan cepat tanpa harus dipusingkan dengan pembuatan fungsi untuk menyelesaikan perhitungan tertentu. R menyediakan banyak <em>packages</em> yang dapat didownload melalui CRAN. Berikut adalah fungsi R yang dapat kita gunakan untuk mendownload dan menginstal paket R:
```R
install.packages("nama packages")
```
