
  ### 1. 🔄 Khởi động lại bot (Restart)
  Thường dùng nhất sau khi cập nhật code hoặc đổi cấu hình (file .env):

    sv restart zalo-tg

  ### 2. 📊 Kiểm tra trạng thái (Status)

  Xem bot có đang chạy không và chạy được bao lâu rồi:

    sv status zalo-tg

  (Kết quả run: zalo-tg: (pid 1234) 600s; nghĩa là đang chạy ngon lành được 10 phút. Nếu hiện down:... nghĩa là đang tắt).

  ### 3. ⏹️ Dừng bot (Stop / Down)

  Tắt bot tạm thời, hệ thống sẽ không tự động bật lại nó:

    sv down zalo-tg

  ### 4. ▶️ Bật lại bot (Start / Up)

  Bật bot lên sau khi đã bị dừng (bị down):

    sv up zalo-tg
  ──────
  ### 🛠️ Xem Log (Nhật ký hoạt động)

  Trong Debian, bot đang ghi log ra file. Để theo dõi bot đang làm gì theo thời gian thực:

    # Xem log trực tiếp (khi có người nhắn tin Zalo, log sẽ nảy số ở đây)
    # Nhấn Ctrl + C để thoát xem
    tail -f /var/log/zalo-tg.log

    # Xem 50 dòng log gần nhất để tra lỗi
    tail -n 50 /var/log/zalo-tg.log