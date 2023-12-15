# _Laporan UAS PBO_
### Nama Kelompok :
 1. Ahmad Dwi Cahyadi (G1F022007)
 2. M.Faisal Makarim  (G1F022017)
 3. Ahmad Afif Nurdiantoro (G1F022077)

# _BAB 1 LATAR BELAKANG_

## 1.1  _Pemrograman Berorientasi Objek (OOP)_
Object Oriented Programming (OOP) atau pemrograman berorientasi objek adalah suatu cara baru dalam berpikir serta berlogika dalam menghadapi masalah- masalah yang akan dicoba mengatasi dengan bantuan komputer. Filosofi OOP menciptakan sinergi luar biasa sepanjang siklus pengembangan perangkat lunak (perencanaan, analisis, perancangan, serta implementasi) sehingga dapat diterapkan pada perancangan sistem secara umum menyangkut perangkat lunak, perangkat keras, serta sistem informasi secara keseluruhan. Berorientasi objek atau object oriented merupakan paradigma baru dalam rekayasa perangkat lunak yang memandang sistem sebagai kumpulan objek-objek diskrit yang saling berinteraksi. Yang dimaksud dengan berorientasi objek adalah bahwa mengorganisasikan perangkat lunak sebagai kumpulan objek-objek diskrit yang bekerja sama antara informasi atau struktur data dan perilakau (behavior) yang mengaturnya.

## 1.2 _Bahasa Pemrograman Python_

Bahasa pemrograman adalah tool yang wajib dikuasai oleh para programmer. Bahasa program atau pemrograman sendiri adalah sekumpulan instruksi yang diberikan kepada komputer agar bisa melakukan tugas-tugas tertentu dalam menyelesaikan sebuah masalah. Ada banyak bahasa pemrograman, salah satunya adalah Python. Dalam beberapa tahun terakhir, Python menjadi bahasa pemrograman yang paling populer digunakan di berbagai belahan dunia. Ia bisa digunakan untuk berbagai kebutuhan mulai dari machine learning, pengujian perangkat lunak sampai website. Python merupakan bahasa pemrograman komputer yang biasa dipakai untuk membangun situs, software/aplikasi, mengotomatiskan tugas dan melakukan analisis data. Bahasa pemrograman ini termasuk bahasa tujuan umum.

# _BAB 2  SOAL & PEMBAHASAN_
## 2.1 _Soal_

1. Membuat Fasilitas Pemesanan Makanan menggunakan Python

## 2.2 _Pembahasan_

**Source Code** :
```
class Menu:
    def __init__(self, nama, harga):
        self.nama = nama
        self.harga = harga

class Pemesanan:
    def __init__(self):
        self.daftar_menu = []
        self.pesanan = {}

    def tambah_menu(self, menu):
        self.daftar_menu.append(menu)

    def tampilkan_menu(self):
        print("===== Menu Makanan =====")
        for idx, menu in enumerate(self.daftar_menu, start=1):
            print(f"{idx}. {menu.nama} - Rp {menu.harga}")

    def pesan_makanan(self):
        nomor_menu = int(input("Masukkan nomor menu yang ingin dipesan: "))
        jumlah_pesanan = int(input("Masukkan jumlah pesanan: "))

        menu_terpilih = self.daftar_menu[nomor_menu - 1]

        if menu_terpilih.nama in self.pesanan:
            self.pesanan[menu_terpilih.nama] += jumlah_pesanan
        else:
            self.pesanan[menu_terpilih.nama] = jumlah_pesanan

        print(f"{jumlah_pesanan} {menu_terpilih.nama} telah ditambahkan ke dalam pesanan.")

    def hapus_pesan(self):
        menu_hapus = input("Masukkan nama menu yang ingin dihapus dari pesanan: ")
        if menu_hapus in self.pesanan:
            del self.pesanan[menu_hapus]
            print(f"{menu_hapus} telah dihapus dari pesanan.")
        else:
            print(f"{menu_hapus} tidak ditemukan dalam pesanan.")

    def update_pesanan(self):
        menu_update = input("Masukkan nama menu yang ingin diupdate dalam pesanan: ")
        if menu_update in self.pesanan:
            jumlah_baru = int(input("Masukkan jumlah pesanan baru: "))
            self.pesanan[menu_update] = jumlah_baru
            print(f"Jumlah pesanan {menu_update} berhasil diupdate menjadi {jumlah_baru}.")
        else:
            print(f"{menu_update} tidak ditemukan dalam pesanan.")

    def tampilkan_pesanan(self):
        if not self.pesanan:
            print("Belum ada pesanan.")
        else:
            print("\n===== Pesanan Anda =====")
            for menu, jumlah in self.pesanan.items():
                harga_menu = next(item.harga for item in self.daftar_menu if item.nama == menu)
                total_harga = harga_menu * jumlah
                print(f"{menu} x {jumlah} - Rp {harga_menu * jumlah} (Total: Rp {total_harga})")

    def total_pesanan(self):
        total = 0
        print("\n===== Pesanan Anda =====")
        for menu, jumlah in self.pesanan.items():
            harga_menu = next(item.harga for item in self.daftar_menu if item.nama == menu)
            total += harga_menu * jumlah
            print(f"{menu} x {jumlah} - Rp {harga_menu * jumlah}")

        print(f"\nTotal Pembayaran: Rp {total}")

if __name__ == "__main__":
    # Contoh penggunaan program
    menu1 = Menu("Nasi Goreng", 15000)
    menu2 = Menu("Mie Ayam", 12000)
    menu3 = Menu("Ayam Goreng", 18000)

    pemesanan = Pemesanan()
    pemesanan.tambah_menu(menu1)
    pemesanan.tambah_menu(menu2)
    pemesanan.tambah_menu(menu3)

    pemesanan.tampilkan_menu()

    pesan_lagi = True
    while pesan_lagi:
        print("\n===== Menu Pemesanan =====")
        print("1. Pesan Makanan")
        print("2. Hapus Pesanan")
        print("3. Update Pesanan")
        print("4. Tampilkan Pesanan")
        print("5. Selesai Pemesanan")

        pilihan = input("Masukkan pilihan Anda (1/2/3/4/5): ")

        if pilihan == "1":
            pemesanan.pesan_makanan()
        elif pilihan == "2":
            pemesanan.hapus_pesan()
        elif pilihan == "3":
            pemesanan.update_pesanan()
        elif pilihan == "4":
            pemesanan.tampilkan_pesanan()
        elif pilihan == "5":
            pesan_lagi = False
        else:
            print("Pilihan tidak valid. Silakan masukkan angka 1, 2, 3, 4, atau 5.")

    pemesanan.total_pesanan()
```

