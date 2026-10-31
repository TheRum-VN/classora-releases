<div align="center">

# Lab Manager

**Nền tảng quản lý phòng thực hành, thiết bị và lịch sử dụng tập trung**

Tổ chức tài nguyên, theo dõi trạng thái và hỗ trợ vận hành phòng Lab trên một hệ thống thống nhất.

[![Last Commit](https://img.shields.io/github/last-commit/TheRum-VN/lab-manager?style=flat-square)](https://github.com/TheRum-VN/lab-manager/commits/main)
[![GitHub Issues](https://img.shields.io/github/issues/TheRum-VN/lab-manager?style=flat-square)](https://github.com/TheRum-VN/lab-manager/issues)
[![Contributors](https://img.shields.io/github/contributors/TheRum-VN/lab-manager?style=flat-square)](https://github.com/TheRum-VN/lab-manager/graphs/contributors)

[**Tổng quan**](#tong-quan) · [**Chức năng**](#chuc-nang) · [**Bắt đầu**](#bat-dau) · [**Đóng góp**](#dong-gop)

</div>

---

<a id="tong-quan"></a>
## 01. Tổng quan

**Lab Manager** là dự án phần mềm hướng tới việc số hóa và chuẩn hóa công tác quản lý phòng thực hành (Lab), từ theo dõi thiết bị, đăng ký sử dụng phòng cho tới phân quyền vận hành và tổng hợp báo cáo.

Hệ thống được định hướng phục vụ nhiều nhóm người dùng — quản trị viên, người phụ trách phòng Lab, giảng viên, kỹ thuật viên và thành viên — với thông tin được tổ chức tập trung nhằm giảm thao tác thủ công và cải thiện khả năng theo dõi tài nguyên.

### Mục tiêu

- **Minh bạch tài nguyên:** dễ dàng nắm được số lượng, tình trạng và lịch sử bảo trì thiết bị.
- **Tối ưu lịch sử dụng:** hỗ trợ đăng ký phòng, thiết bị và hạn chế xung đột lịch.
- **Rõ ràng trách nhiệm:** phân định vai trò và quyền truy cập theo từng nhóm người dùng.
- **Dữ liệu dễ khai thác:** tổng hợp thông tin sử dụng, theo dõi bảo trì và hỗ trợ lập báo cáo.

<a id="chuc-nang"></a>
## 02. Phạm vi chức năng

Các nhóm chức năng dưới đây được tổng hợp từ tài liệu mô tả dự án. **Tài liệu nguồn chưa phân biệt chức năng đã hoàn thành và chức năng đang phát triển.**

| Nhóm chức năng | Nội dung |
| --- | --- |
| **Thiết bị & vật tư** | Quản lý danh mục, số lượng, trạng thái hoạt động và lịch sử sửa chữa/bảo trì. |
| **Đặt lịch phòng Lab** | Tiếp nhận đăng ký sử dụng phòng, thiết bị, quản lý ca trực và kiểm tra trùng lịch. |
| **Người dùng & phân quyền** | Tổ chức tài khoản theo vai trò quản trị, quản lý Lab, giảng viên/kỹ thuật viên và thành viên. |
| **Dashboard & báo cáo** | Theo dõi tần suất sử dụng, tổng hợp dữ liệu và cung cấp cảnh báo liên quan đến bảo trì. |
| **Thông báo** | Hỗ trợ nhắc lịch và cập nhật trạng thái phê duyệt yêu cầu mượn thiết bị. |

### Các nhóm người dùng

| Vai trò | Phạm vi sử dụng dự kiến |
| --- | --- |
| **Administrator** | Quản trị hệ thống và chính sách phân quyền. |
| **Lab Manager** | Điều phối phòng, thiết bị, lịch sử dụng và công tác bảo trì. |
| **Giảng viên / Kỹ thuật viên** | Thực hiện công việc chuyên môn, đăng ký hoặc quản lý tài nguyên theo quyền được cấp. |
| **Sinh viên / Thành viên** | Gửi yêu cầu và theo dõi thông tin được phép truy cập. |

> Quyền chi tiết của từng vai trò cần được đối chiếu với cấu hình phân quyền trong mã nguồn.

## 03. Cấu trúc dự án

Tài liệu ban đầu mô tả mã nguồn ứng dụng trong thư mục `apps/` với bố cục tham chiếu như sau:

```text
lab-manager/
└── apps/
    ├── src/                # Mã nguồn ứng dụng
    ├── public/             # Tài nguyên tĩnh
    ├── config/             # Cấu hình hệ thống
    ├── .env.example        # Mẫu biến môi trường (nếu có)
    ├── package.json        # Dependencies và scripts (nếu sử dụng Node.js)
    └── README.md           # Tài liệu dự án
```

> Đây là cấu trúc được mô tả trong README gốc, **không phải danh sách đã kiểm chứng từ repository**. Khi phát hành, hãy cập nhật cây thư mục theo mã nguồn thực tế.

<a id="bat-dau"></a>
## 04. Bắt đầu

### 4.1. Lấy mã nguồn

Cài đặt [Git](https://git-scm.com/) và chạy:

```bash
git clone https://github.com/TheRum-VN/lab-manager.git
cd lab-manager
```

### 4.2. Xác định môi trường chạy

README gốc chưa cung cấp thông tin xác thực về framework, cơ sở dữ liệu, phiên bản runtime hay các script thực tế. **Hãy kiểm tra mã nguồn và tệp cấu hình trước khi cài đặt**, thay vì mặc định dự án sử dụng một công nghệ cụ thể.

Nếu ứng dụng được triển khai bằng Node.js và có `apps/package.json`, có thể bắt đầu bằng:

```bash
cd apps
npm install
npm run
```

`npm run` sẽ liệt kê các script đã khai báo. Nếu có script `dev`, khởi chạy bằng:

```bash
npm run dev
```

### 4.3. Cấu hình môi trường

Nếu repository có `.env.example`, tạo bản sao `.env` trước khi chạy ứng dụng.

**Windows (PowerShell):**

```powershell
Copy-Item .env.example .env
```

**macOS / Linux:**

```bash
cp .env.example .env
```

Mở `.env` và thiết lập đúng các biến mà ứng dụng yêu cầu. Giá trị cổng, chuỗi kết nối cơ sở dữ liệu và khóa xác thực phải được lấy từ cấu hình thực tế; README này không mặc định bất kỳ tên biến hoặc giá trị nào.

> **Bảo mật:** Không đưa `.env`, mật khẩu, access token hoặc khóa bí mật vào commit. Chỉ chia sẻ tệp mẫu chứa giá trị giả lập.

### 4.4. Kiểm tra sau khi khởi chạy

- Kiểm tra log để xác nhận ứng dụng khởi tạo thành công.
- Xác định địa chỉ truy cập và cổng từ cấu hình đang dùng.
- Kiểm tra kết nối tới các dịch vụ phụ thuộc (nếu có).
- Xác nhận các quyền và chức năng chính hoạt động như mong đợi.

## 05. Vận hành và bảo mật

Đối với hệ thống quản lý tài nguyên và tài khoản, nên tuân thủ các nguyên tắc sau khi triển khai:

- Cấp quyền theo nguyên tắc **ít quyền nhất**; không dùng chung tài khoản quản trị.
- Bảo vệ thông tin xác thực và cấu hình nhạy cảm bằng biến môi trường hoặc công cụ quản lý bí mật phù hợp.
- Thiết lập cơ chế sao lưu và phục hồi đối với dữ liệu vận hành quan trọng.
- Theo dõi lỗi, lịch sử thay đổi và kiểm tra truy cập định kỳ.
- Kiểm thử chức năng và phân quyền trước khi đưa bản cập nhật vào sử dụng chính thức.

Đây là **khuyến nghị triển khai**, không phải tuyên bố rằng các cơ chế trên đã có sẵn trong phiên bản hiện tại.

<a id="dong-gop"></a>
## 06. Đóng góp

Báo lỗi, đề xuất cải tiến và pull request đều được hoan nghênh.

1. Kiểm tra các [issue đang mở](https://github.com/TheRum-VN/lab-manager/issues) để tránh trùng lặp.
2. Fork repository và tạo nhánh riêng cho thay đổi.
3. Thực hiện thay đổi, tự kiểm tra và cập nhật tài liệu liên quan.
4. Tạo commit có thông điệp rõ ràng, sau đó mở pull request để mô tả mục tiêu, cách kiểm thử và ảnh hưởng của thay đổi.

```bash
git checkout -b feat/ten-tinh-nang
# Thực hiện và kiểm tra thay đổi
git add .
git commit -m "feat: mo ta ngan gon thay doi"
git push origin feat/ten-tinh-nang
```

Khi báo lỗi, vui lòng cung cấp cách tái hiện, kết quả mong đợi, kết quả thực tế và thông tin môi trường có liên quan. **Không đăng tải log chứa dữ liệu cá nhân hoặc thông tin bí mật.**

## 07. Hỗ trợ và liên hệ

- **Maintainer:** [TheRum-VN](https://github.com/TheRum-VN)
- **Repository:** [github.com/TheRum-VN/lab-manager](https://github.com/TheRum-VN/lab-manager)
- **Báo lỗi / đề xuất:** [GitHub Issues](https://github.com/TheRum-VN/lab-manager/issues)

---

<div align="center">

**Lab Manager** · Quản lý có hệ thống, vận hành hiệu quả.

</div>
