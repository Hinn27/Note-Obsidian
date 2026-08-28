Thay vì gõ snippet tạo Service, bạn chỉ cần mở Terminal (của WebStorm hoặc
  Neovim) và gõ:

    nest g s auth

  (g = generate, s = service, auth = tên)
  Ngay lập tức, Nest CLI sẽ tự động:

  1. Tạo 1 file auth.service.ts với đầy đủ code @Injectable() chuẩn.
  2. Tạo 1 file test auth.service.spec.ts.
  3. Tự động import cái Service đó vào file Module gần nhất (Điều mà Snippet
  không bao giờ làm được).

  Nên kết luận lại: Cứ tập xài lệnh nest g ... của Nest CLI là bạn code nhanh
  hơn dùng Snippet gấp 10 lần!