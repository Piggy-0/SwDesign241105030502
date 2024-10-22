# LAB 1 PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
 
## 1. PHÂN TÍCH KIẾN TRÚC
Hệ thống phù hợp với kiến trúc phân lớp (Layered Architecture) vì tính chất rõ ràng giữa các tầng xử lý.

Các tầng trong hệ thống:
  - Tầng trình bày (Presentation Layer): Xử lý tương tác người dùng (ví dụ: nhập bảng công, xem lương).
  - Tầng logic nghiệp vụ (Business Logic Layer): Tính toán lương, quản lý bảng công, xử lý thanh toán.
  - Tầng truy cập dữ liệu (Data Access Layer): Quản lý việc truy xuất dữ liệu từ cơ sở dữ liệu (ví dụ: thông tin nhân viên, lịch sử thanh toán).
  - Tầng cơ sở dữ liệu (Database Layer): Lưu trữ và truy xuất dữ liệu.
