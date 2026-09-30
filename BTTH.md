**Phần 1 — Xác định Entity/Attribute/Khóa chính:**

| **Entity** | **Attribute cần lưu**                 | **Khóa chính (PK)** |
| ---------------- | --------------------------------------------- | --------------------------- |
| LOP_TAP          | MaLop, TenLop, HocPhi                         | MaLop                       |
| HOI_VIEN         | MaHoiVien, TenHoiVen, NgayThamGia,SoDienThoai | MaHoiVien                   |
| HUAN_LUYEN_VIEN  | MaHuanLuyenVien, TenHuanLuyenVien, KinhNghiem | MaHuanLuyenVien             |

**Phần 2 — Xác định quan hệ và Khóa ngoại:**

| **Cặp Entity**      | **Loại quan hệ** | **Khóa ngoại đặt ở Entity nào (nếu N-N** **thì nêu tên bảng trung gian)**    |
| -------------------------- | ------------------------ | --------------------------------------------------------------------------------------------------- |
| HUAN_LUYEN_VIEN — LOP_TAP | 1-N                      | LOP_TAP                                                                                             |
| HOI_VIEN — LOP_TAP        | N-N                      | Đặt ở bảng trung gian DANG_KY với 2 khóa ngoại liên kết với khóa chính của mỗi bảng |

**Phần 3 — Xử lý 2 lỗi chuẩn hóa ở mục 4:**

| **Lỗi ở mục 4**              | **Vi phạm dạng chuẩn nào** | **Tách thành bảng nào, gồm cột gì**                 |
| ------------------------------------- | ------------------------------------ | ---------------------------------------------------------------- |
| TenLop, HocPhi chỉ phụ thuộc MaLop | *2NF*                              | Tách thành bảngLOP_TAP (MaLop, TenLop, HocPhi)                |
| SoDienThoai phụ thuộc TenHoiVien    | 3NF                                  | Tách thành bảng HOI_VIEN (MaHoiVien, TenHoiVien, SoDienThoai) |
