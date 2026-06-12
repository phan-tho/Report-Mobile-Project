# Phân tích Công nghệ và Thư viện (Tech Stack)

Dựa trên việc phân tích các file cấu hình `build.gradle.kts` và `gradle/libs.versions.toml` cùng với cấu trúc thư mục của dự án **MyBooksLibrary**, dưới đây là danh sách chi tiết các công nghệ và thư viện cốt lõi được sử dụng, cùng với vai trò của chúng trong dự án.

## 1. Ngôn ngữ và Giao diện (UI)
*   **Kotlin (v2.3.21)**: Ngôn ngữ lập trình chính của toàn bộ dự án. Dự án sử dụng các tính năng hiện đại của Kotlin như Coroutines và Flow để xử lý bất đồng bộ.
*   **Jetpack Compose**: Bộ công cụ UI hiện đại của Android để xây dựng giao diện người dùng theo hướng khai báo (declarative UI). Thay vì dùng XML Layout, toàn bộ giao diện (trong package `ui`) được viết bằng mã Kotlin.
*   **Material Design 3 (Material3)**: Hệ thống thiết kế cốt lõi được tích hợp sẵn với Jetpack Compose để tạo ra các thành phần giao diện nhất quán, đẹp mắt và hỗ trợ tốt các kích thước màn hình khác nhau (window size classes).

## 2. Kiến trúc Ứng dụng (Architecture)
Dựa vào cấu trúc thư mục `app/src/main/java/com/example/mybookslibrary/` gồm các package `data`, `domain`, `ui`, `di`, có thể thấy dự án áp dụng **Clean Architecture** kết hợp với mô hình **MVVM**:
*   **Clean Architecture**: Phân tách dự án thành các lớp (layers) rõ ràng:
    *   `domain`: Chứa các User Cases và Models cốt lõi, hoàn toàn độc lập với Android framework.
    *   `data`: Chứa logic thao tác dữ liệu (Repositories, Data Sources từ API hoặc Database cục bộ).
    *   `ui`: Tầng hiển thị (Screens, Components).
*   **MVVM (Model-View-ViewModel)**: Tầng `ui` sử dụng ViewModel (`androidx.lifecycle.viewmodel.compose`) để quản lý trạng thái (state) và tương tác với tầng `domain`/`data`.
*   **Hilt / Dagger (v2.59.2)**: Thư viện Dependency Injection (Tiêm phụ thuộc) được sử dụng (trong package `di`) để tự động khởi tạo và cung cấp các instances (như Repository, Database, API client) cho các lớp khác (đặc biệt là ViewModels).

## 3. Các thư viện cốt lõi khác
*   **Room Database (v2.8.4)**: Thư viện ORM của Google dùng để lưu trữ dữ liệu cục bộ trên SQLite. Nó được sử dụng trong tầng `data.local` để lưu sách offline, lịch sử đọc, cache dữ liệu.
*   **DataStore Preferences (v1.2.1)**: Dùng để lưu trữ các tuỳ chọn người dùng (như theme, settings) dưới dạng key-value bất đồng bộ, thay thế cho SharedPreferences cũ.
*   **Retrofit (v3.0.0) & OkHttp (v5.3.2)**: Quản lý các kết nối mạng HTTP. Retrofit giúp định nghĩa các API endpoints (ví dụ như MangaDex API trong `data.remote`), còn OkHttp đóng vai trò làm client xử lý kết nối và logging.
*   **Kotlinx Serialization (v1.10.0)**: Thư viện phân tích cú pháp (parse) dữ liệu JSON trả về từ API thành các object Kotlin.
*   **Coil (v3.4.0)**: Thư viện tải hình ảnh (Image Loading) được thiết kế chuyên biệt cho Kotlin và tích hợp sẵn với Jetpack Compose (`coil-compose`). Dùng để load bìa sách, trang truyện từ mạng.
*   **Firebase Auth & Credential Manager**: Xử lý đăng nhập, quản lý người dùng (Google Sign-In) ở tầng `data.repository` và `domain`.
*   **WorkManager (v2.11.2)**: Xử lý các tác vụ ngầm (background work) đảm bảo hoàn thành ngay cả khi người dùng đã thoát app (ví dụ: `SyncWorker` đồng bộ tiến trình đọc sách lên cloud).

---

## 4. Minh chứng (Trích xuất code cấu hình tiêu biểu)

### Cấu hình các Plugins chính (`app/build.gradle.kts`)
```kotlin
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.kotlin.compose)
    alias(libs.plugins.kotlin.serialization) // Dùng cho Kotlinx Serialization
    alias(libs.plugins.ksp)                  // Kotlin Symbol Processing (cho Room, Hilt)
    alias(libs.plugins.hilt.android)         // Dependency Injection
}
```

### Cấu hình Dependency Injection, Room, Network (`app/build.gradle.kts`)
```kotlin
dependencies {
    // ...
    // Local data and background work (Room, DataStore, WorkManager)
    implementation(libs.androidx.datastore.preferences)
    implementation(libs.androidx.room.runtime)
    implementation(libs.androidx.room.ktx)
    ksp(libs.androidx.room.compiler)
    implementation(libs.androidx.work.runtime.ktx)

    // Network and image loading (Retrofit, OkHttp, Coil)
    implementation(libs.retrofit.core)
    implementation(libs.retrofit.converter.kotlinx.serialization)
    implementation(libs.kotlinx.serialization.json)
    implementation(libs.okhttp.core)
    implementation(libs.coil.compose)

    // Dependency injection (Hilt)
    implementation(libs.hilt.android)
    implementation(libs.androidx.hilt.navigation.compose)
    ksp(libs.androidx.hilt.compiler)
    // ...
}
```

### Quản lý phiên bản tập trung (`gradle/libs.versions.toml`)
Dự án sử dụng Version Catalog để quản lý phiên bản thư viện gọn gàng:
```toml
[versions]
kotlin = "2.3.21"
composeBom = "2026.05.01"
room = "2.8.4"
hilt = "2.59.2"
retrofit = "3.0.0"
coil = "3.4.0"

[libraries]
androidx-room-runtime = { module = "androidx.room:room-runtime", version.ref = "room" }
hilt-android = { module = "com.google.dagger:hilt-android", version.ref = "hilt" }
coil-compose = { module = "io.coil-kt.coil3:coil-compose", version.ref = "coil" }
```
