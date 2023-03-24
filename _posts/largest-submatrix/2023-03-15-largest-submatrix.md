---
title: Finding the largest zero submatrix
date: 2023-03-15 16:01 +07:00
modified:
description:
images:
---
"Finding the largest zero submatrix" atau dalam bahasa Indonesia "menemukan submatriks nol terbesar" mengacu pada tugas untuk mencari submatriks bersebelahan terbesar yang hanya berisikan nol. 
Submatriks adalah himpunan bagian dari matriks yang diperoleh dengan memilih baris dan kolom yang berdekatan. Submatriks nol adalah submatriks yang hanya berisi elemen nol.

Tugas menemukan submatriks nol terbesar sering ditemui dalam ilmu komputer dan analisis data, dan dapat memiliki berbagai aplikasi seperti pemrosesan gambar, pengenalan pola, dan pengelompokan. Ukuran submatriks nol terbesar dapat menjadi faktor penting dalam menentukan kompleksitas atau efisiensi algoritma tertentu.

Contoh nyata untuk menemukan submatriks nol terbesar bisa dalam pemrosesan gambar atau visi komputer. Pertimbangkan gambar yang direpresentasikan sebagai matriks piksel. Katakanlah gambar memiliki sebagian besar latar belakang yang benar-benar hitam (yaitu, semua piksel memiliki nilai nol).

Dalam skenario ini, kita mungkin ingin mengidentifikasi wilayah persegi panjang terbesar dari gambar yang benar-benar hitam, yang dapat berguna untuk tugas seperti deteksi objek, segmentasi gambar, atau penghapusan latar belakang.

Dengan menemukan submatriks nol terbesar dalam matriks gambar, kita dapat menemukan wilayah latar belakang hitam secara efisien, dan kemudian melakukan operasi yang diinginkan. 

### Algoritma
Elements of the matrix will be a[i][j], where i = 0...n - 1, j = 0... m - 1. For simplicity, we will consider all non-zero elements equal to 1.

#### Tahap 1
Pertama, kita hitung matriks "bantu" berikut: d[i][j], baris terdekat yang memiliki 1 di atas a[i][j]. d[i][j] adalah nomor baris terbesar (dari 0 ke i -1)

irst, we calculate the following auxiliary matrix: d[i][j], nearest row that has a 1 above a[i][j]. Formally speaking, d[i][j] is the largest row number (from 0 to i - 1), in which there is a element equal to 1 in the j-th column. While iterating from top-left to bottom-right, when we stand in row i, we know the values from the previous row, so, it is enough to update just the elements with value 1. We can save the values in a simple array d[i], i = 1...m - 1, because in the further algorithm we will process the matrix one row at a time and only need the values of the current row.
```c++
vector<int> d(m, -1);
for (int i = 0; i < n; ++i) {
    for (int j = 0; j < m; ++j) {
        if (a[i][j] == 1) {
            d[j] = i;
        }
    }
}
```