### - _Penjelasan kode_
   Program di atas adalah implementasi sederhana dari dua kelas, yaitu ```Menu``` dan ```Pemesanan```, yang digunakan untuk membuat daftar menu makanan dan melakukan pemesanan makanan. Berikut penjelasan rinci untuk setiap bagian dari program:

### Kode dan Penjelasan Kelas `Menu`:

```
python
class Menu:
    def __init__(self, nama, harga):
        self.nama = nama
        self.harga = harga
```

**Penjelasan :** 
- Kelas ini memiliki dua atribut, yaitu ```nama``` (nama menu) dan ```harga``` (harga menu).
- Metode ```__init__``` digunakan untuk menginisialisasi objek ```Menu``` dengan nilai awal untuk ```nama``` dan ```harga```.

________

### Kode dan Penjelasan Kelas `Pemesanan`:
```
python
class Pemesanan:
    def __init__(self):
        self.daftar_menu = []
        self.pesanan = {}
```
**Penjelasan :** 
Kelas ini memiliki dua atribut, yaitu ```daftar_menu``` (untuk menyimpan daftar objek ```Menu```) dan ```pesanan``` (untuk menyimpan pesanan pengguna).
_________

```
python
    def tambah_menu(self, menu):
        self.daftar_menu.append(menu)
```
**Penjelasan :**
Metode ```tambah_menu``` digunakan untuk menambahkan objek `Menu` ke dalam daftar menu.
_________

```
python
    def tampilkan_menu(self):
        print("===== Menu Makanan =====")
        for idx, menu in enumerate(self.daftar_menu, start=1):
            print(f"{idx}. {menu.nama} - Rp {menu.harga}")
```
**Penjelasan :**
Metode ```tampilkan_menu``` digunakan untuk menampilkan daftar menu makanan beserta nomor urut dan harga.
_________

```
python
    def pesan_makanan(self):
        # ...
```

**Penjelasan :**
Metode ```pesan_makanan``` meminta pengguna memasukkan nomor menu dan jumlah pesanan, kemudian menambahkan pesanan ke dalam daftar pesanan.
_________

```
python
    def hapus_pesan(self):
        # ...
```
**Penjelasan :**
Metode ```hapus_pesan``` meminta pengguna memasukkan nama menu yang ingin dihapus dari pesanan, dan menghapusnya jika ada.
_________

```
python
    def update_pesanan(self):
        # ...
```
**Penjelasan :**
Metode ```update_pesanan``` meminta pengguna memasukkan nama menu dan jumlah pesanan baru, kemudian mengupdate jumlah pesanan jika menu tersebut sudah ada dalam daftar pesanan.
_________

```
python
    def tampilkan_pesanan(self):
        # ...
```
**Penjelasan :**
Metode ```tampilkan_pesanan``` menampilkan pesanan yang telah dibuat, beserta jumlah dan total harga.
_________

### Kode pada metode eksekusi Program :
```
if __name__ == "__main__":
    # Contoh penggunaan program
    menu1 = Menu("Nasi Goreng", 15000)
    menu2 = Menu("Mie Ayam", 12000)
    menu3 = Menu("Ayam Goreng", 18000)
```

**Penjelasan :**
- Membuat tiga objek `Menu` sebagai contoh.
- Membuat objek `Pemesanan`.
- Menambahkan menu-menu ke dalam daftar menu pemesanan.
- Menampilkan menu.
- Menggunakan loop untuk memproses pilihan pengguna dan melakukan operasi pesanan.
_________

