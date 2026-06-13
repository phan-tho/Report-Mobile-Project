Listed directory MyBooksLibrary
Searched for "firestore"
Viewed FirestoreLibraryItem.kt:1-23
Viewed FirestoreChapterProgress.kt:1-11
Viewed FirestoreReview.kt:1-20
Viewed firestore.rules:1-47

Cấu trúc Firestore đồng bộ và lưu trữ dữ liệu của ứng dụng gồm 3 phần chính:

### 1. Thư viện cá nhân (`users/{userId}/library/{mangaId}`)
Lưu danh sách truyện được lưu/theo dõi bởi người dùng.
* **mangaId**: ID của manga (Document ID).
* **title**: Tên truyện.
* **coverUrl**: Link ảnh bìa.
* **status**: Trạng thái đọc (READING, COMPLETED, v.v.).
* **isFavorite**: Đánh dấu yêu thích.
* **addedAt**: Thời điểm thêm vào thư viện (ms).
* **lastReadAt**: Thời điểm đọc gần nhất (ms).
* **lastChapterId**: ID chapter đọc gần nhất.
* **lastReadPageIndex**: Trang đọc gần nhất.
* **updatedAt**: Thời điểm cập nhật local (ms).
* **serverUpdatedAt**: Thời điểm cập nhật phía server (Date).

### 2. Tiến độ đọc (`users/{userId}/progress/{chapterId}`)
Lưu chi tiết trang đã đọc của từng chapter.
* **chapterId**: ID của chapter.
* **mangaId**: ID của manga tương ứng.
* **status**: Trạng thái đọc của chapter.
* **lastReadPage**: Trang đọc cuối cùng.
* **totalPages**: Tổng số trang.
* **updatedAt**: Thời điểm cập nhật (ms).

### 3. Đánh giá truyện (`manga_reviews/{mangaId}/reviews/{authorUid}`)
Lưu đánh giá công khai của người dùng về truyện.
* **authorUid**: UID của người đánh giá (Document ID).
* **rating**: Điểm đánh giá (từ 1 đến 5).
* **title**: Tiêu đề đánh giá.
* **body**: Nội dung đánh giá.
* **authorName**: Tên hiển thị của người đánh giá.
* **createdAt**: Thời điểm tạo đánh giá (ms).
* **updatedAt**: Thời điểm cập nhật đánh giá (ms).
