# LAB 1: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
## I - Phân tích kiến trúc
- Hệ thống Payroll hiện tại của Acme, Inc. đang sử dụng một hệ thống cũ, không đáp ứng được yêu cầu hiện tại về quản lý thời gian và thanh toán cho nhân viên. Để phát triển một hệ thống mới, cần thiết phải đảm bảo các yếu tố như tính bảo mật, khả năng mở rộng và dễ dàng quản lý.
#### 1. Đề xuất kiến trúc
### Mô Hình 3 Lớp (Three-tier Architecture)
  - Lựa chọn mô hình 3 lớp là phù hợp cho hệ thống Payroll của Acme, Inc. với các thành phần chính như sau:
#### 1.1. Lớp Giao Diện (Presentation Layer)
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
#### 1.2. Cơ chế tính toán hoa hồng (Commission Calculation)
- **Giải thích**: Đối với nhân viên nhận lương dựa trên doanh số (commissioned employees), hệ thống cần tính toán và tổng hợp doanh số bán hàng để áp dụng phần trăm hoa hồng chính xác.
- **Lý do**: Đây là yếu tố cần thiết để xác định thu nhập thực tế của nhân viên nhận hoa hồng, đảm bảo tính đúng lương dựa trên doanh số bán hàng và tỷ lệ hoa hồng.
#### 1.3. Cơ chế tính toán lương cơ bản (Salary Calculation)
- **Giải thích**: Hệ thống cần tính toán lương cố định hàng tháng cho các nhân viên nhận lương theo tháng (salaried employees) và cho cả nhân viên hưởng hoa hồng nếu họ nhận lương cố định cùng hoa hồng.
- **Lý do**: Đảm bảo lương cơ bản được tính toán và phát hành vào đúng thời gian cho các nhân viên nhận lương cố định.
#### 1.4. Cơ chế cập nhật thông tin nhân viên (Employee Information Update)
- **Giải thích**: Hệ thống cần có chức năng để Payroll Administrator cập nhật thông tin cá nhân và thông tin làm việc của nhân viên (chẳng hạn như tên, địa chỉ, phương thức thanh toán, loại lương nhận).
- **Lý do**: Nhân viên có thể thay đổi địa chỉ, thông tin ngân hàng, hoặc thậm chí chuyển đổi từ nhân viên hưởng lương theo giờ sang hưởng lương cố định. Hệ thống cần phải linh hoạt trong việc cập nhật thông tin.
#### 1.5. Cơ chế lựa chọn phương thức thanh toán (Payment Method Selection)
- **Giải thích**: Nhân viên có thể chọn cách nhận lương qua chuyển khoản ngân hàng, nhận trực tiếp tại công ty, hoặc nhận qua bưu điện.
- **Lý do**: Đáp ứng nhu cầu cá nhân của nhân viên về phương thức nhận lương, đảm bảo tính linh hoạt và tiện lợi cho người lao động.
#### 1.6. Cơ chế bảo mật dữ liệu (Data Security Mechanism)
- **Giải thích**: Đảm bảo rằng chỉ nhân viên mới có quyền truy cập vào thông tin cá nhân của họ và chỉ Payroll Administrator có quyền chỉnh sửa thông tin liên quan đến nhân viên.
- **Lý do**: Bảo mật thông tin cá nhân và dữ liệu nhạy cảm liên quan đến lương là rất quan trọng để tránh lộ thông tin và bảo vệ quyền riêng tư của nhân viên.
#### 1.7. Cơ chế kết nối và tương tác với hệ thống DB2 (DB2 Integration)
- **Giải thích**: Hệ thống mới phải có khả năng kết nối và truy vấn từ hệ thống quản lý dự án hiện tại sử dụng DB2, nhưng không được phép chỉnh sửa dữ liệu trên hệ thống này.
- **Lý do**: Dữ liệu dự án và số tài khoản mã dự án cần được truy cập để tính toán chi phí và theo dõi chấm công, tuy nhiên hệ thống này phải được bảo toàn và chỉ sử dụng để tham khảo.
#### 1.8. Cơ chế tự động xử lý thanh toán (Automated Payroll Processing)
- **Giải thích**: Vào mỗi thứ Sáu và ngày làm việc cuối cùng của tháng, hệ thống phải tự động xử lý lương cho nhân viên, không cần sự can thiệp thủ công.
- **Lý do**: Đảm bảo tính chính xác và đúng hạn trong việc chi trả lương cho nhân viên. Giảm thiểu rủi ro sai sót do xử lý thủ công và tối ưu hóa quy trình.
## 2. Danh sách các cơ chế phù hợp
1. Xử lý chấm công
2. Tính toán hoa hồng
3. Tính toán lương cơ bản
4. Cập nhật thông tin nhân viên
5. Lựa chọn phương thức thanh toán
6. Bảo mật dữ liệu
7. Tương tác với DB2
8. Tự động xử lý thanh toán

