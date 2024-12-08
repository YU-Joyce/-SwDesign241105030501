# Thiết kế hệ thống PAYROLL SYSTEM
## 1. Xác định các operations và methods
![](https://www.planttext.com/api/plantuml/png/h5LBRjim4Dth58GtLGfhqIrX62dY0WcGD8PTe6jQd4XiH5BW9wZGzcHTz4YzGYcBeaLzWA285x8rVFDvmpVZlx__N6j3bB6yIlAAQ8tsf56ogewDDi3HZmITFyeAVv1IOW2ZdNjUOVGY6Kr-9Txt4wyhsG1ujmmnYX4Jnhy9mftdqIWc2cyYb2hGUcIjISD1c0SmfNGHziDN3p6CGquKTQxtJ9lD5_--lOIuTNQf6W_mGRQUK4wgt5QEXBEdvnRi0gyr0a5tGvfKsbC5tjNLt6TB-p8mwarzKpfi0UO0jLGclGeSGxjkfLLLCsbQUJOVplcZnFzLSyXs91LH3EWadsuFcZVDTICvPrepALwNBqDvy9WGTvTfLLuI3O-AWkflV3yqlisrHY5JsJwT-eR6YUGZROPngPNCdQpzOKgujCBq-IOnUkc43br6R209_LMgPw3ZlfL45V3PybDRwrXXKUtBuUFw9kHUxTWP-UpO3eEsU-GZvKo4Xhdczpf9mV_0OP_4CwM0onUOmE-wNHDZRTtMt6Fln9CSuzVkyIGnUY3rfclV6ZsUla5kjgEqLfnhdfldT-XU5io93nt0gS-fM9UiracyJ5SVLYZBjcZrVdLPbHXn8aW1EWccpSyi6oy7ZE2xSVeTmoPJlGIS7SaPS2ZIVSVYniXgc4CwEa7265MoM03rSiAex5PpCYAv4551xcPH9nEk2tYZIFwiard6KJtHT62axOapusujiiyp28icN78dw8Kx9ksX8-tMLtBj6jx-t_u3003__mC0)

## 2. Xác định trạng thái
![](https://www.planttext.com/api/plantuml/png/T9AzJiCm481tFyNDI7q11bHKEh1LH69138TzJItvJxwpK9wDWKVY5R2JL8b2MIpRztrtzja_Nzzx5inIl5DlT--mspt0it6aL1l7vHCA7eFa0UxXw9EB0n6us3FOe9RW5Nr5PmsAZQ7oNVdmLa2i9utPGCoGIjONPAfpGrbjb6t1LUYCrf6v9PnmoD6v0pfTtBNqYad8N4rrWvjrJq5EEMfYjg6lzY7Mcv8GC3gi9z6Be_xoBSiBfPXbikTGBJoIeETivXztx7NjRgWTEZUh7HFI12crf5x1qoRq52XZIxsyM3UmaEykHKpyRBruDDu6O8c9WSUWsZ1Dg--lzXHC-mk_0000__y30000)

### 2.1 Mô tả
1. Từ Idle → DataEntry
- Điều kiện kích hoạt: Nhân viên hoặc quản trị viên đăng nhập vào hệ thống.
- Hành động:
  + Hệ thống xác thực thông tin đăng nhập.
  + Hiển thị giao diện nhập liệu (timecard, purchase order, hoặc thông tin liên quan).
2. Từ DataEntry → DataValidation
- Điều kiện kích hoạt: Nhân viên gửi timecard hoặc purchase order
- Hành động:
  + Hệ thống nhận dữ liệu nhập và chuyển sang bước kiểm tra tính hợp lệ.
  + Thông báo trạng thái "Đang xác minh dữ liệu."
3. Từ DataValidation → DataEntry (Validation Failed):
- Điều kiện kích hoạt: Dữ liệu nhập không hợp lệ (VD: giờ làm vượt giới hạn, mã dự án không tồn tại, v.v.).
- Hành động:
  + Hệ thống hiển thị lỗi và yêu cầu nhân viên sửa dữ liệu nhập.
  + Chuyển về giao diện nhập liệu.
4. Từ DataValidation → PayrollCalculation:
- Điều kiện kích hoạt: Dữ liệu nhập hợp lệ.
- Hành động:
  + Hệ thống ghi lại dữ liệu đã xác thực.
  + Bắt đầu tính toán lương dựa trên loại hình làm việc của nhân viên:
  + Nhân viên theo giờ: Tính giờ làm bình thường và giờ tăng ca.
  + Nhân viên cố định: Tính theo lương cố định.
  + Nhân viên hoa hồng: Tính lương cố định + hoa hồng dựa trên doanh số.
5. Từ PayrollCalculation → PaymentProcessing:
- Điều kiện kích hoạt: Lương được tính toán thành công.
- Hành động:
  + Xác định phương thức thanh toán (chuyển khoản, gửi bưu điện, nhận tại văn phòng).
  + Hệ thống xử lý thanh toán theo phương thức được chọn.
6. Từ PaymentProcessing → Reporting:
- Điều kiện kích hoạt: Thanh toán hoàn thành.
- Hành động:
  + Hệ thống tạo báo cáo liên quan:
  + Tổng số giờ làm việc.
  + Tổng lương đã nhận.
  + Tổng số ngày nghỉ còn lại.
  + Hiển thị kết quả báo cáo cho nhân viên hoặc quản trị viên.
7. Từ PaymentProcessing → Idle:
- Điều kiện kích hoạt: Thanh toán hoàn thành, không yêu cầu báo cáo.
- Hành động:
  + Hệ thống kết thúc quy trình xử lý lương và quay lại trạng thái chờ
8. Từ Reporting → Idle:
- Điều kiện kích hoạt: Báo cáo được tạo xong.
- Hành động:
  + Hệ thống lưu trữ báo cáo và quay lại trạng thái chờ để sẵn sàng xử lý yêu cầu tiếp theo.
9. Từ Idle → SystemShutdown:
- Điều kiện kích hoạt: Quản trị viên tắt hệ thống.
- Hành động:
  + Hệ thống lưu trạng thái hiện tại và đóng tất cả quy trình hoạt động.
  + Kết thúc vận hành hệ thống

## 3 Xác định các thuộc tính
![](https://www.planttext.com/api/plantuml/png/X5DDJuGm4BtpAngE9hjnhyIGLJ7PJNIp4QFdRXdPQZ_Cj1o8yPTvy2Vv5onGsAMGo0KwR-RDl3Vbz_jdRIn5MqaHCK6D8NjQenOYhuq5IJuZqZvtyaFe6c2RaOJa5hag0sH79OIOuvAWx0FOeov2y8bBO1IB32pbmZZudXjxrOTJdxRH5OhwaTg6FTFLGO17SYeerc7qLal9ZU5QpTMyQ7nl69jsMsMX1EphZXHBs5No01YE-amPjOxnndLKR4AwH_q6p0P2V3GTUx5na6wdxfAwQ1fzHTx_NlzWVUPbkDUP9QPH0iL4_QoAWTpFD73xytIh7fXRwdyjEaMd5jrvgk9QwihbXLxENnb7FxwOyIecYmM9BvVBY_XaMaAuOg8gm8JvNM9Jicg_UYiIWl0A26wlavfHZrvOGafGW4w8YTQWYkRN-GC00F__0m00)

## 4. Xác định các phụ thuộc, quan hệ kết hợp
![](https://www.planttext.com/api/plantuml/png/f5JBJiCm4BpdAwoS0AaLN2DKbH94Aq5LjHMStMH93NvKQmSfGdmP1pw9Ny1fdAHDsWQ9NABiZ6V7itP-lhw7sb0qgU1UnAdMP4OpL9mlCcr0a0-FR9yxiU4g0vY4920BWqmc3MHA1JGngoL0caSmQnKtmIKJ456CGp2KSMtX1wRDTLaUEDfOfSYpEJMvUgZI5GU7B2Ydc3Mhjqe8fZLJyj2QPuLlkMBURY8D983bkZN51AQfM04shJxHY1ghEB8TPTGIdQ5wXSWqDkAgW_qinXPIMzS5gQWEl4_FvL_c-S_eGzZOiURQVnnAPQ0SG6KWT3dQryvCT1ubnAtu3yPOYRlcbRRxRhUu4IhTUjzFkiExoxoMBxxRqJdWK78TEvZ3Hc7TuHuaeBLTpgA0pywRgYNFNQyspJROlth-bKzwFU9VzliNVdqi0YAef0dea_HgY05XCk9ftC4lvnAGn1djuBkW0uBm0WZsLfnUu6BRrQ-sTDIwJbU2cQFCsZH21Emzj-1y7PNaJDfJkrJU46IS__L-0G00__y30000)
