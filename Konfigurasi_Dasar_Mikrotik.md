### 1. Membuat node (mikrotik)
  - nama          : `r_mikrotik`
  - ethernet      : `5`
  - qemu options  : `kosongkan`
  - **save**
---

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
---   

### 3. Seberapa perintah ip address
  - perintah `set` untuk mengubah sesuatu yang sudah ada
      - mengubah ip lama dengan yang baru
      > `ip address set numbers=0 address=192.168.20.1`
      
  - perintah `print` untuk menampilkan daftar
    
  - perintah `add` untuk menambah data baru
    - Menambahkan ip address pada sebuah interface
      > `ip address add address=192.168.10.1/24 interface=lubnag1`
      
  - perintah `disable` untuk menonaktifkan sesuatu secara sementara
    - ip (192.168.10.1/24) akan dinonaktifkan sementara
    > `ip address disable numbers=0`
    
  - perintah `enable` untuk menaktifkan sesuatu
    > `ip address enable numbers=0`
---

### 4. Latihan ke-1 yaitu membuat ip address pada interface seperti ip dibawah ini :
    1) ether2 : 192.168.50.1
    2) ether3 : 192.168.60.1
    3) ether4 : 192.168.70.1
    4) ether5 : 192.168.80.1
    5) lubang1 : 192.168.90.1
---

### 5. Masuk ke PNET lab dan sambungkan microtik dengan PC kemudian nyalakan PC-nya  
  ```
    1) Masuk ke terminal PC dan setting ip address dengan ip 192.168.90.2/24
    2) kemudian cek koneksi dengan router mikrotik dengan ip address 192.168.90.1
  ```
   `ping 192.168.90.1`
  - Jika ping berjalan berarti PC1 dengan router microtik saling terkoneksi.
---

### 6. Latihan ke-2 yaitu melakukan koneksi antar PC dan ether :
  1) pvc2 ke ether2
     > `(192.168.50.2) ke (192.168.50.1)`
  3) pvc3 ke ether3
     > `(192.168.60.2) ke (192.168.60.1)`
  5) pvc4 ke ether4
     > `(192.168.70.2) ke (192.168.60.1)`
---

### 7. Router bertujuannya untuk meneruskan packet ke tempat yang dituju.
  - Pada microtik, ip route untuk melihat tujuan packet 
  - `ip route print` = melihat data lootinganya.
---

### 8. Permasalahan : apakah ip di ether1 dan ether 2 terkoneksi?
- [x] ping PVC1 dengan ether1 = (terkoneksi)
- [ ] ping PVC1 dengan ether2 = (tidak terkoneksi karna perbedaan gateway / gateway tidak ditemukan)
- [ ] ping PVC1 dengan PVC2   = (tidak terkoneksi)
- [ ] ping PVC2 dengan PVC1   = (tidak terkoneksi)
      
### 9. Solusi : tambahkan gateway-nya, gateway yang berhubungan dengan mirotiknya. 
```
Jadi untuk mengatasi permasalahan konektivitas antar jaringan, cukup menambahkan
default gateway pada masing-masing host yang mengarah ke router (Mikrotik).
```

```
PVC1 (192.168.90.2) menggunakan gateway 192.168.90.1 = jalurnya menuju ke microtik kita.
Gateway diarahkan ke 192.168.90.1 yang merupakan interface router pada jaringan tersebut.
```

- IP address VPC1 + gateway masing-masing
  `ip 192.168.90.2/24 (255.255. 255.0) 192.168.90.1`
- IP address VPC2 + gateway masing-masing
  `ip 192.168.50.2/24 (255.255. 255.0) 192.168.50.1`
  
```
Kemudian ping pvc2 dengan pvc1
maka keduanya akan saling terkoneksi karena sudah menggunakan jalur yang sama.
```

- [x] ping PVC1 dengan ether1 = (terkoneksi)
- [x] ping PVC1 dengan ether2 = (terkoneksi)
- [x] ping PVC1 dengan PVC2   = (terkoneksi)
- [x] ping PVC2 dengan PVC1   = (terkoneksi)

```
Dengan konfigurasi ini, paket data dari pvc1 ke pvc2 akan diteruskan melalui router, 
sehingga kedua perangkat dapat saling berkomunikasi (ping berhasil), 
selama router telah dikonfigurasi dengan benar dan memiliki jalur ke kedua jaringan.
```















