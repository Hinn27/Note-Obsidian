# Quy trình Setup chuẩn xác nhất sẽ là:
### 1. Chỉ cài duy nhất fnm vào hệ thống của bạn trước. Không cài Node.js vội.
2. Dùng fnm để tải và cài phiên bản Node LTS hiện tại:
• Ví dụ lệnh: fnm install --lts
3. Set phiên bản LTS vừa tải làm mặc định (global) cho toàn bộ máy tính:
• Ví dụ lệnh: fnm default <tên-bản-lts>
4. Lúc này, Node.js mặc định trên máy bạn đang được quản lý bởi fnm. Bây giờ bạn mới cài pnpm. Có 2 cách:
• Kích hoạt corepack (khuyên dùng): gõ lệnh corepack enable pnpm
• Hoặc cài qua npm: npm install -g pnpm

  Sau này, nếu làm dự án mới, nó sẽ tự động dùng bản LTS mặc định. Nếu gặp dự án cũ cần bản Node khác (vd: v16), gõ fnm install 16 rồi fnm use 16.
──────
### 2. Làm sao để biết dự án cần dùng phiên bản Node.js nào?
Khi đi làm hoặc tải code trên mạng về, bạn sẽ kiểm tra theo thứ tự ưu tiên sau:
- Ưu tiên 1: Tìm các file cấu hình phiên bản
  Một dự án chuẩn chỉnh thường sẽ khai báo rõ phiên bản Node.js nó cần. Bạn hãy tìm ở thư mục gốc của dự án:
  • File .nvmrc hoặc .node-version: Trong file này thường chỉ chứa 1 con số (ví dụ: 18.17.0 hoặc 16).
  • Trong file package.json: Hãy tìm mục "engines". Ví dụ:
    "engines": {
      "node": ">=18.0.0"
    }
Nghĩa là bạn phải dùng Node.js từ phiên bản 18 trở lên.

- Ưu tiên 2: Xem các file cấu hình triển khai (CI/CD / Docker)
  Nếu không có các file trên, bạn có thể "soi" vào các file dùng để deploy:
  • File Dockerfile: Tìm dòng FROM node:18-alpine (nghĩa là nó xài Node 18).
  • Thư mục .github/workflows/: Các file YAML test tự động thường có ghi phiên bản Node.js được dùng để test.

  Ưu tiên 3: Dự đoán dựa trên thời gian (Giải pháp cuối cùng)
  Nếu dự án không có bất kỳ thông tin nào ở trên, lúc này bạn mới áp dụng cách đoán dựa trên ngày dự án được viết:

  • Bạn xem ngày commit đầu tiên hoặc commit lớn cuối cùng.
  • Tra cứu xem ở thời điểm năm đó, phiên bản Node.js LTS nào đang phổ biến.
      • Ví dụ: Code viết từ 2020-2021 thường chạy tốt ở Node 12 hoặc 14.
      • Code viết từ 2022 thường là Node 16.
      • Code viết từ 2023 thường là Node 18.
      • Code mới 2024 thì Node 20 hoặc 22.
