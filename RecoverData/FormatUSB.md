# Format USB bị lỗi sau khi tạo Boot USB (DiskPart)

## 1. Mở CMD với quyền Administrator

```cmd
diskpart
```

## 2. Liệt kê các ổ đĩa

```cmd
list disk
```

Ví dụ:

```text
Disk 0    953 GB   (Ổ cứng máy)
Disk 1     57 GB   (USB)
```

## 3. Chọn USB

```cmd
select disk 1
```

## 4. Kiểm tra trạng thái Read-only

```cmd
attributes disk
```

Nếu:

```text
Read-only : Yes
```

thì chạy:

```cmd
attributes disk clear readonly
```

## 5. Xóa toàn bộ bảng phân vùng

⚠️ Bước này xóa sạch dữ liệu trên USB.

```cmd
clean
```

Kết quả mong đợi:

```text
DiskPart succeeded in cleaning the disk.
```

## 6. Tạo phân vùng mới

```cmd
create partition primary
```

Kết quả mong đợi:

```text
DiskPart succeeded in creating the specified partition.
```

## 7. Chọn phân vùng vừa tạo

```cmd
select partition 1
```

## 8. Format USB

```cmd
format fs=exfat quick
```

Hoặc:

```cmd
format fs=fat32 quick
```

Hoặc:

```cmd
format fs=ntfs quick
```

## 9. Gán ký tự ổ đĩa

```cmd
assign
```

Kết quả mong đợi:

```text
DiskPart successfully assigned the drive letter or mount point.
```

## 10. Thoát DiskPart

```cmd
exit
```

---

## Full lệnh nhanh

```cmd
diskpart
list disk
select disk 1
clean
create partition primary
select partition 1
format fs=exfat quick
assign
exit
```

## Khi nào dùng cách này?

- USB sau khi tạo boot bằng Rufus/Ventoy không hiện đúng dung lượng.
- USB xuất hiện nhiều phân vùng lạ.
- Explorer báo dung lượng sai.
- Muốn đưa USB về trạng thái ban đầu.
- Chấp nhận mất toàn bộ dữ liệu trên USB.
