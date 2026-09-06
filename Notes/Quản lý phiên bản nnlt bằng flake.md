> [!NOTE]
> Thay vì dự án nào cũng setup môi trường, hãy gom các dự án cùng ngôn ngữ vào một thư mục cha (Workspace).
> 1. Tạo thư mục cha (VD: mkdir Java-Workspace && cd Java-Workspace)
> 2. Chạy 3 lệnh khởi tạo Nix ở đây.
> 3. Kể từ giờ, cứ vô tư dùng các lệnh sinh code (nest new, pnpm create...) để tạo ra hàng loạt dự án con bên trong. Công cụ direnv sẽ tự động mang môi trường từ thư mục cha áp dụng xuống thư mục con.
---
## 1. HỆ SINH THÁI NODE.JS (React, Vue, NestJS, TS thuần...)
Cơ chế của Node.js (nhờ file package.json và node_modules) quản lý thư viện độc lập cho từng thư mục. Do đó, áp dụng chiến thuật Workspace Cấp Cha là hoàn hảo 100%.
### Bước 1: Setup 1 lần ở thư mục cha
```
nix flake init -t github:the-nix-way/dev-templates#node
echo "use flake" > .envrc
direnv allow
```
### Bước 2: Tạo các dự án con (bên trong thư mục cha)
- Nếu làm **Frontend** (React/Vue bằng Vite):
Sinh thẳng code vào thư mục hiện tại (nhờ dấu .)
```
mkdir frontend && cd frontend
pnpm create vite@latest . --template react-ts
pnpm install
pnpm run dev
```
- Nếu làm **Backend** (NestJS):
Lệnh này tự sinh ra thư mục backend
```
nest new backend --package-manager pnpm
cd backend
pnpm start:dev
```
---
## 2. PYTHON (Data Science, AI, Backend Python)
Lưu ý cực kỳ quan trọng: Không giống Node.js, Python quản lý thư viện bằng môi trường ảo (Virtualenv).
- Nếu setup Nix ở thư mục cha: Toàn bộ dự án con sẽ dùng chung một rổ thư viện. (Tuyệt vời để học tập, làm bài tập vì cài 1 lần xài ở
  mọi thư mục).
- Nếu làm dự án công ty: Khuyên bạn KHÔNG setup ở thư mục cha, mà dự án nào phải tự setup Nix riêng cho dự án đó để không bị dính chùm thư viện.
### Quy trình chuẩn cho 1 dự án (hoặc 1 Workspace học tập):
1. Khởi tạo môi trường
```
nix flake init -t github:the-nix-way/dev-templates#python
```
2. RẤT QUAN TRỌNG: Thêm layout python để chống lỗi Read-only khi dùng lệnh pip
```
echo "use flake" > .envrc
echo "layout python3" >> .envrc
direnv allow
```

> [!NOTE]
> Từ giờ cứ dùng pip install <tên> bình thường, thư viện sẽ lưu vào thư mục ẩn .direnv của dự án.
---
## 3. JAVA (Spring Boot, Java Core)
Giống như Node.js, Maven và Gradle tự quản lý file thư viện nội bộ.
Bạn có thể áp dụng chiến thuật Workspace Cấp Cha thoải mái!
Quy trình:
Tải môi trường Java (JDK) vào thư mục cha
```
nix flake init -t github:the-nix-way/dev-templates#java
echo "use flake" > .envrc
direnv allow
```
> [!NOTE]
> Lệnh này chỉ "bơm" bộ biên dịch Java JDK vào máy. Sau đó bạn dùng Spring Initializr hoặc IDE như IntelliJ/Eclipse để sinh code dự án con bình thường.
---
## 4. HTML / CSS / JS (Giao diện tĩnh)
Không cần dùng Nix hay setup môi trường!
- Trình duyệt đã hiểu sẵn HTML/CSS.
- Mẹo: Nếu muốn chạy Live Server (tự động tải lại trang khi lưu
  file), hãy chạy môi trường #node, sau đó gõ: pnpm dlx live-server
- Ngay khi chạy lệnh, trình duyệt web của bạn sẽ tự động bật lên (hoặc bạn click vào link http://127.0.0.1:8080 trên Terminal).
- Từ giờ, bạn cứ mở code lên sửa. Cứ mỗi lần bấm Lưu, màn hình web sẽ lập tức thay đổi theo thời gian thực! (Khi nào code xong, quay lại Terminal bấm Ctrl + C để tắt server).