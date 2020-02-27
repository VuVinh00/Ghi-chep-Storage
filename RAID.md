## Tìm hiểu về RAID

RAID là viết tắt của Redundant Array of Inexpensive Disks (Hệ thống đĩa dự phòng).

Đây là hệ thống hoạt động bằng cách kết nối một dãy các ổ cứng có chi phí thấp lại với nhau để hình thành một thiết bị nhớ đơn có dung lượng lớn hỗ trợ hiệu quả cao và đáng tin cậy.

Có 3 lý do chính để áp dụng RAID:

- Dự phòng
- Hiệu quả cao
- Giá thành thấp

Sự dự phòng là nhân tố quan trọng nhất trong RAID. Cho phép sao lưu dữ liệu bộ nhớ khi gặp sự cố. Nếu một ổ cứng trong dãy bị trục trặc thì có thể thay thế sang ổ cứng khác mà không cần tắt cả hệ thống. Phương pháp dự phòng phụ thuộc vào phiên bản RAID được sử dụng.

Khi áp dụng các phiên bản RAID mạnh, hiệu năng có thể tăng cao. Hiệu quả cũng tùy thuộc vào số lượng ổ cứng được liên kết với nhau và các mạch điều khiển.

Raid được chia làm nhiều loại. Các Raid được sử dụng có thể là Raid 0, Raid 1, Raid 3, Raid 4, Raid 5, RAID 01, RAID 03, RAID 10, RAID 50, RAID 60

## Các loại RAID

### Raid 0

<img src="https://github.com/VuVinh00/Images/blob/master/Raid%200.png">

Raid 0 là loại Raid khá phổ biến, bởi có khả năng nâng cao hiệu suất tốc độc đọc ghi trao đổi dữ liệu của ổ cứng. Để tiến hành setup Raid 0 thì cần tối thiểu 2 ổ đĩa (Disk 0, Disk 1).

Cách lưu trữ dữ liệu: Có 1 file A dung lượng 100MB. Khi tiến hành lưu trữ thay vì file A sẽ được lưu vào 1 ổ cứng duy nhất, Raid 0 sẽ lưu vào 2 ổ đĩa disk 0, disk 1 mỗi ổ 50MB (Striping), giảm thời gian đọc ghi xuống 1 nửa theo lý thuyết.

Ưu điểm:
- Tốc độ đọc ghi nhanh (gấp đôi bình thường theo lý thuyết).

Nhược điểm:

- Tiềm ẩn rủi ro về dữ liệu. Lý do dữ liệu được chia đôi lưu trên 2 ổ đĩa.Trường hợp 1 trong 2 ổ đĩa bị hỏng thì nguy cơ mất dữ liệu rất cao. Về ổ cứng yêu cầu phải 2 ổ cùng dung lượng, nếu 2 ổ khác dung lượng thì lấy ổ thấp nhất.

Đối tượng sử dụng:

Thích hợp với những dịch vụ cần lưu trữ và truy xuất với tốc độ cao. Chẳng hạn như dịch vụ video streaming, chạy cơ sở dữ liệu.

### Raid 1

<img src="https://github.com/VuVinh00/Images/blob/master/Raid%201.png">

Raid 1 là loại Raid cơ bản. Tăng độ an toàn về dữ liệu. Tiến hành setup Raid 1 cần tối thiểu 2 ổ cứng để lưu trữ.

Raid 1 đảm bảo an toàn dữ liệu do dữ liệu được ghi vào 2 ổ giống hệt nhau (Mirroring).

Ưu điểm:

- An toàn về dữ liệu, trường hợp 1 trong 2 ổ đĩa bị hỏng thì dữ liệu vẫn có khả năng đáp ứng dịch vụ.

Nhược điểm:

- Hiệu suất không cao, Nâng cao chi phí (giả sử khách hàng sử dụng 2 ổ cứng 500GB. Khi sử dụng Raid 1 thì dung lượng lưu trữ có thể sử dụng chỉ được 500GB). Về ổ cứng yêu cầu phải 2 ổ cùng dung lượng, nếu 2 ổ khác dung lượng thì lấy ổ thấp nhất.

Đối tượng sử dụng:

