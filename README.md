# Bloomy, demo giao diện

Bản demo tĩnh một tệp, bảy màn, bốn tab, tiếng Việt. Không có máy chủ, không lưu dữ liệu: mọi trạng thái (đổi hoạt động, lưu kỷ niệm, đánh dấu cột mốc) chỉ nằm trong bộ nhớ trang và mất khi tải lại.

## Mở thử

Mở `index.html` qua một máy chủ tĩnh bất kỳ, ví dụ `python3 -m http.server` trong thư mục này rồi vào `http://127.0.0.1:8000/`. Các màn đi bằng đường dẫn băm: `#/home`, `#/activity`, `#/swap`, `#/milestones`, `#/milestone/2`, `#/growth`, `#/profile`.

## Thay ảnh minh hoạ: chỉ đổi tệp

Mọi ảnh nằm trong thư mục `img/` với tên cố định. Thay một ảnh thì lưu tệp mới ĐÚNG TÊN đó vào `img/`, không sửa mã. Ảnh được cắt theo khung (cover), nên tỉ lệ nào cũng dùng được; nên giữ chủ thể ở giữa.

| Tệp | Dùng ở | Khung hiển thị | Cỡ gợi ý |
|---|---|---|---|
| `bloomy-activity-play.jpg` | Hôm nay (card đầu), Hoạt động "Xếp, chờ, đổ", Lớn lên (dòng kỷ niệm, và card kỷ niệm mới sau khi lưu) | 141 x 93, 342 x 228, 64 x 48 | vuông 1024 |
| `bloomy-activity-motor.jpg` | Chọn hoạt động khác, Hoạt động "Đẩy xe, diễu hành" (kèm card Hôm nay và Lớn lên khi chọn) | 88 x 88, 342 x 228, 141 x 93 | vuông 1024 |
| `bloomy-activity-language.jpg` | Chọn hoạt động khác, Hoạt động "Gọi tên, chờ, reo" (kèm card Hôm nay và Lớn lên khi chọn) | 88 x 88, 342 x 228, 141 x 93 | vuông 1024 |
| `bloomy-activity-social.jpg` | Chọn hoạt động khác, Hoạt động "Tiệc trà cho hai gấu" (kèm card Hôm nay và Lớn lên khi chọn) | 88 x 88, 342 x 228, 141 x 93 | vuông 1024 |
| `bloomy-spot-sprout.jpg` | Hôm nay (chân trang), Lớn lên (khi tuần này chưa có kỷ niệm) | 96 x 96, 112 x 112 | vuông 1024, nền giấy kem |
| `bloomy-hero.webp` | Hồ sơ (card Mầm) | 141 x 93 | 1920 x 1280 |

Ảnh nhỏ được phóng 7 phần trăm trong khung để cắt mép giấy có sẵn trong ảnh. Riêng `bloomy-spot-sprout.jpg` đặt kiểu hoà vào nền (multiply, viền mờ dần), nên ảnh thay vào cũng nên có nền giấy sáng và chủ thể ở giữa.

Muốn đổi cách cắt của một ảnh hoạt động thì sửa trường `pos` (ví dụ `"50% 40%"`) của hoạt động đó trong mảng `ACT` ở đầu khối `<script>`. Mỗi ảnh nên dưới 800 KB.

## Chữ

Font Reddit Sans (giấy phép SIL OFL, kèm trong `fonts/OFL.txt`), tự host ba bộ ký tự `latin`, `latin-ext`, `vietnamese` trong `fonts/`, nên trang không gọi dịch vụ font bên ngoài. Thang chữ có mười vai (tiêu đề màn, lời chào, tít card, tít card nhỏ, thân, mô tả, nhãn, nhãn phụ, nút, tab), khai ở đầu thẻ `<style>` dưới dạng lớp `.t-tên-vai`; đổi một vai ở một chỗ là đổi cả app.

## Bố cục

Cột ứng dụng rộng tối đa 430 px, căn giữa; ở màn rộng hơn phần còn lại là nền trơn, không vẽ khung máy. Lề 24, tab bar cao 96 gồm vùng an toàn 34, nút chính cao 48, vùng chạm tối thiểu 44.
