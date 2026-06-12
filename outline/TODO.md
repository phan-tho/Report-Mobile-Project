# Danh sách công việc cần làm (TODO) cho Phần 2

Phần mã LaTeX cho **Chương 2 (Các công nghệ và thư viện sử dụng)** đã chừa sẵn các câu lệnh `\includegraphics{placeholder_xxx.png}`. Để báo cáo đầy đủ trực quan, bạn cần tải/chèn các ảnh minh hoạ thực tế cho các mô hình này. 

Dưới đây là gợi ý từ khoá tìm kiếm trên Google Images hoặc câu lệnh (prompt) dùng cho AI (như ChatGPT/Gemini/Midjourney) để tạo/tìm ảnh cho từng placeholder:

## 1. Hình `placeholder_compose.png` (Mô hình hoạt động Jetpack Compose)
* **Keyword tìm kiếm:** `Jetpack Compose recomposition architecture diagram`, `Declarative UI Android Compose diagram`
* **Prompt vẽ ảnh AI:** "A technical diagram explaining Android Jetpack Compose declarative UI model showing State flowing down to UI components and Events flowing up."
* **Hành động:** Đổi tên file ảnh thành `placeholder_compose.png` (hoặc sửa tên trong code LaTeX) và lưu vào thư mục chứa ảnh (thường là `images/` hoặc `assets/` trong template LaTeX của bạn).

## 2. Hình `placeholder_clean_architecture.png` (Sơ đồ Clean Architecture + MVVM)
* **Keyword tìm kiếm:** `Clean Architecture Android MVVM diagram`, `Android App Architecture guide diagram`
* **Prompt vẽ ảnh AI:** "A standard Clean Architecture diagram tailored for Android development featuring Presentation layer (MVVM), Domain layer (Use cases, Entities), and Data layer (Repository, Local DB, Remote API)."
* **Hành động:** Chèn ảnh vào thư mục cấu hình và update tên file.

## 3. Hình `placeholder_hilt.png` (Cơ chế Dependency Injection với Hilt)
* **Keyword tìm kiếm:** `Android Hilt dependency injection diagram`, `Dagger Hilt components hierarchy`
* **Prompt vẽ ảnh AI:** "A simple flowchart diagram showing how Dagger Hilt manages Dependency Injection in Android, providing instances to ViewModels and Fragments automatically."

## 4. Hình `placeholder_room.png` (Các thành phần cốt lõi của Room)
* **Keyword tìm kiếm:** `Android Room architecture diagram`, `Room Database components Entity DAO`
* **Gợi ý nguồn:** Lấy trực tiếp hình ảnh chuẩn từ tài liệu của Google Developer: [Lưu dữ liệu cục bộ bằng Room](https://developer.android.com/training/data-storage/room). Sẽ có sơ đồ 3 khối kinh điển: Database, DAO, Entity.

## 5. Hình `placeholder_retrofit.png` (Luồng giao tiếp HTTP qua Retrofit)
* **Keyword tìm kiếm:** `Retrofit Android architecture diagram`, `Retrofit OkHttp Network flow Android`
* **Prompt vẽ ảnh AI:** "A block diagram showing an Android app making a network request via Retrofit interface, passing through OkHttp client, hitting a REST API, and returning JSON parsed into Kotlin Data Classes."

## Chương 4: Đánh giá và kiểm thử
Chương này yêu cầu chèn 4 ảnh chụp màn hình thực tế (screenshot) từ chính điện thoại/máy ảo khi chạy ứng dụng của bạn. Bạn hãy chạy app, chụp màn hình, đặt tên file tương ứng và thả vào thư mục `figures/` nhé:
1. `screenshot_discover.png`: Chụp giao diện tab Khám phá (Discover) hiển thị danh sách các truyện mới/phổ biến.
2. `screenshot_search.png`: Chụp giao diện lúc đang tìm kiếm hoặc mở bộ lọc (Search Filter).
3. `screenshot_reader.png`: Chụp lúc đang đọc truyện (hiển thị trang truyện, có thể vuốt lên một chút để thấy nội dung).
4. `screenshot_library.png`: Chụp giao diện tab Thư viện cá nhân chứa các truyện đã lưu.
5. `CIflow.pdf`: Lấy đoạn code sơ đồ luồng CI trong `testing_ci_context.md`, dán vào mermaid.live và xuất ra file PDF (hoặc PNG rồi đổi thành `CIflow.png` và sửa tên trong code LaTeX tương ứng).
6. `github_actions_success.png`: Chụp lại màn hình một workflow "CI" trên tab Actions của GitHub báo dấu tick xanh thành công.
