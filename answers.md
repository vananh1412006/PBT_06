# PHẦN A — ĐỌC HIỂU (20 điểm)

## Câu A1 (10đ) — Grid System

### 1. Bảng phân tích kích thước và layout

| Kích thước | < 768px (Mobile) | 768px - 991px (Tablet) | ≥ 992px (Desktop) |
| :--- | :--- | :--- | :--- |
| **Class áp dụng** | `col-12` | `col-md-6` | `col-lg-3` |
| **Số cột chiếm** | 12 / 12 cột (100% width) | 6 / 12 cột (50% width) | 3 / 12 cột (25% width) |
| **Box layout** | **4 dòng đơn**<br>Mỗi Box nằm riêng biệt trên 1 dòng. | **2 dòng, mỗi dòng 2 Box**<br>- Dòng 1: Box 1, Box 2<br>- Dòng 2: Box 3, Box 4 | **1 dòng duy nhất**<br>Cả 4 Box nằm thẳng hàng ngang với nhau. |

---

### 2. Trả lời câu hỏi thêm

#### * Ý nghĩa của class `col-md-6`:
- **`col-`**: Khai báo phần tử là một cột nằm trong hệ thống lưới (Grid System).
- **`md` (Medium)**: Breakpoint áp dụng cho màn hình có độ rộng từ `768px` trở lên.
- **`6`**: Chiếm 6 cột trên tổng số 12 cột mặc định của một hàng (tương đương với `50%` chiều rộng của thành phần cha `.row`).
- **Ý nghĩa chung**: Khi hiển thị trên màn hình cỡ trung bình (như máy tính bảng) có độ rộng từ 768px đến dưới 992px, phần tử này sẽ chiếm đúng một nửa chiều rộng màn hình.

#### * Tại sao không cần viết `col-sm-12`?
- Vì Bootstrap được thiết kế theo nguyên lý **Mobile-First** (ưu tiên màn hình nhỏ trước). Các class không có tiền tố kích thước cụ thể như `col-12` sẽ mặc định áp dụng cho kích thước nhỏ nhất (từ 0px trở lên).
- Thuộc tính này sẽ tự động **kế thừa từ dưới lên trên** (từ cỡ màn hình nhỏ lên cỡ màn hình lớn hơn) cho đến khi nó gặp một breakpoint lớn hơn ghi đè lên.
- Do màn hình nhỏ nhất đã nhận `col-12`, nên ở kích thước màn hình `sm` (từ 576px đến 767px), nếu không khai báo gì thêm thì nó vẫn tự động kế thừa giá trị `12`. Việc viết `col-sm-12` lúc này là dư thừa code.

## Câu A2 (10đ) — Utilities & Components

### 1. Giải thích class `d-none d-md-block`

Sự kết hợp của hai class này dựa trên nguyên lý **Mobile-First** để ẩn/hiển thị phần tử theo kích thước màn hình:

- **`d-none`**: Ẩn phần tử này mặc định trên tất cả các kích thước màn hình (bắt đầu từ màn hình nhỏ nhất `xs`: từ 0px trở lên). Phần tử sẽ bị gán thuộc tính CSS `display: none;`.
- **`d-md-block`**: Khi màn hình đạt kích thước từ breakpoint `md` trở lên (độ rộng `≥ 768px`), class này sẽ ghi đè class `d-none` trước đó và gán thuộc tính `display: block;`.

**Kết luận:**
- **Ẩn khi:** Màn hình có độ rộng nhỏ hơn `768px` (Màn hình điện thoại di động - Mobile).
- **Hiển thị khi:** Màn hình có độ rộng từ `768px` trở lên (Màn hình máy tính bảng - Tablet, máy tính xách tay - Laptop, và máy tính để bàn - Desktop).

---

### 2. Liệt kê và giải thích 5 Spacing Utilities (Margin/Padding)

Hệ thống Spacing của Bootstrap sử dụng công thức quy đổi kích thước theo đơn vị `rem` (mặc định với cấu hình từ 0 đến 5, trong đó `1rem = 16px`):

1. **`mt-3` (Margin Top 3):**
   - Thêm khoảng cách lề **phía trên** (Top) của phần tử.
   - Kích thước: Cấp độ 3 (Mặc định tương đương với `1rem` hoặc `16px`).
2. **`px-4` (Padding X 4):**
   - Thêm khoảng cách đệm đồng thời ở cả hai bên **trái và phải** (Trục X - Left & Right) bên trong phần tử.
   - Kích thước: Cấp độ 4 (Mặc định tương đương với `1.5rem` hoặc `24px`).
3. **`mb-auto` (Margin Bottom Auto):**
   - Tự động tính toán khoảng cách lề **phía dưới** (Bottom) để đẩy các phần tử khác ra xa hết mức có thể.
   - Thường được sử dụng trong Layout Flexbox để đẩy các phần tử đi cùng hàng xuống dưới cùng hoặc căn chỉnh vị trí linh hoạt.
4. **`pt-5` (Padding Top 5):**
   - Thêm khoảng cách đệm **phía trên** (Top) bên trong phần tử.
   - Kích thước: Cấp độ 5 (Đây là cấp độ lớn nhất mặc định, tương đương với `3rem` hoặc `48px`).
5. **`mx-2` (Margin X 2):**
   - Thêm khoảng cách lề đồng thời ở cả hai bên **trái và phải** (Trục X) bên ngoài phần tử.
   - Kích thước: Cấp độ 2 (Mặc định tương đương với `0.5rem` hoặc `8px`).

---

### 3. Sự khác nhau giữa `.container`, `.container-fluid`, và `.container-md`

Các class này đều dùng để bao bọc và căn giữa nội dung (chứa hệ thống lưới Grid), nhưng khác nhau về cách co giãn chiều rộng tối đa (`max-width`) theo kích thước màn hình:

| Đặc tính | `.container` | `.container-fluid` | `.container-md` |
| :--- | :--- | :--- | :--- |
| **Cơ chế hoạt động** | Co giãn theo từng breakpoint (Responsive cố định). | Luôn chiếm toàn bộ chiều rộng