# Hệ Thống Quản Lý Chấm Công và Thanh Toán Lương Nhân Viên

## 1. Nhập thông tin bảng chấm công (Submit Timecard Information)
- **Diễn giải:** Nhân viên nhập thông tin thời gian làm việc của mình, bao gồm ngày làm việc, số giờ đã làm và mã công việc (charge number).
- **Tác nhân:** Nhân viên (Hourly Employee, Salaried Employee).
- **Mục đích:** Ghi nhận giờ làm việc của nhân viên để làm cơ sở tính lương.

## 2. Nhập thông tin đơn hàng (Submit Purchase Orders)
- **Diễn giải:** Nhân viên hưởng hoa hồng nhập thông tin đơn hàng, bao gồm ngày và số tiền của đơn hàng.
- **Tác nhân:** Nhân viên hưởng hoa hồng (Commissioned Employee).
- **Mục đích:** Ghi nhận doanh thu để tính hoa hồng cho nhân viên.

## 3. Thay đổi phương thức thanh toán (Change Payment Method)
- **Diễn giải:** Nhân viên có thể thay đổi phương thức nhận lương (qua thư, chuyển khoản ngân hàng, hoặc nhận trực tiếp tại văn phòng).
- **Tác nhân:** Nhân viên.
- **Mục đích:** Đảm bảo rằng nhân viên có thể lựa chọn phương thức nhận lương phù hợp nhất với nhu cầu của mình.

## 4. Tạo báo cáo cá nhân (Generate Personal Reports)
- **Diễn giải:** Nhân viên yêu cầu tạo các báo cáo cá nhân, bao gồm số giờ làm, tổng giờ đã chấm công, tổng thu nhập từ đầu năm, số ngày nghỉ phép còn lại, v.v.
- **Tác nhân:** Nhân viên.
- **Mục đích:** Giúp nhân viên theo dõi thông tin công việc và thu nhập của mình một cách minh bạch.

## 5. Thêm nhân viên mới (Add New Employee)
- **Diễn giải:** Quản trị viên hệ thống thêm thông tin nhân viên mới, bao gồm tên, địa chỉ, phân loại (theo giờ, lương cứng, hưởng hoa hồng), và các thông tin cần thiết khác.
- **Tác nhân:** Quản trị viên hệ thống (Payroll Administrator).
- **Mục đích:** Đảm bảo rằng nhân viên mới được thêm vào hệ thống và được chi trả lương đúng hạn.

## 6. Xóa nhân viên (Delete Employee)
- **Diễn giải:** Quản trị viên hệ thống có thể xóa thông tin nhân viên khi họ nghỉ việc hoặc bị sa thải.
- **Tác nhân:** Quản trị viên hệ thống.
- **Mục đích:** Loại bỏ thông tin nhân viên không còn làm việc để hệ thống chỉ lưu trữ dữ liệu nhân viên hiện tại.

## 7. Thay đổi thông tin nhân viên (Edit Employee Information)
- **Diễn giải:** Quản trị viên có thể thay đổi các thông tin của nhân viên, bao gồm tên, địa chỉ, và phân loại nhân viên.
- **Tác nhân:** Quản trị viên hệ thống.
- **Mục đích:** Đảm bảo thông tin nhân viên luôn được cập nhật chính xác để hệ thống tính toán lương phù hợp.

## 8. Tạo các báo cáo hành chính (Generate Administrative Reports)
- **Diễn giải:** Quản trị viên tạo các báo cáo phục vụ cho quản lý hành chính, như báo cáo tổng số nhân viên, báo cáo các khoản thanh toán, v.v.
- **Tác nhân:** Quản trị viên hệ thống.
- **Mục đích:** Hỗ trợ công tác quản lý và theo dõi thông tin nhân sự của công ty.

