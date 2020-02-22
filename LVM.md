## Giới thiệu LVM

LVM là một phương pháp cho phép ấn định không gian đĩa cứng thành những Logical Volume => khiến cho việc thay đổi kích thước trở nên dễ dàng (so với partition)

Có thể thay đổi kích thước mà không cần phải sửa lại partition table của OS. Hữu ích khi sử dụng hết phần bộ nhớ còn trống của partition và muốn mở rộng dung lượng

Chỉ cần ấn định lại dung lượng mà không cần phân vùng lại, cũng không phải đối mặt với nguy cơ mất dữ liệu khi thay đổi dung lượng như khi thao tác trên Partition.

## Thuật ngữ trong LVM

#### Physical volumes (PV):

Đĩa cứng vật lý trong server

Có thể kết hợp nhiều PV để tạo thành một Volume Groups với dung lượng bằng tổng dung lượng các PV

PV chỉ là đại diện cho các ổ đĩa vật lý chứ không phải là bản thân ổ đĩa đó

#### Volume Groups (VG)

<img src="https://github.com/VuVinh00/Images/blob/master/vg.png">

Một tập hợp các PV, từ VG sẽ có thể phân chia thành các Logical Volumes và các Logical Volumes này có thể thay đổi kích thước dễ dàng.

#### Logical Volumes (LV)

<img src="https://github.com/VuVinh00/Images/blob/master/lv.png">

Đơn vị cuối cùng của hệ thống LVM, các LV tương đương với partition theo cách phân chia truyền thống

LV có thể thay đổi kích thước dễ dàng, tất cả chỉ phụ thuộc vào kích thước của VG.

## Làm việc với LVM 

### Tạo Logical Volume trên LVM

Bước 1: Kiểm tra các disk hiện tại bằng câu lệnh ``lsblk``:

Bước 2: Tạo Physical Volume 

Tạo Physical Volume bằng câu lệnh:

```
[root@2node2 ~]# pvcreate /dev/vdc /dev/vdd
  Physical volume "/dev/vdc" successfully created.
  Physical volume "/dev/vdd" successfully created.
```

Bước 3: Tạo Volume Group

Nhóm các Physical Volume thành Volume Group bằng câu lệnh :

```
[root@2node2 ~]# vgcreate vg-test /dev/vdc /dev/vdd
  Volume group "vg-test" successfully created
```

Kiểm tra Volume Group: 

``vgs``

Bước 4 : Tạo Logical Volume

Từ một Volume Group, tạo ra các Logical Volume bằng câu lệnh:

```
[root@2node2 ~]# lvcreate -L 5G -n lv-test vg-test
  Logical volume "lv-test" created.
```

Trong đó: -L: Chỉ ra dung lượng của logical volume -n: Chỉ ra tên của logical volume Note: lv-test là tên Logical Volume, vg-test là Volume Group mà vừa tạo

Kiểm tra lại Logical Volume bằng câu lệnh: 

``lvs``

Bước 5 : Định dạng Logical Volume bằng câu lệnh mkfs

```
[root@2node2 ~]# mkfs.xfs /dev/vg-test/lv-test
meta-data=/dev/vg-test/lv-test   isize=512    agcount=4, agsize=327680 blks
         =                       sectsz=512   attr=2, projid32bit=1
         =                       crc=1        finobt=0, sparse=0
data     =                       bsize=4096   blocks=1310720, imaxpct=25
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0 ftype=1
log      =internal log           bsize=4096   blocks=2560, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
```

Bước 6 : Mount và sử dụng:

Tạo thư mục để mount là ``/mnt/lvm-test`` sau đó mount LV vào để sử dụng :

```
[root@2node2 ~]# mkdir /mnt/lvm-test
[root@2node2 ~]# mount /dev/vg-test/lv-test /mnt/lvm-test/
```

### Thay đổi kích thước LV

1. Tăng kích thước LV

``lvextend -L +50M /dev/vg-test/lv-test``

Kích thước cho Logical Volume thì Logical Volume đã được tăng nhưng file system trên volume này vẫn chưa thay đổi, sử dụng lệnh sau:

``resize2fs /dev/vg-test/lv-test``

2. Giảm kích thước LV

``lvreduce -L 20M /dev/vg-test/lv-test``

Sau đó tiến hành format lại filesystem và mount để sử dụng

### Thay đổi kích thước VG

1. Thêm các PV vào VG :

``vgextend /dev/vg-test /dev/vdb``

2. Xóa PV ra khỏi VG

``vgreduce /dev/vg-test /dev/vdb``

### Xóa LV, VG, PV

Trước tiên ta phải umount LV 

1. Xóa lV 

``lvremove /dev/vg-test/lv-test``

2. Xóa VG

``vgremove /dev/vg-test``

3. Xóa PV 

``pvremove /dev/vdb``
