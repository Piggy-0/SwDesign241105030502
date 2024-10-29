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
 - Diễn giả chính: Nhân viên
 - Mô tả: Nhân viên thực hiện thanh toán cho đơn hàng của họ thông qua hệ thống. Hệ thống xử lý thanh toán và gửi thông báo cho nhân viên về trạng thái thanh toán.
### b. Các lớp phân tích cho ca sử dụng Selected Payment
 - Boundary Class: PaymentUI
 - Control Class: PaymentController
 - Entity Class: Payment, Order

### c. Biểu Sequence của ca sử dụng Select Payment

![Sequence Diagram](https://www.planttext.com/api/plantuml/png/T9AnJiCm443t-ufJ9nZu0GPKAKAb4WAaKedLJQmcQc8Nnq7oY1YP-WT45MCb1gPuw13K__0Ny0kScng1r8pdUtVtxkHlknsMcYbT5Jb0kSW4Abbo01PhgV2oMERIS0upMOc4AOE3EsOABgRZ0R8IHzCnn59e9VEGqL4NvrpjaKa4z9XfWuTy26zLmXK0X1buTk7xuJdUfAxPB56dxQUOeoOddJAHefPjBKvEmLC4Jo9YHyvkidwK62BtemY-Tisx-Gj_hNQrmBHz4tE2EonqlbUkMUEJiy_z5LtxmsA-nZMr9CRP5KdjFfnT-xf_Ie4ESnxQEaRXLpuktztaAdFsnGFElkB2DLkDZvKNF7gQtvkIKkS-Qqcilmw6N2Jq1tu0003__mC0)

### d. Nhiệm vụ của từng lớp phân tích
Boundary Class: PaymentUI
  - Mô tả: Lớp này quản lý giao diện người dùng cho việc thực hiện thanh toán.
  - Nhiệm vụ: Thu thập thông tin thanh toán và hiển thị kết quả thanh toán.

Control Class: PaymentController
  - Mô tả: Lớp này xử lý logic thanh toán.
  - Nhiệm vụ: Điều phối các bước thực hiện thanh toán và tương tác giữa các lớp khác.

Entity Class: Payment
  - Mô tả: Lớp này đại diện cho thông tin thanh toán.
  - Nhiệm vụ: Lưu trữ thông tin thanh toán, chẳng hạn như số tiền, phương thức thanh toán và trạng thái thanh toán.

Entity Class: Order
  - Mô tả: Lớp này đại diện cho đơn hàng mà nhân viên đang thanh toán.
  - Nhiệm vụ: Lưu trữ thông tin chi tiết của đơn hàng.

### e. Một số thuộc tính và phương thức của các lớp phân tích
PaymentUI:
  - Không có thuộc tính, tập trung vào các phương thức hiển thị yêu cầu nhập thông tin và hiển thị kết quả.
  - Thu thập thông tin thanh toán (số thẻ, ngày hết hạn, v.v.).
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

### f. Mối quan hệ giữa các lớp
  - PaymentUI - PaymentController: Kết hợp (Association). PaymentUI gửi thông tin thanh toán từ khách hàng đến PaymentController và nhận kết quả xử lý.
  - PaymentController - Payment: Thành phần (Composition). PaymentController tạo và quản lý các đối tượng Payment để lưu thông tin thanh toán.
  - PaymentController - Order: Kết hợp (Association). PaymentController truy cập Order để lấy thông tin đơn hàng cần thanh toán.

### g. Biểu đồ lớp

![Class Diagram](https://www.planttext.com/api/plantuml/png/T94zJiGm48NxdC8b5Bb02hG8cYqG2CG1BDiRBEoPo3CkLeZ3fA14eYO51TBU8oVW2ZZ48Sh-kFDyC-yzZt-whnMn31ozA-ZPWWX8fb1E4eaxkVK6-74jNWen70jDv5ozDYojexFp4MbBZPFR3EyDHSU9lHPBhIi43kYS2PDc4r0PeimdkThmRT0cp2xxIdc-b1uZS2Ks3YMFfMRik37yXBeInC52lK0FB3dI0Wc5iB71pq7-7V-IJ7uuNDP9raAsKv4O_LwHaQMxFCXs_67peilouiYgKj2-UnUwxzvIsaC-J8qXAy6xZrqBjU3lLfredJQOcllF5ekL0Jty_oy0003__mC0)

Giải Thích Biểu Đồ Lớp

  - PaymentUI: Chịu trách nhiệm giao tiếp với người dùng để thu thập thông tin thanh toán và hiển thị kết quả.
  - PaymentController: Chịu trách nhiệm xử lý logic thanh toán. Nó tương tác với Order để lấy thông tin cần thiết và với Payment để lưu trữ thông tin thanh toán.
  - Payment: Lưu trữ các thông tin liên quan đến thanh toán, bao gồm số tiền, phương thức thanh toán và trạng thái thanh toán. Nó cung cấp phương thức để xác nhận thanh toán.
  - Order: Chứa thông tin về đơn hàng mà khách hàng đang thanh toán. Nó cung cấp phương thức để lấy thông tin chi tiết về đơn hàng.

 ## 4. Phân tích ca sử dụng Maintain Timecard
### a. Mô Tả Ca Sử Dụng "Payment"
` - Tên ca sử dụng: Maintain Timecard
  - Diễn giả chính: Nhân viên (Employee)
  - Mô tả: Nhân viên có thể xem, thêm, sửa đổi và xóa thông tin thời gian làm việc của họ thông qua hệ thống. Hệ thống lưu trữ và quản lý thông tin thời gian làm việc cho các nhân viên.
### b. Các lớp phân tích cho ca sử dụng Selected Payment
  - Boundary Class: TimecardUI
  - Control Class: TimecardController
  - Entity Class: Timecard, Employee

### c. Biểu Sequence của ca sử dụng Select Payment

![Diagram](https://www.planttext.com/api/plantuml/png/f9DFIWCn5CRtESLRseKNS2658YguZ52Nqqpe1FEdP3A5MHONBZo222qYGg4xLvE5Yvma9_0APWoTPZDsq5qItlVxllSU-RAVuz9asbI2e_AUIT2gf2WZHccu40kkQahHJ5KoptGDc0bACftVNYEYfD6ATq-JUETK8oeDCuVY_Rt3eVq9JiyJ99p1b0emXRSl3EOiay3TMi2IUVj8JaOeAKs41-C0k7FR2eXltgl0SHzo3YRqb20JJ29CS05ouvkt-hY-DmJMldc5fRUhluRu6SPLwFiXwfwEW-9GkiaEbVVl0XTk-yzjN7gxOptU8BnzPaFMWNspKKCflLccRaD05hxPjO3Gsh0bu6WxSp72MXP0sfVV9Zy99elePPBSGJAcCcz_sZS0003__mC0)

### d. Nhiệm vụ của từng lớp phân tích
Boundary Class: TimecardUI
  - Mô tả: Lớp này quản lý giao diện người dùng cho việc quản lý thời gian làm việc.
  - Nhiệm vụ: Hiển thị thông tin thời gian làm việc cho nhân viên và cho phép họ thêm, sửa đổi hoặc xóa thông tin.
Control Class: TimecardController
  - Mô tả: Lớp này xử lý logic quản lý thời gian làm việc.
  - Nhiệm vụ: Điều phối các bước thực hiện thao tác với thông tin thời gian làm việc và tương tác giữa các lớp khác.
Entity Class: Timecard
  - Mô tả: Lớp này đại diện cho thông tin thời gian làm việc của nhân viên.
  - Nhiệm vụ: Lưu trữ thông tin thời gian vào và ra của nhân viên, cùng với ngày tháng và trạng thái.
Entity Class: Employee
  - Mô tả: Lớp này đại diện cho thông tin nhân viên.
  - Nhiệm vụ: Lưu trữ thông tin chi tiết của nhân viên, như ID, tên, và các thông tin liên quan khác.

### e. Một số thuộc tính và phương thức của các lớp phân tích
TimecardUI:
  - Hiển thị thông tin thời gian làm việc cho nhân viên.
  - Cung cấp giao diện để thêm, sửa đổi hoặc xóa thông tin thời gian làm việc.
TimecardController:
  - Nhận yêu cầu từ TimecardUI và điều phối các thao tác cần thiết.
  - Tương tác với lớp Timecard để lấy, thêm, sửa đổi hoặc xóa thông tin thời gian làm việc.
Timecard:
  - Chứa các thuộc tính như employeeId, date, timeIn, timeOut, status.
  - Cung cấp các phương thức để thêm, sửa đổi và lấy thông tin thời gian làm việc.
Employee:
  - Chứa các thuộc tính như employeeId, name, position.
  - Cung cấp thông tin liên quan đến nhân viên để hỗ trợ việc quản lý thời gian làm việc.

### f. Mối quan hệ giữa các lớp
  - TimecardUI - TimecardController: Gọi phương thức trực tiếp (Direct Association) hoặc Quan hệ Sử dụng (Usage Association). TimecardUI tương tác trực tiếp với TimecardController để truyền các yêu cầu từ nhân viên. Khi nhân viên muốn xem, thêm, sửa hoặc xóa thông tin thời gian làm việc, TimecardUI sẽ gửi yêu cầu đến TimecardController
  - TimecardController - Timecard: Kết hợp (Association). TimecardController tương tác với Timecard để quản lý dữ liệu thời gian làm việc thông qua các phương thức của Timecard.
  - TimecardController - Employee: Phụ thuộc (Dependency). TimecardController phụ thuộc vào Employee để lấy thông tin nhân viên cần thiết cho việc xác thực và quản lý thời gian làm việc.
  - Timecard - Employee: Kết hợp (Association). Timecard liên kết với Employee qua thuộc tính employeeId, gắn mỗi mục thời gian làm việc với một nhân viên cụ thể.

### g. Biểu đồ lớp

![Class Diagram](https://www.planttext.com/api/plantuml/png/j98nJiGm44Nxd69AA7A156Wbe4X50mUmub7MmXb7zWIqGXncaRP1GgAW8WL5fBr7Ji0Li9KrEAjb9GfSsFBJpFm_zdps7ml7mdBNwCpTAW9h76QL5ix1jMgm4bRUbF2GGLXt2kyZTIUd4nHIHXPHrqh1k4ybQfpHnsnFwTmGMwCrsgXO8_-du4ucnwRLPeLOoW8KyGH3oGB2FjtP9vLKG3X_o5N7AVAloPqhmB5LLF_HSD9jwlPov-weMn8DpcJprZZ5oj3SZDU8zIwGXT9kaaf-Ey_F3ds9hpFsBo37VkEB7GX8ytmqRr-tQwg1XtNrM_XtQmNeyNsp0buERo77Zo8jXoVoCpSyKxP0ac56lm000F__0m00)

Giải Thích Biểu Đồ Lớp

  - PaymentUI: Chịu trách nhiệm giao tiếp với người dùng để thu thập thông tin thanh toán và hiển thị kết quả.
  - PaymentController: Chịu trách nhiệm xử lý logic thanh toán. Nó tương tác với Order để lấy thông tin cần thiết và với Payment để lưu trữ thông tin thanh toán.
  - Payment: Lưu trữ các thông tin liên quan đến thanh toán, bao gồm số tiền, phương thức thanh toán và trạng thái thanh toán. Nó cung cấp phương thức để xác nhận thanh toán.
  - Order: Chứa thông tin về đơn hàng mà khách hàng đang thanh toán. Nó cung cấp phương thức để lấy thông tin chi tiết về đơn hàng.

 ## 5. Hợp nhất kết quả phân tích
  - Lớp Employee: Sử dụng chung cho cả hai ca sử dụng "Maintain Timecard" và "Payment", do đó chỉ cần một lớp Employee duy nhất để lưu trữ thông tin của nhân viên.
  - Lớp TimecardUI và PaymentUI: Các lớp này quản lý giao diện cho các chức năng khác nhau của hai ca sử dụng. TimecardUI xử lý giao diện cho việc ghi nhận thời gian làm việc, trong khi PaymentUI xử lý giao diện cho việc chọn phương thức thanh toán.
  - Lớp TimecardController và PaymentController: Các lớp điều khiển riêng biệt để xử lý logic cho hai ca sử dụng khác nhau. TimecardController quản lý việc cập nhật và gửi thời gian làm việc, trong khi PaymentController quản lý việc chọn phương thức thanh toán.
  - Lớp Timecard: Lưu trữ thông tin về thời gian làm việc của nhân viên. Thông tin này bao gồm số giờ làm việc, ngày bắt đầu và kết thúc.
  - Lớp Payment: Lưu trữ thông tin về thanh toán cho nhân viên, bao gồm phương thức thanh toán đã chọn (nhận trực tiếp, qua bưu điện, hoặc chuyển khoản trực tiếp).

Class diagram

![](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTnTcQUGb5-SIeN5rT1Od9sOdggWf9lOcPU2H0hX6JcfYOd5gKeALHpAG11SavYSJ5SDDHJmSOcARyqBoMngDBE3ge61C2CMYuiUfppyqgAydDoKek0UfCX72Ijk3K2bQVcbMIM4BB8DRSW9xyoDHMl-beapmOaLkO2LQ9w4If8YW-XMWXu48_E4amdWrsA5DowkdROGj9AeVZXxhKAAGztByrBvqAu7QGSqrcegh4OXsmBK7N9iGt75kQbAvGSNfZCXMaSaYKbwAfn60wF8ok5d8UxbbOgb6GStWBI0qnoUHc75-Kfb6KUNfM7mp9YTNCvfEQbWD8u0000__y30000)

### Tài Liệu Mô Tả Ca Sử Dụng: Quản Lý Thời Gian và Phương Thức Thanh Toán
#### 1. Mô Tả Ngắn Gọn
      Ca sử dụng này cho phép Nhân viên cập nhật và gửi thông tin thời gian làm việc, đồng thời chọn phương thức thanh toán cho khoản lương của mình. Nhân viên sẽ ghi lại giờ làm việc hàng tuần cho các dự án cụ thể và có thể chọn cách nhận lương, bao gồm nhận trực tiếp, nhận qua bưu điện, hoặc chuyển khoản trực tiếp vào tài khoản ngân hàng.
#### 2. Luồng Sự Kiện
     Luồng Cơ Bản
      Ca sử dụng này bắt đầu khi Nhân viên muốn nhập số giờ làm việc và chọn phương thức thanh toán.
  ##### a. Cập Nhật Thời Gian Làm Việc
      - Hệ thống lấy và hiển thị thời gian làm việc hiện tại của Nhân viên. Nếu không có thời gian làm việc cho kỳ thanh toán hiện tại, hệ thống sẽ tạo một cái mới. Ngày bắt đầu và kết thúc của thời gian làm việc được hệ thống thiết lập và không thể thay đổi.
      - Hệ thống lấy và hiển thị danh sách các mã dự án có sẵn từ Cơ sở Dữ liệu Quản lý Dự án.
      - Nhân viên chọn mã dự án thích hợp và nhập số giờ làm việc cho bất kỳ ngày nào trong khoảng thời gian của thời gian làm việc.
      - Khi Nhân viên đã nhập thông tin, hệ thống lưu thời gian làm việc.
  ##### b. Gửi Thời Gian Làm Việc
      - Nhân viên có thể yêu cầu hệ thống gửi thời gian làm việc. Hệ thống sẽ gán ngày hiện tại cho thời gian làm việc như ngày gửi và thay đổi trạng thái thành “đã gửi.” Không được phép thay đổi sau khi gửi.
      - Hệ thống xác thực thời gian làm việc, đảm bảo tổng số giờ không vượt quá giới hạn quy định.
      - Hệ thống lưu và làm cho thời gian làm việc trở thành chỉ đọc.
  ##### c. Chọn Phương Thức Thanh Toán
      - Hệ thống yêu cầu Nhân viên chỉ định phương thức thanh toán mong muốn (nhận trực tiếp, qua bưu điện, hoặc chuyển khoản trực tiếp).
       + Nếu Nhân viên chọn phương thức “nhận trực tiếp”, không yêu cầu thêm thông tin.
       + Nếu Nhân viên chọn phương thức “qua bưu điện”, hệ thống yêu cầu Nhân viên cung cấp địa chỉ nhận séc.
       + Nếu Nhân viên chọn phương thức “chuyển khoản trực tiếp”, hệ thống yêu cầu Nhân viên cung cấp tên ngân hàng và số tài khoản.
      - Hệ thống cập nhật thông tin Nhân viên với phương thức thanh toán đã chọn.
#### 3. Luồng Thay Thế
      - Số Giờ Không Hợp Lệ: Nếu số giờ không hợp lệ được nhập (>24 hoặc vượt quá giới hạn), hệ thống hiển thị thông báo lỗi và yêu cầu nhập lại.
      - Thời Gian Làm Việc Đã Được Gửi: Nếu thời gian làm việc đã được gửi, hệ thống hiển thị bản sao chỉ đọc và thông báo rằng không thể thay đổi.
      - Cơ Sở Dữ Liệu Quản Lý Dự Án Không Có Sẵn: Nếu không có danh sách mã dự án, hệ thống thông báo lỗi và cho phép Nhân viên chọn tiếp tục hoặc hủy bỏ.
      - Nhân Viên Không Được Tìm Thấy: Nếu thông tin Nhân viên không thể tìm thấy, hệ thống hiển thị thông báo lỗi và ca sử dụng kết thúc.
#### 4. Điều Kiện Tiền Đề: 
      Nhân viên phải đăng nhập vào hệ thống trước khi ca sử dụng này bắt đầu.
#### 5. Điều Kiện Hậu Đề: 
      Nếu ca sử dụng thành công, thông tin thời gian làm việc và phương thức thanh toán của Nhân viên sẽ được lưu vào hệ thống. Ngược lại, trạng thái của hệ thống không thay đổi.
