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

Raid 0 là loại Raid khá phổ biến, bởi có khả năng nâng cao hiệu suất tốc độc đọc ghi trao đổi dữ liệu của ổ cứng. Để tiến hành setup Raid 0 thì cần tối thiểu 2 ổ đĩa (Disk 0, Disk 1).

Cách lưu trữ dữ liệu: Có 1 file A dung lượng 100MB. Khi tiến hành lưu trữ thay vì file A sẽ được lưu vào 1 ổ cứng duy nhất, Raid 0 sẽ lưu vào 2 ổ đĩa disk 0, disk 1 mỗi ổ 50MB (Striping), giảm thời gian đọc ghi xuống 1 nửa theo lý thuyết.

Ưu điểm:
- Tốc độ đọc ghi nhanh (gấp đôi bình thường theo lý thuyết).

Nhược điểm:

- Tiềm ẩn rủi ro về dữ liệu. Lý do dữ liệu được chia đôi lưu trên 2 ổ đĩa.Trường hợp 1 trong 2 ổ đĩa bị hỏng thì nguy cơ mất dữ liệu rất cao. Về ổ cứng yêu cầu phải 2 ổ cùng dung lượng, nếu 2 ổ khác dung lượng thì lấy ổ thấp nhất.

Đối tượng sử dụng:

Thích hợp với những dịch vụ cần lưu trữ và truy xuất với tốc độ cao. Chẳng hạn như dịch vụ video streaming, chạy cơ sở dữ liệu.

### Raid 1
