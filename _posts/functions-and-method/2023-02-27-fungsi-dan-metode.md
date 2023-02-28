---
title: fungsi dan metode dalam pemrograman
date: 2023-02-27 19:19:00 +07:00
modified: 
tags: [programming, fungsi, metode, python]
description:
image:
---
Dalam pemrograman, konsep tentang fungsi dan metode sangat penting untuk dipahami. Fungsi dan metode merupakan salah satu konsep paling penting. Fungsi adalah kode yang dibuat khusus untuk melakukan tugas tertentu. Fungsi tidak terikat dengan data, ia menerima data atau bahkan dapat membuat data baru. Sementara itu, metode adalah jenis fungsi spesifik yang sebetulnya sangat mirip dengan fungsi, namun invokasinya berbeda. Selain itu, metode dapat mengubah keadaan suatu data. Membingungkan? 

Berikut adalah perbedaan <em>fungsi</em> dan <em>metode</em> ditinjau dari segi invokasi/ pemanggilannya:

Secara umum pemanggilan fungsi adalah sebagai berikut:
```python
hasil = function(argument)
```
Fungsi menerima satu argumen dan memproduksi hasil.

Sementara itu, pemanggilan metode secara adalah sebagai berikut:
```python
hasil = data.metode(argumen)
```
Kode di atas menunjukkan bahwa dalam pemanggilan metode, didahului oleh data yang "memiliki" metode tersebut. Kemudian diikuti oleh titik (.) dan nama metode dan diakhiri dengan argumen di dalam kurung. 

Metode sangat mirip dengan fungsi, hanya saja metode dapat mengubah keadaan internal data yang memanggilnya (metode tersebut). Berikut adalah contoh penggunaan metode:
```python
nomor = [1, 2, 3, 4, 5]
nomor.append(6)
```
output:
```[1, 2, 3, 4, 5, 6]```

Contoh di atas menggunakan metode append untuk menambahkan satu <em>element</em> pada akhir koleksi data yang ada pada <em>list</em> nomor. Contoh lain penggunaan meotde untuk mengubah keadaan internal suatu data adalah sebagai berikut:
```python
nomor = [1, 2, 3, 4, 5, 6]
nomor.insert(2, 10)
```
Kode di atas menunjukkan metode dengan dua argumen. Argumen pertama (2) adalah lokasi nilai yang akan kita ubah. Argumen kedua (10) adalah nilai yang akan kita masukan ke posisi/index 2 pada list nomor. Hasil dari kode di atas adalah sebagai berikut:
```[1, 2, 10, 4, 5, 6]```

Kita dapat mengkombinasikan metode dengan konsep lain misalnya <em>loop</em> dan <em>list</em> seperti contoh berikut. 
```python
nomor = [] # menginisiasi list kosong untuk menyimpan data yang akan digenerate nanti
for i in range(5):
    nomor.insert(0, i + 1)
print(nomor)
```
kode di atas akan menghasilkan output berikut:
```[1, 2, 3, 4, 5]```


