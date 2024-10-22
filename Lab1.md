# Lab 1

## 1. Phân tích kiến trúc

Kiến trúc được đề xuất cho hệ thống Payroll là kiến trúc **Layered Architecture** với 3 tầng chính:

### Tầng Giao diện (UI Layer):
Chức năng: Giao diện người dùng, nơi người dùng nhập liệu và xem kết quả.

Vai trò: Cung cấp trải nghiệm thân thiện, dễ sử dụng.

Ví dụ: Màn hình nhập thông tin nhân viên, màn hình chấm công, báo cáo.

### Tầng Logic (Business Logic Layer):
Chức năng: Xử lý các yêu cầu từ người dùng và thực hiện các tính toán nghiệp vụ.

Vai trò: Đảm bảo logic nghiệp vụ được thực hiện chính xác và hiệu quả.

Ví dụ: Tính toán lương, xử lý thanh toán, kiểm tra và xác nhận thông tin chấm công.

### Tầng Dữ liệu (Data Access Layer):
Chức năng: Lưu trữ và truy xuất dữ liệu liên quan đến hệ thống.

Vai trò: Quản lý dữ liệu an toàn, nhất quán và hiệu quả.

Ví dụ: Kết nối cơ sở dữ liệu, thao tác với bảng dữ liệu nhân viên, bảng lương, bảng chấm công.

## Đề xuất kiến trúc
**Lớp Presentation (Giao diện): Xử lý giao diện người dùng (UI).**
Ý nghĩa: Đảm bảo người dùng có thể dễ dàng nhập liệu và xem báo cáo.

Ví dụ: Màn hình nhập thông tin nhân viên, màn hình chấm công, màn hình báo cáo.

**Lớp Business Logic (Logic nghiệp vụ): Xử lý các logic nghiệp vụ chính.**
Ý nghĩa: Thực hiện các tính toán lương, xử lý chấm công, và các quy trình nghiệp vụ khác.

Ví dụ: Tính toán lương, xử lý thanh toán, cập nhật giờ làm việc.

**Lớp Data Access (Truy cập dữ liệu): Kết nối và thao tác với cơ sở dữ liệu.**
Ý nghĩa: Đảm bảo dữ liệu được lưu trữ an toàn và có thể truy cập một cách hiệu quả.

Ví dụ: Các lớp DAO (Data Access Object) để tương tác với bảng dữ liệu nhân viên, bảng lương, bảng chấm công.

**Lớp Database (Cơ sở dữ liệu): Lưu trữ dữ liệu.**
Ý nghĩa: Lưu trữ và quản lý thông tin nhân viên, lương, giờ làm việc.

Ví dụ: Cơ sở dữ liệu nhân viên, cơ sở dữ liệu lương, cơ sở dữ liệu chấm công.

### Biểu đồ Package mô tả kiến trúc
![Package Diagram](http://www.plantuml.com/plantuml/png/SoEncodedDiagramText)

## 2. Cơ chế phân tích

### Đề xuất các cơ chế cần giải quyết
1. **Cơ chế xác thực người dùng**: Đảm bảo rằng chỉ những người dùng có thông tin hợp lệ mới có thể truy cập vào hệ thống.
2. **Cơ chế quản lý thời gian**: Ghi lại số giờ làm việc của nhân viên và tính toán lương dựa trên thời gian làm việc đó.
3. **Cơ chế thanh toán**: Xác định các phương thức thanh toán và xử lý quy trình thanh toán chính xác.
4. **Cơ chế báo cáo lương**: Hệ thống cần cho phép nhân viên truy cập và xem chi tiết thông tin thanh toán.

## 3. Phân tích ca sử dụng Payment

### Xác định các lớp phân tích
- Lớp `Employee`: Đối tượng nhân viên, có thể yêu cầu thông tin thanh toán.
- Lớp `Payment`: Chứa thông tin về tiền lương và phương thức thanh toán.
- Lớp `PaymentController`: Xử lý yêu cầu từ nhân viên liên quan đến thông tin thanh toán.

### Biểu đồ tuần tự cho ca sử dụng Payment
![Sequence Diagram](http://www.plantuml.com/plantuml/png/SoEncodedDiagramText)

### Biểu đồ lớp phân tích Payment
![Class Diagram](http://www.plantuml.com/plantuml/png/SoEncodedDiagramText)

## 4. Phân tích ca sử dụng Maintain Timecard

### Xác định các lớp phân tích
- Lớp `Employee`: Đối tượng nhân viên, có thể gửi dữ liệu thẻ chấm công.
- Lớp `Timecard`: Chứa thông tin về giờ làm việc.
- Lớp `TimecardController`: Xử lý yêu cầu nộp thẻ chấm công từ nhân viên.

### Biểu đồ tuần tự cho ca sử dụng Maintain Timecard
![Sequence Diagram](http://www.plantuml.com/plantuml/png/SoEncodedDiagramText)

### Biểu đồ lớp phân tích Maintain Timecard
![Class Diagram](http://www.plantuml.com/plantuml/png/SoEncodedDiagramText)

## 5. Hợp nhất kết quả phân tích

Kết hợp các kết quả phân tích từ hai ca sử dụng trên cho thấy sự tương tác giữa các lớp `Employee`, `Payment`, `Timecard`, và các lớp điều khiển tương ứng (`PaymentController`, `TimecardController`). Hệ thống Payroll yêu cầu sự phối hợp giữa nhiều lớp để xử lý chính xác thông tin liên quan đến lương và thời gian làm việc.


