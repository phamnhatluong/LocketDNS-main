# LocketDNS

Tài liệu này hướng dẫn cài và gỡ cấu hình DNS dành cho iPhone/iPad trong file
[`Phamnhatluong.mobileconfig`](./Phamnhatluong.mobileconfig).

> **Lưu ý về phạm vi:** hồ sơ này chỉ cấu hình DNS cho một số tên miền được liệt kê
> bên dưới. Nó không cài ứng dụng, không mở khóa tính năng trả phí và không thay
> đổi toàn bộ DNS trên thiết bị.

## Hồ sơ DNS làm gì?

Hồ sơ sử dụng DNS-over-HTTPS của NextDNS tại địa chỉ:

```text
https://dns.nextdns.io/d1447b
```

Hồ sơ được thiết lập để tự kết nối trên Wi-Fi và mạng di động. Các miền được khai
báo trong hồ sơ gồm:

- RevenueCat: `revenuecat.com`, `rc-backup.com`
- Firebase Remote Config và logging
- App Center và App Measurement
- Mixpanel

Do hồ sơ dùng danh sách miền bổ sung (`SupplementalMatchDomains`), đây không phải
cấu hình VPN hay DNS toàn thiết bị. Tác động cụ thể còn phụ thuộc vào thiết lập
NextDNS của cấu hình `d1447b`. Nhà vận hành cấu hình NextDNS có thể xử lý truy vấn
DNS gửi đến dịch vụ đó.

## Cài trên iPhone hoặc iPad

1. Đưa file `Phamnhatluong.mobileconfig` lên GitHub cùng repository.
2. Trên iPhone/iPad, mở file từ trang GitHub hoặc mở liên kết tải file trực tiếp.
   Nếu tải trên máy tính trước, chuyển file sang thiết bị bằng iCloud Drive hoặc
   một phương thức bạn tin cậy.
3. Khi iOS hỏi, chọn **Cho phép** để tải hồ sơ.
4. Mở **Cài đặt**. Chọn **Đã tải về hồ sơ**; nếu không thấy mục này, vào
   **Cài đặt chung → VPN & Quản lý thiết bị**.
5. Chọn **DNS Phạm Nhật Lương**, nhấn **Cài đặt** và xác nhận bằng mật mã thiết bị
   nếu được yêu cầu.
6. Quay lại **VPN & Quản lý thiết bị** để kiểm tra hồ sơ đã được cài.

Chỉ cài hồ sơ cấu hình từ nguồn bạn tin cậy. Hồ sơ DNS sẽ định tuyến truy vấn của
các miền được liệt kê qua nhà cung cấp DNS đã cấu hình.

## Gỡ hồ sơ

Mở **Cài đặt → Cài đặt chung → VPN & Quản lý thiết bị**, chọn hồ sơ DNS rồi nhấn
**Xóa hồ sơ**. Tên menu có thể hơi khác tùy phiên bản iOS/iPadOS.

## Khắc phục sự cố

- **Không thấy “Đã tải về hồ sơ”:** kiểm tra file đã tải xong; thử mở lại file
  trên thiết bị.
- **Không cài được:** kiểm tra xem hồ sơ đã được cài trước đó chưa, rồi khởi động
  lại thiết bị và thử lại.
- **Một ứng dụng gặp lỗi mạng:** tạm gỡ hồ sơ để kiểm tra. Nếu lỗi biến mất, có
  thể một miền cần thiết đang bị ảnh hưởng bởi thiết lập DNS.
- **Muốn thay đổi bộ lọc hoặc chính sách DNS:** cần quyền quản lý cấu hình NextDNS
  tương ứng; đổi tên hiển thị trong file không thay đổi chính sách phía NextDNS.

## Các tệp khác trong repository

Repository còn có `CamTu.sgmodule` và các script JavaScript có khả năng sửa đổi
phản hồi mạng của ứng dụng bên thứ ba, bao gồm dữ liệu trạng thái thuê bao. Chúng
không cần thiết để cài hồ sơ DNS ở trên và không được hướng dẫn cài đặt trong tài
liệu này. Chỉ kiểm tra hoặc sử dụng mã mạng với ứng dụng, tài khoản và hệ thống mà
bạn sở hữu hoặc được phép kiểm thử; không dùng để né tránh thanh toán hoặc quyền
truy cập.

