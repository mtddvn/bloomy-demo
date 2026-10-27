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

## Màu

Màu chủ đạo là tím `#4B14A5` (nút chữ trắng 10,8:1, tab chọn, link, dấu check), lime `#BEFA87` chỉ là nhấn phụ và luôn nằm TRONG một hình tím, như nhụy trong logo (nhụy hoa ở thanh trên, nhụy chấm "đang diễn ra", nền dấu check hoàn thành); không đặt chữ trắng lên lime, và lime không bao giờ là mảng nền tự đứng (trên nền kem chỉ 1,17:1). Chip lọc đang chọn là nền tím chữ trắng. Nền nhấn nhẹ tím rất nhạt `#E9E2F5` và `#F2EDF9`. Nền kem `#FBFAF7`, card `#F5EFE6`, chữ đen `#1D2733`, chữ thân `#434C59` giữ nguyên. Bốn màu miền (Vận động, Ngôn ngữ, Chơi, Xã hội) tách khỏi màu chủ đạo. Tất cả khai ở đầu thẻ `<style>` dưới dạng biến `--primary-deep`, `--accent`, `--tint`, `--tint2`, `--primary` (tím giữa, dùng cho đồ hoạ); đổi một biến là đổi cả app.

## Minh hoạ phẳng trên thẻ cột mốc

Thẻ "Đang diễn ra" ở Cột mốc dùng minh hoạ phẳng theo miền (Vận động, Ngôn ngữ, Chơi, Xã hội), đặt sát góc phải dưới và để thẻ cắt mép, theo kiểu thẻ khám phá. Bốn tệp nằm trong `img/illus/`: `illus-01-motor-alpha-640.png`, `illus-02-language-alpha-640.png`, `illus-03-play-alpha-640.png`, `illus-04-social-alpha-640.png` (nền trong suốt, vuông, hiển thị 112 x 112). Thay minh hoạ chỉ cần lưu đúng tên tệp.

## Chỗ cho minh hoạ mới

Mọi ô minh hoạ trong card là một khung `.im` có kích thước cố định (141 x 93 ở Hôm nay, kỷ niệm mới và Hồ sơ; 88 x 88 ở Chọn hoạt động khác và Thử hoạt động này; 64 x 48 ở dòng kỷ niệm). Bộ minh hoạ phẳng mới chỉ cần lưu đúng tên tệp trong bảng trên; ảnh được cắt theo khung nên không cần sửa mã.

## Biểu đồ

Mọi biểu đồ vẽ bằng thư viện, không có SVG hay canvas vẽ tay: Apache ECharts 6.1.0, bản dựng riêng chỉ gồm đường, cột, điểm, lưới, chú giải, gợi ý khi chạm và bộ vẽ SVG (khoảng 580 KB, 200 KB khi nén). Tệp tự host ở `vendor/echarts-6.1.0.bloomy.min.js`, kèm giấy phép Apache-2.0 (`vendor/LICENSE-echarts`, `vendor/NOTICE-echarts`, `vendor/LICENSE-zrender`). Trang không gọi CDN, và chỉ nạp thư viện khi mở màn Lớn lên hoặc Chi tiết cột mốc. Có hai biểu đồ: cân nặng theo tháng (màn Lớn lên, số liệu minh hoạ nằm ở mảng `WEIGHT` trong khối `<script>`) và dải khoảng tuổi của cột mốc. Màu theo token (đường tím, lưới `#E4E7DD`, chữ trục Reddit Sans), có bảng số cho người đọc màn hình và nhãn `aria-label`. Dựng lại bản ECharts: `npm i echarts@6.1.0 esbuild`, rồi `esbuild tools/echarts-entry.js --bundle --minify --format=iife`.

## Chữ

Font Reddit Sans (giấy phép SIL OFL, kèm trong `fonts/OFL.txt`), tự host ba bộ ký tự `latin`, `latin-ext`, `vietnamese` trong `fonts/`, nên trang không gọi dịch vụ font bên ngoài. Thang chữ có mười vai (tiêu đề màn, lời chào, tít card, tít card nhỏ, thân, mô tả, nhãn, nhãn phụ, nút, tab), khai ở đầu thẻ `<style>` dưới dạng lớp `.t-tên-vai`; đổi một vai ở một chỗ là đổi cả app.

## Bố cục

Cột ứng dụng rộng tối đa 430 px, căn giữa; ở màn rộng hơn phần còn lại là nền trơn, không vẽ khung máy. Lề 24, tab bar cao 96 gồm vùng an toàn 34, nút chính cao 48, vùng chạm tối thiểu 44.