Các dịch vụ lưu trữ, các website vừa và nhỏ không yêu cầu quá cao về tốc độ đọc ghi (in/out) của ổ cứng. Các đối tượng yêu cầu sự an toàn về dữ liệu như các dịch vụ kế toán,lưu trữ thông tin khách hàng, bất động sản v.v…

### Raid 10

<img src="https://github.com/VuVinh00/Images/blob/master/raid10.png">

Raid 10 là sự kết hợp giữa 2 loại raid phổ biến và Raid 1 và Raid 0. Để setup Raid 10 cần sử dụng tối thiểu 4 ổ cứng (Disk 0, Disk 1, Disk 2, Disk 3).

Dữ liệu sẽ được lưu đồng thời vào 4 ổ cứng. 2 ổ dạng Striping (Raid 0) và 2 ổ (Mirroring) Raid 1.

Ưu điểm:

- Đây là 1 hình thức lưu trữ nhanh nhẹn và an toàn, vừa nâng cao hiệu suất mà lại đảm bảo dữ liệu không bị thất thoát khi 1 trong số 4 ổ cứng bị hỏng.

Nhược điểm:

- Chi phí cao. Đối với Raid 10 dung lượng sẵn sàng sử dụng chỉ bằng ½ dung lượng của 4 ổ. (giống như raid 1).

Đối tượng sử dụng:

Raid 10 thích hợp với tất cả các đối tượng sử dụng (từ những yêu cầu về hiệu suất đến việc đảm bảo an toàn dữ liệu). Về ổ cứng yêu cầu phải 4 ổ cùng dung lượng, nếu 4 ổ khác dung lượng thì lấy ổ thấp nhất.

### Raid 5 

<img src="https://github.com/VuVinh00/Images/blob/master/r5.png">

Nguyên tắc của Raid 5 gần giống với 2 loại raid lưu trữ truyền thống là Raid 1 và Raid 0. Tách ra lưu trữ các ổ cứng riêng biệt và có phương án dự phòng khi có sự cố phát sinh đối với 1 ổ cứng bất kì trong cụm.

Setup Raid 5 cần tối thiểu 3 ổ cứng. Giả sử có 1 file A thì khi lưu trữ sẽ tách ra 3 phần A1, A2, A3. Ba phần nãy sẽ tương ứng lưu trên ổ đĩa Disk 0, Disk 1, Disk 2, còn ổ đĩa Disk 3 sẽ giữ bản sao lưu backup của 3 phần này. Tương tự các file sau cũng vậy và tùy theo tiến trình thực hiện mà bản sao lưu có thể được lưu ở bất kì 1 trong những ổ trong cụm Raid.

Ưu điểm:

- Nâng cao hiệu suất, an toàn dữ liệu, tiết kiệm chi phí hơn so với hình thức lưu trữ Raid 10.

Nhược điểm:
- Chi phí phát sinh thêm 1 ổ so với hình thức lưu trữ thông thường. (tổng dung lượng ổ cứng sau cùng sẽ bằng tổng dung lượng đĩa sử dụng trừ đi 1 ổ. Giả sử bạn có 4 ổ 500GB thì dung lượng sử dụng sau cùng khi triển khai Raid 5 bạn chỉ còn 1500GB).

Đối tượng sử dụng:

Tất cả những website, dịch vụ, ứng dụng có số lượng truy cập và yêu cầu tài nguyên từ nhỏ đến vừa và lớn.

### Raid 6

<img src="https://github.com/VuVinh00/Images/blob/master/r6.png">

Mở rộng, và tương tự RAID 5. Lặp lại nhiều hơn số lần sự phân tách dữ liệu để ghi vào các đĩa cứng khác nhau RAID 6 yêu cầu tối thiểu 4 ổ cứng.

Ưu điểm:
- Nâng cao hiệu suất, an toàn dữ liệu, tiết kiệm chi phí hơn so với hình thức lưu trữ Raid 10.

Nhược điểm:

- Chi phí phát sinh sẽ cao hơn RAID 5.

### Cấu hình soft RAID

RAID được quản lý bằng gói ``mdadm`` trong hầu hết các bản phân phối Linux. Để cài gói ``mdadm`` chạy lệnh:

``yum install mdadm``

#### RAID 0

Bước 1: Kiểm tra thông tin ổ đĩa trên máy:

Trước khi tạo RAID0, cần đảm bảo có ít nhất 2 ổ cứng, ta có thể kiểm tra các ổ cứng có sử dụng RAID nào chưa bằng lệnh ``mdadm``:

