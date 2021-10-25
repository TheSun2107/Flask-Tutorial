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
#### Đầu tiên hãy cài đặt Python nhé: 
https://www.python.org/downloads/

Phiên bản python mình sử dụng để làm phần này: Python 3.9.7

#### Khởi tạo thư mục chính:
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

### Khởi tạo thư mục chứa ứng dụng

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

### Khởi chạy ứng dụng lần đầu tiên:
Nếu như các bài hướng dẫn khác, họ tạo trực tiếp file _app.py_ ngay bên ngoài thư mục chính do đó chỉ cần chạy _flask run_ theo mặc định flask sẽ tìm được _app_ và khởi tạo nó. Tuy nhiên, phần này ta cần phải chỉ định cho Flask biết tìm _app_ ở đâu:
```
(venv) $ \flask-tutorial> set FLASK_APP=flaskr
(venv) $ \flask-tutorial> set FLASK_ENV=development
(venv) $ \flask-tutorial> flask run
```

Đây là hướng dẫn trực tiếp từ tutorial của flask tuy nhiên nếu chạy không được thì hãy sử dụng:
```
(venv) $ \flask-tutorial> $env:FLASK_APP = "flaskr"
(venv) $ \flask-tutorial> $env:FLASK_ENV = "development"
(venv) $ \flask-tutorial> flask run
```

Bạn sẽ thấy một thống báo từ terminal tương tự:
```
* Serving Flask app "flaskr"
* Environment: development
* Debug mode: on
* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
* Restarting with stat
* Debugger is active!
* Debugger PIN: 855-212-761
```
Mở chrome và gõ vào địa chỉ : http://127.0.0.1:5000/ bạn sẽ thấy dòng chữ "Hello, World!"

<a name="Sudungcosodulieu"></a>
### 3. Sử dụng cơ sở dữ liệu
Ứng dụng sẽ sử dụng SQLite để lưu trữ người dùng(user) và bài đăng(post). SQLite tiện lợi vì nó được tích hợp sẵn trong Python. Tuy nhiên nó sẽ chậm một chút nếu các yêu cầu ghi vào cơ sở dữ liệu xảy ra đồng thời. Với ứng dụng nhỏ sẽ không nhận ra điều này tuy nhiên khi ứng dụng trở nên lớn hơn, bạn sẽ muốn chuyển qua một cơ sở dữ liệu khác.

#### Kết nối với cơ sở dữ liệu
Điều đầu tiên khi làm việc với SQLite và các cơ sở dữ liệu khác đó là tạo kết nối với nó. Mọi truy vấn, thao tác đều được thực hiện bằng kết nối và nó sẽ được đóng sau khi kết thúc công việc.
Trong các ứng dụng web, các kết nối này thường gắn với yêu cầu(request). Nó được tạo tại một số thời điểm khi xử lý một yêu cầu và đóng trước khi phản hổi được gửi đi.

```flaskr/db.py```
```
import sqlite3

import click
from flask import current_app, g
from flask.cli import with_appcontext


def get_db():
    if 'db' not in g:
        g.db = sqlite3.connect(
            current_app.config['DATABASE'],
            detect_types=sqlite3.PARSE_DECLTYPES
        )
        g.db.row_factory = sqlite3.Row

    return g.db


def close_db(e=None):
    db = g.pop('db', None)

    if db is not None:
        db.close()
```
- ```g``` là một đối tượng đặc biệt duy nhất cho mỗi yêu cầu. Nó được sử dụng để lưu trữ dữ liệu có thể được truy cập bởi nhiều chức năng trong quá trình yêu cầu. Kết nối được lưu trữ và sử dụng lại thay vì tạo kết nối mới nếu get_db được gọi lần thứ hai trong cùng một yêu cầu.
- ```current_app```là một đối tượng đặc biệt khác trỏ đến ứng dụng Flask xử lý yêu cầu. Vì bạn đã sử dụng một nhà máy ứng dụng, nên không có đối tượng ứng dụng nào để viết phần còn lại mã của bạn. _get_db_ sẽ được gọi khi ứng dụng đã được tạo và đang xử lý một yêu cầu, do đó, _current_app_ có thể được sử dụng.
- ```sqlite3.connect()``` thiết lập kết nối đến tệp được chỉ vào bởi khóa cấu hình _DATABASE_. Tệp này không cần phải tồn tại và sẽ không tồn tại cho đến khi bạn khởi chạy cơ sở dữ liệu sau đó.
- ```sqlite3.Row``` cho kết nối trả về các hàng hoạt động giống như các dòng. Điều này cho phép truy cập các cột theo tên.
- ```close_db``` kiểm tra xem kết nối đã được tạo chưa bằng cách kiểm tra xem _g.db_ đã được đặt chưa. Nếu kết nối tồn tại, nó bị đóng. Sâu hơn nữa, bạn sẽ thông báo cho ứng dụng của mình về hàm _close_db_ trong nhà máy ứng dụng để nó được gọi sau mỗi yêu cầu.

