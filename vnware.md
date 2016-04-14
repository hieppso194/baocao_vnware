# Thiết lập IP tĩnh, IP động và 2 card mạng trên Ubuntu server

----
# Mục lục
##[I. Thiết lập IP tĩnh, IP động]  (#phanI)
 * [1. Thiết lập IP tĩnh, IP động bằng dòng lệnh] (#phanI.1)
 * [2. Thiết lập IP tĩnh, IP động bằng sửa file] (#phanI.2)
 
##[II. Thêm card mạng cho ubuntu server và cấu hình cho card mạng]  (#phanII)
----
<a name="phanI"></a>
##I. Thiết lập IP tĩnh, IP động
<a name="phanI.1"></a>
###1. Thiết lập IP tĩnh, IP động bằng dòng lệnh (hay còn gọi là cấu hình địa chỉ IP tạm thời)
> Ta gõ lệnh như sau :

 ``` sudo ifconfig ethX ip address netmask subnet-mask```.
 * Trong đó:
   * ethX : là tên card mạng thứ X.
   * ip address: là địa chỉ ip cần truyền cho card mạng.
   * subnet-mask: là địa chỉ netmask

Ví dụ muốn gán địa chỉ 192.168.1.1 cho eth0 thì câu lệnh sẽ như sau 

```sudo ifconfig 192.168.1.1 netmask 255.255.255.0```

 ![](https://raw.githubusercontent.com/hieppso194/baocao_vnware/master/22.PNG)

----
<a name="phanI.2"></a>
###2. Thiết lập IP tĩnh, IP động bằng sửa file
1. Truy nhập vào /etc/interfaces/networking (ở đây tôi mở file bằng nano) để sửa các thông số.

2. Thêm các dòng lệnh sau vào file. Ở đây tôi đổi địa chỉ ip eth0 thành 10.10.10.10
 ```
auto eth0
iface eth0 inet static
ipaddress 172.16.100
netmask 255.255.255.0
gateway 172.16.19.1
dns-nameservers 8.8.8.8
```.
* Trong đó:
	* `eth1`: tên card mạng
	* `static`: chỉ ra rằng, card mạng sẽ nhận địa chỉ ip do người quản trị đặt.
	* `address`: địa chỉ ip.
	* `netmask`: địa chỉ netmask.
	* `gateway`: địa chỉ gateway.
	* `dns-nameserver`: địa chỉ dns server phân giải tên miền.
 
![](https://raw.githubusercontent.com/hieppso194/baocao_vnware/master/23.PNG)
3. Sau khi save file thì chúng ta restart card mạng băng câu lệnh ```/etc/init.d/networking restart```

 **Lưu ý: Để đổi ip động ta chỉ việc thay static thành dhcp và làm tương tự.**

![](https://raw.githubusercontent.com/hieppso194/baocao_vnware/master/232.png)

----
<a name="phanII"></a>
##II.Thêm card mạng cho ubuntu server và cấu hình cho card mạng
1. Chọn setting trong máy ảo-> chọn add-> network adapter Chọn custom và chọn vmnetx(ví dụ ở đây tôi chọn vmnet1)
  
![](https://raw.githubusercontent.com/hieppso194/baocao_vnware/master/24.PNG)
2. Bây giờ tiến hành cấu hình cho 2 card mạng ở file /etc/network/interface , file cấu hình như sau.

![](https://raw.githubusercontent.com/hieppso194/baocao_vnware/master/25.png)

