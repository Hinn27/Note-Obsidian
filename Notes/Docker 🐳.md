## 1. Hai Khái Niệm Quan Trọng Nhất

Để dễ hình dung, hãy tưởng tượng Docker giống như việc đi mua một chiếc đĩa game:
*   **Image (Cái đĩa game):** Là một file nén đóng gói sẵn mọi thứ (Hệ điều hành, mã nguồn, thư viện,...). Image mang tính chất **chỉ đọc (read-only)**. Ví dụ: Image của MS SQL Server, Image của Ubuntu, Image của NodeJS...
*   **Container (Máy chơi game):** Bỏ cái đĩa (Image) vào máy ảo để nó chạy lên, nó biến thành một **Container**. Một Image (1 cái đĩa) có thể tạo ra được hàng trăm cái Container (hàng trăm cái máy đang chơi game đó) chạy độc lập với nhau.
## 2. Các Lệnh Vòng Đời Cơ Bản
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
Khi không dùng nữa, tắt đi để đỡ tốn RAM.
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
## 3. Khái Niệm Nâng Cao Bắt Buộc Phải Biết: VOLUME

> [!WARNING]
> **Vấn đề nguy hiểm:** Bản chất của Container là "tạm thời". Nếu chạy MS SQL Server bằng Docker, sếp tạo bảng, thêm dữ liệu chán chê. Xong sếp lỡ tay gõ lệnh `docker rm` xóa cái Container đó đi... **BÙM! Mất sạch toàn bộ database vĩnh viễn!**

Để giải quyết, chúng ta dùng **Volume** (như kiểu cắm cái USB ngoài vào trong thùng container).
```bash
docker run -d -p 1433:1433 -v /home/hinne/data_cua_tui:/var/opt/mssql --name mssql_co_volume mcr.microsoft.com/mssql/server:2022-latest
```
Nhờ cái đoạn `-v /home/hinne/data_cua_tui:/var/opt/mssql`, Docker sẽ map thư mục dữ liệu ở trong container ra thư mục thật trên máy (`/home/hinne/data_cua_tui`). 
Bây giờ dù có xóa tung cái Container đi, thì dữ liệu Database vẫn còn nguyên vẹn nằm trên máy. Lần sau chạy container mới chỉ cần map lại đúng cái thư mục đó là Database cũ hiện hồn về!
## 4. Trải Nghiệm Thử Ngay Bây Giờ!
```bash
docker run -d -p 8080:80 --name thu_nghiem nginx
```
Mở trình duyệt (Thorium/Zen) và gõ vào thanh địa chỉ: `http://localhost:8080`

Thấy dòng chữ **"Welcome to nginx!"** là thành công triển khai một máy chủ web thực thụ bằng Docker.

Khi chán rồi, dọn dẹp bằng lệnh: `docker rm -f thu_nghiem`.
## 5. Test với MS SQL Server và kết nối với DataGrip
### Bước 1: Bật MS SQL Server bằng Docker
- Tạo và chạy SQL Server ngầm:
```
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=MatKhauKho!123' -p
  1433:1433 --name mssql -d mcr.microsoft.com/mssql/server:2022-latest
```
- Mật khẩu bắt buộc phải có chữ HOA, chữ thường, số và ký tự đặc biệt.
### Bước 2: Dùng DataGrip (Tự code hàng ngày)
- Bấm dấu + chọn kết nối SQL Server.
- IP: localhost, Port: 1433, User: sa, Password: MatKhauKho!123.
### Bước 3: Tạo máy ảo Windows siêu tốc (Dùng để chiếu cho thầy xem)
- Mở terminal gõ: quickget windows 10 (Nó sẽ tự động tải file ISO của Win 10 bản chuẩn nhất về máy sếp, sếp đợi một lúc cho nó tải xong).
- Tải xong: `quickemu --vm windows-10.conf`
- Cửa sổ Windows 10 sẽ bật lên, mượt mà và có sẵn mạng. Sếp cài SSMS vào cái Win 10 đó.
- Khi dùng SSMS trong máy ảo, sếp nhập IP của Database là: 10.0.2.2 (Đây là dải IP để máy ảo nhìn ra cái Docker chạy ngầm ngoài máy thật của sếp).