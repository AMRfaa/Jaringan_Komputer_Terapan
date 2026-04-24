### 1. Membuat node (mikrotik)
  - nama          : `r_mikrotik`
  - ethernet      : `5`
  - qemu options  : `kosongkan`
  - **save**

### 2. Konfigurasi mikrotik
  - login (admin, passwd kosongkan)
  - set nama router :
    > `system identity set name=jarkomTerapan`
  - melihat daftar isi interface :
    > `interface print`
  - ganti nama ether pada interface :
    > `interface ethernet set ether1 name=lubang1`
  - menampilkan isi interface secara detail
    > `interface print detail`
    
### 3. Seberapa perintah ip address
  - perintah `set` untuk mengubah sesuatu yang sudah ada
  - perintah `print` untuk menampilkan daftar
  - perintah `add` untuk menambah data baru
    - Menambahkan ip address pada sebuah interface
      > `ip address add address=192.168.10.1/24 interface=lubnag1`
  - perintah `disable` untuk menonaktifkan sesuatu secara sementara
    > `ip address disable numbers=0`
  - perintah `enable` untuk menaktifkan sesuatu
    > `ip address enable numbers=0`
