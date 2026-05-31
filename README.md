# VFFS Packaging Machine SCADA Simulation

## Giới thiệu
Dự án này mô phỏng hệ thống máy đóng gói đứng VFFS trên TIA Portal, bao gồm mô hình điều khiển PLC, giao diện SCADA/HMI, giám sát trạng thái máy và điều khiển các cụm cơ khí chính trong quá trình đóng gói.
Hệ thống được xây dựng nhằm mô phỏng quy trình đóng gói tự động với các công đoạn như cấp liệu, kéo màng, hàn, cắt, đếm gói và giám sát lỗi. Ngoài ra, project còn thực hiện tuning bộ điều khiển PID cho nhiệt độ dao hàn và vận tốc servo để nâng cao chất lượng mô phỏng và ổn định quá trình vận hành.

## Chức năng
* Mô phỏng quy trình hoạt động của máy đóng gói đứng VFFS.
* Thiết kế giao diện SCADA/HMI giám sát và điều khiển hệ thống.
* Điều khiển các cụm chính của máy:
  * Cụm cấp liệu.
  * Cụm kéo màng.
  * Cụm hàn.
  * Cụm cắt.
  * Cụm đếm gói.
* Cài đặt thông số công nghệ:
  * Tốc độ đóng gói.
  * Chiều dài gói.
  * Nhiệt độ dao hàn.
  * Trạng thái Start/Stop.
* Giám sát trạng thái từng cụm máy.
* Hiển thị cảnh báo và lỗi hệ thống.
* Mô phỏng các lỗi thường gặp:
  * Mất đồng bộ.
  * Thiếu màng.
  * Kẹt sản phẩm.
  * Lệch nhiệt độ.
  * Lỗi cảm biến mark.
* Thống kê số gói đạt, thời gian chu kỳ và số lần dừng máy.
* Tuning PID cho:
  * Nhiệt độ dao hàn.
  * Vận tốc cụm servo cuộn màng.
* Đánh giá ảnh hưởng của thông số tốc độ và nhiệt độ đến chất lượng đóng gói mô phỏng.

## Công nghệ sử dụng
* TIA Portal
* PLC Siemens
* WinCC / HMI / SCADA
* Ladder Logic / Function Block
* PID Control
* Servo Control
* Mô phỏng hệ thống đóng gói tự động
* Điều khiển nhiệt độ
* Điều khiển vận tốc

## Phần cứng / Mô hình mô phỏng
| Thành phần        | Mô tả                                      |
| ----------------- | ------------------------------------------ |
| PLC Siemens       | Bộ điều khiển trung tâm của hệ thống       |
| HMI/SCADA         | Giao diện giám sát và điều khiển máy       |
| Cảm biến mark     | Phát hiện vị trí dấu in trên màng          |
| Cảm biến sản phẩm | Kiểm tra sản phẩm trong quá trình đóng gói |
| Servo kéo màng    | Điều khiển kéo màng theo chiều dài gói     |
| Dao hàn           | Gia nhiệt và hàn miệng bao bì              |
| Dao cắt           | Cắt bao bì sau khi hàn                     |
| Cụm cấp liệu      | Cấp sản phẩm vào bao bì                    |
| Bộ PID nhiệt độ   | Điều khiển nhiệt độ dao hàn                |
| Bộ PID vận tốc    | Điều khiển vận tốc servo                   |

## Nguyên lý hoạt động
Máy đóng gói đứng VFFS hoạt động theo chu trình tự động. Ban đầu, hệ thống cấp liệu đưa sản phẩm vào vùng đóng gói. Servo kéo màng thực hiện kéo màng theo chiều dài gói đã cài đặt. Cảm biến mark được sử dụng để xác định vị trí cắt và đồng bộ chiều dài bao bì.
Sau khi màng được kéo đúng vị trí, cụm dao hàn thực hiện hàn bao bì theo nhiệt độ đặt trước. Nhiệt độ dao hàn được điều khiển bằng bộ PID nhằm đảm bảo nhiệt độ ổn định trong quá trình làm việc. Tiếp theo, cụm dao cắt thực hiện cắt bao bì thành từng gói riêng biệt. Sau mỗi chu kỳ, hệ thống cập nhật số lượng gói và trạng thái vận hành trên giao diện SCADA.
Trong quá trình mô phỏng, hệ thống có khả năng phát hiện và cảnh báo các lỗi như mất đồng bộ, thiếu màng, kẹt sản phẩm, sai lệch nhiệt độ hoặc lỗi cảm biến mark. Người vận hành có thể theo dõi trạng thái từng cụm máy, thay đổi thông số công nghệ và quan sát ảnh hưởng của thông số tốc độ/nhiệt độ đến chất lượng đóng gói.

