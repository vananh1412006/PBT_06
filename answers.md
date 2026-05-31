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

# PHẦN C — PHÂN TÍCH (20 điểm)

## Câu C1 (10đ) — Tùy biến Bootstrap

### 1. Quy trình đổi màu `$primary` từ xanh mặc định sang `#E63946`

Để thay đổi biến cốt lõi của Bootstrap một cách hệ thống, chúng ta không sửa trực tiếp trong file mã nguồn của Bootstrap (trong thư mục `node_modules`) mà sẽ thực hiện qua quy trình biên dịch SASS (SCSS) như sau:

#### * Công cụ cần thiết:
- **Node.js & npm:** Để quản lý và cài đặt các gói phụ thuộc.
- **Bootstrap Source Code:** Được cài đặt qua npm (`npm install bootstrap`).
- **Trình biên dịch SASS:** Có thể dùng gói `sass` của npm hoặc extension **Live Sass Compiler** trên VS Code để biên dịch file `.scss` thành file `.css`.

#### * Quy trình thực hiện chi tiết:
1. **Khởi tạo dự án:** Chạy lệnh `npm init -y` và `npm install bootstrap` để tải mã nguồn thư viện về máy.
2. **Tạo file cấu hình tùy biến:** Tạo một file SASS riêng của dự án, ví dụ đặt tên là `assets/scss/custom.scss`.
3. **Modify file (Ghi đè biến):** Trong file `custom.scss`, ta sẽ khai báo lại giá trị của biến `$primary` **trước** khi import Bootstrap. Cụ thể code sẽ như sau:
   ```scss
   // 1. Khởi tạo hoặc import các hàm màu sắc của Bootstrap (nếu cần sử dụng các hàm như tint-color, shade-color)
   @import "../node_modules/bootstrap/scss/functions";
   @import "../node_modules/bootstrap/scss/variables";

   // 2. Ghi đè màu primary theo ý muốn
   $primary: #E63946;

   // 3. Import toàn bộ phần còn lại của Bootstrap để áp dụng thay đổi
   @import "../node_modules/bootstrap/scss/bootstrap";

### 2. Tại sao KHÔNG nên override trực tiếp bằng CSS truyền thống?
Việc viết đè kiểu .btn-primary { background: red; } bằng CSS thuần tuy chạy được ngay nhưng mang lại rất nhiều hệ lụy xấu. Việc dùng SASS Variables vượt trội hơn hoàn toàn vì các lý do sau:

Tính đồng bộ và nhất quán hệ thống: Trong Bootstrap, biến $primary không chỉ quy định màu nền của nút bấm .btn-primary, mà nó còn được dùng tự động cho hàng loạt thành phần khác như: màu chữ .text-primary, màu nền .bg-primary, màu viền .border-primary, trạng thái active/focus của form input, các thanh tiến trình (progress bar), badge, v.v. Nếu chỉ override CSS của .btn-primary, các thành phần khác vẫn sẽ mang màu xanh mặc định, gây lệch tone giao diện. Thay đổi biến SASS giúp tất cả chuyển sang màu mới chỉ với 1 dòng code.

Giữ nguyên các hiệu ứng động (States): Một nút bấm chuẩn cần có các trạng thái như :hover (rê chuột), :focus (nhấp chọn), :active (đang bấm). Bootstrap dùng các hàm toán học của SASS để tự động tính toán tạo ra màu hover đậm hơn một chút từ màu gốc $primary. Nếu dùng CSS thuần override, ta sẽ phải tự viết tay lại toàn bộ các class phức tạp như .btn-primary:hover, .btn-primary:focus, gây tốn thời gian và dễ sót.

Tránh xung đột độ ưu tiên (Specificity): Khai báo bằng SASS Variables giúp mã CSS sinh ra sạch sẽ, tự nhiên, không cần lạm dụng các mẹo tăng độ ưu tiên hoặc dùng từ khóa tệ hại !important trong CSS làm code khó bảo trì sau này.

## Câu C2 (10đ) — So sánh (CSS thuần vs Bootstrap)

### 1. Bảng so sánh thực tế khi xây dựng Giao diện (Navbar Responsive + Product Card)

| Tiêu chí so sánh | Sử dụng CSS thuần (Vanilla CSS) | Sử dụng Bootstrap Framework |
| :--- | :--- | :--- |
| **Số dòng CSS cần viết** | **Rất nhiều (Khoảng 80 - 150 dòng CSS)**<br>- Phải tự viết Reset CSS, Flexbox/Grid layout.<br>- Viết Media Queries chi tiết cho từng breakpoint.<br>- Viết hiệu ứng `@keyframes` hoặc `transition` cho Mobile Menu toggle. | **Gần như bằng 0 (Hoặc chỉ vài dòng bổ sung)**<br>- Không cần viết file `.css` riêng.<br>- Sử dụng hoàn toàn các Utility Classes có sẵn (`navbar`, `d-flex`, `card`, `col-*`, `g-*`). |
| **Thời gian phát triển** | **Lâu (Mất từ 1 - 2 tiếng)**<br>- Tốn thời gian căn chỉnh pixel, test hiển thị chéo trên nhiều thiết bị, xử lý ẩn/hiện menu bằng JavaScript thuần. | **Cực nhanh (Mất 10 - 15 phút)**<br>- Chỉ cần ráp các component chuẩn từ tài liệu của Bootstrap.<br>- Tính năng Responsive đã được tối ưu sẵn vô cùng mượt mà. |
| **Khả năng tùy biến** | **Vô hạn và Tuyệt đối**<br>- Kiểm soát 100% từng thuộc tính, không phụ thuộc cấu trúc.<br>- Dễ dàng tạo ra các layout độc lạ, hiệu ứng Animation phức tạp theo ý muốn cá nhân. | **Bị giới hạn (Nếu chỉ dùng class cơ bản)**<br>- Giao diện dễ bị đại trà, mang "màu sắc Bootstrap".<br>- Muốn tùy biến sâu phải can thiệp cấu trúc SASS phức tạp hoặc viết đè CSS khá cồng kềnh. |

---

### 2. Khi nào NÊN và KHÔNG NÊN sử dụng Bootstrap?

#### * Khi nào NÊN dùng Bootstrap?
- **Dự án cần phát triển thần tốc (Mẫu thử - Prototype / MVP):** Khi thời gian hoàn thành dự án cực kỳ gấp rút, cần giao diện trực quan ngay để demo.
- **Trang quản trị (Dashboard / Admin Panel):** Những hệ thống chú trọng vào công năng, dữ liệu, không đòi hỏi giao diện quá nghệ thuật hay phá cách.
- **Làm việc nhóm (Teamwork):** Khung thiết kế chuẩn của Bootstrap giúp tất cả thành viên trong đội ngũ lập trình có chung một tiếng nói, dễ đọc code và bảo trì giao diện của nhau mà không sợ mỗi người viết CSS một kiểu.
- **Lập trình viên Backend làm Fullstack:** Khi bạn mạnh về logic hệ thống nhưng không muốn tốn quá nhiều thời gian để tự mò mẫm cắt CSS giao diện từ đầu.

#### * Khi nào KHÔNG NÊN dùng Bootstrap?
- **Website đòi hỏi thiết kế độc quyền, đậm tính thương hiệu:** Các trang Landing Page sáng tạo, Portfolio nghệ thuật, trang chiến dịch Marketing cần độ tùy biến giao diện cao, hiệu ứng chuyển động lạ mắt.
- **Yêu cầu tối ưu hiệu năng tối đa (Performance):** Bootstrap đi kèm với dung lượng file CSS và JS khá lớn (chứa hàng nghìn class mà dự án có thể không bao giờ dùng tới). Nếu cần một trang web siêu nhẹ, tải nhanh tuyệt đối trên mobile, CSS thuần hoặc TailwindCSS (chỉ giữ lại class được dùng) là lựa chọn tốt hơn.
- **Mục đích học tập cốt lõi:** Khi mới tiếp cận lập trình Web, lạm dụng Bootstrap quá sớm sẽ khiến người học bị rỗng kiến thức nền tảng về CSS Layout (Flexbox, Grid, Position), dẫn đến việc bị phụ thuộc hoàn toàn vào framework.