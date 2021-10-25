# Flask-Tutorial
Bài viết này được lấy từ trang chủ của flask: https://flask.palletsprojects.com/en/2.0.x/
### Mục lục

[I. Mở đầu](#Modau)
- [1. Lời giới thiệu](#Loigioithieu)
- [2. Kiến thức cần chuẩn bị](#Kienthuccanchuanbi)

[II. Cài đặt](#Caidat)

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

Flask không như Django, khi bạn khởi tạo một project từ Django, nó sẽ tạo cho bạn một cây thư mục sẵn và tối ưu nhất bao gồm các folders static, templates, các files routes, models,... Tuy nhiên Flask không như thế, bạn phải tạo ra tất cả các folders cũng như các files theo ý của bạn, đó vừa là cái ưu điểm vừa là cái nhược điểm. Điều này khiến cho các bạn mới bắt đầu với Flask khá hoang mang khi không biết đâu là một cây thư mục tối ưu nhất. Mình là một người đang tự học và tìm hiểu về Flask cũng đang bị như vậy, trước khi làm bài này mình đã tham khảo hàng tá bài viết về Flask trên internet, mỗi bài tạo một tên files khác nhau, một vị trí khác nhau khiến mình càng xem càng không hiểu. Mình quyết định tham khảo trực tiếp trên trang chủ của Flask và làm theo từng bước của nó đồng thời vietsub ra cho các bạn cùng đồng hành với mình(Xài gg dịch nhé).
<a name="Kienthuccanchuanbi"></a>
### 2. Kiến thức cần chuẩn bị
Để bắt đầu lập trình backend một cách thuận lợi nhất, chúng ta cẩn chuẩn bị cho mình các kiến thức cơ bản:
- Mạng máy tính, Hệ điều hành...
- Frontend: HTML, CSS, Javascript, Bootstrap.
- Ngôn ngữ backend(ở đây là Python)
- Mô hình MVC, WSGI, Jinja, SQL, Virtual environment.
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
Đầu tiên hãy cài đặt Python nhé: https://www.python.org/downloads/

Phiên bản python mình sử dụng để làm phần này: Python 3.9.7

Khởi tạo thư mục chính:
```
$ mkdir flask-tutorial
$ cd flask-tutorial
```
Tiếp theo chúng ta cài đặt môi trường ảo(virtual environment) điều này khiến dự án của chúng ta tách biệt với HDH.

```
$ \flask-tutorial>py -m venv venv
```
Sau khi khởi tạo môi trường ảo thành công bạn sẽ có môi trường ảo trong thư mục venv. Đến đây cần kích hoạt môi trường ảo này:

```
$ flask-tutorial> cd venv\Scripts\
$ flask-tutorial\venv\Scripts> activate
```
Sau khi activate xong thì dấu nhắc lệnh của chúng ta sẽ hiểu thị như sau:
```
(venv) $ flask-tutorial\venv\Scripts>
```
Dưới đây là cây thư mục cuối cùng của dự án, chúng ta sẽ khởi tạo từ từ từng file một nhé:
```
flask-tutorial/
|-- flaskr/
|   |-- static/
|   |   |-- style.css
|   |-- templates/
|   |   |-- auth/
|   |   |     login.html
|   |   |     register.html
|   |   |-- blog/
|   |   |     create.html
|   |   |     index.html
|   |   |     update.html
|   |   |-- base.html
|   |-- __init__.py
|   |-- auth.py
|   |-- blog.py
|   |-- db.py
|   |-- schema.sql
|-- instance/
|-- tests/
|-- venv/
|-- setup.py
|-- MANIFEST.in
 ```
 - **flaskr/**, một gói chứa code ứng dụng và các tệp.
 - **tests/**, một thư mục chứa các module kiểm tra.
 - **venv/**, một môi trường ảo Python nơi Flask và các gói phụ thuộc được cài đặt độc lập so với hdh.
 - Bất kì tệp nào khác bạn thêm vào trong tương lai.
<a name="Thietlapungdung"></a>
### 2. Thiết lập ứng dụng
Như mình đã giới thiệu cấu trúc này dựa trên tutorial chính thức của Flask, nên mình nghĩ hãy đi theo cách khởi tạo ứng dụng của Flask để đạt được sự tối ưu nhất cho ứng dụng.

Khởi tạo thư mục chứa ứng dụng:

```
$ \flask-tutorial> mkdir flaskr
$ \flask-tutorial> cd flaskr
```

```flaskr/__init__.py```

```
import os

from flask import Flask

def create_app(test_config=None):
    # create and configure the app
    app = Flask(__name__, instance_relative_config=True)
    app.config.from_mapping(
        SECRET_KEY='dev',
        DATABASE=os.path.join(app.instance_path, 'flaskr.sqlite'),
    )

    if test_config is None:
        # load the instance config, if it exists, when not testing
        app.config.from_pyfile('config.py', silent=True)
    else:
        # load the test config if passed in
        app.config.from_mapping(test_config)

    # ensure the instance folder exists
    try:
        os.makedirs(app.instance_path)
    except OSError:
        pass

    # a simple page that says hello
    @app.route('/hello')
    def hello():
        return 'Hello, World!'

    return app
```
- ```create_app``` là chức năng của factory application.

- ```app = Flask(__name__, instance_relative_config=True)``` khởi tạo phiên bản Flask.

- ```_name__``` là tên module python hiện tại, nó giúp  ứng dụng biết được vị trí của nó để thiết lập đường dẫn. Phần này muốn hiểu rõ hơn thì tham khảo thêm phần blueprint nhé.

- ```instance_relative_config=True``` giúp ứng dụng biết rằng các tệp cấu hình có liên quan đến thư mục flaskr nhưng nằm ở bên ngoài thư mục flaskr và có thể chứa dữ liệu cục bộ.

- ```app.config.from_mapping``` thiết đặt một số cấu hình mặc định cho ứng dụng.

- ```SECRET_KEY``` là một tiện ích mở rộng giúp Flask bảo mật dữ liệu( có thể khai báo một giá trị ngẫu nhiên cho nó)

- ```DATABASE``` là đường dẫn tới cơ sở dữ liệu SQLite, nó nằm ở _app.instance_path_, mặc định nó tạo ra một folder _instance_ trong _folder flask-tutorial_.

- ```app.config.from_pyfile``` ghi đè cấu hình mặc định với các giá trị trong file _config.py_(Điều này để cấu hình các giá trị thực cho ứng dụng)

- ```test_config``` cũng để ghi đè cấu hình để thực hiện trong các bài kiểm tra.

- ```os.makedirs()``` đảm bảo rằng _app.instance_path_ tồn tại. Flask không tự động tạo thư mục cá thế, thư mục cá thể cần bạn tạo ra để nó có thể khởi tạo SQLite ở đó.

<a name="Sudungcosodulieu"></a>
<a name="Banthietke"></a>
<a name="Mau"></a>
<a name="Filestinh"></a>