```
[root@node2 ~]# mdadm --examine /dev/sdb /dev/sdc
mdadm: No md superblock detected on /dev/sdb.
mdadm: No md superblock detected on /dev/sdc.
```
Bước 2: Tạo phân vùng đĩa cứng

Thực hiện tạo phân vùng trên đĩa có tên là ``sdb`` và ``sdc`` cho RAID bằng ``fdisk``

**Tạo phân vùng trên ổ đĩa sdb**:

Chạy lệnh ``fdisk /dev/sdb`` để tạo phân vùng cho ``sdb`` và thực hiện các thao tác sau:

- Nhấn **n** để tạo phân vùng mới
- Chọn **p** cho phân vùng chính
- Chọn số phân vùng là **1**
- Nhập giá trị ban đầu, giá trị kết thúc và nhấn phím **Enter**

Sau đây sẽ tạo Linux RAID tự động trên các phân vùng:

- Nhập **t** để chọn phân vùng
- Nhập **fd** để chọn loại phân vùng **Linux raid auto** và nhấn **Enter** để áp dụng
- Cuối cùng nhấn **w** để lưu và thoát

Thực hiện tương tự các phân vùng cho ``sdc``

Tiếp theo chạy lệnh bên dưới để xem các đĩa có tham gia RAID nào không

```
[root@node2 test]# mdadm --examine /dev/sdb /dev/sdc
/dev/sdb:
   MBR Magic : aa55
Partition[0] :     41940992 sectors at         2048 (type fd)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :     52426752 sectors at         2048 (type fd)
[root@node2 test]# mdadm --examine /dev/sdb1 /dev/sdc1
mdadm: No md superblock detected on /dev/sdb1.
mdadm: No md superblock detected on /dev/sdc1.
```
Bước 3: Tạo RAID0

Chúng ta chạy lệnh sau để tạo RAID0:

```
mdadm -C /dev/md0 -l raid0 -n 2 /dev/sdb1 /dev/sdc1
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
```
Trong đó:
- -C: tạo RAID mới
- -l: Level của RAID
- -n: Số lượng thiết bị RAID

Ngoài ra lệnh tạo RAID0 sau đây cũng có ý nghĩa như lệnh chúng ta vừa chạy:

``mdadm --create /dev/md0 --level=stripe --raid-devices=2 /dev/sd[b-c]1``

Ta có thể chạy lệnh sau đây để kiểm tra:

```
[root@node2 ~]# mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Thu Feb 27 07:01:22 2020
        Raid Level : raid0
        Array Size : 47149056 (44.96 GiB 48.28 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

       Update Time : Thu Feb 27 07:01:22 2020
             State : clean
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

        Chunk Size : 512K

Consistency Policy : none

              Name : node2:0  (local to host node2)
              UUID : f3971b3e:c5d54cde:872f53ea:2b572102
            Events : 0

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
```
Bước 4: Tạo filesystem cho thiết bị RAID ``/dev/md0``:

```
[root@localhost ~]#  mkfs.xfs /dev/md0
mke2fs 1.42.9 (28-Dec-2013)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=256 blocks
1310720 inodes, 5237760 blocks
261888 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2153775104
160 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
	4096000

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done
```

Tạo thư mục ``/mnt/test`` để mount ``/dev/md0``:

```
[root@node2 ~]# mkdir /mnt/test
[root@node2 ~]# mount /dev/md0 /mnt/test
```

Ta chạy lệnh ``df -h`` để kiểm tra xem thiết bị ``/dev/md0`` được mount vào ``/mnt/test`` chưa:

```
[root@node2 ~]# df -h
Filesystem               Size  Used Avail Use% Mounted on
devtmpfs                 1.9G     0  1.9G   0% /dev
tmpfs                    1.9G     0  1.9G   0% /dev/shm
tmpfs                    1.9G  8.9M  1.9G   1% /run
tmpfs                    1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mapper/centos-root   17G  3.7G   14G  22% /
/dev/sda1               1014M  179M  836M  18% /boot
/dev/md0                  45G  2.1G   40G   5% /mnt/test
tmpfs                    379M     0  379M   0% /run/user/0
```

