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
i = 5
while jumlah > 0:
    print("nilai i sekarang adalah", i)
    i -= 1
```
Kode di atas adalah contoh sederhana penggunaan ```while``` loop di python. Kode tersebut dapat kita terjemahkan secara sederhana bahwa kode ```print(jumlah)``` dan ```jumlah -= 1``` akan dieksekusi secara berulang selama kondisi ```jumlah > 0``` masih terpenuhi sehingga ketika jumlah nilainya sama dengan atau lebih kecil dari 0 maka kode akan berhenti. Jika kode tersebut kita eksekusi, maka output berikut akan muncul:
```
nilai i sekarang adalah 5
nilai i sekarang adalah 4
nilai i sekarang adalah 3
nilai i sekarang adalah 2
nilai i sekarang adalah 1
```

