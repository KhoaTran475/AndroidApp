# 📱 IELTS Vision - Học Tiếng Anh 4 Kỹ Năng Tích Hợp Nhận Diện Vật Thể AI Trên Di Động (Android)

> **Đồ án:** Phát triển ứng dụng di động học tiếng Anh IELTS kết hợp Thị giác máy tính AI (Computer Vision) On-device  
> **Nền tảng:** 100% Flutter / Dart (Tối ưu hóa riêng cho Android)  
> **Mô hình AI:** YOLOv8n TFLite (80 lớp COCO, On-device Offline, < 35ms)  
> **Cơ sở dữ liệu:** SQLite cục bộ (sqflite) với phân quyền người dùng RBAC  

---

## 🌟 TÍNH NĂNG CHÍNH

1. **Quét Vật Thể AI Thời Gian Thực (Live AI Camera Scan):**
   - Tự động phát hiện và đóng khung vật thể qua camera (chuột máy tính, điện thoại, ô tô, xe đạp, ba lô...).
   - Thuật toán **Letterbox 640x640** bảo toàn 100% tỷ lệ hình ảnh, chống méo ảnh.
   - Kỹ thuật **Cross-Class NMS (IoU = 0.50)** triệt tiêu hộp trùng lặp gây nhầm lẫn giữa các vật thể.
   - **Smart Tap Selection:** Chạm thông minh chọn đúng vật thể nhỏ nằm trên nền lớn.
2. **Kho Bài Học IELTS Học Thuật (Band 7.0 - 8.5):**
   - 82 nhãn nhận diện liên kết trực tiếp với bộ từ điển học thuật chuẩn ZIM Academy.
   - Cung cấp: Từ vựng học thuật C1/C2, Phiên âm IPA chuẩn, Nghĩa tiếng Việt, Collocations nâng cao, Topic Idiom, Câu mẫu IELTS Speaking Part 1 song ngữ Anh - Việt.
   - **Phát âm Text-to-Speech (TTS):** Đọc phát âm chuẩn bản xứ theo thời gian thực.
3. **Sổ Tay Từ Vựng Cá Nhân (Vocabulary Notebook):**
   - Lưu trữ không giới hạn từ vựng yêu thích vào cơ sở dữ liệu SQLite offline.
   - Tìm kiếm thời gian thực theo từ vựng hoặc nghĩa tiếng Việt.
   - Bộ lọc linh hoạt theo Band điểm (Tất cả, Band 7.0, Band 7.5, Band 8.0+).
   - Mở rộng xem chi tiết Collocations, Idiom, Speaking và xóa từ vựng.
4. **Hệ Thống Quản Trị Toàn Diện (Admin Dashboard):**
   - **Báo cáo KPIs:** Theo dõi tổng từ vựng AI, người dùng, học viên, số lượt lưu sổ tay, trạng thái AI Model.
   - **Biểu đồ phân bố Band:** Tỷ lệ phân bố từ vựng theo từng thang điểm IELTS.
   - **Quản lý kho từ vựng (CRUD):** Thêm nhãn mới, sửa thông tin từ vựng, nghe thử TTS, xóa nhãn.
   - **Khôi phục dữ liệu gốc (1 Click):** Đặt lại nguyên vẹn 82 nhãn chuẩn từ file JSON gốc.
   - **Quản lý tài khoản (RBAC):** Danh sách người dùng, thêm tài khoản mới, xóa tài khoản an toàn.

---

## 🛠️ CÔNG NGHỆ CỐT LÕI & CÁC GÓI SỬ DỤNG (TECH STACK)

| Gói thư viện | Phiên bản | Công dụng & Vai trò |
| :--- | :--- | :--- |
| `camera` | `^0.11.0+1` | Điều khiển camera Android, thu nhận luồng hình ảnh YUV420 thời gian thực. |
| `tflite_flutter` | `^0.11.0` | Nạp mô hình nhị phân YOLOv8n TFLite và thực thi suy luận AI trên phần cứng di động. |
| `image` | `^4.1.7` | Chuyển đổi YUV420 sang RGB, xoay góc ảnh, thuật toán chèn viền Letterbox 640x640. |
| `sqflite` & `path` | `^2.3.2` | Quản trị cơ sở dữ liệu quan hệ cục bộ SQLite offline (`ielts_vision_v2.db`). |
| `flutter_tts` | `^4.0.2` | Phát âm từ vựng chuẩn giọng bản xứ Mỹ (en-US). |
| `provider` | `^6.1.2` | Quản lý trạng thái (State Management) toàn cục theo kiến trúc Provider. |
| `shared_preferences`| `^2.2.3` | Lưu phiên đăng nhập người dùng tự động. |

---

## 🚀 HƯỚNG DẪN CÀI ĐẶT & CHẠY ỨNG DỤNG (SETUP GUIDE)

### 1. Chuẩn bị (Chi phí: 0 VNĐ - Hoàn toàn Miễn phí)
- **Không tốn phí mua API:** Chạy On-device 100% không tốn tiền API OpenAI hay Google Cloud.
- **Phần mềm cần cài:**
  - [Flutter SDK](https://docs.flutter.dev/get-started/install) ($\ge$ 3.19.x)
  - [Android Studio](https://developer.android.com/studio) (Android SDK & Command-line Tools)
  - [Git](https://git-scm.com/)

### 2. Các bước cài đặt từ Git

```bash
# 1. Clone mã nguồn
git clone <URL_REPO_CUA_BAN>
cd doancuoiki

# 2. Cài đặt các gói phụ thuộc
flutter pub get

# 3. Kiểm tra môi trường
flutter doctor -v

# 4. Chạy ứng dụng trên máy Android thật (hoặc máy ảo)
flutter run
```

### 3. Đóng gói file cài đặt APK nộp bài

```bash
flutter build apk --release
```
File APK sau khi build xong sẽ nằm tại:
`build/app/outputs/flutter-apk/app-release.apk`

---

## 🔑 TÀI KHOẢN KIỂM THỬ MẶC ĐỊNH (TEST ACCOUNTS)

Hệ thống tự động khởi tạo sẵn 2 tài khoản mẫu trong SQLite:

| Tài khoản | Mật khẩu | Quyền hạn (Role) | Chức năng kiểm thử |
| :--- | :--- | :--- | :--- |
| **`learner`** | `password123` | Học viên (`learner`) | Quét vật thể AI, tra từ IELTS, nghe phát âm, lưu và quản lý Sổ tay từ vựng. |
| **`admin`** | `password123` | Quản trị (`admin`) | Xem báo cáo KPIs, chỉnh sửa kho 82 từ, thêm nhãn, quản lý người dùng, khôi phục dữ liệu gốc. |