## 9. Chạy chương trình tính lương tự động (Run Payroll Process Automatically)
- **Diễn giải:** Hệ thống tự động tính toán và phát lương vào các ngày quy định: Thứ Sáu hàng tuần cho nhân viên làm theo giờ và ngày làm việc cuối cùng của tháng cho nhân viên lương cứng.
- **Tác nhân:** Hệ thống (tự động).
- **Mục đích:** Đảm bảo việc phát lương diễn ra đúng hạn, đúng quy trình, mà không cần can thiệp thủ công.

## 10. Truy cập thông tin dự án (Access Project Information)
- **Diễn giải:** Hệ thống lấy thông tin về mã công việc từ cơ sở dữ liệu quản lý dự án khi nhân viên nhập bảng chấm công, nhưng không thay đổi thông tin trong cơ sở dữ liệu này.
- **Tác nhân:** Hệ thống (tự động).
- **Mục đích:** Đảm bảo hệ thống sử dụng đúng thông tin về mã công việc khi tính toán lương và ghi nhận giờ làm việc.

## 11. Thanh toán nhân viên (Process Employee Payment)
- **Diễn giải:** Hệ thống thực hiện việc thanh toán cho nhân viên vào các ngày chỉ định, dựa trên phương thức thanh toán mà nhân viên đã chọn (thư, chuyển khoản ngân hàng, hoặc nhận tại văn phòng).
- **Tác nhân:** Hệ thống (tự động).
- **Mục đích:** Đảm bảo việc trả lương cho nhân viên được thực hiện đầy đủ và đúng cách, phù hợp với lựa chọn của mỗi nhân viên.
- ---------------------------------------------------------------------------------------------------------------------------------------------------------
# Code JAVA Maintain Timecard.
 ```java
class Timecard {
    private String ngayLamViec;
    private double soGioLam;
    private String maCongViec;

    public Timecard(String ngayLamViec, double soGioLam, String maCongViec) {
        this.ngayLamViec = ngayLamViec;
        this.soGioLam = soGioLam;
        this.maCongViec = maCongViec;
    }

    public String getNgayLamViec() {
        return ngayLamViec;
    }

    public double getSoGioLam() {
        return soGioLam;
    }

    public String getMaCongViec() {
        return maCongViec;
    }

    @Override
    public String toString() {
        return "Ngày làm việc: " + ngayLamViec + ", Số giờ làm: " + soGioLam + ", Mã công việc: " + maCongViec;
    }
}



class NhanVien {
    private String maNhanVien;
    private String tenNhanVien;
    private List<Timecard> danhSachTimecard;

    public NhanVien(String maNhanVien, String tenNhanVien) {
        this.maNhanVien = maNhanVien;
        this.tenNhanVien = tenNhanVien;
        this.danhSachTimecard = new ArrayList<>();
    }

    public void themTimecard(Timecard timecard) {
        danhSachTimecard.add(timecard);
    }

    public void hienThiTimecards() {
        System.out.println("Danh sách bảng chấm công của nhân viên: " + tenNhanVien);
        for (Timecard tc : danhSachTimecard) {
            System.out.println(tc);
        }
    }
}



import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class PayrollSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Tạo nhân viên mẫu
        NhanVien nhanVien = new NhanVien("NV001", "Nguyen Van A");

        // Nhập thông tin bảng chấm công
        System.out.println("Nhập số lượng bảng chấm công:");
        int soLuongTimecards = scanner.nextInt();
        scanner.nextLine();  // Đọc dòng mới còn lại

        for (int i = 0; i < soLuongTimecards; i++) {
            System.out.println("Nhập thông tin bảng chấm công thứ " + (i + 1) + ":");
            System.out.print("Ngày làm việc (dd/MM/yyyy): ");
            String ngayLamViec = scanner.nextLine();
            System.out.print("Số giờ làm: ");
            double soGioLam = scanner.nextDouble();
            scanner.nextLine();  // Đọc dòng mới còn lại
            System.out.print("Mã công việc: ");
            String maCongViec = scanner.nextLine();

            Timecard timecard = new Timecard(ngayLamViec, soGioLam, maCongViec);
            nhanVien.themTimecard(timecard);
        }

        // Hiển thị bảng chấm công của nhân viên
        nhanVien.hienThiTimecards();
    }
}
