# LAB3 Xác định các phần tử thiết kế của hệ thống “Payroll System”

## 1. Subsystem context diagrams
### a. Hệ thống con BankSystem

![Sybsystem](https://www.planttext.com/api/plantuml/png/n9DBQiCm48RtFiNWbLCIqxK98QHfePjIo0baUTAAw64q8rfJUh8kUgHUeVA3aDYXa5Mra1_p_wFlj-IVh-yriV0SZ4uIEYWBtX4c2SIXBAFV2udmk17si6k8qS17L-i7Us5fZ_uXs8eo8QKBbf-2AT4Ni6ElxCiSX6dV5h1reTGuxqr2id9sAnXZ8Swp0ZREQHIsQ__P4qWjYE1ayUMIGadzVUtTUxDQ_GFGisYyq_hEMMwlw2ENF3wCa2AcHABeCMWvcqtRtPjQkmPnaCHcSLOypXRgAdBHfGu3q8KT6bOVswO95elLsJONa8PeIplvQQ4LZebRSK_Nww-KZ-kjvpnIT2WwXgcWRDBJ77-lTVm6aDtc-SrimfZda-pTsOzdWk1DyMkQ96kqLVkJ_0800F__0m00)

### b. Hệ thống con PrintService

![Sybsystem](https://www.planttext.com/api/plantuml/png/j551QWCn3Bph5IAd1f8FB649RIzx2-G5ZbTjJRJsrf9RJCZBUkYJyeLu5nAwJNgiBcPcD1fXdRw-rw8cQkeOGFREOmn20CuhnHTZ2PjDB61BySCLT00Sgn_8ZSd2hd-WhkUGYPgsmgqMvNM1OjZ4NE5pI3kc1RRK9gikUBbmymeVGs0o7eu0beq8Jh9MAqaxoQBKrVM_9viS0_DJy3gy54kylO8V-P7U4ybrW_ban40L8tbrcaTJKMz7BvVrht-jS9Q4P0OJzcxVU1fZLV3JwTiTnsKFQFwIO4s-7Kv-1W00__y30000)

### c. Hệ thống con ProjectManagementDatabase

![ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/x9J1JiCm343l_OfefmwnYdCrLHDmsG49QL_WjTuMI9CfTe4AyMKS-2H-WRJDK5kwLaWSoIbL_1pxMStd-yUA62mNkGe2UfHQM4CO1C8jgHdj3b8Kwtjh7Z3bEz2mnnmrtmB35WZ5QntQB69ZqOTM0U7Hxv51Aeh5XgtK-taiherH2Bh5MdHd-3I4hxCMsMnQO77CWCUnI_6BGZ9KE96lnxqrkb85HEAygUMIYYsLn9XNzRoKIV9lRzZUZT5iZL9edRNq-wCdBAyTUoISd-sgATi735td8znTRbwI-uCvTQ1tPYo9d_EccN0xmG5qff3QLZfvVdQzM2HZFrqiPWKXpMfw9AvAq-lHeOqtJ_y5V3fk4rqR3fJaFMHYMtRnRkpmlTwX2A-Yw68-LNiKJVch7pT8cSIpvCCi25Qei-eL_0800F__0m00)

## 2. Analysis class to design element map:
- Dưới đây là ánh xạ các lớp phân tích từ sơ đồ trên sang các phần tử thiết kế của hệ thống:
  
|  Analysis Class | Design Element |  
|-----------------|----------------|
| LoginForm | LoginForm|
| MaintainTimecardForm | MainEmployeeForm |
| TimecardController | TimecardController |
| PayrollController | PayrollController |
| PayCheck | PayCheck |
| BankService | BankService |
| SystemClockInterface | SystemCLockInterface |
| PayrollController | PayrollControllerImpl |
| Employee | EmployeeEntity |
| Timecard | TimecardEntity |
| Payroll | PayrollProcessor |
| BankTransaction | BankTransactionProcessor |
| PaymentUI | PaymentUIComponent |
| PrintService | PrintServiceProcessor |

## 3. Design element to owning package map:
- Hãy ánh xạ các phần tử thiết kế vào các gói:
  
|  Design Element | "Owning" Package |  
|-----------------|----------------|
| LoginForm | Middleware::Security::GUIFramwork |
| MainEmployeeForm | Applications::Employee Activities |
| TimecardController | Applications::Employee Activities |
| SystemClockInterface | Applications::Payroll |
| PayrollController | Applications: Payroll |
| PayCheck | Business Services::Payroll Artifacts |
| BankService | Business::Banking |
| EmployeeEntity | Data Access::Employee Management |
| TimecardEntity | Data Access::Employee Management |
| PayrollProcessor | Business Services::Payroll Processing |
| BankTransactionProcessor | Business Services::Banking |
| PaymentUIComponent | Middleware::User Interface Components |
| PaymentUIComponent | Middleware::Print Services |

## 4. Architectural layers and their dependencies
![Diagram](https://planttext.com/api/plantuml/png/X98nJiD044NxESLNcbIvW1LP2U8084umh2Vs2djjxUmcYX0r1GrNe4p50LnGa8lu15o1E8Z28Gxjp9i_UgFvQZyM6jY7M9L4K-nVk_R55N1viTynpEURGSbRyKeDcmVE1PFv_5X9KznuKN61WwtT18_qHEUePTEKrlm3NKMrJbHn9tvjZOoJrnmOIsCEy6NedlKtPehRo0v5rpuZjrtxFbGRLPhDqb6J1AQkgkZwWYWsDXGqnfxa_9LDa4af-J4fr7IHFGaRt2D1L1a83TfdHd-kbC1By5RMX_rPFx7oTKMq49Vrd_4D003__mC0)
