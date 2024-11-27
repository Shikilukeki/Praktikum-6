# Praktikum-6

Nama : Rifqi Maulana

NIM : 312410529

Kelas : TI.24.A.5

# Penjelasan program sederhana tabel data mahasiswa

## Flowchart program :

![Image](https://github.com/Shikilukeki/Foto/blob/main/Flowchart%20%20program%20mendata%20mahasiswa.png?raw=true)

## Penjelasan :

```python
def hitung_nilai_akhir(nilai_tugas, nilai_uts, nilai_uas):
    return (0.3 * nilai_tugas) + (0.35 * nilai_uts) + (0.35 * nilai_uas)

```
Fungsi utama untuk menghitung nilai akhir mahasiswa berdasarkan bobot nilai tugas, UTS, dan UAS.

```python
data_mahasiswa = {}

```
Dictionary untuk menyimpan data mahasiswa

```python
def menu_utama():
    print("Program mendata mahasiswa")
    pilihan = input("[(t)ambah data, (u)bah data, (h)apus data, (l)ihat data, (k)eluar] : ")
    return pilihan
```
Fungsi untuk menapilkan menu utama, pilihan operasi, dan menerima inputan operasi yang akan digunakan pengguna

```python
def tambah():
    while True:
        try:
            nama = input("Masukkan nama: ")
            nim = input("Masukkan NIM: ")
            nilai_tugas = float(input("Masukkan nilai tugas: "))
            nilai_uts = float(input("Masukkan nilai UTS: "))
            nilai_uas = float(input("Masukkan nilai UAS: "))
            
            nilai_akhir = hitung_nilai_akhir(nilai_tugas, nilai_uts, nilai_uas)
            data_mahasiswa[nim] = {
                "nama": nama,
                "nilai_tugas": nilai_tugas,
                "nilai_uts": nilai_uts,
                "nilai_uas": nilai_uas,
                "nilai_akhir": nilai_akhir
            }
            print("Data berhasil ditambahkan.")
            break
        except ValueError:
            print("Input tidak valid. Silakan coba lagi.")
```
Fungsi yang digunakan untuk menyimpan data baru mahasiwa yang diinputkan keadalam dictionary ```data_mahasiswa```

```python
def ubah(nama):
    nama_lower = nama.lower()
    for nim, mahasiswa in data_mahasiswa.items():
        if mahasiswa["nama"].lower() == nama_lower:
            while True:
                try:
                    nama_baru = input("Masukkan nama baru: ")
                    nilai_tugas = float(input("Masukkan nilai tugas baru: "))
                    nilai_uts = float(input("Masukkan nilai UTS baru: "))
                    nilai_uas = float(input("Masukkan nilai UAS baru: "))
                    
                    nilai_akhir = hitung_nilai_akhir(nilai_tugas, nilai_uts, nilai_uas)
                    data_mahasiswa[nim] = {
                        "nama": nama_baru,
                        "nilai_tugas": nilai_tugas,
                        "nilai_uts": nilai_uts,
                        "nilai_uas": nilai_uas,
                        "nilai_akhir": nilai_akhir
                    }
                    print("Data berhasil diubah.")
                    return
                except ValueError:
                    print("Input tidak valid. Silakan coba lagi.")
    print("Data tidak ditemukan.")
```
Fungsi yang digunakan untuk mengubah / menggantikan data mahasiswa yang sudah ada

```python
def hapus_data():
    nim = input("Masukkan NIM mahasiswa yang akan dihapus: ")
    if nim in data_mahasiswa:
        del data_mahasiswa[nim]
        print("Data berhasil dihapus.")
    else:
        print("Data tidak ditemukan.")
```
Fungsi yang berfungsi menghapus data mahasiswa berdasarkan nama mahasiswa

```python
def tampilkan_data():
    print("\nDaftar Data Mahasiswa:")
    print("==========================================================================================")
    print("| No | Nama                      | NIM       | Tugas | UTS   | UAS   | Akhir             |")
    print("==========================================================================================")
    
    if data_mahasiswa:
        for i, (nim, mahasiswa) in enumerate(data_mahasiswa.items(), start=1):
            print(f"| {i:>2} | {mahasiswa['nama']:<25} | {nim:<9} | {mahasiswa['nilai_tugas']:<5} | {mahasiswa['nilai_uts']:<5} | {mahasiswa['nilai_uas']:<5} | {mahasiswa['nilai_akhir']:<17.2f} |")
            print("==========================================================================================")
    else:
        print("|                             Belum ada data mahasiswa                                  |")
        print("==========================================================================================")
```
Fungsi yang menampilkan data mahsiswa berbentuk tabel

```python
while True:
    pilihan = menu_utama()
    
    if pilihan == 't':
        tambah_data()
    elif pilihan == 'u':
        ubah_data()
    elif pilihan == 'h':
        hapus_data()
    elif pilihan == 'l':
        tampilkan_data()
    elif pilihan == 'k':
        print("Keluar dari program. Terima kasih!")
        break
    else:
        print("Pilihan tidak valid. Silakan coba lagi.")
```

Loop untuk menampilkan menu utama dan pemilihan hingga pengguna memilih keluar (memasukan pilihan k)

## Contoh hasil eksekusi program :

### Contoh eksekusi untuk menampilkan data dan menambahkan data baru mahasiswa:
![Image](https://github.com/Shikilukeki/Foto/blob/main/Eksekusi%20melihat%20dan%20menambah%20data%20mahasiswa.png?raw=true)

### Contoh hasil eksekusi untuk mengubah data mahasiswa:
![Image](https://github.com/Shikilukeki/Foto/blob/main/Eksekusi%20mengubah%20data%20mahasiswa.png?raw=true)

### Contoh eksekusi untuk menghapus data mahasiswa:
![Image](https://github.com/Shikilukeki/Foto/blob/main/Eksekusi%20menghapus%20data%20mahasiswa.png?raw=true)
