### 1. Membuat node (mikrotik)
  - nama          : r_mikrotik
  - ethernet      : 5
  - qemu options  : kosongkan
  - **save**

### 2. Konfigurasi mikrotik
  - set nama router :
system identity set name=jarkomTerapan
- list interface dan ganti nama :
interface print
interface ethernet set ether1 name=lubang1