#### Tạo các bảng

Trong SQLite, dữ liệu được lưu trữ trong các bảng và cột. Chúng cần được tạo trước khi bạn có thể lưu trữ và truy xuất dữ liệu. Flaskr sẽ lưu trữ người dùng trong bảng _user_ và bài đăng trong bảng _post_. Tạo tệp bằng các lệnh SQL cần thiết để tạo bảng trống:

```flaskr/schema.sql```
```
DROP TABLE IF EXISTS user;
DROP TABLE IF EXISTS post;

CREATE TABLE user (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  username TEXT UNIQUE NOT NULL,
  password TEXT NOT NULL
);

CREATE TABLE post (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  author_id INTEGER NOT NULL,
  created TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  title TEXT NOT NULL,
  body TEXT NOT NULL,
  FOREIGN KEY (author_id) REFERENCES user (id)
);
```
Thêm hàm cho python trong _db.py_ để thực thi lệnh SQL trên:

```flaskr/db.py```

```
def init_db():
    db = get_db()

    with current_app.open_resource('schema.sql') as f:
        db.executescript(f.read().decode('utf8'))


@click.command('init-db')
@with_appcontext
def init_db_command():
    """Clear the existing data and create new tables."""
    init_db()
    click.echo('Initialized the database.')
```
- ```open_resource()```mở một tệp liên quan đến gói flaskr, nó rất hữu ích vì bạn sẽ không nhất thiết phải biết vị trí đó khi triển khai ứng dụng sau này. _get_db_ trả về một kết nối cơ sở dữ liệu, được sử dụng để thực thi các lệnh được đọc từ tệp.
- ```click.command()``` định nghĩa một dòng lệnh có tên _init-db_ gọi hàm _init_db_ và hiển thị thông báo thành công cho người dùng.
- 
#### Đăng ký với ứng dụng
Các hàm _close_db_ và _init_db_command_ cần được đăng ký với phiên bản ứng dụng; nếu không, chúng sẽ không được ứng dụng sử dụng. Tuy nhiên, vì bạn đang sử dụng một hàm gốc nên phiên bản đó không khả dụng khi viết các hàm. Thay vào đó, hãy viết một hàm nhận đơn đăng ký và thực hiện đăng ký.

```flaskr/db.py```

```
def init_app(app):
    app.teardown_appcontext(close_db)
    app.cli.add_command(init_db_command)
```
- ```app.teardown_appcontext()``` yêu cầu Flask gọi hàm đó khi dọn dẹp sau khi trả lại phản hồi.
- ```app.cli.add_command()``` thêm một lệnh mới có thể được gọi bằng lệnh flask.

Khai báo init_app với Flask:

```flaskr/__init__.py```
```
def create_app():
    ....

    from . import db
    db.init_app(app)

    return app
 ```
 #### Khởi tạo tệp cơ sở dữ liệu
 
 Bây giờ _init-db_ đã được đăng kí với ứng dụng, nó có thể được gọi bằng lệnh flask.
 
 _Note:_
 Nếu bạn đang chạy server từ phần trước thì hãy dừng nó lại và sử dụng lệnh bên dưới hoặc chạy nó trong một terminal mới. Nếu bây giờ bạn mới bắt đầu chạy server hãy xem lại phần khai báo _FLASK_APP_ và _FLASK_ENV_ để có thể chạy server.
 
 Chạy _init-db_:
 ```
 (venv) $ \flask-tutorial> flask init-db
 Initialized the database.
 ```
 Bây giờ sẽ có một tệp _flaskr.sqlite_ trong thư mục _instance_.
 
<a name="Banthietke"></a>
<a name="Mau"></a>
<a name="Filestinh"></a>
