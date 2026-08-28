Bước 1: Bật MS SQL Server bằng Docker
  Tạo và chạy SQL Server ngầm:
```
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=MatKhauKho!123' -p
  1433:1433 --name mssql -d mcr.microsoft.com/mssql/server:2022-latest
```

  (Cái mật khẩu MatKhauKho!123 sếp có thể tự đổi tùy ý, nhưng bắt buộc phải có chữ HOA, chữ thường, số và ký tự đặc biệt theo chuẩn của Microsoft nhé).

Bước 2: Dùng DataGrip (Tự code hàng ngày)
  • Bấm dấu + chọn kết nối SQL Server.
  • IP: localhost, Port: 1433, User: sa, Password: MatKhauKho!123.

Bước 3: Tạo máy ảo Windows siêu tốc (Dùng để chiếu cho thầy xem)
  • Mở terminal gõ: quickget windows 10 (Nó sẽ tự động tải file ISO của Win 10 bản chuẩn nhất về máy sếp, sếp đợi một lúc cho nó tải xong).
  • Tải xong: quickemu --vm windows-10.conf
  • Cửa sổ Windows 10 sẽ bật lên, mượt mà và có sẵn mạng. Sếp cài SSMS vào cái Win 10 đó.
  • Khi dùng SSMS trong máy ảo, sếp nhập IP của Database là: 10.0.2.2 (Đây là dải IP để máy ảo nhìn ra cái Docker chạy ngầm ngoài máy thật của sếp).