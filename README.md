# UAS_py
## Praktikum UAS
### Membuat package dan modul dengan struktur seperti berikut:

- daftar_nilai.py berisi modul untuk tambah data, ubah data, cari data, hapus data
- cetak_nilai.py berisi modul untuk cetak daftar nilai, cetak hasil pencarian
- input_nilai.py berisi modul untuk input data yang diminta pengguna untuk memasukkan data
- main.py berisi program secara keseluruhan



### Ini adalah gambar dari Susunan package dan modul:

![1](https://user-images.githubusercontent.com/92704969/149062245-a3b04ec4-0e13-404e-86d4-2755adbf75fc.png)


### Dibawah ini adalah code-code dari program tersebut

- Code syntax program daftar_nilai.py:

```python
from view.input_nilai import *
dataMahasiswa = {}
def tambah_data():
    global dataMahasiswa
    nama = input_nama()
    nim = input_nim()
    nilaiTugas = input_nilaiTugas()
    nilaiUts = input_nilaiUts()
    nilaiUas = input_nilaiUas()
    nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
    dataMahasiswa[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
    print("\nData Berhasil Ditambahkan!")
    return dataMahasiswa
def ubah_data():
    nama = input("Masukkan Nama: ")
    if nama in dataMahasiswa.keys():
        nim = input_nim()
        nilaitugas = input_nilaiTugas()
        nilaiUts = input_nilaiUts()
        nilaiUas = input_nilaiUas()
        nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
        dataMahasiswa[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
        print("\nData Berhasil Di Update!")
    else:
        print("Data tidak ditemukan!")
def hapus_data():
    nama = input("Masukkan Nama:  ")
    if nama in dataMahasiswa.keys():
        del dataMahasiswa[nama]
        print("Data",nama, "Telah dihapus!")
    else:
        print("Data Mahasiswa Tidak Ada".format(nama))
```

- Code syntax program view_nilai.py:
```python
from model.daftar_nilai import *
def cetak_daftar_nilai():
    if dataMahasiswa.items():
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        i = 0
        for x in dataMahasiswa.items():
            i += 1
            print("| {6:2} | {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6} |".format(x[0], x[1][0], x[1][1], x[1][2], x[1][3], x[1][4], i))
        print("==================================================================")
    else:
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        print("|                          TIDAK ADA DATA!                       |")
        print("==================================================================")
def cetak_hasil_pencarian():
    nama = input("Masukkan Nama        : ")
    if nama in dataMahasiswa.keys():
        print("\n                   DAFTAR NILAI MAHASISWA                   ")
        print("==============================================================")
        print("|     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir  |")
        print("==============================================================")
        print("| {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6}  |".format(nama, dataMahasiswa[nama][0], dataMahasiswa[nama][1], dataMahasiswa[nama][2], dataMahasiswa[nama][3], dataMahasiswa[nama][4]))
        print("==============================================================")
    else:
        print("Datanya {0} Tidak Ada ".format(nama))
```

- Code syntax program input_nilai.py:
```python
def input_nama():
    global nama
    nama = input("Masukkan Nama        : ")
    return nama
def input_nim():
    global nim
    nim = input("Masukkan NIM         : ")
    return nim
def input_nilaiTugas():
    global nilaiTugas
    nilaiTugas = int(input("Masukkan Nilai Tugas : "))
    return nilaiTugas
def input_nilaiUts():
    global nilaiUts
    nilaiUts = int(input("Masukkan Nilai UTS   : "))
    return nilaiUts
def input_nilaiUas():
    global nilaiUas
    nilaiUas = int(input("Masukkan Nilai UAS   : "))
    return nilaiUas
```

- Code syntax program main.py:
```python
from view.cetak_nilai import *
while True:
    c = input("\nT)ambah, U)bah, C)ari, H)apus, L)ihat, K)eluar: ")
    if c.lower() == 't':
        tambah_data()
    elif c.lower() == 'u':
        ubah_data()
    elif c.lower() == 'c':
        cetak_hasil_pencarian()
    elif c.lower() == 'h':
        hapus_data()
    elif c.lower() == 'l':
        cetak_daftar_nilai()
    elif c.lower() == 'k':
        break
    else:
        print("Menu yang anda maksud tidak tersedia, Silahkan pilih menu yang tersedia")
```


### Dan dibawah adalah tampilan dari hasil programnya

- Dibawah adalah hasil program ketika dijalankan, dan memasukan perintah untuk Tambah data, dengan input T

![2](https://user-images.githubusercontent.com/92704969/149062248-0b8cc34e-0d6f-4b52-b09f-d02c410babb9.png)


- Dibawah adalah hasil ketika program dijalankan, dan memasukkan perintah untuk melihat data dengan input L

![3](https://user-images.githubusercontent.com/92704969/149062249-a8801d88-5c68-4873-8308-4d752619f0b1.png)

- Dibawah adalah hasil program ketika dijalankan, dan memasukkan perintah untuk tambah data, dengan input T 

![4](https://user-images.githubusercontent.com/92704969/149062252-a06b20b6-5931-484d-a42f-519fafda242c.png)

- Dibawah adalah hasil ketika program dijalankan, dan memasukkan perintah untuk melihat data dengan input L, maka akan menampilkan seluruh data yang telah di inputkan sebelumnya

![5](https://user-images.githubusercontent.com/92704969/149062253-fb46013d-4b4c-4edf-a5bd-e7519a7d550f.png)

- Dibawah adalah hasil program ketika dijalankan, dan memasukkan perintah untuk mengubah data, dengan input U

![6](https://user-images.githubusercontent.com/92704969/149062256-1f131939-ad90-45ec-9576-b5d55e8cd2c1.png)

- Dibawah adalah hasil ketika program dijalankan, dan memasukkan perintah untuk melihat data dengan input L, untuk menampilkan data yang telah di ubah sebelumnya

![7](https://user-images.githubusercontent.com/92704969/149062257-ea45170b-ba5b-44ae-afcc-d9424da5fa5b.png)

- Dibawah adalah hasil ketika program dijalankan, dan memasukkan perintah untuk hapus data yang telah di input sebelumnya, dengan input perintah H, lalu masukkan nama yang akan di hapus

![8](https://user-images.githubusercontent.com/92704969/149062258-0cb70a38-df75-4e5e-a461-ed4d919f4cd5.png)

- Dibawah adalah hasil ketika program dijalankan, dam melihat data apakah sudah terhapus atau belum, dengan input L

![9](https://user-images.githubusercontent.com/92704969/149062259-4dd62bf6-72cb-4cb9-b7aa-a01d61c223f5.png)

- Dan dibawah adalah hasil ketika program dijalankan dan input K untuk keluar dari program

![10](https://user-images.githubusercontent.com/92704969/149062262-5816d905-1c3b-4d8d-a511-21a352d43433.png)



### SEKIAN, TUGAS UAS YANG BERISI PENJELASAN TENTANG PACKAGE DAN MODUL SERTA HASIL DARI PROGRAM TERSEBUT MENGGUNAKAN BAHASA PEMROGRAMAN PYTHON MELALUI APLIKASI PYCHARM, TERIMAKASIH