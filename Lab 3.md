# Lab 3. Identify design elements
# I - BankSystem
## 1.1 Subsystem context diagrams
![](https://www.planttext.com/api/plantuml/svg/h5AzRi8m4Dxz52TF83LGriYA44nibVe4hdEe5eaT-IvLexPFrg6Fr5SWDWG5Yih2TBxpz-UJVxz_biGwS5jNmbIQ2EIJxeAlghLt72i62KgPGrSKy240vdC8hOFcW9nCnPSGrZ66hJO8ShFIRlVS4MCj4xx4nfFbYUwrpIkQ7UGm71-WP_h8w8UnRDpMXrgpzIu97sEDDPMYzeLI0qtmxzqnrpry1dnqGSUMU_5nXX5D2d5jMrbMNEmWXz86D3m494WM16zMYtEe-iooyyVcy3YRBIvWoUCKzThbdwpoF_vj-X9T6N_97W00__y30000)
- Mô tả hệ thống con BankSystem
  
| **Yếu Tố**                       | **Chi Tiết**                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| **Lớp "BankSystem"**             | `subsystem proxy` (Proxy subsystem).                                         |
| Phương thức                      | `deposit(aPaycheck: Paycheck, intoBank: BankInformation)`: Gửi tiền vào tài khoản ngân hàng. |
| Mối quan hệ                      | Liên kết với `Paycheck` và `BankInformation` để thực hiện chuyển tiền.     |
| **Vai trò**                      | Xử lý giao dịch chuyển tiền vào tài khoản ngân hàng.                        |
| **Mối quan hệ với "IBankSystem"**| Triển khai giao diện `IBankSystem` và thực hiện phương thức `deposit`.     |
  

## 1.2 Analysis class to design element map
| Analysis Class              | Design Element                |
| --------------------------- | ----------------------------- |
| LoginForm                   | LoginForm                     |
| MaintainTimecardForm        | MainEmployeeForm, TimecardForm |
|                             | MainApplicationForm           |
| TimecardController          | TimecardController            |
| SystemClockInterface        | SystemClockInterface          |
| PayrollController           | PayrollController             |
| Paycheck                    | Paycheck                      |


## 1.3 Design element to owning package map
| Design Element              | "Owning" Package                |
| --------------------------- | ----------------------------- |
| LoginForm                   | Middleware::Security:GUI Framework |
| MainEmployeeForm            | Applications::Employee Activities| 
  TimecardForm                 
| Main ApplicationForm        | Middleware::Security:GUI Framework|
| TimecardController          | Applications::Employee        |
| SystemClockInterface        | Applications::Payroll          |
| PayrollController           | Applications::Payroll            |
| Paycheck                    | Business Services::Payroll Artifacts|

## 1.4 Architectural layers and their dependencies
![](https://www.planttext.com/api/plantuml/png/T99BJiCm443tFiMeh7k3AYe9gLIf2wGiKHU3CxHM73iQEqWHucGiE19N83OKajHTsPvdl_d8Nn-VM-UHVTzguHfbEcHiGIj3VkW8BFkpdG0cwT6SDC6R0CXHDYUslQaBgot3tQxSbKKPYEMQ-2UQw_6QU1VY__7glkkqakYLDN30WNW5cuqEcom3T33o68vfdXvnOAjrOOqFA_5neSjxDrRi75J4hqgIIqf_uKIypz4qrU0yjKjbrJ-x2DAg2vt8RhiUq6DI4y2yJtacsHmlkhrviTp6CKLdOXAmNcVpHa3CZ_72d5_XlymfkAm4n9PC7NxCDm000F__0m00)
# II - PrintService
## 2.1 Subsystem context diagrams
![](https://www.planttext.com/api/plantuml/png/T95DJiD038NtSmgpWqKkq0LgLQ9kAAhQNi1C7cZG_9InYnGXJiQ28t45sfIa6L1N8_czD_viVtz-JKKvwpvuSzNWoKNGkfvlPm-B-vgiPn5ZpeKwx7ng0NetH1MjyRg7wE7TfQnYFiRULNPHDyXlplR-hjIxwNh5RKxUttJQ0X6P5RHr0PPp8x_6KZraXdQ5C4yXE16NuWMSKxDDAuhGyvngTCVAV-7J2wmkEV8p0g8UBOyivqawVKWEYwcgstBoIRyb6RWAlGiKR1EQMGiHI0duFtOHSlp5cDHC4PlZhNy0003__mC0)
- Mô tả hệ thống con PrintService
  
**PrintService** là một hệ thống con trong hệ thống lương của công ty, chịu trách nhiệm xử lý việc in và tạo các báo cáo khác nhau liên quan đến lương, thẻ công, trả lương, và hoa hồng. Hệ thống này tương tác với các hệ thống khác để lấy dữ liệu cần thiết và cung cấp báo cáo cho nhân viên.

- Chức Năng Chính

**In Báo Cáo Lương**: Tạo và in báo cáo lương cho nhân viên, bao gồm thông tin về tiền lương, giờ làm việc, và các khoản trừ.

**In Báo Cáo Thẻ Công**: Tạo và in báo cáo thẻ công, bao gồm thông tin về giờ làm việc và dự án mà nhân viên đã tham gia.

**In Báo Cáo Trả Lương**: Tạo và in báo cáo trả lương, bao gồm thông tin về khoản tiền đã trả và phương thức thanh toán.

**In Báo Cáo Hoa Hồng**: Tạo và in báo cáo hoa hồng cho nhân viên nhận hoa hồng, bao gồm thông tin về doanh số bán hàng và tỷ lệ hoa hồng.

- Tương Tác với Các Hệ Thống Khác

**Nhân Viên (Employee)**: Nhân viên gửi yêu cầu báo cáo đến **PrintService**.

**Hệ Thống Lương (PayrollSystem)**: **PrintService** truy cập dữ liệu lương từ **PayrollSystem** để tạo báo cáo lương và trả lương.

**Cơ Sở Dữ Liệu Quản Lý Dự Án (ProjectManagementDatabase)**: **PrintService** truy cập dữ liệu dự án từ **ProjectManagementDatabase** để tạo báo cáo thẻ công và hoa hồng.

- Quy Trình Hoạt Động

**Nhân viên** yêu cầu báo cáo từ **PrintService**.
  
**PrintService** nhận yêu cầu và xác định loại báo cáo cần tạo.

**PrintService** truy cập dữ liệu cần thiết từ **PayrollSystem** và **ProjectManagementDatabase**.

**PrintService** tạo báo cáo dựa trên dữ liệu đã lấy được.

**PrintService** in và cung cấp báo cáo cho nhân viên.

## 2.2 Analysis class to design element map
| **Analysis Class**                  | **Design Element**                                                                 |
|-------------------------------------|-------------------------------------------------------------------------------------|
| Employee                            | User Interface (UI) for employees to request reports                               |
| PrintService                        | PrintService Module (handles report generation and printing)                      |
| PayrollSystem                       | PayrollSystem API (provides payroll data)                                        |
| ProjectManagementDatabase           | ProjectManagementDatabase API (provides project data)                              |
| PayrollReport                      | PayrollReport Class (specific report type for payroll data)                       |
| TimecardReport                     | TimecardReport Class (specific report type for timecard data)                    |
| PayReport                          | PayReport Class (specific report type for payment data)                          |
| CommissionReport                    | CommissionReport Class (specific report type for commission data)                 |

## 2.3 Design element to owning package map
| **Design Element**                                                                 | **Owning Package**                                                                 |
|-------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| User Interface (UI) for employees to request reports                               | `com.acme.printservice.ui`                                                         |
| PrintService Module (handles report generation and printing)                      | `com.acme.printservice.core`                                                       |
| PayrollSystem API (provides payroll data)                                         | `com.acme.payrollsystem.api`                                                       |
| ProjectManagementDatabase API (provides project data)                              | `com.acme.projectmanagement.api`                                                   |
| PayrollReport Class (specific report type for payroll data)                       | `com.acme.printservice.reports`                                                    |
| TimecardReport Class (specific report type for timecard data)                     | `com.acme.printservice.reports`                                                     |
| PayReport Class (specific report type for payment data)                           | `com.acme.printservice.reports`                                                    |
| CommissionReport Class (specific report type for commission data)                 | `com.acme.printservice.reports`                                                    |

## 2.4 Architectural layers and their dependencies
![](https://www.planttext.com/api/plantuml/png/X9EnJiD038RtFCMf4mnz0GRKgZ1qGAfe4REvkkLeSXTi1wXGduo1H-8LE3U9w8K48cM8V_-VVOxlw-DpmW8aLP5dnfHWTx15CwhSoBp7W34s1sPpnqXpBqWRiDWe-X0-LyXoYsKWuRFpet38z3t5sK2O0XVal2oHNbp2sw970i4Kg4-fXl_gKArtIi6UGfxNtfvQYNw2RlqhLw05MWy2qeGUGgpmL_L1tomKXMDsmG_Qkoc3eu7IzOvbkMV1OhgO9t1fr2iGw3iGXIUqSWC-iWlqedaFmFYRKsTsE6bhpcy8MAYoKdNtf0NFWlUH4yzvmhTrS1NQh9vMhz_Yrdh8crtJ9Tx6mQKWrqJntibZnz5jkt9cFBuqkjBcGYy6PwR-qd2pWJzA6r0n_eCeJAr5haKDg91E8EOSxnhOw7kD7MM7R89-hNVq6m00__y30000)

# III - ProjectManagementDatabase subsystems
## 3.1 Subsystem context diagrams
![](https://www.planttext.com/api/plantuml/png/h991Zi8m34NtEONPCOjUe0i40eIGPYe4Sm6JcbAKf2Xs5mXnCXPpfBd2Y4u5AHGG4hleVt_xESdlyQVFWbvAQrGdfLNk2ERZuVSWcNoEGHjaLkeYp73d2sCMEnQoi5S04Q3Mn3ppnOQqJDsgw6xhSnh3GdpkieyO0Zz83TVeCqfAkoHVHNKW1EdhEdLeKFtt_aA76LboCaB19J9LX00PoMjuLUIjR2UZfhaP7we9MchJHoIO6pvRZHdN1FMWDjx0Q6dPVDuewZsusXXA9bRt2u9u1HM39oczUvQvsUOIL7rowUch_W400F__0m00)
- Mô tả ProjectManagementDatabase

| **Thành phần**          | **Trách nhiệm**                                                                 | **Phương thức/Thuộc tính**                                                                 | **Mô tả**                                                                 |
|-------------------------|----------------------------------------------------------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| **ProjectManagementDatabase** | Lưu trữ và cung cấp quyền truy cập vào thông tin dự án và số thứ tự tính phí.     | `getProjectInfo(projectId: String): ProjectInfo`                            | Trả về thông tin dự án cho một ID dự án cụ thể.                            |
|                         |                                                                                  | `getChargeNumberInfo(chargeNumber: String): ChargeNumberInfo`               | Trả về thông tin số thứ tự tính phí cho một số thứ tự tính phí cụ thể.     |
| **ProjectInfo**         | Đại diện cho thông tin liên quan đến một dự án.                                 | `projectId: String`                                                         | ID duy nhất của dự án.                                                       |
|                         |                                                                                  | `projectName: String`                                                       | Tên của dự án.                                                              |
|                         |                                                                                  | `projectDetails: String`                                                    | Thông tin chi tiết bổ sung về dự án.                                        |
| **ChargeNumberInfo**    | Đại diện cho thông tin liên quan đến một số thứ tự tính phí.                    | `chargeNumber: String`                                                      | ID duy nhất của số thứ tự tính phí.                                         |
|                         |                                                                                  | `chargeDetails: String`                                                     | Thông tin chi tiết bổ sung về số thứ tự tính phí.                           |

## 3.2 Analysis class to design element map
## 3.3 Design element to owning package map
## 3.4 Architectural layers and their dependencies

