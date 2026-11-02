# 📱 BÀI TẬP VỀ NHÀ: LẬP TRÌNH CHO THIẾT BỊ DI ĐỘNG
## ĐỀ TÀI: ỨNG DỤNG TRÒ CHƠI SẮP XẾP TỪ (UNSCRAMBLE GAME)

[![Platform](https://img.shields.io/badge/Platform-Android-3DDC84.svg?style=flat&logo=android&logoColor=white)](https://developer.android.com)
[![Kotlin](https://img.shields.io/badge/Kotlin-Native-7F52FF.svg?style=flat&logo=kotlin&logoColor=white)](https://kotlinlang.org)
[![Min SDK](https://img.shields.io/badge/Min%20SDK-26-orange.svg?style=flat)](https://developer.android.com)
[![Target SDK](https://img.shields.io/badge/Target%20SDK-37-brightgreen.svg?style=flat)](https://developer.android.com)
[![Design](https://img.shields.io/badge/UI-Material%20Design%203-purple.svg?style=flat)](https://m3.material.io/)

---

## 👨‍🎓 Thông tin

- **Môn học**: Lập trình cho thiết bị di động
- **Sinh viên thực hiện**: Bùi Đình Tuấn

---

## 📖 1. Giới thiệu đề tài & Mục tiêu bài tập

**Unscramble** là trò chơi giải đố sắp xếp chữ cái tiếng Anh dành cho người học tiếng Anh hoặc rèn luyện trí não. Ứng dụng đưa ra một từ vựng tiếng Anh đã bị xáo trộn thứ tự các chữ cái, người chơi có nhiệm vụ sắp xếp lại thành từ có nghĩa đúng trong số lượt câu hỏi cho trước.

### Mục tiêu bài tập giai đoạn này:
- Nắm vững quy trình khởi tạo và cấu trúc một dự án Android Native bằng **Kotlin**.
- Thiết kế giao diện người dùng (UI) hoàn chỉnh dựa trên **XML Layout** và **Material Design 3 Components**.
- Sử dụng hiệu quả **ConstraintLayout** để xây dựng giao diện tương thích đa kích thước màn hình.
- Cấu hình hiển thị tràn viền chuẩn mực (**Edge-to-Edge**) với `WindowInsetsCompat`.
- Tuân thủ quy chuẩn quản lý tài nguyên trong Android (tách biệt `strings.xml`, `colors.xml`, không hardcode giao diện).

---

## ✨ 2. Các yêu cầu & Kết quả đã hoàn thành

| Thành phần UI | Widget / View sử dụng | Mô tả chức năng |
| :--- | :--- | :--- |
| **Top App Bar** | `MaterialToolbar` | Thanh tiêu đề phía trên cùng của ứng dụng (`@id/topAddBar`). |
| **Khung câu hỏi** | `MaterialCardView` | Thẻ bo tròn góc (`16dp`), làm nổi bật khu vực hiển thị nội dung câu đố (`@id/cardQuestion`). |
| **Tiến trình câu hỏi** | `TextView` | Huy hiệu (Badge) đếm số câu hỏi (ví dụ: `1/10`) ở góc trên thẻ (`@id/tvWordCount`). |
| **Từ bị xáo trộn** | `TextView` | Hiển thị từ vựng đã đảo lộn ký tự để thử thách người chơi (`@id/tvScrambledWrd`). |
| **Dòng hướng dẫn** | `TextView` | Dòng chữ nhắc nhở luật chơi cho sinh viên/người dùng (`@id/tvInstructions`). |
| **Ô nhập đáp án** | `TextInputLayout` + `TextInputEditText` | Ô nhập liệu Material hỗ trợ gợi ý (hint) và tự động tương thích bàn phím (`@id/textFieldLayout`). |
| **Nút Gửi** | `MaterialButton` | Nút hành động gửi câu trả lời để kiểm tra (`@id/btnSubmit`). |
| **Nút Bỏ qua** | `MaterialButton` | Nút bỏ qua câu hỏi hiện tại để chuyển sang câu kế tiếp (`@id/btnSkip`). |
| **Tối ưu hiển thị** | `WindowInsetsCompat` & `enableEdgeToEdge()` | Đảm bảo các view không bị che khuất bởi Status Bar và Navigation Bar trên Android mới. |

---

## 🛠 3. Công nghệ & Môi trường phát triển

- **Ngôn ngữ lập trình**: Kotlin (Tương thích Java 11)
- **Hệ thống build**: Gradle (Kotlin DSL `.gradle.kts`) kết hợp **Version Catalog** (`gradle/libs.versions.toml`)
- **Android Gradle Plugin (AGP)**: `9.5.0`
- **Phiên bản SDK**:
  - `compileSdk`: `37` (Android 15+)
  - `targetSdk`: `37`
  - `minSdk`: `26` (Hỗ trợ từ Android 8.0 Oreo trở lên)
- **Thư viện chính (Dependencies)**:
  - `androidx.core:core-ktx:1.10.1`: Tiện ích mở rộng Kotlin cho AndroidX Core
  - `androidx.appcompat:appcompat:1.6.1`: Hỗ trợ tương thích ngược giao diện
  - `androidx.activity:activity-ktx:1.13.0`: Hỗ trợ Edge-to-Edge và xử lý vòng đời Activity
  - `androidx.constraintlayout:constraintlayout:2.1.4`: Bố cục ràng buộc linh hoạt
  - `com.google.android.material:material:1.10.0`: Thành phần giao diện Material Design 3
- **Kiểm thử (Testing)**: JUnit 4, AndroidX Test JUnit, Espresso Core

---

## 📂 4. Cấu trúc thư mục dự án

```text
Unscramble/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/unscramble/
│   │   │   │   └── MainActivity.kt             # Khởi tạo Activity, cấu hình Edge-to-Edge và Insets
│   │   │   ├── res/
│   │   │   │   ├── layout/
│   │   │   │   │   └── activity_main.xml       # Giao diện chính của game (ConstraintLayout)
│   │   │   │   ├── values/
│   │   │   │   │   ├── colors.xml              # Định nghĩa bảng màu sử dụng trong app
│   │   │   │   │   ├── strings.xml             # Toàn bộ chuỗi văn bản (Việt hóa, không hardcode)
│   │   │   │   │   └── themes.xml              # Material 3 Day/Night theme
│   │   │   │   └── AndroidManifest.xml         # Khai báo cấu hình, adjustResize bàn phím
│   │   └── test/                               # Thư mục chứa Unit Test
│   └── build.gradle.kts                        # Cấu hình build & dependencies của app
├── gradle/
│   ├── libs.versions.toml                      # Quản lý phiên bản thư viện tập trung
│   └── wrapper/                                # Gradle Wrapper
├── build.gradle.kts                            # Cấu hình build cấp root
└── README.md                                   # Tài liệu báo cáo bài tập
```

---

## 🚀 5. Hướng dẫn cài đặt & Khởi chạy

### Yêu cầu môi trường:
- Cài đặt **Android Studio** (phiên bản Ladybug, Iguana hoặc mới hơn).
- JDK 11 hoặc JDK tích hợp sẵn trong Android Studio.
- Thiết bị thật hoặc máy ảo Android (Emulator) chạy hệ điều hành Android 8.0 (API 26) trở lên.

### Các bước thực hiện:
1. **Tải mã nguồn về máy**:
   ```bash
   git clone https://github.com/tuanbui69/Unscramble.git
   cd Unscramble
   ```
2. **Mở dự án trong Android Studio**:
   - Chọn **File > Open** và dẫn tới thư mục `Unscramble`.
   - Chờ Android Studio và Gradle đồng bộ thư viện (Sync Project with Gradle Files).
3. **Chạy ứng dụng**:
   - Khởi động một thiết bị ảo (AVD) hoặc kết nối điện thoại Android qua cáp USB (đã bật *USB Debugging*).
   - Nhấn nút **Run 'app'** (hoặc tổ hợp phím `Shift + F10`) để cài đặt và chạy ứng dụng.

---

## 📌 6. Lộ trình hoàn thiện bài tập (Kế hoạch các tuần tiếp theo)

- [x] **Giai đoạn 1**: Thiết kế hoàn chỉnh Layout giao diện (`activity_main.xml`), định nghĩa tài nguyên (`strings.xml`, `colors.xml`).
- [x] **Giai đoạn 2**: Cấu hình hiển thị tràn màn hình (`enableEdgeToEdge`), xử lý bàn phím ảo không che khuất ô nhập liệu.
- [ ] **Giai đoạn 3**: Xây dựng danh sách dữ liệu từ vựng tiếng Anh mẫu (`allWordsList`).
- [ ] **Giai đoạn 4**: Xây dựng kiến trúc MVVM (`GameViewModel`, `GameUiState`) để quản lý trạng thái trò chơi.
- [ ] **Giai đoạn 5**: Lập trình thuật toán xáo trộn từ (Scramble word) và gắn sự kiện cho các nút **Gửi (Submit)** / **Bỏ qua (Skip)**.
- [ ] **Giai đoạn 6**: Xây dựng tính năng tính điểm, giới hạn 10 câu hỏi và hiển thị Dialog chúc mừng khi hoàn thành vòng chơi.

---

## 📄 Bản quyền & Ghi chú

- Dự án phục vụ mục đích học tập môn **Lập trình cho thiết bị di động**.
- Sinh viên thực hiện: **Bùi Đình Tuấn**.

