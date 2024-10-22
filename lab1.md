# LAB 1: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
## I - Phân tích kiến trúc
- Hệ thống Payroll hiện tại của Acme, Inc. đang sử dụng một hệ thống cũ, không đáp ứng được yêu cầu hiện tại về quản lý thời gian và thanh toán cho nhân viên. Để phát triển một hệ thống mới, cần thiết phải đảm bảo các yếu tố như tính bảo mật, khả năng mở rộng và dễ dàng quản lý.
#### 1. Đề xuất kiến trúc
### Mô Hình 3 Lớp (Three-tier Architecture)
  - Lựa chọn mô hình 3 lớp là phù hợp cho hệ thống Payroll của Acme, Inc. với các thành phần chính như sau:
### 1.1. Lớp Giao Diện (Presentation Layer)
- **Chức năng**: Cung cấp giao diện cho nhân viên để nhập thông tin về thời gian làm việc, yêu cầu thanh toán và truy xuất các báo cáo.
- **Công nghệ**: Sử dụng Windows Forms hoặc WPF cho ứng dụng desktop.
- **Ý nghĩa**: Tạo trải nghiệm người dùng tốt và dễ dàng trong việc tương tác với hệ thống.
#### 1.2. Lớp Logic Kinh Doanh (Business Logic Layer)
- **Chức năng**: Xử lý các quy tắc và logic liên quan đến tính toán tiền lương, xác định giờ làm việc và quản lý hoa hồng.
- **Công nghệ**: Ngôn ngữ lập trình như C#, Java, hoặc Python để triển khai các thuật toán.
- **Ý nghĩa**: Tách biệt logic khỏi giao diện và cơ sở dữ liệu, giúp dễ dàng bảo trì và nâng cấp.
#### 1.3. Lớp Cơ Sở Dữ Liệu (Data Access Layer)
- **Chức năng**: Truy cập và quản lý dữ liệu trong cơ sở dữ liệu, lưu trữ thông tin về nhân viên và các giao dịch.
- **Công nghệ**: Sử dụng ORM (Object-Relational Mapping) như Entity Framework hoặc Hibernate.
- **Ý nghĩa**: Đảm bảo khả năng bảo mật và hiệu suất cao khi tương tác với dữ liệu.
## 2. Giải Thích Lý Do Lựa Chọn
- **Tách Biệt Rõ Ràng**: Giúp dễ dàng bảo trì và nâng cấp hệ thống mà không làm ảnh hưởng đến các thành phần khác.
- **Quản Lý Dễ Dàng**: Nhóm phát triển có thể cập nhật hoặc thay đổi một lớp mà không ảnh hưởng đến các lớp khác.
- **Bảo Mật Cao Hơn**: Quản lý quyền truy cập dữ liệu giúp tăng cường bảo mật cho hệ thống.
- **Khả Năng Mở Rộng**: Dễ dàng tích hợp các tính năng mới hoặc hệ thống bên ngoài trong tương lai.
- **Hỗ Trợ Tương Tác với Nhiều Cơ Sở Dữ Liệu**: Đảm bảo khả năng kết nối với các cơ sở dữ liệu khác nếu cần.
## 3. Biểu Đồ Package Mô Tả Kiến Trúc
![](https://www.planttext.com/api/plantuml/png/b9CnIiH058RxdE9Tm0ji8UXQ24PPSGkjGXnbCp0x2N6oO6rX9HWyWCGWuiBY5bP9iSM4t6DEu1LyGrP9p0IJBZFy_p_V-n_voZU22dODPsK2nQFAd-1GvVSmzLGUynbCtDlGPyoo0ZSKbD30vG9EFFd2dGMLIzwurqv7L4xdnraNZCl4kL7vitEbyW-7KTH7tGcdzi6UPTKUWvrTuniZ95BPAe1BbQK8JV3qEWSYF_dCCXbqa8bb17QvZemn9dcBHnDlC-OohPomq5fYjOJT4ESo8S3rIBoTqmlajvZzzYXGn9Z94BApcrhdJHfJC_qsT26N4H2LlKKWv8fx6g1C1kzdsijhMCeH1jpDGOHkpzMOnpZ-umKKf04m_ExNfbsXLqieudADVb9LqhF9CLuyS0YyRP8Ml6E4vs8pmfS97zgfoX8VywZADj6_tJQccUW3Mb55Mma3VbtUCdy3003__mC0)

## II - Cơ chế phân tích
## 1. Cơ chế xử lý chấm công (Timecard Processing)
- **Giải thích**: Đây là cơ chế quan trọng cho các nhân viên làm việc theo giờ (hourly employees). Hệ thống phải có khả năng ghi nhận, tính toán giờ làm việc, và phân biệt giờ làm thêm (overtime) để trả lương phù hợp.
- **Lý do**: Nhân viên làm việc theo giờ cần phải được trả lương dựa trên số giờ làm việc thực tế và có mức lương đặc biệt cho giờ làm thêm.
## 2. Cơ chế tính toán hoa hồng (Commission Calculation)
- **Giải thích**: Đối với nhân viên nhận lương dựa trên doanh số (commissioned employees), hệ thống cần tính toán và tổng hợp doanh số bán hàng để áp dụng phần trăm hoa hồng chính xác.
- **Lý do**: Đây là yếu tố cần thiết để xác định thu nhập thực tế của nhân viên nhận hoa hồng, đảm bảo tính đúng lương dựa trên doanh số bán hàng và tỷ lệ hoa hồng.
## 3. Cơ chế tính toán lương cơ bản (Salary Calculation)
- **Giải thích**: Hệ thống cần tính toán lương cố định hàng tháng cho các nhân viên nhận lương theo tháng (salaried employees) và cho cả nhân viên hưởng hoa hồng nếu họ nhận lương cố định cùng hoa hồng.
- **Lý do**: Đảm bảo lương cơ bản được tính toán và phát hành vào đúng thời gian cho các nhân viên nhận lương cố định.
## 4. Cơ chế cập nhật thông tin nhân viên (Employee Information Update)
- **Giải thích**: Hệ thống cần có chức năng để Payroll Administrator cập nhật thông tin cá nhân và thông tin làm việc của nhân viên (chẳng hạn như tên, địa chỉ, phương thức thanh toán, loại lương nhận).
- **Lý do**: Nhân viên có thể thay đổi địa chỉ, thông tin ngân hàng, hoặc thậm chí chuyển đổi từ nhân viên hưởng lương theo giờ sang hưởng lương cố định. Hệ thống cần phải linh hoạt trong việc cập nhật thông tin.
## 5. Cơ chế lựa chọn phương thức thanh toán (Payment Method Selection)
- **Giải thích**: Nhân viên có thể chọn cách nhận lương qua chuyển khoản ngân hàng, nhận trực tiếp tại công ty, hoặc nhận qua bưu điện.
- **Lý do**: Đáp ứng nhu cầu cá nhân của nhân viên về phương thức nhận lương, đảm bảo tính linh hoạt và tiện lợi cho người lao động.
## 6. Cơ chế bảo mật dữ liệu (Data Security Mechanism)
- **Giải thích**: Đảm bảo rằng chỉ nhân viên mới có quyền truy cập vào thông tin cá nhân của họ và chỉ Payroll Administrator có quyền chỉnh sửa thông tin liên quan đến nhân viên.
- **Lý do**: Bảo mật thông tin cá nhân và dữ liệu nhạy cảm liên quan đến lương là rất quan trọng để tránh lộ thông tin và bảo vệ quyền riêng tư của nhân viên.
## 7. Cơ chế kết nối và tương tác với hệ thống DB2 (DB2 Integration)
- **Giải thích**: Hệ thống mới phải có khả năng kết nối và truy vấn từ hệ thống quản lý dự án hiện tại sử dụng DB2, nhưng không được phép chỉnh sửa dữ liệu trên hệ thống này.
- **Lý do**: Dữ liệu dự án và số tài khoản mã dự án cần được truy cập để tính toán chi phí và theo dõi chấm công, tuy nhiên hệ thống này phải được bảo toàn và chỉ sử dụng để tham khảo.
## 8. Cơ chế tự động xử lý thanh toán (Automated Payroll Processing)
- **Giải thích**: Vào mỗi thứ Sáu và ngày làm việc cuối cùng của tháng, hệ thống phải tự động xử lý lương cho nhân viên, không cần sự can thiệp thủ công.
- **Lý do**: Đảm bảo tính chính xác và đúng hạn trong việc chi trả lương cho nhân viên. Giảm thiểu rủi ro sai sót do xử lý thủ công và tối ưu hóa quy trình.
## Danh sách các cơ chế phù hợp
1. Xử lý chấm công
2. Tính toán hoa hồng
3. Tính toán lương cơ bản
4. Cập nhật thông tin nhân viên
5. Lựa chọn phương thức thanh toán
6. Bảo mật dữ liệu
7. Tương tác với DB2
8. Tự động xử lý thanh toán

## III - Phân tích ca sử dụng Payment
