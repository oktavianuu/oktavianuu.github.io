---
title: Kurva Pertumbuhan dengan GAMLSS
date: 2023-02-20 03:52:00 +07:00
modified:
tags: [Gamlss, R, Machine Learning, Statistics]
description: cara menentukan kurva pertumbuhan menggunakan R dan gamlss.
---

Estimasi sentil mencakup metode untuk memprediksi pertumbuhan manusia terkait usia. Estimasi standar kurva sentil terdiri dua variabel:
1. Variabel respon, yaitu variabel yang akan dicari kurva sentilnya, contohnya berat badan, BMI, lingkar kepala dll.
2. Variabel penjelas, misalnya usia.

#### Model LMS dan Extensinya
Untuk menentukan percentile kurva pertumbuhan dapat menggunakan metode LMS (Lambda, Mu, Sigma). Lms dapat difit dengan GAMLSS:
```R rumus lms nanti tambahkan```

dimana fY() adalah suatu distribusi, khususnya BCCG (Box-Cox Cole and Green), BCPE (Box-Cox power exponential), dan BCT (Box-Cox t).

* a BCCG by assuming that the response variable has , which is suitable for positively or negatively skewed data with Y > 0
* a BCPE assumes that the transformed random variable Z has a truncated power exponential distribution
* a BCT assumes that Z has a truncated t distribution 
Y = head circumference and X = AGE

Berikut adalah tutorial estimasi percentil dan pembuatan kurva pertumbuhan menggunakan R dan R Studio. 

Langkah pertama adalah memasukan library yang diperlukan dengan memasukan kode berukut ke pada console R studio.
```R
library(repmis)
library(ggplot2)
library(gamlss)
library(tidyverse)
```
Kemudian memasukkan data yang akan digunakan dengan mengetikkan perintah berikut:
```R
source_data("https://github.com/cran/expectreg/blob/master/data/dutchboys.rda?raw=True")
``` 

Ketikkan perintah berikut untuk menampilkan dimensi data
```R
dim(dutchboys)
```
Pastikan muncul output berikut:
```R 
[1] 6848 10
```
Ketikkan command berikut untuk menampilkan nama-nama kolom pada dataset:
```R 
names(dutchboys)
```
Pastikan output berikut muncul:
```R
[1] "defnr" "age"   "hgt"   "wgt"   "hc"    "hgt.z" "wgt.z" "hc.z"  "bmi.z" 
[10] "hfw.z"
```
Untuk melihat pola sebaran data, kita dapat membuat plot menggunakan bantuan library ggplot2 yang telah kita masukkan sebelumnya. Berikut adalah script ggplot2 untuk memploting dataset:
```R
ggplot(dutchboys, aes(x=age, y=hc)) +
  geom_point(shape = 1, color = "#0052bb", size = 1.5) + 
  ggtitle("The Dutch boys data") +
  xlab("age") + ylab("head circumference") +
  theme_bw()
```


