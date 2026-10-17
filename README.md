# [Thực hành] Bố cục trang web Responsive với CSS Flexbox

Bài thực hành luyện tập sử dụng **CSS Flexbox** để xây dựng một bố cục trang web hoàn chỉnh, có khả năng thích ứng linh hoạt (responsive) trên cả máy tính (**Desktop**) và điện thoại (**Mobile**).

---

## 📋 1. Mô tả bài tập

Bố cục trang web gồm **5 thành phần chính**:
1. **Header:** Hiển thị tiêu đề trang và logo.
2. **Navigation:** Chứa thanh điều hướng liên kết.
3. **Main Content:** Khu vực hiển thị nội dung chính bài viết (`flex: 3;` chiếm 75% chiều rộng).
4. **Sidebar:** Chứa nội dung phụ như danh sách tin mới và banner quảng cáo (`flex: 1;` chiếm 25% chiều rộng).
5. **Footer:** Hiển thị thông tin bản quyền và liên hệ cuối trang.

---

## 📐 2. Phân tích nguyên lý CSS Flexbox & Responsive

### Bố cục trên Desktop (> 768px):
```css
.page-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

.content-wrapper {
    display: flex;
    flex: 1;
    gap: 20px;
}

.main-content {
    flex: 3; /* Chiếm 75% chiều rộng */
}

.sidebar {
    flex: 1; /* Chiếm 25% chiều rộng */
}
```
- Khung bao ngoài `.page-container` xếp theo cột dọc (`flex-direction: column`).
- Vùng giữa `.content-wrapper` xếp theo hàng ngang (`row`), chia tỷ lệ linh hoạt giữa Content (3 phần) và Sidebar (1 phần).

### Bố cục trên Mobile (≤ 768px):
```css
@media (max-width: 768px) {
    .content-wrapper {
        flex-direction: column;
    }

    .nav-menu {
        flex-direction: column;
    }
}
```
- Khi kích thước màn hình nhỏ hơn hoặc bằng 768px, `.content-wrapper` và `.nav-menu` tự động chuyển sang `flex-direction: column`.
- Tất cả các khối được xếp dọc tuần tự: **Header &rarr; Navigation &rarr; Main Content &rarr; Sidebar &rarr; Footer**, giúp nội dung hiển thị rõ ràng, không bị co ép trên màn hình hẹp.

---

## 📁 3. Cấu trúc thư mục dự án

```text
css-flexbox-responsive/
├── index.html                  # Mã nguồn HTML (5 phần: Header, Nav, Main Content, Sidebar, Footer)
├── style.css                   # Định kiểu CSS Flexbox Desktop & Media Query Responsive Mobile
└── README.md                   # Tài liệu thuyết minh chi tiết
```

---

## 🚀 4. Hướng dẫn kiểm tra trên trình duyệt
1. Mở file `index.html` bằng trình duyệt web bất kỳ (Chrome, Edge, Firefox).
2. Nhấn phím `F12` (hoặc `Ctrl + Shift + I`), chọn biểu tượng **Device Toggle Toolbar** (`Ctrl + Shift + M`).
3. Kéo thay đổi độ rộng màn hình qua lại ngưỡng `768px` để quan sát sự chuyển đổi linh hoạt giữa giao diện Desktop (2 cột song song) và Mobile (các khối xếp dọc 1 cột).
