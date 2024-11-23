# Lab 4 thiết kế các ca sử dụng cho hệ thống "Payroll System"
![Hình ảnh hệ thống Payroll System](https://s.net.vn/j92K)
## **1. Tổng Quan Thiết Kế**
Hệ thống **Payroll System** được thiết kế để đáp ứng nhu cầu quản lý thông tin nhân viên, xử lý bảng lương, và cung cấp khả năng tương tác đơn giản nhưng hiệu quả giữa hai vai trò chính: **Employee** (Nhân viên) và **Payroll Administrator** (Quản trị viên hệ thống lương). Sơ đồ Use Case đã được thiết kế dựa trên các yêu cầu cụ thể và đảm bảo rằng mỗi chức năng đều có ý nghĩa và phù hợp với vai trò của từng tác nhân.

---

## **2. Lý Do Đưa Ra Thiết Kế**
Thiết kế này tập trung vào việc phân chia rõ ràng trách nhiệm giữa các tác nhân và đảm bảo hệ thống dễ mở rộng, bảo mật, và thân thiện với người dùng.

### **2.1. Các tác nhân**
- **Employee**: 
  - Nhân viên là người sử dụng chính của hệ thống, với nhu cầu nhập thông tin, xem báo cáo, và tùy chỉnh phương thức thanh toán. 
  - Quyền hạn được hạn chế ở mức chỉ có thể thao tác trên dữ liệu cá nhân của họ để đảm bảo bảo mật.

- **Payroll Administrator**: 
  - Vai trò này chịu trách nhiệm quản trị toàn bộ hệ thống, bao gồm việc quản lý thông tin nhân viên, cập nhật cài đặt thanh toán, và tạo các báo cáo tổng quan cho tổ chức.
  - Thiết kế cho phép quản trị viên dễ dàng thao tác mà không ảnh hưởng đến tính tự động hóa của hệ thống.

---

## **3. Giải Thích Các Use Case**
### **3.1. Use Case của Employee**
1. **Enter Timecard Info  (thông tin bản chấm công)**:
   - Nhân viên nhập thông tin về thời gian làm việc để hệ thống tính toán lương một cách chính xác.
   - Điều này đảm bảo nhân viên được trả lương đầy đủ và đúng hạn.

2. **Enter Purchase Order Info  (thông tin đơn hàng mua)**:
   - Dành cho các nhân viên có hoa hồng, họ có thể ghi lại các đơn hàng để hệ thống tính toán phần hoa hồng dựa trên doanh thu.

3. **View Personal Reports (Xem Báo Cáo Cá Nhân)**: 
   - Cho phép nhân viên kiểm tra thông tin cá nhân như số giờ làm, lương đã nhận, và ngày nghỉ còn lại.
   - Tính năng này tăng tính minh bạch và giảm sự phụ thuộc vào bộ phận nhân sự.

4. **Update Payment Method (Cập Nhật Phương Thức Thanh Toán)**:
   - Nhân viên có thể tùy chọn phương thức nhận lương: gửi qua bưu điện, chuyển khoản, hoặc nhận trực tiếp tại văn phòng.
   - Linh hoạt trong cách nhận lương giúp hệ thống thân thiện với người dùng.

### **3.2. Use Case của Payroll Administrator**
1. **Manage Employee Info (Quản Lý Thông Tin Nhân Viên)**:
   - Quản trị viên có thể thêm, xóa hoặc chỉnh sửa thông tin nhân viên, bao gồm các thay đổi về tên, địa chỉ, và phân loại lương (theo giờ, lương cứng, hoặc lương có hoa hồng).

2. **Generate Admin Reports (Báo Cáo Của Quản Trị Viên)**:
   - Tạo các báo cáo hành chính, ví dụ: bảng lương tổng hợp, báo cáo giờ làm việc theo dự án, hoặc phân tích chi phí lao động.

3. **Update Payment Settings**:
   - Quản trị viên có thể cập nhật các cài đặt thanh toán (ví dụ: tần suất trả lương, thay đổi tỷ lệ hoa hồng).

---

## **4. Ưu Điểm Của Thiết Kế**
1. **Tính phân quyền rõ ràng**:
   - Nhân viên và quản trị viên chỉ có thể truy cập và thực hiện các chức năng tương ứng với quyền hạn của họ.
   - Điều này đảm bảo bảo mật dữ liệu và giảm nguy cơ sai sót từ người dùng.

2. **Khả năng mở rộng**:
   - Nếu cần thêm chức năng mới (ví dụ: tích hợp hệ thống ngân hàng hoặc thêm vai trò khác), hệ thống có thể dễ dàng mở rộng.

3. **Tự động hóa cao**:
   - Quy trình xử lý lương sẽ được tự động hóa hoàn toàn, giảm thiểu sai sót thủ công và tối ưu hóa hiệu suất.

4. **Tính linh hoạt**:
   - Nhân viên có thể tùy chỉnh phương thức nhận lương và kiểm tra dữ liệu cá nhân một cách dễ dàng.

---

## **5. Kết Luận**
Thiết kế trên giúp đảm bảo hệ thống **Payroll System** vừa đáp ứng đầy đủ yêu cầu chức năng, vừa tối ưu hóa trải nghiệm người dùng. Với cấu trúc rõ ràng và phân quyền hợp lý, hệ thống có thể vận hành trơn tru, hỗ trợ tốt cho cả nhân viên và quản trị viên trong việc quản lý bảng lương và thông tin liên quan.
