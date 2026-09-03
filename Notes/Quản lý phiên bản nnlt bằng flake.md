# 1. PYTHON
```
nix flake init -t github:the-nix-way/dev-templates#python
echo "use flake" > .envrc
direnv allow
```
- Bắt buộc: Phải có layout python để pip install không bị văng lỗi Read-only.
## 2. JS/TS/VUE/ANGULAR (Hệ sinh thái Node.js)
```
nix flake init -t github:the-nix-way/dev-templates#node
echo "use flake" > .envrc
direnv allow
```
  (Chờ tải xong Node.js)
- Tạo dự án mới: Tùy framework mà gõ lệnh tương ứng (Ví dụ: pnpm create vite, nest new, hoặc npm init).
- Lưu ý: NPM/PNPM đã tự gom thư viện vào thư mục node_modules nội bộ của dự án nên KHÔNG CẦN lệnh layout (như bên Python).
### Phần 2: Khởi tạo dự án (chọn 1 trong 2 mục đích)

  Trường hợp A: Nếu bạn muốn tạo dự án Web Frontend (React + TypeScript)
  Hiện nay cách tốt nhất và nhanh nhất để khởi tạo React là dùng công cụ Vite. Bạn chạy lệnh sau:

    # Tạo mã nguồn React-TS ngay tại thư mục hiện tại (Lưu ý dấu chấm '.')
    pnpm create vite@latest . --template react-ts

    # Cài đặt các thư viện cần thiết cho React
    pnpm install

    # Chạy server phát triển (Mở trình duyệt để xem)
    pnpm run dev

  Trường hợp B: Nếu bạn muốn tạo dự án Backend/CLI thông thường (Node.js + TypeScript - Giống buoi3)

    # Khởi tạo file package.json
    pnpm init

    # Cài đặt TypeScript và công cụ hỗ trợ chạy code nhanh (tsx)
    pnpm add -D typescript @types/node tsx

    # Tạo file cấu hình tsconfig.json
    pnpm exec tsc --init

    # Tạo thư mục và file code đầu tiên
    mkdir src
    echo "console.log('Hello world');" > src/index.ts

    # Chạy thử code
    pnpm exec tsx src/index.ts
## 3. JAVA (Spring Boot, Java Core)
```
nix flake init -t github:the-nix-way/dev-templates#java
echo "use flake" > .envrc
direnv allow
```
- Ghi chú: Maven/Gradle đã tự lo phần quản lý thư viện, file cấu hình này chỉ dùng để "bơm" bản JDK phù hợp vào dự án.
## 4. HTML / CSS thuần
Không cần dùng Nix Flake hay setup môi trường gì cả! Vì trình duyệt web mặc định đã tự hiểu HTML/CSS rồi.
- Cứ tạo thư mục, tạo file index.html và viết code bình thường.
- Nếu muốn chạy một server ảo gọn nhẹ (Live Server), bạn có thể dùng template #node ở trên rồi chạy lệnh: npx serve hoặc npx live-server.