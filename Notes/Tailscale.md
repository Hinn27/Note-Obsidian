  1. 🛡️ Shields up (Bật khiên bảo vệ):
  Giống như sếp tàng hình. Sếp vẫn có thể chui vào máy của bạn bè, nhưng KHÔNG AI trong mạng Tailscale được phép chui vào máy của sếp. Bật cái này khi sếp xài mạng
  công cộng mà sợ bị người khác nhòm ngó.

  2. 💻 Enable SSH (Bật điều khiển từ xa):
  Bình thường muốn điều khiển máy bằng dòng lệnh (Terminal) sếp phải cấu hình SSH lằng nhằng. Bật nút này lên, Tailscale sẽ tự tạo luôn một kênh SSH cực an toàn. Sếp
  cầm máy khác gõ đúng 1 dòng ssh tên-máy-này là chui thẳng vào Terminal được luôn!

  3. 🔀 Accept routes (Nhận đường truyền ngoài):
  Giả sử sếp cài Tailscale trên máy tính ở công ty, và share luôn cả cái mạng công ty lên đó. Khi máy tính ở nhà bật nút này, sếp có thể kết nối thẳng vào cái máy in
  hoặc ổ cứng nội bộ ở công ty luôn, y như sếp đang ngồi tại văn phòng!

  4. 🌐 Advertise exit (Trở thành Cục phát VPN):
  Đây là tính năng đáng tiền nhất! Bật nút này sẽ biến cái máy tính hiện tại của sếp thành một trạm VPN (Exit Node).
  Ví dụ: Sếp ra quán cafe, wifi không an toàn. Sếp mở điện thoại lên, bật mạng Tailscale và chọn kết nối vào cái máy tính ở nhà này. Lúc đó, toàn bộ dữ liệu duyệt web
  trên điện thoại sẽ được mã hóa, bay thẳng về máy tính ở nhà rồi mới đi ra Internet. Mạng cực kỳ an toàn!

  5. 🏠 Allow LAN (Cho phép mạng cục bộ):
  Khi sếp đang mượn mạng của máy khác (dùng Exit Node), máy sếp sẽ bị "mù" với các thiết bị trong nhà. Bật nút này lên để sếp vừa dùng được VPN, vừa có thể điều khiển
  TV hay bấm in tài liệu ở cái máy in ngay sát bên cạnh sếp.