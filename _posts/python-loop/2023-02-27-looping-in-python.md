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
print("pemeriksaan selesai.")
```
Kode di atas adalah contoh sederhana penggunaan ```while``` loop di python. Kode tersebut dapat kita terjemahkan secara sederhana bahwa kode ```print(jumlah)``` dan ```jumlah -= 1``` akan dieksekusi secara berulang selama kondisi ```jumlah > 0``` masih terpenuhi sehingga ketika jumlah nilainya sama dengan atau lebih kecil dari 0 maka kode akan berhenti. Jika kode tersebut kita eksekusi, maka output berikut akan muncul:
```
nilai i sekarang adalah 5
nilai i sekarang adalah 4
nilai i sekarang adalah 3
nilai i sekarang adalah 2
nilai i sekarang adalah 1
```

##### for loop
```for``` loop mengeksekusi sekumpulan perintah sesuai dengan batas yang ditentukan. Struktur dari ```for``` loop adalah sebagai berikut:
```python
nama = 'oktavianu'
for huruf in nama:
    print(huruf) 
```
Kode di atas akan mengeksesi perintah ```print(huruf)``` hingga selesai dari huruf pertama hingga huruf terakhir dan menampilkannya di konsol/terminal seperti pada output berikut:
```
o
k
t
a
v
i
a
n
u
```

Contoh lain penggunaan ```for``` loop adalah untuk mengeksekusi data dengan range tertentu:
```python
for i in range(5):
    print(i)
```
kode di atas akan dieksekusi sebanyak lima kali dimulai dari 0. Output dari kode di atas adalah sebagai berikut:
```
0
1
2
3
4
```
Dalam penggunaannya, ```while``` dan ```for``` loop sering dikombinasikan dengan ```break``` dan ```continue```. 
* ```break``` digunakan untuk berhenti dari pengulangan
* ```continue``` digunakan untuk melangkahi (skip) iterasi dan beralih ke iterasi berikutnya.
berikut adalah implementasi ```break```:
```python
nama = 'oktavianu'
for i in nama:
    if i == "v":
        break
    print(i, end="")
```
Kode di atas akan berhenti ketika iterasi mencapai huruf 'v'. Berikut adalah output dari kode di atas:
```
okta
```
Bagaimana dengan ```continue```? Berikut adalah implementasinya:
```python
teks = "pyxpyxpyx"
for i in teks:
    if i == "x":
        continue
    print(i, end="")
```
Kode di atas akan melewati ```i == "x"``` yang berarti bahwa huruf x tidak akan dieksekusi oleh ```print(i, end="")```, yang dieksekusi hanya huruf selain huruf x. Berikut adalah outputnya:
```
pypypy
```






