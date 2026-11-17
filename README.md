# LAB 2 – MÃ HÓA ĐỐI XỨNG HIỆN ĐẠI

## 1. Thông tin sinh viên

- **Họ và tên:** Cao Xuân Mai
- **MSSV:** 1150070028
- **Lớp:** 11_TTMT
- **Học phần:** An toàn và Bảo mật Thông tin

## 2. Giới thiệu

Chương trình được xây dựng bằng Java Swing trên Apache NetBeans, sử dụng Maven để quản lý thư viện. Nội dung thực hiện các thuật toán mã hóa đối xứng và kết nối SQL Server để quản lý tài khoản, đăng nhập và lưu lịch sử thao tác.

Các chức năng chính:

- DES
- TripleDES
- AES-256-GCM kết hợp đăng ký, đăng nhập và SQL Server
- RC4
- Twofish
- AES-CTR
- AES-256-CBC bằng Python (giao diện Tkinter)

## 3. Công nghệ sử dụng

- Java JDK 17 hoặc 21
- Apache NetBeans 20 trở lên
- Maven
- Microsoft SQL Server Express và SQL Server Management Studio (SSMS)
- Python 3.10 trở lên
- Thư viện Python `cryptography`

## 4. Hướng dẫn chạy chương trình

### 4.1. Chuẩn bị môi trường

Cài đặt các phần mềm cần thiết:

1. JDK 17 hoặc JDK 21.
2. Apache NetBeans 20 trở lên.
3. SQL Server Express và SSMS.
4. Python 3.10 trở lên (dùng cho bài AES-CBC).

Kiểm tra phiên bản Java và Python bằng Command Prompt:

```bash
java -version
py --version
```

### 4.2. Chạy chương trình Java trên NetBeans

**Bước 1:** Giải nén project và mở Apache NetBeans.

**Bước 2:** Chọn `File → Open Project`, sau đó chọn thư mục `LAB2_MaHoaHienDai`.

**Bước 3:** Chờ Maven tải các thư viện cần thiết. Project sử dụng các thư viện được khai báo trong `pom.xml`.

**Bước 4:** Nhấp chuột phải vào project, chọn **Clean and Build** để biên dịch chương trình.

**Bước 5:** Sau khi hiển thị `BUILD SUCCESS`, nhấn `F6` hoặc chọn **Run Project** để chạy chương trình.

Cửa sổ chính `frm_Menu` sẽ xuất hiện. Chọn chức năng tương ứng để sử dụng.

### 4.3. Cấu hình SQL Server

Để sử dụng chức năng đăng ký, đăng nhập AES và xem lịch sử, cần chuẩn bị SQL Server.

**Bước 1:** Khởi động SQL Server và mở SSMS.

**Bước 2:** Mở và chạy lần lượt các tệp SQL theo thứ tự:

1. `01_Tao_Database_Tables.sql`: tạo database `LAB2_MaHoaHienDai` và các bảng dữ liệu.
2. `02_Tao_Tai_Khoan_SQL.sql`: tạo tài khoản kết nối SQL Server và phân quyền.
3. `03_Kiem_Tra_Du_Lieu.sql`: kiểm tra dữ liệu tài khoản và lịch sử thao tác sau khi sử dụng chương trình.

**Bước 3:** Trong chương trình, chọn **Kết nối SQL Server** và nhập thông tin kết nối phù hợp với máy đang sử dụng:

| Thông tin | Giá trị mặc định |
|---|---|
| Server | `127.0.0.1` |
| Port | `14333` |
| Database | `LAB2_MaHoaHienDai` |
| User | `lab2_user` |
| Password | Mật khẩu đã cấu hình trong SQL Server |

**Bước 4:** Nhấn **Test Connection**. Nếu kết nối thành công, có thể sử dụng chức năng AES, đăng ký, đăng nhập và xem lịch sử.

### 4.4. Chạy chương trình AES-CBC bằng Python

Phần AES-CBC là chương trình riêng, sử dụng Python và giao diện Tkinter.

**Bước 1:** Mở Command Prompt và cài đặt thư viện:

```bash
py -m pip install cryptography
```

**Bước 2:** Di chuyển đến thư mục chứa tệp `aes_cbc_gui.py`.

Ví dụ:

```bash
cd C:\BaoMat\LAB2_Python
```

**Bước 3:** Chạy kiểm thử:

```bash
py aes_cbc_gui.py --self-test
```

Nếu hiển thị:

```text
SELF-TEST OK
```

thì phần kiểm thử đã hoàn thành.

**Bước 4:** Khởi động giao diện:

```bash
py aes_cbc_gui.py
```

Sau khi cửa sổ chương trình xuất hiện, chọn Generate Key và Generate IV để tạo khóa, IV mới; sau đó nhập văn bản và thực hiện Encrypt hoặc Decrypt.

## 5. Nội dung kiểm thử

| Chức năng | Kết quả kiểm thử |
|---|---|
| DES | Mã hóa và giải mã đúng; mỗi lần mã hóa tạo bản mã khác nhau do IV ngẫu nhiên |
| TripleDES | Mã hóa, giải mã đúng; kiểm tra khóa không hợp lệ |
| AES-256-GCM | Đăng ký, đăng nhập, tạo Ticket và mã hóa/giải mã |
| SQL Server | Lưu thông tin tài khoản và lịch sử thao tác |
| RC4 | Kiểm tra kết quả bản mã HEX |
| Twofish | Mã hóa, giải mã và lưu/mở tệp |
| AES-CTR | Mã hóa, giải mã và kiểm tra độ dài bản mã |
| AES-CBC Python | Chạy self-test và kiểm tra mã hóa/giải mã văn bản dài |

## 6. Lưu ý

- SQL Server phải được khởi động và cấu hình đúng cổng trước khi sử dụng chức năng liên quan đến cơ sở dữ liệu.
- Không đưa mật khẩu SQL Server thực tế vào mã nguồn hoặc công khai trong quá trình nộp bài.
- RC4 là thuật toán cũ, chỉ sử dụng trong phạm vi thực hành và học tập.

## 7. Kết luận

Bài thực hành đã xây dựng chương trình giao diện Java Swing tích hợp các thuật toán mã hóa đối xứng, kết nối SQL Server để quản lý tài khoản và lịch sử thao tác, đồng thời triển khai thêm chương trình AES-CBC bằng Python. Các chức năng được kiểm tra theo yêu cầu của tài liệu hướng dẫn LAB 2.