# Danh sách công việc cần làm (TODO) cho Phần 2

Phần mã LaTeX cho **Chương 2 (Các công nghệ và thư viện sử dụng)** đã chừa sẵn câu lệnh `\includegraphics{placeholder_clean_architecture.png}`. Để báo cáo đầy đủ trực quan, bạn cần tải/chèn ảnh minh hoạ thực tế cho mô hình này. 

## Hình `placeholder_clean_architecture.png` (Sơ đồ Clean Architecture + MVVM)
* **Keyword tìm kiếm:** `Clean Architecture Android MVVM diagram`, `Android App Architecture guide diagram`
* **Prompt vẽ ảnh AI:** "A standard Clean Architecture diagram tailored for Android development featuring Presentation layer (MVVM), Domain layer (Use cases, Entities), and Data layer (Repository, Local DB, Remote API)."
* **Hành động:** Chèn ảnh vào thư mục cấu hình và update tên file.

## Chương 3: Phân tích yêu cầu và thiết kế hệ thống
1. `usecase_tong.png`: Chụp ảnh hoặc xuất PDF Sơ đồ Use Case tổng quát mà bạn đã vẽ.
2. `FetchListBookApi.png`: Xuất ảnh Sơ đồ tuần tự lấy danh sách truyện.
3. `SaveBook.png`: Xuất ảnh Sơ đồ tuần tự lưu truyện.
4. `db_schema.png`: Lấy đoạn mã Mermaid ERD trong `database_schema.md` (phần 2), dán vào web Mermaid Live Editor, xuất ra dạng PNG/PDF và lưu vào thư mục `figures/` với tên `db_schema.png`.

## Chương 4: Đánh giá và kiểm thử
Chương này yêu cầu chèn 4 ảnh chụp màn hình thực tế (screenshot) từ chính điện thoại/máy ảo khi chạy ứng dụng của bạn. Bạn hãy chạy app, chụp màn hình, đặt tên file tương ứng và thả vào thư mục `figures/` nhé:
1. `screenshot_discover.png`: Chụp giao diện tab Khám phá (Discover) hiển thị danh sách các truyện mới/phổ biến.
2. `screenshot_search.png`: Chụp giao diện lúc đang tìm kiếm hoặc mở bộ lọc (Search Filter).
3. `screenshot_reader.png`: Chụp lúc đang đọc truyện (hiển thị trang truyện, có thể vuốt lên một chút để thấy nội dung).
4. `screenshot_library.png`: Chụp giao diện tab Thư viện cá nhân chứa các truyện đã lưu.
5. `CIflow.pdf`: Lấy đoạn code sơ đồ luồng CI trong `testing_ci_context.md`, dán vào mermaid.live và xuất ra file PDF (hoặc PNG rồi đổi thành `CIflow.png` và sửa tên trong code LaTeX tương ứng).
6. `github_actions_success.png`: Chụp lại màn hình một workflow "CI" trên tab Actions của GitHub báo dấu tick xanh thành công.
