# 🐳 Bí Kíp Nhập Môn Docker Cho Lập Trình Viên

Để hiểu và làm chủ được Docker, sếp chỉ cần nắm được 2 khái niệm cốt lõi và thuộc 5 câu lệnh cơ bản. Đây là công cụ mà 100% các công ty IT hiện nay đều yêu cầu!

---

## 1. Hai Khái Niệm Quan Trọng Nhất

Để dễ hình dung, hãy tưởng tượng Docker giống như việc sếp đi mua một chiếc đĩa game:

*   **Image (Cái đĩa game):** Nó là một file nén đóng gói sẵn mọi thứ (Hệ điều hành, mã nguồn, thư viện,...). Image mang tính chất **chỉ đọc (read-only)**. Ví dụ: Image của MS SQL Server, Image của Ubuntu, Image của NodeJS...
*   **Container (Máy chơi game):** Khi sếp bỏ cái đĩa (Image) vào máy ảo để nó chạy lên, nó biến thành một **Container**. Một Image (1 cái đĩa) có thể tạo ra được hàng trăm cái Container (hàng trăm cái máy đang chơi game đó) chạy độc lập với nhau.

---

## 2. Các Lệnh Vòng Đời Cơ Bản

Sếp mở Terminal lên và luyện tập các lệnh này nhé:

### Khởi tạo và chạy (Lệnh dùng nhiều nhất)
```bash
# Lệnh tổng quát
docker run [tùy_chọn] [tên_image]

# Ví dụ: Chạy một con web server Nginx
docker run -d -p 8080:80 --name web_cua_tui nginx
```
> [!TIP]
> **Giải ngố các Tùy chọn (Flags):**
> *   `-d` (Detached): Báo Docker hãy đem cái thùng này chạy ngầm đi, trả lại con trỏ terminal cho tui gõ lệnh khác. (Rất quan trọng!)
> *   `--name`: Đặt một cái tên gợi nhớ cho Container, nếu không Docker sẽ tự đặt một cái tên ngẫu nhiên rất buồn cười (ví dụ: *crazy_einstein*).
> *   `-p [Port_ngoài]:[Port_trong]`: Đục một lỗ thủng trên thùng container để giao tiếp với bên ngoài. Ví dụ `-p 8080:80` nghĩa là: Lấy cổng `8080` của máy tính sếp, cắm vào cổng `80` của cái container.

### Quản lý các Container đang có
```bash
# Xem các Container ĐANG CHẠY
docker ps

# Xem TẤT CẢ Container (kể cả những cái đã bị tắt)
docker ps -a
```

### Dừng và Bật lại
Khi không dùng nữa, sếp nên tắt đi để đỡ tốn RAM. Cứ coi như tắt máy tính vậy:
```bash
# Tắt 1 container
docker stop web_cua_tui

# Mở lại 1 container đã tắt
docker start web_cua_tui
```

### Xóa bỏ (Dọn rác)
```bash
# 1. Để xóa một Container (Phải tắt nó đi trước khi xóa)
docker rm web_cua_tui

# Lệnh tắt ép buộc và xóa luôn (cực mạnh)
docker rm -f web_cua_tui

# 2. Xóa đĩa cài đặt (Image) cho đỡ tốn ổ cứng
docker rmi nginx
```

---

## 3. Khái Niệm Nâng Cao Bắt Buộc Phải Biết: VOLUME

> [!WARNING]
> **Vấn đề nguy hiểm:** Bản chất của Container là "tạm thời". Nếu sếp chạy MS SQL Server bằng Docker, sếp tạo bảng, thêm dữ liệu chán chê. Xong sếp lỡ tay gõ lệnh `docker rm` xóa cái Container đó đi... **BÙM! Mất sạch toàn bộ database vĩnh viễn!**

Để giải quyết, chúng ta dùng **Volume** (như kiểu cắm cái USB ngoài vào trong thùng container).

```bash
docker run -d -p 1433:1433 -v /home/hinne/data_cua_tui:/var/opt/mssql --name mssql_co_volume mcr.microsoft.com/mssql/server:2022-latest
```
Nhờ cái đoạn `-v /home/hinne/data_cua_tui:/var/opt/mssql`, Docker sẽ map thư mục dữ liệu ở trong container ra một thư mục thật trên máy tính NixOS của sếp (`/home/hinne/data_cua_tui`). 
Bây giờ dù sếp có xóa tung cái Container đi, thì dữ liệu Database vẫn còn nguyên vẹn nằm trên máy sếp. Lần sau chạy container mới chỉ cần map lại đúng cái thư mục đó là Database cũ hiện hồn về!

---

## 4. Trải Nghiệm Thử Ngay Bây Giờ!

Sếp hãy copy nguyên dòng này dán vào Terminal:
```bash
docker run -d -p 8080:80 --name thu_nghiem nginx
```
Sau đó, sếp mở trình duyệt (Thorium/Zen) và gõ vào thanh địa chỉ:
👉 `http://localhost:8080`

Sếp sẽ thấy dòng chữ **"Welcome to nginx!"**. Chúc mừng sếp, sếp vừa tự tay triển khai một máy chủ web thực thụ bằng Docker rồi đó! 

Khi chán rồi, dọn dẹp bằng lệnh: `docker rm -f thu_nghiem`. Sạch sẽ, không để lại một hạt bụi nào!
