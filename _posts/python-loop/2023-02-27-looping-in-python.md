---
title: python loop
date: 2023-02-27 13:20:00 +07:00
modified:
tags: [programming, python, loop]
description:
image: 
---

Loop dalam pemrograman secara harafiah dapat diartikan sebagai kode yang digunakan untuk melakukan pengulangan pada data. Loop memungkinkan kita untuk mengulangi suatu proses tanpa membuat kode pengulangan secara berulang. Python menyediakan dua jenis loop yaitu ```while``` dan ```for``` loop. 

##### while loop
```while``` loop mengeksekusi satu perintah atau sekumpulan perintah selama kondisi yang kita tetapkan masih berlaku (```True```). Secara umum, struktur dari while loop adalah sebagai berikut:
```python
while True:
    # body while loop
```
Implementasi ```while``` loop dapat dilihat pada contoh berikut:
```python
jumlah = 5
while jumlah > 0:
    print(jumlah)
    jumlah -= 1
```
Kode di atas adalah contoh sederhana penggunaan ```while``` loop