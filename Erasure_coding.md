**Erasure coding (EC)** là một phương pháp bảo vệ dữ liệu mà trong đó dữ liệu được chia thành các đoạn, được mở rộng và mã hóa với các phần dữ liệu dự phòng và được lưu trữ trên một tập hợp các vị trí hoặc phương tiện lưu trữ khác nhau

Mục tiêu của EC là để cho phép dữ liệu bị hỏng tại một số điểm trong quá trình lưu trữ đĩa được xây dựng lại bằng cách sử dụng thông tin về dữ liệu được lưu trữ ở nơi khác trong mảng

EC thường được sử dụng thay vì RAID truyền thống vì khả năng giảm thời gian và chi phí cần thiết để tạo lại dữ liệu. Hạn chế của việc EC là nó có thể tốn nhiều CPU và tăng độ trễ

EC có nguồn gốc từ một phương trình toán học: n=k+m

Trong đó:
- **k** : dữ liệu gốc
- **m** : dữ liệu được thêm vào
- **n** : kết quả dữ liệu được erasure

Phương trình này có thể được sử dụng để khôi phục lại dữ liệu ban đầu
