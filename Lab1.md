# LAB 1 PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
 
## 1. PHÂN TÍCH KIẾN TRÚC
   - Lựa chọn kiến trúc: Kiến trúc phân lớp (Layered Architecture)
     + Presentation Layer (Tầng giao diện)
     + Business Logic Layer (Tầng nghiệp vụ)
     + Data Access Layer (Tầng truy cập dữ liệu)
     + Database Layer (Tầng cơ sở dữ liệu)
   - Lý do lựa chọn:
     + Dễ bảo trì vì các tầng hoạt động độc lập, giúp phát hiện và khắc phục lỗi nhanh chóng mà không ảnh hưởng đến các thành phần khác.
     + Dễ mở rộng khi cần thêm chức năng hoặc thay đổi logic nghiệp vụ mà không cần phải thay đổi toàn bộ hệ thống.
     + Có thể dễ dàng thay đổi logic nghiệp vụ hoặc giao diện mà không ảnh hưởng đến dữ liệu.
     + Bảo mật tốt hơn, có thể đặt các cơ chế bảo mật mạnh mẽ ở từng lớp, chẳng hạn xác thực người dùng ở tầng giao diện và mã hóa dữ liệu ở tầng truy cập dữ liệu.
   - Ý nghĩa từng thành phần trong kiến trúc:
     + Presentation Layer (Tầng giao diện): Quản lý giao diện người dùng (UI) và gửi yêu cầu từ người dùng xuống tầng nghiệp vụ để xử lý, như nhân viên, quản lý, bộ phận kế toán.
     + Business Logic Layer (Tầng nghiệp vụ): Thực hiện các quy tắc tính toán và xử lý các quy trình nghiệp vụ liên quan đến tính toán lương, khấu trừ thuế, và phát hành lương.
     + Data Access Layer (Tầng truy cập dữ liệu): Giao tiếp với cơ sở dữ liệu để lấy và cập nhật thông tin về nhân viên, lương, giờ làm việc,....
     + Database Layer (Tầng cơ sở dữ liệu): Lưu trữ toàn bộ dữ liệu của hệ thống, bao gồm thông tin nhân viên, lịch sử lương và các khoản chi trả. Đảm bảo tính toàn vẹn và bảo mật cho dữ liệu
   - Biểu đồ UML Package cho Hệ thống Payroll:


     ![UML](https://www.planttext.com/api/plantuml/png/T9112i9034NtEKKkO8yWjNRPHQyGnb12fpCoIHSYdgmBZ-GLT12fr37B_nuyo6EvrsgKR9uyW8uIC4Lb01FpZ3svaGPMtE7HaogsGaEY2U3y9jWdLWv69Z5qTE64U8NRofjP9R1g5mTn9Q4beuDpMVb36rB-Ph_9gjgNGb3OihfDmdRuI6iPNbTpEEKtFG400F__0m00)

## 2. Cơ chế phân tích

Các cơ chế phân tích giúp giải quyết các vấn đề phức tạp trong hệ thống. Một số cơ chế phân tích có thể áp dụng cho Payroll System là:
  - Persistency (Cơ chế bền vững): Đảm bảo rằng thông tin về nhân viên, thanh toán, và thời gian làm việc được lưu trữ an toàn, giúp hệ thống có thể phục hồi và truy xuất dữ liệu khi cần thiết.
  - Communication (IPC and RPC) (Cơ chế trao đổi dữ liệu): Cần thiết để các thành phần trong hệ thống có thể trao đổi dữ liệu một cách hiệu quả và chính xác, đảm bảo tính liên kết giữa các phần của hệ thống.
  - Transaction Management (Quản lý giao dịch): Quản lý giao dịch để đảm bảo tính nhất quán trong quá trình thanh toán. Đảm bảo tính toàn vẹn của dữ liệu, đặc biệt trong các tình huống giao dịch phức tạp, như khi tính toán lương và ghi nhận thời gian làm việc.
  - Security (Cơ chế bảo mật): Đảm bảo thông tin nhân viên và các thanh toán được lưu trữ an toàn, chỉ có quyền truy cập từ những người có thẩm quyền. Đặc biệt quan trọng trong hệ thống tính lương, nơi chứa nhiều thông tin cá nhân và tài chính của nhân viên.
  - Error Handling (Quản lý lỗi): Quản lý các lỗi phát sinh khi giao dịch không thành công. Giúp nâng cao độ tin cậy của hệ thống và cung cấp thông tin cần thiết để sửa chữa lỗi một cách nhanh chóng.
  - Legacy interface: Đảm bảo rằng hệ thống mới có thể làm việc hiệu quả với các hệ thống cũ mà không gặp khó khăn, giúp giảm thiểu chi phí chuyển đổi và thời gian gián đoạn.
  - Report Management (Cơ chế quản lý báo cáo): Cung cấp các báo cáo chính xác và chi tiết về lương, khấu trừ, thuế và thời gian làm việc, hỗ trợ việc ra quyết định và kiểm soát

 ## 3. Phân tích ca sử dụng Select Payment
### a. Mô Tả Ca Sử Dụng "Payment"
 - Tên ca sử dụng: Payment
 - Diễn giả chính: Khách hàng
 - Mô tả: Khách hàng thực hiện thanh toán cho đơn hàng của họ thông qua hệ thống. Hệ thống xử lý thanh toán và gửi thông báo cho khách hàng về trạng thái thanh toán.
### b. Các lớp phân tích cho ca sử dụng Selected Payment
Boundary Class: PaymentUI
  - Mô tả: Lớp này quản lý giao diện người dùng cho việc thực hiện thanh toán.
  - Nhiệm vụ: Thu thập thông tin thanh toán từ khách hàng và hiển thị kết quả thanh toán.

Control Class: PaymentController
  - Mô tả: Lớp này xử lý logic thanh toán.
  - Nhiệm vụ: Điều phối các bước thực hiện thanh toán và tương tác giữa các lớp khác.

Entity Class: Payment
  - Mô tả: Lớp này đại diện cho thông tin thanh toán.
  - Nhiệm vụ: Lưu trữ thông tin thanh toán, chẳng hạn như số tiền, phương thức thanh toán và trạng thái thanh toán.

Entity Class: Order
  - Mô tả: Lớp này đại diện cho đơn hàng mà khách hàng đang thanh toán.
  - Nhiệm vụ: Lưu trữ thông tin chi tiết của đơn hàng.
### c. Biểu Sequence của ca sử dụng Select Payment

![Sequence Diagram](https://www.planttext.com/api/plantuml/png/Z98nJiD044NxFSMKK7012XGf1I0Xe029rh6js8ez2-inaaj4IPKRO4MKaIYel4KAeznZJi0LcCLnx28cAMTttf__P_V7haOPUORoD57PB4OmEWkLvvCsCCupqcber4Jd67YcW5klI4Ea-qlbQoIZa_Pat9I9D4iLqxQrBMzC87UgbOIJiquCJk4wuchv21JLNpW54XyKUHW1wRh4esFLzNPWDrC4pjakuxry3n6TFq_2Nd7rKVJPx_cwH8ZgTvmAsxGDpBqpN2tWcUtBiC3EuPj39y5LgGLXEvS4wq-s2oUpo_-GYuUwz07T3WyAtj_yHSpsrL5its36rOhWANUP_dc0xIkA-IRqf9O8m_GenC3zi5y0003__mC0)

### d. Nhiệm vụ của từng lớp phân tích
PaymentUI:
  - Thu thập thông tin thanh toán từ khách hàng (số thẻ, ngày hết hạn, v.v.).
  - Hiển thị thông báo kết quả thanh toán cho khách hàng.

PaymentController:
  - Nhận thông tin thanh toán từ PaymentUI.
  - Tương tác với lớp Order để lấy thông tin đơn hàng liên quan.
  - Tạo đối tượng Payment để lưu trữ thông tin thanh toán.
  - Xác nhận thanh toán và gửi kết quả về PaymentUI.

Payment:
  - Chứa các thuộc tính như amount, paymentMethod, paymentStatus.
  - Cung cấp các phương thức để xác nhận thanh toán.

Order:
  - Chứa các thuộc tính như orderId, customerId, totalAmount.
  - Cung cấp thông tin cần thiết cho việc thanh toán.
