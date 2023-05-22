# ProductionMove
## Thành viên nhóm
- 20020216: Phan Công Thành
- 20020474: Nguyễn Việt Thắng

## Công nghệ sử dụng
- ReactJS 18
- ASP.Net Core 7
- Entity framework 7
- MySQL 8.0.31

## Cách xây dựng và chạy ứng dụng
1. Tải code
2. Build ứng dụng: Trên windows chạy file build.windows.bat
3. Cấu hình môi trường
- Thư mục sau build: /build
- Cấu hình lại các tham số trong file: build/appsettings.Development.json (build/appsettings.Production.json với trường hợp ở môi trường Production)
- "UseInMemoryDatabase": false Cấu hình sử dụng MySQL Database (Để true nếu muốn chạy database trên Memory trong trường hợp MySQL có vấn đề)
- “DbContextMySQL”: “...” Kết nối tới MySQL database
- "SecurityKey": “...” Mã bảo mật để sinh token ở backend
4. Chạy ứng dụng: Trên windows chạy file run.development.windows.bat (WebAPI.exe/WebAPI.dll trong thư mục build với trường hợp ở môi trường Production)

## Chức năng 

Vai trò của các bên tham gia như sau:
### Ban điều hành 

- Quản lý danh mục dòng sản phẩm.
- Cấp tài khoản và quản lý danh mục các cơ sở sản xuất, đại lý phân phối và trung tâm bảo hành.
- Theo dõi và xem thống kê sản phẩm trên toàn quốc, theo trạng thái và theo cơ sở sản xuất, đại lý phân phối và trung tâm bảo hành.

### Cơ sở sản xuất
- Nhập các lô sản phẩm mới vừa sản xuất vào kho.
- Xuất sản phẩm cho đại lý.
- Nhận các sản phẩm lỗi về từ các trung tâm bảo hành.
- Thống kê và báo cáo số liệu sản phẩm theo từng loại (trạng thái), theo tháng, quý, năm.
- Thống kê và phân tích số lượng sản phẩm bán ra hàng tháng, quý, năm.
- Thống kê tỉ lệ sản phẩm bị lỗi theo dòng sản phẩm, cơ sở sản xuất, đại lý phân phối.

### Đại lý phân phối
- Nhập sản phẩm mới về từ cơ sở sản xuất. Sản phẩm nhập về được lưu tại kho (riêng, nội bộ) của đại lý.
- Bán sản phẩm cho khách hàng
- Nhận lại sản phẩm cần bảo hành và chuyển đến trung tâm bảo hành.
- Nhận lại sản phẩm từ trung tâm bảo hành để trả cho khách hàng.
- Nếu sản phẩm bảo hành lỗi không thể sửa chữa thì trung tâm bảo hành báo cho đại lý rồi đại lý chuyển sản phẩm về cơ sở sản xuất, đại lý cũng có nhiệm vụ báo cho khách hàng và bàn giao sản phẩm mới thay thế cho khách hàng.
- Trường hợp cần triệu hồi, sản phẩm triệu hồi được xử lý như sản phẩm bảo hành. Điểm khác so với bảo hành là đại lý phải chủ động rà soát những sản phẩm cần triệu hồi và thông báo cho khách hàng.
- Thống kê và báo cáo số liệu sản phẩm theo từng loại (trạng thái liên), theo tháng, quý, năm.
- Thống kê và phân tích số lượng sản phẩm bán ra hàng tháng, quý, năm.

### Trung tâm bảo hành
- Nhận các sản phẩm bảo hành hoặc triệu hồi từ đại lý.
- Trả sản phẩm đã sửa chữa xong cho đại lý.
- Chuyển sản phẩm bảo hành lỗi không thể sửa chữa về cơ sở sản xuất.
- Thống kê và báo cáo số liệu sản phẩm theo từng loại (trạng thái), theo tháng, quý, năm. 