Chúng ta sẽ kiểm tra IOPS bằng công cụ ``fio``, cài đặt ``fio`` bằng câu lệnh:

``yum install fio -y``

Tiến hành kiểm tra read random trên ổ RAID0 đã được mount tại ``/mnt/test``

```
[root@node2 test]# fio -filename=/mnt/test/testfio.txt \
> -direct=1 \
> -rw=randread \
> -bs=4k \
> -size=2G \
> -runtime=1000 \
> -group_reporting \
> -name=mytest
mytest: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=psync, iodepth=1
fio-3.7
Starting 1 process
mytest: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [r(1)][100.0%][r=464KiB/s,w=0KiB/s][r=116,w=0 IOPS][eta 00m:00s]
mytest: (groupid=0, jobs=1): err= 0: pid=16752: Thu Feb 27 07:32:58 2020
   read: IOPS=117, BW=470KiB/s (481kB/s)(459MiB/1000002msec)
    clat (usec): min=108, max=225823, avg=8507.68, stdev=5716.54
     lat (usec): min=108, max=225823, avg=8508.21, stdev=5716.55
    clat percentiles (usec):
     |  1.00th=[   347],  5.00th=[  2409], 10.00th=[  3752], 20.00th=[  5276],
     | 30.00th=[  6325], 40.00th=[  7177], 50.00th=[  8029], 60.00th=[  8848],
     | 70.00th=[  9765], 80.00th=[ 10945], 90.00th=[ 12518], 95.00th=[ 14877],
     | 99.00th=[ 26608], 99.50th=[ 32900], 99.90th=[ 67634], 99.95th=[ 90702],
     | 99.99th=[156238]
   bw (  KiB/s): min=  104, max=  600, per=100.00%, avg=469.66, stdev=66.78, samples=2000
   iops        : min=   26, max=  150, avg=117.36, stdev=16.70, samples=2000
  lat (usec)   : 250=0.34%, 500=1.54%, 750=0.55%, 1000=0.03%
  lat (msec)   : 2=1.48%, 4=7.47%, 10=60.84%, 20=25.30%, 50=2.25%
  lat (msec)   : 100=0.16%, 250=0.04%
  cpu          : usr=0.61%, sys=51.74%, ctx=117438, majf=0, minf=34
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=117447,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=470KiB/s (481kB/s), 470KiB/s-470KiB/s (481kB/s-481kB/s), io=459MiB (481MB), run=1000002-1000002msec

Disk stats (read/write):
    md0: ios=117435/27, merge=0/0, ticks=0/0, in_queue=0, util=0.00%, aggrios=58723/5, aggrmerge=0/8, aggrticks=496431/185, aggrin_queue=496542, aggrutil=49.89%
  sdb: ios=58636/8, merge=0/16, ticks=494615/348, in_queue=494886, util=49.52%
  sdc: ios=58811/2, merge=0/1, ticks=498248/23, in_queue=498199, util=49.89%
```
Tiếp theo ta kiểm tra IOPS trên disk không được RAID

```
[root@node2 test]# fio -filename=/root/testfio.txt -direct=1 -rw=randread -bs=4k -size=2G -runtime=1000 -group_reporting -name=mytest2
mytest2: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=psync, iodepth=1
fio-3.7
Starting 1 process
mytest2: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [r(1)][100.0%][r=9KiB/s,w=0KiB/s][r=2,w=0 IOPS][eta 00m:00s]
mytest2: (groupid=0, jobs=1): err= 0: pid=17391: Thu Feb 27 07:52:20 2020
   read: IOPS=81, BW=326KiB/s (334kB/s)(319MiB/1000248msec)
    clat (usec): min=138, max=1430.8k, avg=12258.81, stdev=18297.30
     lat (usec): min=138, max=1430.8k, avg=12259.35, stdev=18297.33
    clat percentiles (usec):
     |  1.00th=[   461],  5.00th=[  3359], 10.00th=[  4752], 20.00th=[  6325],
     | 30.00th=[  7504], 40.00th=[  8455], 50.00th=[  9503], 60.00th=[ 10683],
     | 70.00th=[ 12125], 80.00th=[ 14746], 90.00th=[ 21365], 95.00th=[ 27919],
     | 99.00th=[ 49021], 99.50th=[ 71828], 99.90th=[261096], 99.95th=[375391],
     | 99.99th=[725615]
   bw (  KiB/s): min=    2, max=  568, per=95.76%, avg=312.19, stdev=140.96, samples=1991
   iops        : min=    0, max=  142, avg=77.92, stdev=35.28, samples=1991
  lat (usec)   : 250=0.14%, 500=1.00%, 750=0.70%, 1000=0.02%
  lat (msec)   : 2=0.59%, 4=4.44%, 10=47.24%, 20=34.20%, 50=10.71%
  lat (msec)   : 100=0.65%, 250=0.21%, 500=0.09%, 750=0.01%, 1000=0.01%
  cpu          : usr=0.59%, sys=51.32%, ctx=81575, majf=0, minf=35
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=81547,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=326KiB/s (334kB/s), 326KiB/s-326KiB/s (334kB/s-334kB/s), io=319MiB (334MB), run=1000248-1000248msec

Disk stats (read/write):
    dm-0: ios=81547/9, merge=0/0, ticks=994411/238, in_queue=995320, util=99.57%, aggrios=81547/8, aggrmerge=0/1, aggrticks=994823/205, aggrin_queue=994922, aggrutil=99.54%
  sda: ios=81547/8, merge=0/1, ticks=994823/205, in_queue=994922, util=99.54%
```