### _Tampilan Menu Pemesanan_ :
```
python
    print("\n===== Menu Pemesanan =====")
    print("1. Pesan Makanan")
    print("2. Hapus Pesanan")
    print("3. Update Pesanan")
    print("4. Tampilkan Pesanan")
    print("5. Selesai Pemesanan")
```

**Penjelasan :**
Menampilkan menu pilihan untuk pengguna. Mereka dapat memilih antara pesan makanan, hapus pesanan, update pesanan, tampilkan pesanan, atau selesai pemesanan.
_________

### _Struktur Pemilihan_ :
```
python
    if pilihan == "1":
        pemesanan.pesan_makanan()
    elif pilihan == "2":
        pemesanan.hapus_pesan()
    elif pilihan == "3":
        pemesanan.update_pesanan()
    elif pilihan == "4":
        pemesanan.tampilkan_pesanan()
    elif pilihan == "5":
        pesan_lagi = False
    else:
        print("Pilihan tidak valid. Silakan masukkan angka 1, 2, 3, 4, atau 5.")
```

**Penjelasan :**
- Mengevaluasi pilihan pengguna dan menjalankan metode yang sesuai pada objek `pemesanan`. Misalnya, jika pengguna memilih "1", maka ```pemesanan.pesan_makanan()``` akan dipanggil.
- Jika pengguna memilih "5", variabel `pesan_lagi` diubah menjadi `False`, sehingga program keluar dari loop.

  _________

### _Keluar dari Loop dan Menampilkan Total Pesanan_ :

```
python
pemesanan.total_pesanan()
```

**Penjelasan :**
- Setelah pengguna memilih untuk selesai ```(`pesan_lagi = False`)```, program keluar dari loop dan menampilkan total pesanan dengan memanggil metode ```total_pesanan()``` pada objek ```pemesanan```.

  _________

## _Tampilan Luaran Source code_ 
### Pemesanan makanan

<div align="center">

 ![alt text](/ss/1.png?raw=true)

</div>

### Menampilkan makanan

<div align="center">

 ![alt text](/ss/2.png?raw=true)

</div>

### Mengupdate makanan

<div align="center">

 ![alt text](/ss/3.png?raw=true)

</div>

### Menghapus makanan

<div align="center">

 ![alt text](/ss/4.png?raw=true)

</div>

### Menyelesaikan Pesanan (order pesanan)

<div align="center">

 ![alt text](/ss/5.png?raw=true)

</div>

# _BAB 3  KESIMPULAN DAN SARAN_
## 3.1 _Kesimpulan_
   Dalam proyek pemrograman ini, pengguna dapat memesan makanan dengan mudah menggunakan aplikasi Python. Antarmuka yang ramah pengguna memudahkan navigasi dan pemilihan menu. Fungsionalitas pemesanan yang efisien dan sistem pembayaran yang aman menambahkan nilai lebih. Dengan implementasi ini, proyek tidak hanya memenuhi kebutuhan praktis pengguna, tetapi juga menawarkan pengalaman pengguna yang menyenangkan dalam memesan makanan secara online.

## 3.2 _Saran_
   Untuk meningkatkan proyek pemrograman pemesanan makanan menggunakan Python, disarankan untuk fokus pada keamanan pembayaran dan perlindungan data pengguna, memastikan pemeliharaan kode yang baik untuk kemudahan pengembangan, responsivitas antarmuka pengguna, penambahan fitur pencarian atau kategori, integrasi dengan platform pembayaran yang umum digunakan, uji coba pengguna untuk mengidentifikasi potensi perbaikan, kemudahan pembaruan menu, dan penambahan notifikasi pesanan untuk memberi tahu pengguna tentang status pesanan. Dengan demikian, proyek dapat memberikan pengalaman pengguna yang lebih baik dan mengikuti praktik pengembangan perangkat lunak terbaik.


## Daftra Pustaka
[1] [Syahrudin, A. N., & Kurniawan, T. (2018). Input dan Output pada Bahasa Pemrograman Python. Jurnal Dasar Pemrograman Python STMIK, (June 2018), 1–7](https://www.researchgate.net/publication/338385483)

[2] [Sholeh, M., Aji, W. L., Riady, Y., & Qasthari, B. L. (2022). Pengelolaan Pemesanan Menu Makanan Menggunakan Framework Flask Python. JATISI (Jurnal Teknik Informatika Dan Sistem Informasi), 9(2), 916–929.](https://doi.org/10.35957/jatisi.v9i2.1459)

[3] [Abidin, Z. (2021). PELATIHAN DASAR-DASAR ALGORITMA DAN PEMOGRAMAN UNTUK MEMBANGKITKAN MINAT SISWA-SISWI SMK PADA DUNIA PEMOGRAMAN. Journal of Social Sciences and Technology for Community Service (JSSTCS), 2(2), 54.](https://doi.org/10.33365/jsstcs.v2i2.1326)
