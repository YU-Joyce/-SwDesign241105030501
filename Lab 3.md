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
