## 1. ### Hoàn thiện SRS bằng Heading Styles và Auto TOC
|Cấp|	Tiêu đề|	Style|
|---|---|---|
|1|	1. Giới thiệu dự án|	Heading 1|
|2|	1.1. Mục tiêu	|Heading 2|
|2	|1.2. Đối tượng sử dụng	|Heading 2|
|1	|2. Chức năng hệ thống	|Heading 1|
|2	|2.1. Quản lý mượn sách	|Heading 2|
|3	|2.1.1. Luồng mượn sách qua thẻ sinh viên	|Heading 3|
|2	|2.2. Quản lý trả sách	|Heading 2|
|1	|3. Yêu cầu bảo mật	|Heading 1|

Nội dung:
- Yêu cầu chức năng: Hệ thống cho phép lập phiếu mượn và quản lý trạng thái mượn/trả sách.
- Yêu cầu bảo mật: Hệ thống yêu cầu đăng nhập và phân quyền người dùng.
AUTO TOC: ```References → Table of Contents → Automatic Table``` → thêm nội dung → ```Update Field → Update entire table.```

## 2. Chuẩn hóa dữ liệu và AutoFilter

###  3 lỗi

|Lỗi	|Hàng	|Quy tắc|
|---|---|---|
|Merge ô	|1|	Không merge|
|Hàng trống	|5	|Không hàng trống|
|Tổng cộng trong vùng dữ liệu|	6	|Không dòng tổng|

### Bảng đúng
|MSSV	|Họ Tên	|Mã Sách	|Ngày Mượn	|Tình Trạng|
|---|---|---|---|---|
|SV001	|Nguyễn Văn An	|S001	|01/10/2026	|Đang mượn|
|SV002	|Trần Thị Bình	|S002	|03/10/2026	|Quá hạn|
|SV003	|Lê Văn Cường	|S003	|10/10/2026	|Đã trả|
|SV004	|Phạm Thu Hà	|S099	|12/10/2026	|Đang mượn|

- Record: 1 dòng, ví dụ SV001.

- Field: 1 cột, ví dụ MSSV.

- AutoFilter:``` Ctrl + Shift + L``` → lọc ```Tình Trạng = Quá hạn``` → còn SV002.

## 3. Nối dữ liệu bằng VLOOKUP
- hêm cột Tên Sách:
```
excel

=VLOOKUP(C2,DanhMucSach!$A$2:$C$4,2,FALSE)
```

- Lỗi:``` S099``` không tồn tại

Lý do: ```S099``` không tồn tại trong cột``` Mã Sách``` của bảng ```DanhMucSach```, nên VLOOKUP không tìm được bản ghi tương ứng.

- Dùng:
```
Excel

=IFERROR(VLOOKUP(C2,DanhMucSach!$A$2:$C$4,2,FALSE),"Không tìm thấy sách")
```

## 4. Slide
Assertion Title:  
“4 phiếu mượn đã được chuẩn hóa, nhưng phát hiện 1 mã sách không hợp lệ.”

Nổi bật:
4 phiếu → 2 đang mượn, 1 quá hạn, 1 đã trả.

Biểu đồ: Donut – phù hợp để thể hiện tỷ lệ các tình trạng.

Rule 10/20/30:  
- 1 slide / 10 slide = 10%
- Thời gian: ~2 phút
- Cỡ chữ: ≥ 30 pt