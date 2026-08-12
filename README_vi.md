# Công Cụ Dịch Trực Tiếp Game Unity trên Winlator

Công cụ dịch trực tiếp các game Unity chạy trên Android thông qua Winlator, sử dụng BepInEx và AutoTranslator.

---

## ✨ Tính Năng

- 🔄 Dịch văn bản trong game theo thời gian thực khi game đang chạy
- 🌐 Hỗ trợ Google Translate V2 làm dịch vụ dịch thuật
- 📱 Chạy trên Android qua Winlator (giả lập Windows bằng Wine)
- 🔧 Cấu hình đơn giản qua file `AutoTranslatorConfig.ini`
- 🗂️ Không cần root

---

## 📦 Yêu Cầu

- **Thiết bị Android**: Android 8.0 trở lên
- Đã cài **Winlator**
- Đã tải file **BepInEx** để vào thư mục game
- Plugin **XUnity.AutoTranslator** đặt trong thư mục plugins của BepInEx Note: Đã tích hợp sẵn không cần làm bước này.
- Kết nối Internet để gọi API dịch thuật

---

## ⚙️ Thiết Lập Trên Winlator

### Bước 1 — Cấu hình Container

Bấm vào dấu + ở trên chỗ Container sau đó tạo nó 
Bấm vào 3 chấm → chọn Edit

### Bước 3 — Bấm vào ENVIRONMENT và bấm vào Add

### Bước 2 — Thiết lập biến môi trường

Bấm vào **Environment ** thêm một biến mới:

| Name | Values |
|-----|---------|
| `WINEDLLOVERRIDES` | `winhttp=n,b` |

> Lệnh này yêu cầu Wine ưu tiên dùng `winhttp.dll` bản native trước built-in, cần thiết để BepInEx inject đúng cách.

Cách thêm: nhấn **Add** → nhập vào name và values như trên → nhấn **OK!**

### Bước 3 — Thêm winhttp trong Winecfg

Bên trong container, mở **Wine Configuration** → chuyển sang tab **Libraries**.

1. Ở ô **New override for library**, gõ `winhttp`
2. Nhấn **Add** (mũi tên ①)
3. Xác nhận `winhttp (native, builtin)` xuất hiện trong danh sách
4. Nhấn **Apply** (mũi tên ①) rồi nhấn **OK** (mũi tên ②)

### Bước 4 — Cấu Hình AutoTranslator

Chạy game một lần để BepInEx tạo file cấu hình, sau đó chỉnh sửa:

```
BepInEx/config/AutoTranslatorConfig.ini
```

Sửa thành như sau:

```ini
[Service]
Endpoint=GoogleTranslateV2
FallbackEndpoint=

[General]
Language=vi
FromLanguage=en
```

> ⚠️ File cấu hình chỉ được tạo **sau khi chạy game ít nhất một lần** với BepInEx đã cài.

- `Language` — mã ngôn ngữ đích (ví dụ: `vi` cho tiếng Việt, `zh` cho tiếng Trung)
- `FromLanguage` — ngôn ngữ nguồn của game (ví dụ: `en` cho tiếng Anh, `ja` cho tiếng Nhật)

---

## 🚀 Hướng Dẫn Sử Dụng + Ở trên đã hướng dẫn rồi bạn không cần để ý phần này

1. Cài Winlator và tạo container cho game của bạn.
2. Sao chép BepInEx vào thư mục game bên trong container.
3. Thêm biến môi trường `WINEDLLOVERRIDES=winhttp=n,b` vào container.
4. Thêm `winhttp` làm DLL override native trong Winecfg.
5. Chạy game một lần để BepInEx tạo các file cấu hình.
6. Chỉnh sửa `BepInEx/config/AutoTranslatorConfig.ini` như hướng dẫn trên.
7. Chạy game lại — văn bản sẽ được dịch tự động.

---

## 🤝 Đóng Góp

1. Fork repository này
2. Tạo nhánh tính năng mới (`git checkout -b feature/TinhNangMoi`)
3. Commit các thay đổi (`git commit -m 'Thêm tính năng mới'`)
4. Push lên nhánh (`git push origin feature/TinhNangMoi`)
5. Mở Pull Request

---

## ⚠️ Lưu Ý Quan Trọng

1. **Pháp lý**: Chỉ dùng cho mục đích học tập và nghiên cứu. Vui lòng ủng hộ game bản quyền.
2. **Tương thích**: Không phải game Unity nào cũng tương thích với BepInEx hoặc AutoTranslator.
3. **Sao lưu**: Luôn sao lưu file gốc trước khi thay đổi bất cứ điều gì.
4. **Giới hạn API**: Google Translate có giới hạn tần suất; lạm dụng có thể bị chặn tạm thời.

---

## 📄 Giấy Phép

Dự án này được cấp phép theo Giấy phép MIT — xem file [LICENSE](LICENSE) để biết chi tiết.

---

## 👥 Thông Tin Nhà Phát Triển

- **Nhà phát triển**: chiuaquang
- **Telegram**: [@dexbillava](https://t.me/dexbillava)
- **Tệp BepInEx**: [BepInEx](https://github.com/BepInEx/BepInEx)
- **Plugin dịch thuật**: [XUnity.AutoTranslator](https://github.com/bbepis/XUnity.AutoTranslator)
- **Báo lỗi**: [GitHub Issues](https://github.com/chiuaquang/TrUnity/issues)

---

## 🌟 Ủng Hộ Dự Án

Nếu công cụ này hữu ích với bạn, hãy:

- ⭐ Star dự án này
- 🐛 Gửi Issue để báo lỗi
- 💬 Tham gia thảo luận

---

## Ghi Chú

- Hướng dẫn này dành riêng cho việc chạy **game Unity trên Windows** qua **Winlator** trên Android.
- BepInEx và AutoTranslator là công cụ bên thứ ba — xem tài liệu của chúng để cấu hình nâng cao.
- Nếu bản dịch không hoạt động, kiểm tra lại biến môi trường `WINEDLLOVERRIDES` và DLL override `winhttp` trong Winecfg.
