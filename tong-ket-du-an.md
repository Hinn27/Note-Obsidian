# Tổng kết dự án React UDA

## 1. Công nghệ sử dụng

- React 19, React Router DOM, Vite
- Material UI (MUI) 7
- framer-motion
- Context API (Auth, Cart, Theme)
- Custom hooks: useForm, useDebounce, useClock, useLocalStorage, useProducts

## 2. Mapping kiến thức React & MUI

| Tính năng/UI                | MUI sử dụng                 | Kiến thức React áp dụng               |
| --------------------------- | --------------------------- | ------------------------------------- |
| Navbar, Footer, Layout      | AppBar, Toolbar, IconButton | React Router, Context, Outlet         |
| Trang chủ, Menu, Cart       | Card, Grid, Typography      | useContext, useReducer, custom hooks  |
| Form đăng nhập/đăng ký      | TextField, Button, Alert    | useForm, useState, validation         |
| Chi tiết sản phẩm           | Dialog, Rating, Avatar      | useParams, useEffect, dynamic routing |
| Thanh toán, QR, chọn phương | Paper, Tabs, Snackbar       | useState, conditional rendering       |
| Đổi theme                   | Switch, ThemeProvider       | Context, useContext                   |
| Animation                   | framer-motion               | Component composition                 |