#### RAID1 

Bước 1: Tương tự như RAID0

Bước 2: Tương tự như RAID0

Bước 3: Tạo RAID1

Ta sẽ tạo thiết bị RAID1 có tên ``dev/md0`` bằng cách sử dụng câu lệnh sau:

```
[root@node2 ~]# mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sd[b-c]1
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: largest drive (/dev/sdc1) exceeds size (20953088K) by more than 1%
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
```

Ta có thể kiểm tra lại bằng lệnh:

```
[root@node2 ~]# mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Thu Feb 27 22:12:19 2020
        Raid Level : raid1
        Array Size : 20953088 (19.98 GiB 21.46 GB)
     Used Dev Size : 20953088 (19.98 GiB 21.46 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

       Update Time : Thu Feb 27 22:19:12 2020
             State : clean, resyncing
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : resync

     Resync Status : 18% complete

              Name : node2:0  (local to host node2)
              UUID : 3270066e:952ca40a:a27438f1:9fa16107
            Events : 374

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
```

Bước 4: Tạo filesystem và mount vào thư mục ``/mnt/test`` như RAID0

Bước 5: Kiểm tra dữ liệu sau khi hỏng đĩa

Thử làm 1 đĩa bị lỗi bằng cách xóa partition sau đó kiểm tra lại dữ liệu, check trạng thái của RAID1 khi đĩa bị lỗi

```
[root@node2 test]# mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Thu Feb 27 22:12:19 2020
        Raid Level : raid1
        Array Size : 20953088 (19.98 GiB 21.46 GB)
     Used Dev Size : 20953088 (19.98 GiB 21.46 GB)
      Raid Devices : 2
     Total Devices : 1
       Persistence : Superblock is persistent

       Update Time : Thu Feb 27 22:26:27 2020
             State : clean, degraded
    Active Devices : 1
   Working Devices : 1
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : resync

              Name : node2:0  (local to host node2)
              UUID : 3270066e:952ca40a:a27438f1:9fa16107
            Events : 399

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
```

Kết quả trả về là một ổ đĩa bị mất. Bây giờ thực hiện kiểm tra lại dữ liệu:

```
[root@node2 ~]# cd /mnt/test/
[root@node2 test]# ls
lost+found  test.cfg
[root@node2 test]# cat test.cfg
Test RAID1
[root@node2 test]# df -h
Filesystem               Size  Used Avail Use% Mounted on
devtmpfs                 908M     0  908M   0% /dev
tmpfs                    919M     0  919M   0% /dev/shm
tmpfs                    919M  8.9M  911M   1% /run
tmpfs                    919M     0  919M   0% /sys/fs/cgroup
/dev/mapper/centos-root   17G  3.7G   14G  22% /
/dev/sda1               1014M  192M  823M  19% /boot
tmpfs                    184M     0  184M   0% /run/user/0
/dev/md0                  20G   45M   19G   1% /mnt/test
```

#### RAID5



## Tham khảo : 

https://github.com/lacoski/khoa-luan/blob/master/RAID/raid%200%201%205.md
