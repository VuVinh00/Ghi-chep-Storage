## Giới thiệu về fdisk 
## Sử dụng fdisk

### 1. Liệt kê các ổ cứng, phân vùng

Sử dụng ``fdisk -l`` để liệt kê các ổ cứng, phân vùng : 

<img src="https://github.com/VuVinh00/Images/blob/master/fdisk1.png">

### 2. Thao tác với fdisk

**1. Chia disk thành các partition** 

Để phân vùng ổ cứng /dev/vdc thành các partition sử dụng câu lệnh : ``fdisk /dev/vdc``

<img src="https://github.com/VuVinh00/Images/blob/master/fdisk2.png">

Để tạo mới phân vùng bấm phím **n** :

Chọn loại phân vùng có 2 loại là :
  - Primary
  - Extended
  
Chọn loại phân vùng primary bằng cách nhập **p** : 

<img src="https://github.com/VuVinh00/Images/blob/master/fdisk3.png">

Sau đó nhập thông tin cho phân vùng :

- Partition number: Từ 1 => 4, nó sẽ tạo phân vùng là /dev/sdb1 => dev/sdb4
- First sector: Vị trí bắt đầu trên ổ đĩa
- Last sector: Vị trí cuối cùng trên ổ đĩa, hoặc thiết lập kích thước dùng lượng +size(K,M,G,T,P)

Để lưu thông tin phân vùng vừa tạo nhập **w** để lưu vào ổ đĩa và thoát khỏi chế độ fdisk command 

<img src="https://github.com/VuVinh00/Images/blob/master/fdisk4.png">

**2. Xóa các partition**

Để xóa partition thuộc disk /dev/vdc ta sử dụng câu lệnh: ``fdisk /dev/vdc``

Để xóa partition bấm phím **d** sau đó nhập partition number muốn xóa sau đó nhập **w** để lưu và thoát

<img src="https://github.com/VuVinh00/Images/blob/master/fdisk5.png">
