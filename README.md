# Firmware Marlin Ender 3 Pro - Minh Hoàng Cơ Điện Tử

Đây là bản firmware tùy chỉnh cho máy in 3D **Ender 3 Pro** sử dụng mainboard **Creality V4.2.2**. Bản firmware này được tinh chỉnh để tăng tính ổn định, dễ sử dụng và nâng cao chất lượng bản in.

## 🛠 Thông tin phần cứng
- **Mainboard:** Creality Silent Board 4.2.2 (STM32F103RET6)
- **Driver động cơ:** TMC2225 (Cấu hình: `TMC2208_STANDALONE`)
- **Màn hình:** CR-10 Stock Display (CR10_STOCKDISPLAY + RET6_12864_LCD)
- **Cảm biến:** Không có BLTouch (Sử dụng Mesh Bed Leveling thủ công)

## ✨ Các tính năng nổi bật

### 1. Giao diện & Cá nhân hóa
- **Custom Bootscreen:** Hiển thị logo khởi động tùy chỉnh (64x64).
- **Máy Name:** Hiển thị "MINH HOANG CODIENTU" trên màn hình LCD.
- **Marlin Bootscreen:** Đã tắt để giảm thời gian khởi động.

### 2. Cân bàn & Bed Leveling
- **Mesh Bed Leveling:** Cho phép đo và lưu lưới cân bàn 3x3 hoặc 4x4.
- **LCD Bed Tramming:** Hỗ trợ cân 4 ốc vít bàn in ngay trên màn hình.
- **LCD Bed Leveling:** Giao diện hướng dẫn từng bước ngay trên núm xoay.

### 3. Nhiệt độ & PID
- **PID Autotune Menu:** Hỗ trợ tự động tinh chỉnh PID cho cả **Đầu in (Hotend)** và **Bàn nhiệt (Bed)** ngay trong menu.
- **PIDTEMPBED:** Bật chế độ PID ổn định nhiệt cho bàn nhiệt (thay vì đóng ngắt thông thường).
- **EEPROM Auto Init:** Tự động sửa lỗi bộ nhớ nếu có xung đột dữ liệu.

### 4. Vận hành & Chất lượng in
- **Babystepping (Double-click):** Nhấn đúp núm xoay để tinh chỉnh độ cao trục Z (Z-offset) ngay khi đang in.
- **S-Curve Acceleration:** Gia tốc hình chữ S giúp máy chạy êm ái, giảm rung động và tiếng ồn.
- **Power Loss Recovery:** Tự động lưu trạng thái in khi mất điện và hỏi tiếp tục khi bật lại.
- **SD Card Support:** Hỗ trợ đọc thẻ nhớ để in độc lập.

## ⚙️ Thông số mặc định (Default Configuration)
> Lưu ý: Các thông số này có thể đã bị thay đổi bởi người dùng thông qua menu LCD và lệnh `M500`.

| Thông số | Giá trị | Ghi chú |
| :--- | :--- | :--- |
| **Max Feedrate (X/Y)** | 300 mm/s | Tốc độ di chuyển tối đa |
| **Max Feedrate (Z)** | 5 mm/s | Tốc độ nâng bàn tối đa |
| **Max Feedrate (E)** | 25 mm/s | Tốc độ đùn nhựa tối đa |
| **Acceleration (In)** | 3000 mm/s² | Gia tốc khi in |
| **Acceleration (Travel)** | 3000 mm/s² | Gia tốc di chuyển trống |
| **Acceleration (Retract)** | 3000 mm/s² | Gia tốc rút nhựa |

## 📦 Hướng dẫn cài đặt (Flashing)

1. **Build Firmware:**
   Chạy lệnh sau trong PowerShell:
   ```powershell
   cd "D:\Firmware ender 3 pro\Marlin-bugfix-2.1.x"
   pio run
   ```
2. **Chuẩn bị thẻ nhớ:**
   - Format thẻ nhớ SD sang định dạng **FAT32**.
   - Tìm file `firmware.bin` trong thư mục `.pio\build\STM32F103RE_creality_maple\`.
   - Copy file `firmware.bin` vào thư mục gốc của thẻ nhớ.
3. **Flash máy:**
   - Tắt nguồn máy in.
   - Cắm thẻ nhớ vào khe đọc.
   - Bật nguồn máy in. Máy sẽ tự động cập nhật trong vài giây (màn hình có thể nháy hoặc tối đen).
   - Khi máy chạy quạt và màn hình bình thường, tắt nguồn và rút thẻ nhớ.

## ⚠️ Lưu ý quan trọng
- **Cân bàn thủ công:** Do không có BLTouch, bạn cần thực hiện **Tramming Bed** (cân 4 góc) mỗi khi thay bàn in hoặc sau một thời gian dài sử dụng.
- **Lưu cài đặt:** Sau khi thay đổi PID hoặc Cân bàn, hãy luôn chọn **Store Settings** (hoặc lệnh `M500`) để lưu vào bộ nhớ.
- **Mất điện:** Tính năng Power Loss Recovery yêu cầu file in phải được chạy từ thẻ nhớ mới hoạt động.


- **Ngày cập nhật:** Tháng 05/2026
