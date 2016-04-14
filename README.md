# Thiết lập IP tĩnh, IP động và 2 card mạng trên Ubuntu server

----
## Thiết lập IP tĩnh, IP động
###1. Thiết lập IP tĩnh, IP động bằng dòng lệnh (hay còn gọi là cấu hình địa chỉ IP tạm thời)
> Ta gõ lệnh như sau :
 ``` sudo ifconfig ethX ip address netmask net address```. Ví dụ muốn gán địa chỉ 192.168.1.1 cho eth0 thì câu lệnh sẽ như sau sudo ```ifconfig 192.168.1.1 netmask 255.255.255.0```

----
###2. Thiết lập IP tĩnh, IP động bằng sửa file
1. Truy nhập vào /etc/interfaces/networking để sửa các thông số.
![](https://camo.githubusercontent.com/3e51ad2f3d2415ffbaabedc2dec873dbd2b4dd0c/687474703a2f2f692e696d6775722e636f6d2f4b4730516c567a2e706e67)
2. Thêm các dòng lệnh sau vào file. Ở đây tôi đổi địa chỉ ip eth0 thành 10.10.10.10
 ```
auto eth0
iface eth0 inet static
ipaddress 10.10.10.10
netmask 255.255.255.0
gateway 10.10.10.1
dns-nameservers 8.8.8.8
```
3. Sau khi save file thì chúng ta restart card mạng băng câu lệnh /etc/init.d/networking 
 ** Lưu ý: Để đổi ip động ta chỉ việc thay static thành dhcp và làm tương tự.**

----
##2.Thêm card mạng cho ubuntu server và cấu hình cho card mạng


