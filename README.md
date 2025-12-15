# PHTV - Bộ gõ tiếng Việt cho macOS

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![macOS 14+](https://img.shields.io/badge/macOS-14+-blue.svg)](https://www.apple.com/macos/)
[![Swift 6.0+](https://img.shields.io/badge/Swift-6.0+-orange.svg)](https://swift.org)
[![OpenKey](https://img.shields.io/badge/Engine-OpenKey-blueviolet.svg)](https://github.com/tuyenvm/OpenKey)
[![Website](https://img.shields.io/badge/Website-phamhungtien.com/PHTV-green.svg)](https://phamhungtien.com/PHTV/)

**PHTV** là bộ gõ tiếng Việt hoàn toàn offline cho macOS, được phát triển bởi **Phạm Hùng Tiến**. Dự án này sử dụng và mở rộng **[OpenKey](https://github.com/tuyenvm/OpenKey)** - công cụ nhập liệu tiếng Việt mạnh mẽ, với tích hợp hiện đại cho macOS và giao diện SwiftUI.

---

## 🧭 Mục lục nhanh

- [Tải xuống](#-tải-xuống--hướng-dẫn)
- [Tính năng](#-tính-năng-chính)
- [Yêu cầu & Cài đặt](#-yêu-cầu-hệ-thống)
- [Sử dụng](#-sử-dụng)
- [Cấu trúc dự án](#-cấu-trúc-dự-án)
- [Đóng góp & Hỗ trợ](#-đóng-góp)

---

## 🎉 Mới trong v1.1.0 - Spotlight Fix

> ✅ **Spotlight hoạt động bình thường!** Bạn giờ có thể gõ tiếng Việt trực tiếp trong Spotlight Search mà không bị garbling/lỗi.

**Lỗi đã được khắc phục:**
- ❌ Trước: "Phạm Hùng Tiến" → "Phaạm Huùng Tieiến" *(garbled)*
- ✅ Giờ: "Phạm Hùng Tiến" → **"Phạm Hùng Tiến"** *(hoàn hảo!)*

**Cách thực hiện:**
- Sử dụng Accessibility API (AX text replacement) thay vì synthetic events phức tạp
- Defer backspaces và áp dụng deterministically trong SendNewCharString()
- Per-character Unicode posting để tránh mark reordering
- HID tap posting + non-coalesced flags + delays cho timing-sensitive Spotlight field

---

## ⚡ Bắt đầu nhanh (3 bước)

1. Tải `PHTV.dmg` hoặc `PHTV.zip` từ [phamhungtien.com/PHTV](https://phamhungtien.com/PHTV/) hoặc [Releases](../../releases/latest) **(v1.1.0 hoặc mới hơn)**
2. Kéo `PHTV.app` vào `Applications`
3. Mở app và cấp **Accessibility** khi được nhắc

---

## 🌐 Tải xuống & Hướng dẫn

> ### 👉 **[Tải PHTV từ phamhungtien.com/PHTV](https://phamhungtien.com/PHTV/)** - Hướng dẫn chi tiết, hình ảnh, và video

<div align="center">

| **Tải ngay**                                               | **Hướng dẫn cài đặt**                               | **Tính năng**                                          | **Liên hệ**                                         |
| ---------------------------------------------------------- | --------------------------------------------------- | ------------------------------------------------------ | --------------------------------------------------- |
| [🔗 phamhungtien.com/PHTV](https://phamhungtien.com/PHTV/) | [📖 Chi tiết](https://phamhungtien.com/PHTV/#setup) | [✨ Xem thêm](https://phamhungtien.com/PHTV/#features) | [📧 Góp ý](https://phamhungtien.com/PHTV/#feedback) |

</div>

---

## ✨ Đặc điểm nổi bật

- ✅ **Hoạt động hoàn toàn offline** - Không cần kết nối Internet
- 🚀 **Hiệu năng cao** - Tối ưu hóa cho macOS với giao diện SwiftUI hiện đại
- 🎨 **Giao diện Liquid Glass** - Tương thích với macOS 14+ với thiết kế đẹp mắt
- 🌙 **Dark Mode** - Tự động thích ứng với chế độ giao diện hệ thống
- 🔧 **Hoàn toàn có thể tùy chỉnh** - Linh hoạt với nhiều tùy chọn cấu hình
- 🔒 **Quyền riêng tư** - Không thu thập hay gửi dữ liệu gõ ra ngoài
- 🔍 **Spotlight Search** - *(v1.1.0+)* Gõ tiếng Việt trực tiếp trong Spotlight mà không bị lỗi

## 🌟 Tính năng chính

### 📱 Phương pháp gõ

- **Telex** - Phương pháp phổ biến nhất (ví dụ: `vieetj` → `việt`)
- **VNI** - Phương pháp sử dụng số (ví dụ: `vie65t` → `việt`)
- **Simple Telex 1 & 2** - Biến thể đơn giản của Telex

### 🔤 Bảng mã hỗ trợ

- **Unicode** (mặc định) - Hỗ trợ đầy đủ các ký tự tiếng Việt
- **TCVN3 (ABC)** - Bảng mã cũ cho tương thích
- **VNI Windows** - Bảng mã VNI trên Windows
- **Unicode Composite** - Unicode tổ hợp
- **Vietnamese Locale (CP1258)** - Bảng mã Windows 1258

### ⚡ Tính năng nâng cao

- Smart Switch Key, Excluded Apps, Macro/gõ tắt
- Thống kê sử dụng, nhiều kiểu gõ và bảng mã
- Chạy hoàn toàn offline, không gửi dữ liệu ra ngoài

### ✅ Sau khi cài đặt nên kiểm tra

- Bật quyền **Accessibility** cho PHTV
- Thử chuyển nhanh Telex/VNI, macro, Excluded Apps
- Mở Settings để bật khởi động cùng macOS nếu cần

## ⚙️ Yêu cầu hệ thống

- **macOS 14.0 trở lên** (Sonoma và các phiên bản mới hơn)
- **Quyền Accessibility** (sẽ được yêu cầu khi khởi động lần đầu)
- **Xcode 16.0+** (nếu build từ source)

### Ma trận hỗ trợ

| Kiến trúc             | Trạng thái       | Ghi chú                             |
| --------------------- | ---------------- | ----------------------------------- |
| Apple Silicon (arm64) | ✅ Hỗ trợ        | Build universal mặc định            |
| Intel (x86_64)        | ✅ Hỗ trợ        | Build universal mặc định            |
| macOS < 14            | ⚠️ Không bảo đảm | Yêu cầu LSMinimumSystemVersion = 14 |

## 📦 Cài đặt

> 📖 **Hướng dẫn chi tiết**: Xem [INSTALL.md](INSTALL.md) hoặc tại [phamhungtien.com/PHTV](https://phamhungtien.com/PHTV/)

### Phương pháp 1: Tải bản phát hành (Khuyến khích)

- Truy cập [phamhungtien.com/PHTV](https://phamhungtien.com/PHTV/) hoặc [GitHub Releases](../../releases/latest)
- Tải `PHTV.dmg` (khuyên dùng) hoặc `PHTV.zip`
- DMG: mở, kéo `PHTV.app` vào `Applications`
- ZIP: giải nén, kéo `PHTV.app` vào `Applications`
- Mở PHTV từ Launchpad/Spotlight

### Phương pháp 2: Homebrew (Sắp tới)

```bash
brew install --cask phtv
```

### Phương pháp 3: Build từ source code

1. Clone repository:

```bash
git clone https://github.com/PhamHungTien/PHTV.git
cd PHTV
```

2. Mở file `PHTV.xcodeproj` trong Xcode:

```bash
open PHTV.xcodeproj
```

3. Build và chạy:

   - Dùng Xcode: **Cmd+R** hoặc **Product > Run**
   - Dòng lệnh (universal):

```bash
xcodebuild -project PHTV.xcodeproj -scheme PHTV -configuration Release -arch arm64 -arch x86_64
```

4. Cấp quyền Accessibility:
   - Khi ứng dụng khởi động lần đầu, nó sẽ yêu cầu quyền Accessibility
   - Mở **System Settings > Privacy & Security > Accessibility**
   - Thêm PHTV vào danh sách ứng dụng được phép

## 🚀 Sử dụng

### Menu Bar

PHTV hoạt động từ menu bar với biểu tượng "Vi" (tiếng Việt) hoặc "En" (tiếng Anh).

**Click vào biểu tượng để:**

- 🔄 Chuyển đổi giữa tiếng Việt và tiếng Anh
- ⌨️ Chọn phương pháp gõ (Telex, VNI, Simple Telex)
- 🔤 Chọn bảng mã (Unicode, TCVN3, VNI Windows, v.v.)
- ✓ Bật/tắt kiểm tra chính tả
- 📝 Bật/tắt gõ tắt (macro)
- ⚙️ Mở cài đặt chi tiết

### ⌨️ Phím tắt mặc định

- **Control + Shift**: Chuyển đổi tiếng Việt/Anh (có thể tùy chỉnh)

### 🔧 Cài đặt nâng cao

Mở **Cài đặt** từ menu bar để truy cập:

- **Kiểu gõ**: Cấu hình phương pháp gõ và bảng mã
- **Tính năng**: Bật/tắt kiểm tra chính tả, chính tả hiện đại, Quick Telex
- **Macro**: Quản lý từ viết tắt tùy chỉnh
- **Excluded Apps**: Danh sách ứng dụng tự động chuyển sang tiếng Anh
- **Hệ thống**: Cấu hình khởi động cùng macOS, sửa lỗi trình duyệt Chromium

## 🏗️ Cấu trúc dự án

```
PHTV/
├── PHTV/
│   ├── Application/          # Delegates và entry point
│   ├── Core/
│   │   ├── Engine/           # Core engine xử lý input (C++, từ OpenKey)
│   │   │   ├── Engine.cpp    # Xử lý chính sự kiện bàn phím
│   │   │   ├── Vietnamese.cpp# Bảng mã và dữ liệu tiếng Việt
│   │   │   ├── Macro.cpp     # Xử lý macro (gõ tắt)
│   │   │   └── ...
│   │   └── Platforms/        # Tích hợp platform-specific
│   ├── Managers/             # Quản lý sự kiện và cấu hình
│   ├── SwiftUI/              # Giao diện người dùng
│   │   ├── Views/            # Các view chính
│   │   ├── Controllers/      # Window và Status Bar controllers
│   │   └── Utilities/        # Helper functions cho UI
│   └── Utils/                # Tiện ích (accessibility, stats, v.v.)
├── PHTV.xcodeproj/           # Xcode project configuration
└── README.md                  # File này
```

## 🛠️ Công nghệ

- **Swift 6.0+** - Ngôn ngữ chính cho giao diện
- **SwiftUI** - Giao diện người dùng hiện đại với Liquid Glass design
- **Objective-C/C++** - Engine xử lý input method (kế thừa từ OpenKey)
- **Core Graphics (CGEvent API)** - Event tap để xử lý bàn phím
- **Cocoa Framework** - Tích hợp macOS
- **NSUserDefaults** - Lưu trữ cài đặt người dùng

## 🤝 Đóng góp

Chúng tôi rất mong nhận được đóng góp từ cộng đồng! Xem [CONTRIBUTING.md](CONTRIBUTING.md) để biết chi tiết.

Các cách bạn có thể giúp đỡ:

- 🐛 Báo cáo lỗi (GitHub Issues)
- 💡 Đề xuất tính năng mới (GitHub Discussions)
- 🔧 Gửi Pull Request với cải thiện
- 📝 Cải thiện tài liệu
- 🌍 Hỗ trợ dịch (i18n)

## 📝 Giấy phép

PHTV được phát hành dưới giấy phép **GNU General Public License v3.0** - xem file [LICENSE](LICENSE) để biết chi tiết.

Dự án này kế thừa và mở rộng engine từ **[OpenKey](https://github.com/tuyenvm/OpenKey)**, một bộ gõ tiếng Việt nổi tiếng được phát triển bởi Tuyến Võ Minh. Chúng tôi cảm ơn những người phát triển OpenKey vì nền tảng tuyệt vời.

## 🐛 Báo cáo lỗi

Nếu bạn phát hiện lỗi, vui lòng:

1. Kiểm tra [GitHub Issues](../../issues) xem lỗi đã được báo cáo chưa
2. Xem [FAQ.md](FAQ.md) để tìm giải pháp cho các vấn đề phổ biến
3. Nếu chưa, tạo issue mới với:
   - Mô tả chi tiết lỗi
   - Cách tái hiện lỗi
   - Thông tin hệ thống (macOS version, Xcode version)
   - Log (nếu có)

## ❓ FAQ

> 📋 **Câu hỏi thường gặp**: Xem [FAQ.md](FAQ.md) để biết thêm chi tiết

**Câu hỏi phổ biến:**

- **PHTV tiêu thụ bao nhiêu tài nguyên?** - Rất nhẹ! ~30-50 MB bộ nhớ
- **Có thể tùy chỉnh phím tắt được không?** - Có! Settings → Keyboard Shortcuts
- **PHTV có gửi dữ liệu gì lên internet không?** - Không! Hoàn toàn offline
- **Phương pháp gõ nào phù hợp nhất?** - Telex phổ biến nhất, nhưng thử từng cái để tìm phù hợp

Xem [FAQ.md](FAQ.md) để có câu trả lời chi tiết hơn.

## � Lịch sử cập nhật gần đây

### v1.1.0 (2025-12-16)
- ✅ **Khắc phục Spotlight**: Gõ tiếng Việt trong Spotlight Search giờ hoạt động bình thường
- 🔤 **Sửa lỗi garbling**: "Phaạm Huùng Tieiến" → "Phạm Hùng Tiến"
- 🎯 **Accessibility API integration**: AX text replacement + per-character Unicode posting
- 🐛 **HID tap posting + non-coalesced flags + delays** cho Spotlight field sensitivity
- 🔍 **Debug logging**: Opt-in via `PHTV_SPOTLIGHT_DEBUG=1` env var

### v1.0.3 (trước đó)
- Cấu hình cơ bản, Macro, Excluded Apps, Smart Switch Key
- macOS integration tốt, giao diện SwiftUI

## �🚀 Tính năng sắp tới

- [ ] Hỗ trợ input method plugin cho các ứng dụng web
- [ ] Đồng bộ hóa cài đặt qua iCloud
- [ ] Theme tùy chỉnh
- [ ] Tiếng Việt Hán Nôm
- [ ] Giao diện đa ngôn ngữ (English, 中文, etc.)

## 📚 Tài liệu thêm

- [**INSTALL.md**](INSTALL.md) - Hướng dẫn cài đặt chi tiết & troubleshooting
- [**FAQ.md**](FAQ.md) - Câu hỏi thường gặp
- [**Releases**](../../releases) - Lịch sử phiên bản và tải xuống
- [**CONTRIBUTING.md**](CONTRIBUTING.md) - Hướng dẫn đóng góp
- [**CODE_OF_CONDUCT.md**](CODE_OF_CONDUCT.md) - Quy tắc ứng xử

## 📞 Liên hệ & Hỗ trợ

- **Issues**: [GitHub Issues](../../issues) - Báo cáo lỗi, yêu cầu tính năng
- **Email**: phamhungtien@maclife.io
- **Website**: [phamhungtien.com/PHTV](https://phamhungtien.com/PHTV/)

---

## 🙏 Ghi nhận

**PHTV** được phát triển dựa trên **[OpenKey](https://github.com/tuyenvm/OpenKey)** - một công cụ nhập liệu tiếng Việt mạnh mẽ và linh hoạt. Cảm ơn tác giả OpenKey đã tạo ra nền tảng tuyệt vời này.

**OpenKey** là một dự án open-source cung cấp công cụ xử lý tiếng Việt chất lượng cao. PHTV mở rộng OpenKey với tích hợp native cho macOS, giao diện SwiftUI hiện đại, và các tính năng bổ sung như Smart Switch Key, Macros, và Excluded Apps.
