# 1. PYTHON
    nix flake init -t github:the-nix-way/dev-templates#python
    echo "use flake" > .envrc
    echo "layout python" >> .envrc
    direnv allow
- Bắt buộc: Phải có layout python để pip install không bị văng lỗi Read-only.
## 2. JS/TS/VUE/ANGULAR (Hệ sinh thái Node.js)
    nix flake init -t github:the-nix-way/dev-templates#node
    echo "use flake" > .envrc
    direnv allow
  (Chờ tải xong Node.js)
- Tạo dự án mới: Tùy framework mà gõ lệnh tương ứng (Ví dụ: pnpm create vite, nest new, hoặc npm init).
- Lưu ý: NPM/PNPM đã tự gom thư viện vào thư mục node_modules nội bộ của dự án nên KHÔNG CẦN lệnh layout (như bên Python).
## 3. JAVA (Spring Boot, Java Core)
    nix flake init -t github:the-nix-way/dev-templates#java
    echo "use flake" > .envrc
    direnv allow
  • Ghi chú: Maven/Gradle đã tự lo phần quản lý thư viện, file cấu hình này chỉ dùng để "bơm" bản JDK phù hợp vào dự án.
## 4. HTML / CSS thuần
  Không cần dùng Nix Flake hay setup môi trường gì cả! Vì trình duyệt web mặc định đã tự hiểu HTML/CSS rồi.

  • Cứ tạo thư mục, tạo file index.html và viết code bình thường.
  • Nếu muốn chạy một server ảo gọn nhẹ (Live Server), bạn có thể dùng template #node ở trên rồi chạy lệnh: npx serve hoặc npx live-server.