# Bloomy, demo giao diện

Bản demo tĩnh một tệp (v0.7.1), mười ba màn, năm tab, tiếng Việt. Không có máy chủ, không lưu dữ liệu: mọi trạng thái (đổi bé, thêm bé, đổi hoạt động, lưu kỷ niệm, đánh dấu cột mốc, chuỗi ngày, trình phát) chỉ nằm trong bộ nhớ trang và mất khi tải lại. Mọi số liệu về bé, chuỗi ngày, radar và bài Academy là SỐ MẪU minh hoạ, không phải dữ liệu thật.

## Mở thử

Mở `index.html` qua một máy chủ tĩnh bất kỳ, ví dụ `python3 -m http.server` trong thư mục này rồi vào `http://127.0.0.1:8000/`. Các màn đi bằng đường dẫn băm: `#/home`, `#/activity`, `#/swap`, `#/milestones`, `#/milestone/2`, `#/growth`, `#/profile` (bảy màn của mốc `approved-2026-10-27`), và các màn mới `#/calendar` (chuỗi hoạt động), `#/skills` (năng lực sáu miền), `#/academy`, `#/article/a1`, `a2`, `a3`, `a5`, `a7`, `a9` (a1 bài đọc, a2 âm thanh, a3 video; mỗi chủ đề một bài).

## Năm tab

Hôm nay, Cột mốc, Academy, Lớn lên, Hồ sơ. Năm tab là NGOẠI LỆ có ghi của luật tối đa bốn trong `BLOOMY-DESIGN.md` (mục 2, `tab-rule`).

## Thay ảnh minh hoạ: chỉ đổi tệp

Mọi ảnh nằm trong thư mục `img/` với tên cố định. Thay một ảnh thì lưu tệp mới ĐÚNG TÊN đó vào `img/`, không sửa mã. Ảnh được cắt theo khung (cover), nên tỉ lệ nào cũng dùng được; nên giữ chủ thể ở giữa.

| Tệp | Dùng ở | Khung hiển thị | Cỡ gợi ý |
|---|---|---|---|
| `bloomy-activity-play.jpg` | Hôm nay (card đầu), Hoạt động "Xếp, chờ, đổ", Lớn lên (dòng kỷ niệm, và card kỷ niệm mới sau khi lưu) | 141 x 93, 342 x 228, 64 x 48 | vuông 1024 |
| `bloomy-activity-motor.jpg` | Chọn hoạt động khác, Hoạt động "Đẩy xe, diễu hành" (kèm card Hôm nay và Lớn lên khi chọn) | 88 x 88, 342 x 228, 141 x 93 | vuông 1024 |
| `bloomy-activity-language.jpg` | Chọn hoạt động khác, Hoạt động "Gọi tên, chờ, reo" (kèm card Hôm nay và Lớn lên khi chọn) | 88 x 88, 342 x 228, 141 x 93 | vuông 1024 |
| `bloomy-activity-social.jpg` | Chọn hoạt động khác, Hoạt động "Tiệc trà cho hai gấu" (kèm card Hôm nay và Lớn lên khi chọn) | 88 x 88, 342 x 228, 141 x 93 | vuông 1024 |
| `bloomy-spot-sprout.jpg` | Lớn lên (khi tuần này chưa có kỷ niệm) | 112 x 112 | vuông 1024, nền giấy kem |
| `bloomy-hero.webp` | Hồ sơ (card bé đang chọn) | 141 x 93 | 1920 x 1280 |

Ảnh nhỏ được phóng 7 phần trăm trong khung để cắt mép giấy có sẵn trong ảnh. Riêng `bloomy-spot-sprout.jpg` đặt kiểu hoà vào nền (multiply, viền mờ dần), nên ảnh thay vào cũng nên có nền giấy sáng và chủ thể ở giữa.

Ảnh bìa các bài Academy tạm dùng lại năm ảnh trên (mảng `ARTICLES` trong `tools/bl_ext.py`, trường `img`); sẽ thay bằng ảnh gen riêng cho từng bài.

Muốn đổi cách cắt của một ảnh hoạt động thì sửa trường `pos` (ví dụ `"50% 40%"`) của hoạt động đó trong mảng `ACT` ở đầu khối `<script>`. Mỗi ảnh nên dưới 800 KB.

## Màu

Màu chủ đạo là tím `#4B14A5` (nút chữ trắng 10,8:1, tab chọn, link, dấu check), lime `#BEFA87` chỉ là nhấn phụ và luôn nằm TRONG một hình tím, như nhụy trong logo (nhụy hoa ở thanh trên, nhụy chấm "đang diễn ra", nền dấu check hoàn thành); không đặt chữ trắng lên lime, và lime không bao giờ là mảng nền tự đứng (trên nền kem chỉ 1,17:1). Chip lọc đang chọn là nền tím chữ trắng. Nền nhấn nhẹ tím rất nhạt `#E9E2F5` và `#F2EDF9`. Nền kem `#FBFAF7`, card `#F5EFE6`, chữ đen `#1D2733`, chữ thân `#434C59` giữ nguyên. Bốn màu miền (Vận động, Ngôn ngữ, Chơi, Xã hội) tách khỏi màu chủ đạo. Tất cả khai ở đầu thẻ `<style>` dưới dạng biến `--primary-deep`, `--accent`, `--tint`, `--tint2`, `--primary` (tím giữa, dùng cho đồ hoạ); đổi một biến là đổi cả app.

## Minh hoạ phẳng trên thẻ chủ đề

