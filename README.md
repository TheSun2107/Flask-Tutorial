# Flask-Tutorial
Bài viết này được lấy từ trang chủ của flask: https://flask.palletsprojects.com/en/2.0.x/
### Mục lục

[I. Mở đầu](#Modau)
- [1. Lời giới thiệu](#Loigioithieu)
- [2. Kiến thức cần chuẩn bị](#Kienthuccanchuanbi)

[II. Cài đặt](#Caidat)
- [1. Python](#Python)
- [2. Sự phụ thuộc](#Suphuthuoc)
- [3. Môi trường ảo](#Moitruongao)
- [4. Cài đặt Flask](CaidatFlask)

[III. Bắt đầu nhanh](#Batdaunhanh)

[IV. Hướng dẫn](#Huongdan)
- [1. Bố cục dự án](#Bocucduan)
- [2. Thiết lập ứng dụng](#Thietlapungdung)
    - [2.1. ]
    - [2.2. ]
- [3. Sử dụng cơ sở dữ liệu](#Sudungcosodulieu)
- [4. Bản thiết kế](#Banthietke)
- [5. Mẫu](#Mau)
- [6. Files tĩnh](#Filestinh)
- [7. Bản thiết kế trang cá nhân](#Banthietketrangcanhan)
- [8. Cấu hình để cài đặt](#Cauhinhdecaidat)
- [9. Kiểm tra](#Kiemtra)
- [10. Triển khai](#Trienkhai)
- [11. Phát triển](#Phatrien)

[V. Mẫu](#Mau)
[VI. Thử nghiệm](#Thunghiem)
[VII. Xử lý lỗi](#Xulyloi)
[VIII. Gỡ lỗi](#Goloi)
[IX. Nhật ký](#Nhatky)
[X. Xử lý cấu hình](#Xulycauhinh)


============================================
<a name="Modau"></a>
## I. Mở đầu
<a name="Loigioithieu"></a>
### 1. Lời giới thiệu
Theo mức độ phổ biến, các ứng dụng Web trên nền tảng Django nhiều hơn là Flask. Tuy vậy, điều đó không đưa đến kết luận là Django tốt hơn Flask. Nếu muốn xây dựng một ứng dụng với thời gian ngắn nhất, Django dĩ nhiên là một lựa chọn tốt. Nhưng xét về tính linh hoạt, Django lại không bằng Flask. Với Django, các thành phần cơ bản của ứng dụng đã được định nghĩa sẵn, vì vậy khó tùy biến hơn. Ngược lại, Flask cho phép người lập trình lựa chọn và ghép nối các thành phần theo ý mình. Vì vậy, Flask là lựa chọn tốt cho những ai muốn tìm hiểu sâu về các Web framework và muốn có mức độ tùy biến cao.
<a name="Kienthuccanchuanbi"></a>
### 2. Kiến thức cần chuẩn bị
Để bắt đầu lập trình backend một cách thuận lợi nhất, chúng ta cẩn chuẩn bị cho mình các kiến thức cơ bản:
- Mạng máy tính, Hệ điều hành...
- Frontend: HTML, CSS, Javascript, Bootstrap.
- Ngôn ngữ backend(ở đây là Python)
- Mô hình MVC, WSGI, Jinja, SQL.
<a name="Caidat"></a>
## II. Cài đặt
Phần này chúng ta sẽ sử dụng luôn phần "hướng dẫn tạo dự án đầu tiên" trong mục IV.
<a name="Batdaunhanh"></a>
## III. Bắt đầu nhanh
<a name="Huongdan"></a>
Phần này Flask hướng dẫn sử dụng các thành phần chính khi xây dựng ứng dụng.
Các bạn có thể xem trực tiếp trên trang chủ Flask.
## IV. Hướng dẫn
Trong phần hướng dẫn này mình sử dụng HDH Windows 10 và Visual Studio Code(1.61.2)
<a name="Bocucduan"></a>
### 1. Bố cục dự án
Khởi tạo thư mục chính:
$ mkdir flask-tutorial

Dưới đây là cây thư mục của dự án:
'''
/flask-tutorial
├── flaskr/
│   ├── __init__.py
│   ├── db.py
│   ├── schema.sql
│   ├── auth.py
│   ├── blog.py
│   ├── templates/
│   │   ├── base.html
│   │   ├── auth/
│   │   │   ├── login.html
│   │   │   └── register.html
│   │   └── blog/
│   │       ├── create.html
│   │       ├── index.html
│   │       └── update.html
│   └── static/
│       └── style.css
├── tests/
│   ├── conftest.py
│   ├── data.sql
│   ├── test_factory.py
│   ├── test_db.py
│   ├── test_auth.py
│   └── test_blog.py
├── venv/
├── setup.py
└── MANIFEST.in
'''
<a name="Thietlapungdung"></a>
<a name="Sudungcosodulieu"></a>
<a name="Banthietke"></a>
<a name="Mau"></a>
<a name="Filestinh"></a>
