# Phím tắt Neovim & Kitty cơ bản
Dưới đây là danh sách tổng hợp các phím tắt di chuyển và quản lý cửa sổ cơ bản nhất khi gõ code bằng Neovim trên Terminal Kitty.
## 🐱 Phím tắt Kitty (Quản lý Pane/Cửa sổ Terminal)
- **`Ctrl + Shift + Enter`** : Chia ngang (Thường dùng để mở Server chạy ngầm bên cạnh Editor)
- **`Ctrl + Shift + O`** : Chia dọc (Hợp lý để mở Log chạy dài xuống dưới)
- **`Ctrl + Shift + H / J / K / L`** : Di chuyển con trỏ qua lại giữa các Pane (giống phong cách Vim)
- **`Ctrl + Shift + Z`** : Phóng to toàn màn hình một Pane (Đổi sang layout Stack để tập trung gõ code), ấn lại để thu nhỏ.
- **`Ctrl + Shift + W`** (hoặc gõ `exit`) : Đóng Pane hiện tại
## 💻 Phím tắt Neovim cơ bản (Di chuyển & Split)
### 🚶‍♂️ Di chuyển cơ bản
- **`h`** / **`j`** / **`k`** / **`l`** : Sang trái / Xuống dưới / Lên trên / Sang phải
- **`w`** / **`b`** : Tiến tới 1 từ / Lùi lại 1 từ
- **`0`** (Số không) : Nhảy về đầu dòng
- **`$`** : Nhảy về cuối dòng
- **`gg`** : Nhảy lên dòng đầu tiên của file
- **`G`** : Nhảy xuống dòng cuối cùng của file
### 🪟 Quản lý Cửa sổ trong Neovim (Split)
- **`:vs`** (hoặc `:vsplit`) : Chia dọc không gian code ra làm 2 (Trái/Phải)
- **`:sp`** (hoặc `:split`) : Chia ngang không gian code ra làm 2 (Trên/Dưới)
- **`Ctrl + H / J / K / L`** : Nhảy con trỏ qua lại giữa các ô code đã split bên trong Neovim
- **`:q`** : Đóng ô code hiện tại
## 📁 Phím tắt Yazi (File Manager)
### 🚶‍♂️ Di chuyển & Điều hướng
- **`k`** / **`j`** (hoặc `Lên`/`Xuống`) : Di chuyển con trỏ lên / xuống
- **`h`** / **`l`** (hoặc `Trái`/`Phải`) : Lùi ra thư mục cha / Vào thư mục (hoặc mở file)
- **`g g`** : Nhảy vọt lên trên cùng danh sách
- **`G`** : Nhảy tọt xuống dưới cùng danh sách
- **`~`** (dấu ngã) hoặc **`F1`** : Mở bảng trợ giúp (Liệt kê *toàn bộ* phím tắt)
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