## III - Phân tích ca sử dụng Payment
## 1. Xác định các lớp phân tích
 Các lớp chính cho ca sử dụng **Payment** có thể bao gồm:
+ **Employee**: Đại diện cho nhân viên, là người thực hiện việc lựa chọn phương thức thanh toán.
+ **PaymentMethod**: Đại diện cho các phương thức thanh toán có sẵn (chuyển khoản ngân hàng, nhận trực tiếp tại công ty, nhận qua bưu điện).
+ **PayrollAdministrator**: Người quản lý thông tin thanh toán và có quyền cập nhật thông tin cho nhân viên.
+ **PaymentSystem**: Hệ thống thực hiện xử lý các phương thức thanh toán.
## 2. Mô tả hành vi qua biểu đồ (Sequence Diagram)
![](https://www.planttext.com/api/plantuml/png/V8z12i8m44NtFSKiTU45id2ZxXI4u052ChQ191ESAILdS-6Hl88Qgr0etNxU-v__l3yECGSgYB3PmjcKY4bqOS6eu4YjJwjrCua_tCzHiFUSWocGlmXG5a-9cuLMZG6j_8s8qf6RMnc3KmKKNB8pWi1LHpUApOIQcTjHklfRXBxgIrzqHmDmRoqolzkPJOil0000__y30000)
#### 2.1 Nhiệm vụ
| Lớp                   | Nhiệm vụ                                                                                               | Thuộc tính                      |
|------------------------|-------------------------------------------------------------------------------------------------------|----------------------------------|
| **Employee**            | Đăng nhập vào hệ thống và chọn phương thức thanh toán.                                                | employeeId, name, email          |
| **PaymentMethod**       | Lưu trữ các phương thức thanh toán và xác nhận lựa chọn của nhân viên.                                | methodId, methodName             |
| **PayrollAdministrator**| Quản lý thông tin thanh toán của nhân viên và thực hiện các thay đổi khi cần thiết.                   | adminId, name, email             |
| **PaymentSystem**       | Xử lý các lựa chọn của nhân viên, cập nhật thông tin thanh toán và phản hồi cho nhân viên.            | systemId, status                 |
#### 2.2 Quan hệ 
+ **Employee** ↔ **PaymentMethod**: Một nhân viên có thể chọn nhiều phương thức thanh toán.
+ **PaymentMethod** ↔ **PayrollAdministrator**: Quản trị viên có quyền cập nhật hoặc thay đổi phương thức thanh toán cho nhân viên.
+ **Employee** ↔ **PaymentSystem**: Nhân viên gửi yêu cầu thanh toán đến hệ thống để xử lý.
## 3. Biểu đồ lớp 
![](https://www.planttext.com/api/plantuml/png/T58xJiKm4EnzYbKgA7812lGeA5u1Ge8Bh9n5MF8dU3U8274o2ex45OX_xoKYT9xPtPdnsZzVtmSMZ38vgxH5PkXktMZ3JDJ1XmBeWIe-3XbwT9GF8ywElDoHl8HK0c2ofELXpLzSvagarucubHRoKpMxJNlpT1bLnmBkYo-03lxPH7VMIYIzavw4_Z68mTgRmHblM29AYCq74taiwQTnm9F2AVsVe8yp2xacm1bLXJ46JSpRP6zeJH9-YkWPjPZWYspRC_JzDMp4uGgwkZ5kQ-xKtZtMioLocYqtuJooKjtjhOjR-UpbElUNDrwqrO7yi7oRNm000F__0m00)
#### 3.1 Giải thích
- **Employee**: Là đối tượng chính, thực hiện hành động chọn phương thức thanh toán và yêu cầu thanh toán. Lớp này liên kết với **PaymentMethod** để chọn phương thức.
- **PaymentMethod**: Quản lý và thực hiện các phương thức thanh toán. Nó có nhiệm vụ xác nhận và thực hiện thanh toán khi nhận yêu cầu từ **Employee**.
- **PayrollAdministrator**: Đảm bảo cập nhật chính xác thông tin thanh toán cho nhân viên trong trường hợp cần thay đổi hoặc điều chỉnh phương thức thanh toán.
- **PaymentSystem**: Đảm nhiệm toàn bộ quy trình xử lý thanh toán, kiểm tra tính hợp lệ và xử lý giao dịch.
## 4. Kết quả mông đợi
- Các lớp phân tích trên đảm bảo hệ thống có thể quản lý linh hoạt phương thức thanh toán, đảm bảo tính chính xác và bảo mật trong quá trình xử lý lương cho nhân viên.

## IV - Phân tích ca sử dụng Maintain Timecard
![](https://www.planttext.com/api/plantuml/png/b5D1IiD05DtFAJvTATGBP27TY1P415lGvNGQqh7992QJO9RIXGitUW2XjKYXK73XAhFeOehtc1Du1ITDGqqx1DtD_BptvlttoBTOjYAEGnvxBiA4-o6SU87hfxQD0ZscX0QOSMXqsmt04NJRrV4bJaFVTQ_IYDlU6b6PLC4Twja4X_qrhhpiw8N-hKrueLIS4IeTmT6nDc31wdarOWwmWSeM0IHo3AcSnq1KDelBQKzbKuqX-lRk0P6Vp47TTgvGCMZ1pPRA1paCE6L6UeMOAvKhM72kOQc9f9N536jJyer1GkMSeP9byD89jG8aIZpypK0UnXbLOiIqToMUZAoz-2wAXEgtXGFco77QX4Y95t3q8wzDyEHqypNHWqToQ8xqL8a5_NUQcxejk9OJKjJ8zbu4lUOq05UVqOPGd-DGPKiETt4-kDyAezeslpvYe-UQwdwRTdE-Nd_C1dNDTOg0UdBY6oX5icLtEptpMchBPltyV_u1003__mC0)

#### Bảng Phân Tích cho Ca Sử Dụng Maintain Timecard

| **Lớp**                | **Nhiệm vụ**                                                                                     | **Thuộc tính**                                                       | **Quan hệ**                                    |
|------------------------|--------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|------------------------------------------------|
| **Nhân viên (Employee)** | - Nhập và chỉnh sửa bảng chấm công. <br> - Chỉ có thể truy cập bảng chấm công của chính mình. | - ID: int <br> - Tên: String <br> - Địa chỉ: String <br> - Loại: String | - Một nhân viên có thể có nhiều bảng chấm công (1-n). |
| **Bảng chấm công (Timecard)** | - Lưu trữ thông tin thời gian làm việc. <br> - Cung cấp thông tin cho hệ thống.           | - Ngày: Date <br> - Số giờ làm việc: float <br> - Số giờ làm thêm: float <br> - Mã công việc: String | - Một bảng chấm công thuộc về một nhân viên (n-1). <br> - Một bảng chấm công liên kết với một hoặc nhiều mã công việc. |
| **Hệ thống Payroll (PayrollSystem)** | - Kiểm soát toàn bộ quy trình chấm công. <br> - Giao tiếp giữa các thành phần khác nhau. | - Danh sách nhân viên: List<Employee> <br> - Danh sách bảng chấm công: List<Timecard> | - Quản lý nhiều nhân viên và bảng chấm công tương ứng (1-n). |
| **Dự án (Project)**    | - Kiểm tra tính hợp lệ của mã công việc.                                                       | - Mã dự án: String <br> - Tên dự án: String                           | - Mã công việc từ bảng chấm công phải khớp với mã dự án (1-n). |

## 4.0 - Kết quả mong đợi
#### 4.1. Biểu đồ lớp
![](https://www.planttext.com/api/plantuml/png/V58xJiGm4ErpYb4QFj8Mj152Ax588C5gfKMYdas6nE1Fi9sL8aHDJKt52JX02WfEaXDm1Uny5YzYQIBxpPjvxqtyrNnCZKLjAy6ZbACnS2PAhceYU8m0u6AM09FM7oKAIc1fDPEvlsEMQJ8cX6nTRb5oijTCK8ewsp_mWAbMWeNOKpJ8ZbWlcw5rWsRkws-5ghIvKVgUiWHkkSBEZrgJjgxht5S3F2rGvpIln8fqQCRWcaB51TPQSRwiZINHozAGtOsxPCOUZxiuwS8D3iVYwBWhhf4pR_eq41yYEzc_0Y-qkgFKziAxF9SzQVvhzJlKtEmzk6gR5mOF5KeeskOPSjOsxmZfvriAl6rUosZpX-EZ62OJY0_Zd_Kd41TeucXxEm5pq-sO0YNcz1yxdEl2fEx1UFu6ZcLFTHtZGXnppEUOKvAPVvpV0000__y30000)

#### 4.2. Giải thích biểu đồ lớp

| **Lớp**                | **Mô Tả**                                                                                                                                           |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| **Employee (Nhân viên)** | - Mỗi nhân viên có một danh sách các bảng chấm công. <br> - Nhân viên có thể gửi và chỉnh sửa bảng chấm công của mình.                          |
| **Timecard (Bảng chấm công)** | - Lưu trữ thông tin về ngày làm việc, số giờ làm việc và mã công việc. <br> - Có mối quan hệ với `Project` để kiểm tra tính hợp lệ của mã công việc. |
| **PayrollSystem (Hệ thống Payroll)** | - Quản lý nhiều nhân viên và các bảng chấm công tương ứng. <br> - Thực hiện quá trình lưu và xác thực các bảng chấm công.                         |
| **Project (Dự án)**    | - Chứa thông tin về mã công việc và tên dự án. <br> - Được sử dụng để xác thực mã công việc từ bảng chấm công của nhân viên.                       |

## V - Hợp nhất kết quả phân tích

