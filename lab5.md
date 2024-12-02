# Hệ thống Payroll System
![](https://www.planttext.com/api/plantuml/png/h5RDRjf04Bxp55lk72hrnA4A94qKgQ6eL8fw7Eo9sR8_rkmQHAiyMGzzfBv2nrvZ1-Cr7Be79Ezyu_c--JD_V_-vSHx85rgDtlaDQXIv0cb68xUL9WS2BN98jf2X-3KIVERyb94jJ7fhbINnMMOR_nsLiljWjvGY1TiTqFQ144rbkRV6Bu0Zp4Y2QgvMyYUAzn-QvwxhwrikYGBd8aoUDz9ZPPaHsNsuNC3kqCjhfS3Z0y5XY5k0pnL7AdaSCp5Ume6iKc9rS1xrk2PK_JIOJpfNze0edi3mXKRZZy3o12KDg3MKPo9aEXKhJz9a7ODXbX4Jf2cXSn5h3eUImnFwZJr_-Mk7s2pLqlmNLfoeSrC8noazITatgJ41IWTJre2wv58kw9HhMpT1QzZOWjopfIqo_NjbmNS0oGOemqMXrqW3cMcADPbyR6bCnPWmuUvourvHouBu_Gx5bx811wKTeG7PrLSry6Ei0b7re7b4V5TuHDKf0vRcYhMMFYODoLa3Idp5t98VrbPZQsXNtCKQUUj1yTprMtUGW9VMb5MvLkef8TQwaxYFA0tZS8NC2XZHM4auSk0nVJHT6NdOAwj2Qw0pgQsGGATKyJOUIyZG874Fn0eMTe1OaaruKt0NzHIgndJPr_iZse3zVHPi-jBIQQQfgapDWFKae992jOBASzgZLpYSbht5yjYYtCLo5NQxkBNcHMO5LUrrdgs02g3pZRHcWy6aT8rjPR8_6D2srDry84trTwUcLievYS-Q2jVgOKNd3ltV9VQKncDMzqwFM-zklkmsiFskS1xOBvUzepDxHU2UEUbutQ19otzD_m000F__0m00)
## 1. Quản lý thông tin nhân viên (Employee Management)
- Mô tả: Quản lý dữ liệu nhân viên, bao gồm thông tin cá nhân, phương thức thanh toán, và các tùy chọn liên quan.
- Chức năng chính:
  Cập nhật thông tin cá nhân (họ tên, địa chỉ, email, số tài khoản ngân hàng, v.v.).
  Quản lý phương thức thanh toán (thư, chuyển khoản, nhận tiền trực tiếp).
  Kiểm tra thông tin lương cá nhân.
- Tương tác:
  Nhân viên (Employee): Chỉnh sửa thông tin cá nhân.
  Quản trị viên (Payroll Admin): Thêm/sửa/xóa dữ liệu nhân viên.
## 2. Quản lý chấm công (Timecard Management)
- Mô tả: Hệ thống ghi nhận và xử lý thông tin giờ làm việc của nhân viên.
- Chức năng chính:
  Nhập thông tin thẻ chấm công.
  Tính giờ làm việc bình thường và giờ tăng ca.
  Phân bổ giờ làm việc vào các mã dự án.
- Tương tác:
  Nhân viên: Nhập thông tin thẻ chấm công.
  Payroll System: Tự động tính toán lương dựa trên giờ làm việc.
## 3. Quản lý đơn hàng (Purchase Order Management)
- Mô tả: Xử lý thông tin về đơn hàng mua hàng để tính hoa hồng cho nhân viên bán hàng.
- Chức năng chính:
  Nhập thông tin đơn hàng (ngày, số tiền, mã nhân viên).
  Tính toán hoa hồng dựa trên tỷ lệ được cấu hình.
- Tương tác:
  Nhân viên: Nhập thông tin đơn hàng.
  Payroll System: Tự động tính toán hoa hồng.
## 4. Quản lý báo cáo cá nhân (Personal Report Management)
- Mô tả: Cung cấp báo cáo chi tiết cho từng nhân viên.
- Chức năng chính:
  Hiển thị số giờ làm việc đã ghi nhận.
  Tổng hợp số ngày nghỉ phép còn lại.
  Tính tổng lương đã nhận từ đầu năm.
- Tương tác:
  Nhân viên: Truy cập để xem báo cáo cá nhân.
## 5.Quản lý báo cáo quản trị (Admin Report Management)
- Mô tả: Cung cấp báo cáo cho quản trị viên để quản lý hiệu quả hệ thống.
- Chức năng chính:
  Tạo báo cáo tổng hợp về lương, giờ làm việc, và hoa hồng.
  Xem danh sách nhân viên và trạng thái thanh toán.
- Tương tác:
  Quản trị viên: Xem và tạo báo cáo.
## 6.Quản lý cấu hình hệ thống (System Configuration)
- Mô tả: Cấu hình các thiết lập thanh toán và quy trình vận hành.
- Chức năng chính:
  Cập nhật tỷ lệ hoa hồng.
  Cấu hình ngày thanh toán tự động (thứ Sáu hàng tuần hoặc cuối tháng).
  Tích hợp với cơ sở dữ liệu DB2.
- Tương tác:
  Quản trị viên: Cập nhật và thay đổi thiết lập hệ thống.
## 7.Xử lý thanh toán (Payment Processing)
- Mô tả: Tự động xử lý thanh toán lương cho nhân viên.
- Chức năng chính:
  Tính toán lương theo giờ, lương cố định, và hoa hồng.
  Gửi thanh toán qua phương thức được chọn (thư, chuyển khoản, hoặc trực tiếp).
  Lưu trữ hóa đơn và lịch sử thanh toán.
- Tương tác:
  Payroll System: Chạy quy trình thanh toán tự động.
  Cơ sở dữ liệu: Ghi nhận thông tin thanh toán.
