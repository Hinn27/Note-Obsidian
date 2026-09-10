---
tags:
  - os/linux
  - tool/wm
  - type/cheatsheet
aliases:
  - Niri Shortcuts
  - Yazi Shortcuts
---
# Phím tắt Neovim & Kitty cơ bản
Dưới đây là danh sách tổng hợp các phím tắt di chuyển và quản lý cửa sổ cơ bản nhất khi gõ code bằng Neovim trên Terminal Kitty.
## 🐱 Phím tắt Kitty (Quản lý Pane/Cửa sổ Terminal)
- **`Ctrl + Shift + Enter`** : Chia ngang (Thường dùng để mở Server chạy ngầm bên cạnh Editor)
- **`Ctrl + Shift + O`** : Chia dọc (Hợp lý để mở Log chạy dài xuống dưới)
- **`Ctrl + Shift + H / J / K / L`** : Di chuyển con trỏ qua lại giữa các Pane (giống phong cách Vim)
- **`Ctrl + Shift + Z`** : Phóng to toàn màn hình một Pane (Đổi sang layout Stack để tập trung gõ code), ấn lại để thu nhỏ.
- **`Ctrl + Shift + W`** (hoặc gõ `exit`) : Đóng Pane hiện tại
## 💻 Phím tắt Neovim cơ bản (Di chuyển & Split)
### 1. Phím tắt Cơ bản & Cửa sổ
| **Phím tắt**      | **Chức năng**                                                         |
| :---------------- | :-------------------------------------------------------------------- |
| jk (trong lúc gõ) | Thoát chế độ gõ (về Normal mode) siêu tốc, không cần với tay bấm ESC. |
| <leader>nh        | Xóa các vệt màu vàng highlight sau khi tìm kiếm xong.                 |
| <leader>sv        | Chia đôi màn hình theo chiều Dọc (Split Vertical).                    |
| <leader>sh        | Chia đôi màn hình theo chiều Ngang (Split Horizontal).                |
| <leader>se        | Cân bằng lại kích thước của tất cả các cửa sổ đang mở.                |
| <leader>sx        | Đóng cửa sổ hiện tại (Close).                                         |
### 2. Giao diện & Tìm kiếm

| Phím tắt   | Chức năng                                                             |
| ---------- | --------------------------------------------------------------------- |
| <leader>e  | Bật/Tắt cây thư mục bên trái (NvimTree).                              |
| <leader>un | Xóa ngay lập tức mọi hộp thoại thông báo đang trôi nổi trên màn hình. |
| <leader>ff | Mở bảng tìm kiếm file theo tên (cực nhanh).                           |
| <leader>fg | Tìm một đoạn chữ/code nằm sâu bên trong toàn bộ Project.              |
| <leader>fb | Chuyển đổi qua lại giữa các file đang được mở trong RAM (Buffers).    |
### 3. Terminal (Mới nâng cấp) 🚀

| Phím tắt            | Chức năng                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------------ |
| Alt + F12           | Bật/Tắt Terminal trượt từ dưới lên (Phong cách chuẩn Jetbrains). Lệnh bên trong vẫn chạy ngầm khi tắt. |
| Ctrl + \            | Phím phụ để Bật/Tắt Terminal (Dành cho những ai quen tay xài VSCode).                                  |
| jk (trong Terminal) | Khi bạn đang gõ lệnh, bấm jk để thoát ra ngoài chế độ gõ, cho phép bạn cuộn chuột lên xuống để xem Log |
### 4. Lập trình & Code (LSP & Git)

| Phím tắt              | Chức năng                                                                                                   |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| s (bấm ở Normal mode) | Nhảy siêu tốc: Bấm s + gõ 2 chữ cái đầu của từ, màn hình sẽ gán phím tắt để bạn nhảy chuột thẳng đến từ đó. |
| <leader>a             | Bật/Tắt mục lục xem danh sách Hàm/Biến (Outline) ở bên phải.                                                |
| <leader>fm            | Auto-format (Căn chỉnh code cho đẹp) dùng được cho cả file hoặc 1 đoạn bôi đen.                             |
| ]h                    | Nhảy đến đoạn code có thay đổi so với Git tiếp theo.                                                        |
| [h                    | Nhảy lùi về đoạn code có thay đổi trước đó.                                                                 |
| <leader>hp            | Xem trước (Preview) đoạn code gốc đã bị bạn xóa hoặc sửa trước khi Commit.                                  |
### 📝 Thao tác với File / Thư mục
- **`Space`** (Phím cách) : Chọn hoặc Bỏ chọn file (để thao tác nhiều file cùng lúc)
- **`y`** : Copy (Yank)
- **`x`** : Cắt (Cut)
- **`p`** : Dán (Paste)
- **`d`** : Xóa bỏ file vào thùng rác (Trash)
- **`D`** (Shift + d) : Xóa vĩnh viễn không thể khôi phục!
- **`a`** : Tạo file hoặc thư mục mới (gõ thêm `/` ở cuối tên để tạo thư mục, ví dụ `tailieu/`)
- **`r`** : Đổi tên file (Rename)
- **`/`** hoặc **`f`** : Lọc/tìm kiếm nhanh file trong thư mục hiện tại
- **`s`** : Tìm kiếm nội dung file (tích hợp `fd`/`ripgrep`)
### ⚡ Tác vụ Nâng cao (Custom & Task Manager)
- **`w`** : **Mở Task Manager** (Để xem tiến độ % của các việc đang chạy ngầm như Copy/Paste, Nén/Giải nén, hoặc để Hủy ngang bằng phím `x`)
- **`e`** : **Giải nén** file (zip, rar, 7z...) tuôn hết ra thư mục hiện hành
- **`E`** (Shift + e) : **Giải nén nâng cao** (Sẽ hiện hộp thoại hỏi bạn muốn xả nén vào đâu)
- **`c`** : **Nén file** (Cách dùng: Bấm `Space` chọn nhiều file -> Bấm `c` -> Đặt tên file nén `ten_file.zip` -> Enter)