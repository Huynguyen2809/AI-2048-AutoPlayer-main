# AI 2048 - Auto Player

Dự án tự động chơi tựa game 2048 kinh điển bằng thuật toán AI **Expectimax**, kết hợp với giao diện trực quan được xây dựng trên nền tảng **Pygame**.

## ✨ Tính năng nổi bật

- **Thuật toán Expectimax**: Là giải pháp hoàn hảo để xử lý yếu tố ngẫu nhiên (chance nodes) trong 2048.
- **Hàm Heuristic đa chiều**: Đánh giá bàn cờ cực kỳ thông minh dựa trên:
  - **Tính đơn điệu (Monotonicity)**: Dồn số lớn về một phía.
  - **Độ mượt (Smoothness)**: Sắp xếp các con số tăng/giảm một cách liền mạch.
  - **Ô trống (Free Tiles)**: Khuyến khích tối đa hóa không gian trống.
  - **Giá trị lớn nhất (Max Tile)**: Ưu tiên gom giá trị lớn nhất có thể.
- **Tối ưu hóa (Optimization)**: Sử dụng kĩ thuật List Comprehension thay thế deepcopy và cơ chế Transposition Table (Cache) để giảm chi phí tính toán, tăng đáng kể FPS.
- **UI thân thiện**: Xem AI chơi trực tiếp với các nút điều chỉnh Tốc độ (Speed), Chế độ (Mode) ngay trong lúc chạy.

## 📂 Cấu trúc thư mục

Cấu trúc dự án được phân chia module rất rõ ràng để dễ bảo trì và nâng cấp:

```
AI-2048-AutoPlayer-main/
│
├── ai/                     # Module chứa thuật toán AI
│   ├── algorithms.py       # Cài đặt Expectimax và Move Ordering
│   └── heuristics.py       # Các hàm đánh giá bàn cờ
│
├── game/                   # Logic trò chơi 2048 thuần (Backend)
│   ├── board.py            # Khởi tạo và quản lý bàn cờ
│   └── logic.py            # Logic di chuyển, gộp số và tính điểm
│
├── ui/                     # Giao diện đồ họa (Frontend)
│   ├── colors.py           # Mã màu cho từng con số
│   └── display.py          # Vẽ lưới, dashboard và nút bấm
│
├── tests/                  # Các bài test cho logic game
│   └── test_logic.py
│
├── config.py               # Chứa các thông số hằng số (kích thước, tốc độ, màu)
├── main.py                 # File thực thi chính để khởi chạy Game & AI
├── requirements.txt        # Các thư viện phụ thuộc
└── README.md               # Tài liệu hướng dẫn này
```

## 🚀 Hướng dẫn cài đặt và khởi chạy

> [!NOTE]
> Phiên bản Python được khuyến nghị là **3.11.9**. Nếu bạn dùng các bản Python mới hơn (như 3.12+), thư viện `pygame` cũ có thể sẽ không hỗ trợ. Thay vào đó, dự án đang ưu tiên dùng `pygame-ce` (Community Edition).

**Bước 1: Cài đặt thư viện**
Mở terminal tại thư mục dự án và chạy lệnh sau:

```bash
pip install pygame-ce numpy
```

**Bước 2: Khởi chạy dự án**

```bash
python main.py
```

## 🎮 Cách sử dụng

- Nhấn nút **RUN AI** trên màn hình để xem máy tự động chơi.
- Bạn cũng có thể chọn chơi thủ công bằng các phím mũi tên (lúc AI đang tắt).
- Thay đổi tốc độ AI thông qua các tuỳ chọn: **Slow**, **Fast**, **Full**.
- Chuyển đổi giữa chế độ đi bừa (**Random**) và đi khôn (**Smart AI**).
- Nhấn **Q** để thoát và lưu lại kỷ lục (High Score).