Luật vai: minh hoạ phẳng dành cho CHỦ ĐỀ và DANH MỤC (miền, chủ đề Academy, trạng thái rỗng); ảnh crayon dành cho hoạt động cụ thể và cảnh có người (hoạt động, ảnh hero, ảnh bìa bài). Bảy tệp nằm trong `img/illus/` (nền trong suốt, vuông 640): `illus-01-motor`, `illus-02-language`, `illus-03-play`, `illus-04-social`, `illus-06-memory`, `illus-07-growth` (card Năng lực sáu miền, chủ đề Lớn lên), `illus-08-sleep` (chủ đề Giấc ngủ), mỗi tên có hậu tố `-alpha-640.png`. Thay minh hoạ chỉ cần lưu đúng tên tệp.

## Chỗ cho minh hoạ mới

Mọi ô minh hoạ trong card là một khung `.im` có kích thước cố định (141 x 93 ở Hôm nay, kỷ niệm mới và Hồ sơ; 88 x 88 ở Chọn hoạt động khác và Thử hoạt động này; 64 x 48 ở dòng kỷ niệm). Bộ minh hoạ phẳng mới chỉ cần lưu đúng tên tệp trong bảng trên; ảnh được cắt theo khung nên không cần sửa mã.

## Biểu đồ

Mọi biểu đồ vẽ bằng thư viện, không có SVG hay canvas vẽ tay: Apache ECharts 6.1.0, bản dựng riêng chỉ gồm đường, cột, điểm, radar, lưới, chú giải, gợi ý khi chạm và bộ vẽ SVG (khoảng 600 KB, 210 KB khi nén). Tệp tự host ở `vendor/echarts-6.1.0.bloomy-r2.min.js`, kèm giấy phép Apache-2.0 (`vendor/LICENSE-echarts`, `vendor/NOTICE-echarts`, `vendor/LICENSE-zrender`). Trang không gọi CDN, và chỉ nạp thư viện khi mở màn có biểu đồ (Lớn lên, Chi tiết cột mốc, Năng lực sáu miền). Có ba biểu đồ: cân nặng theo tháng của từng bé (màn Lớn lên), dải khoảng tuổi của cột mốc, và radar sáu miền (bé so với đường tham chiếu 75%). Màu theo token (đường tím, lưới `#E4E7DD`, chữ trục Reddit Sans), có bảng số cho người đọc màn hình và nhãn `aria-label`. Dựng lại bản ECharts: `npm i echarts@6.1.0 esbuild`, rồi `esbuild tools/echarts-entry.js --bundle --minify --format=iife`.

## Số liệu trên radar: nguồn và giới hạn

Điểm của bé trên radar là số minh hoạ (nhãn "Số liệu minh hoạ" hiện trên màn). Đường nét đứt là "Đường tham chiếu 75%", KHÔNG phải số CDC công bố: Bloomy đặt tạm theo định nghĩa mốc của CDC "Learn the Signs. Act Early." (bản sửa 2022: một mốc là điều từ 75% trẻ cùng tuổi làm được từng mốc). Cần lưu ý: 75% trẻ làm được từng mốc khác với trẻ điển hình làm được 75% số mốc, nên đường này lệch về phía trấn an và cần chuyên gia soi trước khi dùng thật. Không có nguồn công khai miễn phí nào cho số trung bình thế giới của cả sáu miền ở 18 và 24 tháng, nên demo KHÔNG gọi đường đó là trung bình thế giới. Nguồn có số thật duy nhất đã xác minh là WHO Multicentre Growth Reference Study (WHO Motor Development Study, Acta Paediatrica Suppl 450, 2006) cho sáu mốc vận động thô; bảng này nằm trong mục "Nguồn số liệu" của màn Năng lực sáu miền. Các nguồn đã kiểm nhưng không dùng được nêu ở cùng chỗ; nguồn dự kiến để thay số minh hoạ khi có bản quyền sử dụng: ASQ-3, ECDI2030, GSED, CREDI.

## Hồ sơ nhiều bé

Hai bé mẫu (Mầm 18 tháng, Bơ 24 tháng) khai ở mảng `KIDS` đầu khối `<script>` (sinh từ `tools/bl_ext.py`). Bộ chọn bé ở thanh trên Hôm nay và danh sách ở Hồ sơ dùng chung một sheet. Mỗi bé có tuổi, trạng thái cột mốc, chuỗi, radar, số đo và kỷ niệm riêng. Thêm bé: tên + tuổi từ 12 đến 26 tháng; bé mới bắt đầu ở trạng thái lần đầu (chuỗi "Bắt đầu chuỗi nào!", radar và số đo rỗng).

## Chữ

Font Reddit Sans (giấy phép SIL OFL, kèm trong `fonts/OFL.txt`), tự host ba bộ ký tự `latin`, `latin-ext`, `vietnamese` trong `fonts/`, nên trang không gọi dịch vụ font bên ngoài. Thang chữ có mười vai (tiêu đề màn, lời chào, tít card, tít card nhỏ, thân, mô tả, nhãn, nhãn phụ, nút, tab), khai ở đầu thẻ `<style>` dưới dạng lớp `.t-tên-vai`; đổi một vai ở một chỗ là đổi cả app.

## Bố cục

Cột ứng dụng rộng tối đa 430 px, căn giữa; ở màn rộng hơn phần còn lại là nền trơn, không vẽ khung máy. Lề 24, tab bar cao 96 gồm vùng an toàn 34, nút chính cao 48, vùng chạm tối thiểu 44.