## Cấu trúc thư mục
```text
.
├── VFFS_TIA_Portal/
├── PID_Tuning/
├── Documents/
├── Images/
└── README.md
```
| File/Thư mục       | Mô tả                                                          |
| ------------------ | -------------------------------------------------------------- |
| `VFFS_TIA_Portal/` | Chứa project mô phỏng máy đóng gói đứng trên TIA Portal        |
| `PID_Tuning/`      | Chứa dữ liệu hoặc kết quả tuning PID nhiệt độ và vận tốc servo |
| `Documents/`       | Chứa tài liệu, báo cáo hoặc thuyết minh project                |
| `Images/`          | Chứa hình ảnh giao diện SCADA/HMI và mô hình mô phỏng          |
| `README.md`        | File giới thiệu tổng quan về project                           |

## Hướng dẫn chạy
### Bước 1: Mở project TIA Portal
Mở phần mềm TIA Portal, sau đó mở project trong thư mục:
```text
VFFS_TIA_Portal/
```
Kiểm tra lại cấu hình PLC, HMI và các tag điều khiển trước khi chạy mô phỏng.
### Bước 2: Kiểm tra chương trình PLC
Trong project PLC, kiểm tra các khối chương trình chính:
* Khối điều khiển trình tự máy.
* Khối điều khiển cụm cấp liệu.
* Khối điều khiển servo kéo màng.
* Khối điều khiển dao hàn.
* Khối điều khiển dao cắt.
* Khối xử lý cảnh báo và lỗi.
* Khối thống kê số gói và chu kỳ máy.
* Khối PID nhiệt độ.
* Khối PID vận tốc servo.
### Bước 3: Chạy mô phỏng PLC/HMI
Khởi động mô phỏng PLC và HMI trên TIA Portal. Sau đó mở giao diện SCADA/HMI để điều khiển và giám sát hệ thống.
Trên giao diện, người dùng có thể:
* Nhấn Start/Stop.
* Cài đặt chiều dài gói.
* Cài đặt tốc độ đóng gói.
* Cài đặt nhiệt độ dao hàn.
* Quan sát trạng thái từng cụm máy.
* Theo dõi cảnh báo và lỗi.
* Xem số lượng gói đã đóng.
### Bước 4: Tuning bộ điều khiển PID
Thực hiện tuning PID cho hai đối tượng chính:
1. **PID nhiệt độ dao hàn**
   * Mục tiêu: giữ nhiệt độ dao hàn ổn định quanh giá trị đặt.
   * Biến điều khiển: công suất gia nhiệt.
   * Biến phản hồi: nhiệt độ dao hàn.
2. **PID vận tốc servo**
   * Mục tiêu: điều khiển servo kéo màng chạy ổn định theo tốc độ đặt.
   * Biến điều khiển: tín hiệu điều khiển servo.
   * Biến phản hồi: vận tốc thực tế của servo.
Sau khi tuning, quan sát đáp ứng hệ thống để đánh giá:
* Thời gian quá độ.
* Độ vọt lố.
* Sai số xác lập.
* Độ ổn định khi thay đổi tốc độ máy.
* Ảnh hưởng của nhiệt độ đến chất lượng hàn mô phỏng.
* 
## Kết quả đạt được
* Xây dựng được mô hình SCADA mô phỏng máy đóng gói đứng VFFS.
* Thiết kế được giao diện cài đặt thông số công nghệ.
* Thiết kế được giao diện giám sát trạng thái từng cụm máy.
* Mô phỏng được chu trình đóng gói tự động.
* Mô phỏng được các cảnh báo và lỗi trong quá trình vận hành.
* Thống kê được số gói đạt, thời gian chu kỳ và số lần dừng máy.
* Tuning được bộ PID nhiệt độ dao hàn.
* Tuning được bộ PID vận tốc servo kéo màng.
* Đánh giá được ảnh hưởng của tốc độ và nhiệt độ đến chất lượng đóng gói mô phỏng.

## Ghi chú
* Project tập trung vào mô phỏng và thiết kế SCADA cho máy đóng gói đứng VFFS.
* Các thông số PID cần được hiệu chỉnh tùy theo mô hình mô phỏng hoặc yêu cầu công nghệ.
* Có thể mở rộng project để kết nối với phần cứng thực tế như PLC Siemens, HMI Siemens, biến tần, servo drive và cảm biến công nghiệp.
* Chi tiết: thuật toán, mô phỏng cảm biến,.. được giải thích trong file báo cáo SCADA_nhom26.pdf
