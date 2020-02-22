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
