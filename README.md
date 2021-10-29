# Flask-Tutorial
Bài viết này được dịch dựa trên <a href="https://flask.palletsprojects.com/">trang chủ</a> của Flask.
### Mục lục

[I. Mở đầu](#Modau)

[1. Lời giới thiệu](#Loigioithieu)

[2. Kiến thức cần chuẩn bị](#Kienthuccanchuanbi)

[II. Cài đặt](#Caidat)

[III. Bắt đầu nhanh](#Batdaunhanh)

[IV. Hướng dẫn](#tutorial)

[1. Bố cục dự án](#projectlayout)
- [1.1 Cài đặt](#install)
- [1.2 Tạo thư mục dự án](#createproject)

[2. Bắt đầu](#start)
- [2.1 Tạo ứng dụng](#createapp)
- [2.2 Chạy ứng dụng](#runapp)

[3. Database - cơ sở dữ liệu](#usedatabase)
- [3.1 Kết nối cơ sở dữ liệu](#connectdatabase)
- [3.2 Tạo bảng](#createtable)
- [3.3 Đăng ký cơ sở dữ liệu với ứng dụng](#registerdatabase)
- [3.4 Tạo nơi lưu trữ cho cơ sở dữ liệu](#createfiledatabase)

[4. Blueprint - Bản thiết kế](#blueprint)
- [4.1 Đăng ký](#register)
- [4.2 Đăng nhập](#login)
- [4.3 Xác thực](#authentication)
 
[5. Templates - Mẫu](#templates)
- [5.1 Mẫu chung](#basetemplate)
- [5.2 Mẫu trang đăng ký](#registertemplate)
- [5.3 Mẫu trang đăng nhập](#logintemplate)
- [5.4 Mẫu trang chỉ mục](#indextemplate)
- [5.5 Mẫu tạo bài đăng](#createtemplate)
- [5.6 Mẫu cập nhật](#updatetemplate)
- [5.7 Mẫu xóa](#deletetemplate)
- [5.8 Nâng cấp giao diện](#updatetemplate)

[V. Project Installable - Cài đặt dự án](#projectinstallable)

[1. Describe - Mô tả dự án](#projectdescribe)
[2. Install - Cài đặt dự án](#projectinstall)

[VI. Test - Thử nghiệm](#test)

[1. Cài đặt thử nghiệm](#installtest)

[2. Thiết lập thử nghiệm](#setuptest)

- [2.1 Thử nghiệm nhà máy ứng dụng](#factorytest)
- [2.2 Thử nghiệm cơ sở dữ liệu](#databasetest)
- [2.3 Thử nghiệm xác thực](#authenicationtest)
- [2.4 Thử nghiệm blog](#blogtest)

[3. Chạy thử nghiệm](runtest)

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

Flask không như Django, khi bạn khởi tạo một project từ Django, nó sẽ tạo cho bạn một cấu trúc ứng dụng hoàn chỉnh và tối ưu nhất bao gồm các folders static, templates, các files routes, models,... Tuy nhiên Flask không như thế, bạn phải tạo ra tất cả các folders cũng như các files theo ý của bạn, đó vừa là ưu điểm vừa là nhược điểm. Điều này khiến cho các bạn mới bắt đầu với Flask khá hoang mang khi không biết đâu là một cấu trúc tốt nhất. Mình là một người đang tự học và tìm hiểu về Flask cũng đang bị như vậy, trước khi làm bài này mình đã tham khảo hàng tá bài viết về Flask trên internet, mỗi bài tạo một tên files khác nhau, một vị trí khác nhau khiến mình càng xem càng không hiểu. Mình quyết định tham khảo trực tiếp trên trang chủ của Flask và làm theo từng bước của nó đồng thời vietsub ra cho các bạn cùng đồng hành với mình(Xài gg dịch nhé).
<a name="Kienthuccanchuanbi"></a>
### 2. Kiến thức cần chuẩn bị
Để bắt đầu lập trình backend một cách thuận lợi nhất, chúng ta cẩn chuẩn bị cho mình các kiến thức cơ bản:
- Mạng máy tính, Hệ điều hành...
- Frontend: HTML, CSS, Javascript, Bootstrap.
- Ngôn ngữ backend(ở đây là Python)
- Mô hình MVC, WSGI, Jinja, SQL, Virtual environment.
<a name="Caidat"></a>
## II. Cài đặt
Phần này chúng ta sẽ sử dụng luôn phần IV.
<a name="Batdaunhanh"></a>
## III. Bắt đầu nhanh
Phần này Flask hướng dẫn sử dụng các thành phần chính khi xây dựng ứng dụng.
Các bạn có thể xem trực tiếp trên trang chủ Flask.
<a name="tutorial"></a>
## IV. Hướng dẫn
Trong hướng dẫn này mình sử dụng HDH Windows 10 và Visual Studio Code(1.61.2)
<a name="projectlayout"></a>
### 1. Bố cục dự án
<a name="install"></a>
#### 1.1 Cài đặt Python

Phiên bản python mình sử dụng: <a href="https://www.python.org/downloads/release/python-397/">Python 3.9.7</a>
<a name="createproject"></a>
#### 1.2 Tạo dự án:
```
$ mkdir flask-tutorial
$ cd flask-tutorial
```
Tiếp theo chúng ta cài đặt môi trường ảo(virtual environment) điều này khiến dự án của chúng ta tách biệt với HDH.

```
$ \flask-tutorial>py -m venv venv
```
Sau khi khởi tạo thành công bạn sẽ có môi trường ảo trong thư mục _venv_. Đến đây cần kích hoạt môi trường ảo này:

```
$ flask-tutorial> cd venv\Scripts\
$ flask-tutorial\venv\Scripts> activate
```
Sau khi _activate_ xong thì dấu nhắc lệnh của chúng ta sẽ hiểu thị như sau:
```
(venv) $ flask-tutorial\venv\Scripts>
```
Dưới đây là cây thư mục cuối cùng của dự án, chúng ta sẽ đi theo từng mục một nhé:
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
<a name="start"></a>
### 2. Bắt đầu
Như mình đã giới thiệu bài viết này là tutorial chính thức của Flask, nên hãy làm theo Flask để đạt được sự tối ưu nhất cho ứng dụng.
<a name="createapp"></a>
#### 2.1 Tạo ứng dụng

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
<a name="runapp"></a>
#### 2.2 Chạy ứng dụng lần đầu:
Các bài hướng dẫn khác, thường tạo trực tiếp file _app.py_ ngay bên ngoài thư mục chính do đó chỉ cần chạy _flask run_ theo mặc định flask sẽ tìm được _app_ và khởi tạo nó. Tuy nhiên, phần này ta cần phải chỉ định cho Flask biết tìm _app_ ở đâu:
```
(venv) $ \flask-tutorial> set FLASK_APP=flaskr
(venv) $ \flask-tutorial> set FLASK_ENV=development
(venv) $ \flask-tutorial> flask run
```

Tuy nhiên nếu không được(mình không biết vì sao luôn) thì hãy sử dụng:
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
Mở browser và nhập địa chỉ : http://127.0.0.1:5000/ bạn sẽ thấy dòng chữ "Hello, World!"

<a name="usedatabase"></a>
### 3. Sử dụng cơ sở dữ liệu
Ứng dụng sẽ sử dụng SQLite để lưu trữ người dùng( user) và bài đăng( post). SQLite tiện lợi vì nó được tích hợp sẵn trong Python. Tuy nhiên nó sẽ chậm một chút nếu các yêu cầu ghi vào cơ sở dữ liệu xảy ra đồng thời. Với ứng dụng nhỏ sẽ không nhận ra điều này tuy nhiên khi ứng dụng trở nên lớn hơn, bạn sẽ muốn chuyển qua một cơ sở dữ liệu khác.
<a name="connectdatabase"></a>
#### 3.1 Kết nối cơ sở dữ liệu
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
<a name="createtable"></a>
#### 3.2 Tạo bảng
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
<a name="registerdatabase"></a>
#### 3.3 Đăng ký cơ sở dữ liệu với ứng dụng
Các hàm _close_db_ và _init_db_command_ cần được đăng ký với ứng dụng; nếu không, chúng sẽ không được ứng dụng sử dụng. Tuy nhiên, vì bạn đang sử dụng một hàm gốc nên phiên bản đó không khả dụng khi viết các hàm. Thay vào đó, hãy viết một hàm nhận đơn đăng ký và thực hiện đăng ký.

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
 <a name="createfiledatabase"></a>
 #### 3.4 Tạo nơi lưu trữ cho cơ sở dữ liệu
 Bây giờ _init-db_ đã được đăng kí với ứng dụng, nó có thể được gọi bằng lệnh flask.
 
 _Note:_
 Nếu bạn đang chạy server từ phần trước thì hãy dừng nó lại và sử dụng lệnh bên dưới hoặc chạy nó trong một terminal mới. Nếu bây giờ bạn mới bắt đầu chạy server hãy xem lại phần khai báo _FLASK_APP_ và _FLASK_ENV_ để có thể chạy server.
 
 Chạy _init-db_:
 ```
 (venv) $ \flask-tutorial> flask init-db
 Initialized the database.
 ```
 Bây giờ sẽ có một tệp _flaskr.sqlite_ trong thư mục _instance_.
 <a name="blueprint"></a>
 ### 4. Blueprint: Bản thiết kế
 Blueprint hiểu như là một khuôn mẫu tối ưu nhất cho ứng dụng của bạn. Thông thường mỗi khi thêm tính năng cho ứng dụng ta phải khai báo cho ứng dụng biết. Blueprint giúp ta quy hoạch các tính năng thành từng gói để dễ dàng quản lý và định tuyến hơn. Ta sẽ tạo từng tính năng với các modules khác nhau và khai báo chúng với blueprint, Blueprint sẽ khai báo với ứng dụng để sử dụng chúng.

 ```flaskr/auth.py```
```
import functools

from flask import (
    Blueprint, flash, g, redirect, render_template, request, session, url_for
)
from werkzeug.security import check_password_hash, generate_password_hash

from flaskr.db import get_db

bp = Blueprint('auth', __name__, url_prefix='/auth')
```
Ta tạo một blueprint tên là 'auth' được xác định tại biến __name__ Url_prefix sẽ được thêm vào trước tất cả các URL liên kết với blueprint.

```flaskr/__init__.py```
```
def create_app():
    ...

    from . import auth
    app.register_blueprint(auth.bp)

    return app
```
Khai báo blueprint 'auth' cho ứng dụng biết.
<a name="register"></a>
#### 4.1 Đăng ký

```flaskr/auth.py```
```
@bp.route('/register', methods=('GET', 'POST'))
def register():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        db = get_db()
        error = None

        if not username:
            error = 'Username is required.'
        elif not password:
            error = 'Password is required.'

        if error is None:
            try:
                db.execute(
                    "INSERT INTO user (username, password) VALUES (?, ?)",
                    (username, generate_password_hash(password)),
                )
                db.commit()
            except db.IntegrityError:
                error = f"User {username} is already registered."
            else:
                return redirect(url_for("auth.login"))

        flash(error)

    return render_template('auth/register.html')
```
- ```@bp.route('/register'..)``` Tạo một liên kết với URL và hàm xử lý nó.
- Nếu người dùng đã gửi biểu mẫu với request.method là 'POST' thì hãy bắt đầu xác thực input.
- ```request.form``` sẽ lấy giá trị người dùng nhập vào gồm "username" và "password" Nếu thành công sẽ ghi người dùng mới vào cơ sở dữ liệu.
- ```db.execute()``` sẽ đảm bảo rằng SQL của bạn khỏi hình thức tấn công SQL Injection.
- ```create_password_hash()``` để bảo mật không lưu password dưới dạng text trong cơ sở dữ liệu.
- ```sqlite3.IntegrityError``` sẽ xảy ra nếu tên người dùng đã tồn tại, điều này sẽ được hiển thị cho người dùng dưới dạng một lỗi xác thực khác.
- Sau đó user được chuyển đến trang đăng nhập với url_for(). Điều này tốt hơn là viết URL trực tiếp vì nó cho phép bạn thay đổi URL sau này mà không cần thay đổi tất cả mã liên kết đến nó. redirect () tạo phản hồi chuyển hướng đến URL đã tạo.
- Nếu xác thực không thành công, lỗi sẽ được hiển thị cho người dùng. flash() lưu trữ các thông báo có thể được truy xuất khi hiển thị template.
- Khi người dùng ban đầu điều hướng đến auth/register hoặc có lỗi xác thực, một trang HTML có biểu mẫu đăng ký sẽ được hiển thị.
<a name="login"></a>
#### 4.2 Đăng nhập

```flaskr/auth.py```
```
@bp.route('/login', methods=('GET', 'POST'))
def login():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        db = get_db()
        error = None
        user = db.execute(
            'SELECT * FROM user WHERE username = ?', (username,)
        ).fetchone()

        if user is None:
            error = 'Incorrect username.'
        elif not check_password_hash(user['password'], password):
            error = 'Incorrect password.'

        if error is None:
            session.clear()
            session['user_id'] = user['id']
            return redirect(url_for('index'))

        flash(error)

    return render_template('auth/login.html')
```
- ```@bp.route('/login')``` tương tự như register khi người dùng truy cập đường dẫn /auth/login nó sẽ gọi đến hàm xử lý URL đó.
- Người dùng được truy vấn đầu tiên và được lưu trữ trong một biến để sử dụng sau này.
- ```fetchone()``` trả về một hàng từ truy vấn. Nếu truy vấn không trả về kết quả, nó sẽ trả về Không có. Sau đó, hàm fetchall() sẽ được sử dụng, nó sẽ trả về một danh sách tất cả các kết quả.
- ```check_password_hash()``` băm mật khẩu đã gửi theo cách giống như băm được lưu trữ và so sánh chúng một cách an toàn. Nếu chúng khớp, mật khẩu hợp lệ.
- ```session``` là một mệnh lệnh lưu trữ dữ liệu qua các yêu cầu. Khi xác thực thành công, id của người dùng được lưu trữ trong một phiên mới. Dữ liệu được lưu trữ trong một cookie được gửi đến trình duyệt và sau đó trình duyệt sẽ gửi lại dữ liệu đó với các yêu cầu tiếp theo. Flask ký vào dữ liệu một cách an toàn để dữ liệu đó không thể bị giả mạo.

Bây giờ, id của người dùng đã được lưu trữ trong phiên, nó sẽ có sẵn trong các yêu cầu tiếp theo. Khi bắt đầu mỗi yêu cầu, nếu người dùng đã đăng nhập, thông tin của họ sẽ được tải và cung cấp cho các chế độ xem khác.

```flaskr/auth.py```
```
@bp.before_app_request
def load_logged_in_user():
    user_id = session.get('user_id')

    if user_id is None:
        g.user = None
    else:
        g.user = get_db().execute(
            'SELECT * FROM user WHERE id = ?', (user_id,)
        ).fetchone()

@bp.route('/logout')
def logout():
    session.clear()
    return redirect(url_for('index'))
```
- ```bp.before_app_request()``` đăng ký một hàm chạy trước hàm xem, bất kể URL nào được yêu cầu. load_logged_in_user kiểm tra xem id người dùng có được lưu trữ trong phiên hay không và lấy dữ liệu của người dùng đó từ cơ sở dữ liệu, lưu trữ trên g.user, kéo dài trong thời gian yêu cầu. Nếu không có id người dùng hoặc nếu id không tồn tại, g.user sẽ là None.
- Để đăng xuất, bạn cần xóa id người dùng khỏi phiên. Sau đó load_logged_in_user sẽ không tải người dùng trong các yêu cầu tiếp theo.
<a name="authentication"></a>
#### 4.3 Xác thực
Việc tạo, chỉnh sửa và xóa các bài đăng trên blog sẽ yêu cầu người dùng đăng nhập. Có thể sử dụng trình trang trí để kiểm tra điều này cho từng chế độ xem được áp dụng.
```flaskr/auth.py```
```
def login_required(view):
    @functools.wraps(view)
    def wrapped_view(**kwargs):
        if g.user is None:
            return redirect(url_for('auth.login'))

        return view(**kwargs)

    return wrapped_view
```
- Trình trang trí này trả về một hàm chế độ xem mới bao bọc chế độ xem ban đầu mà nó được áp dụng. Chức năng mới sẽ kiểm tra xem người dùng có được tải hay không và chuyển hướng đến trang đăng nhập theo cách khác. Nếu người dùng được tải, chế độ xem ban đầu được gọi và tiếp tục bình thường. Bạn sẽ sử dụng trình trang trí này khi viết các lượt xem blog.
<a name="templates"></a>
### 5. Templates
Phần trên chúng ta mới xử lý xong việc Flask sẽ làm việc như thế nào với cơ sở dữ liệu, tuy nhiên có một số chỗ cần để ý tới: khi auth yêu cầu trả về register.html, login.html, index.html.
Để hiểu được phần này bạn cần có chút kiến thức về Jinja nữa nhé.
Các file HTML chúng ta sẽ lưu toàn bộ vào folder templates để dễ dàng quản lý.
Hầu hết các trang web sẽ có một cấu trúc cố định và giống nhau khi truy cập từng tính năng trong đó, để giảm thiểu dòng code và tăng tốc cho Flask ta sẽ sử dụng một cấu trúc chung cho trang web là base.html
<a name="basetemplate"></a>
#### 5.1 Mẫu chung
```flaskr/templates/base.html```
```
<!doctype html>
<title>{% block title %}{% endblock %} - Flaskr</title>
<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
<nav>
  <h1>Flaskr</h1>
  <ul>
    {% if g.user %}
      <li><span>{{ g.user['username'] }}</span>
      <li><a href="{{ url_for('auth.logout') }}">Log Out</a>
    {% else %}
      <li><a href="{{ url_for('auth.register') }}">Register</a>
      <li><a href="{{ url_for('auth.login') }}">Log In</a>
    {% endif %}
  </ul>
</nav>
<section class="content">
  <header>
    {% block header %}{% endblock %}
  </header>
  {% for message in get_flashed_messages() %}
    <div class="flash">{{ message }}</div>
  {% endfor %}
  {% block content %}{% endblock %}
</section>
```
- ```g``` tự động có sẵn trong các templates. Dựa trên nếu g.user được đặt (từ load_logged_in_user), tên người dùng và liên kết đăng xuất được hiển thị hoặc các liên kết để đăng ký và đăng nhập được hiển thị. url_for() cũng tự động có sẵn và được sử dụng để tạo URL cho các chế độ xem thay vì viết chúng ra theo cách thủ công.
- Sau tiêu đề trang và trước nội dung, mẫu lặp lại từng thông báo được trả về bởi get_flashed_messages(). Bạn đã sử dụng flash() trong các dạng xem để hiển thị thông báo lỗi và đây là mã sẽ hiển thị chúng.
- ```{% block title%}``` sẽ thay đổi tiêu đề được hiển thị trong tab và tiêu đề cửa sổ của trình duyệt.
- ```{% block header%}``` tương tự như title nhưng sẽ thay đổi tiêu đề hiển thị trên trang.
- ```{% block content%}``` là nơi chứa nội dung của mỗi trang, chẳng hạn như biểu mẫu đăng nhập hoặc một bài đăng trên blog.
<a name="registertemplate"></a>
#### 5.2 Mẫu đăng ký

```flaskr/templates/auth/register.html```
```
<!doctype html>
<title>{% block title %}{% endblock %} - Flaskr</title>
<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
<nav>
  <h1>Flaskr</h1>
  <ul>
    {% if g.user %}
      <li><span>{{ g.user['username'] }}</span>
      <li><a href="{{ url_for('auth.logout') }}">Log Out</a>
    {% else %}
      <li><a href="{{ url_for('auth.register') }}">Register</a>
      <li><a href="{{ url_for('auth.login') }}">Log In</a>
    {% endif %}
  </ul>
</nav>
<section class="content">
  <header>
    {% block header %}{% endblock %}
  </header>
  {% for message in get_flashed_messages() %}
    <div class="flash">{{ message }}</div>
  {% endfor %}
  {% block content %}{% endblock %}
</section>
```
- {% extends 'base.html' %} register.html sẽ kế thừa các block của base.html
- Các thẻ đầu vào đang sử dụng thuộc tính bắt buộc ở đây. Điều này yêu cầu trình duyệt không gửi biểu mẫu cho đến khi các trường đó được điền vào. Nếu người dùng đang sử dụng trình duyệt cũ hơn không hỗ trợ thuộc tính đó hoặc nếu họ đang sử dụng thứ gì đó ngoài trình duyệt để thực hiện yêu cầu, bạn vẫn muốn xác thực dữ liệu trong chế độ xem Bình. Điều quan trọng là phải luôn xác thực đầy đủ dữ liệu trên máy chủ, ngay cả khi máy khách cũng thực hiện một số xác thực.
<a name="logintemplate"></a>
#### 5.3 Mẫu đăng nhập

Tương tự như register.html
```flaskr/templates/auth/login.html```
```
{% extends 'base.html' %}

{% block header %}
  <h1>{% block title %}Log In{% endblock %}</h1>
{% endblock %}

{% block content %}
  <form method="post">
    <label for="username">Username</label>
    <input name="username" id="username" required>
    <label for="password">Password</label>
    <input type="password" name="password" id="password" required>
    <input type="submit" value="Log In">
  </form>
{% endblock %}
```
Đến đây hay thử chạy server và đăng kí một user.

Note: Hãy lưu ý phần ```FLASK_APP``` nhé.
<a name="indextemplate"></a>
#### 5.4 Mẫu trang chỉ mục

Tiếp theo: Sau khi đăng nhập Flask sẽ trả về url_for('index'). Index này ta sẽ đặt trong blueprint 'blog', trước hết ta sẽ khai báo một blueprint là 'blog' với ứng dụng tương tự như khi khai báo blueprint 'auth' nhé.

```flaskr/blog.py```
```
from flask import (
    Blueprint, flash, g, redirect, render_template, request, url_for
)
from werkzeug.exceptions import abort

from flaskr.auth import login_required
from flaskr.db import get_db

bp = Blueprint('blog', __name__)
```
```flaskr/__init__.py```
```
def create_app():
    ...

    from . import blog
    app.register_blueprint(blog.bp)
    app.add_url_rule('/', endpoint='index')

    return app
```
- Không giống như blueprint 'auth', 'blog' không có url_prefix. Vì vậy, dạng xem index sẽ ở /, Blog là tính năng chính của Flaskr, vì vậy có ý nghĩa rằng chỉ mục blog sẽ là chỉ mục chính.
- Tuy nhiên, điểm cuối cho chế độ xem index được xác định bên dưới sẽ là blog.index. Một số dạng xem xác thực đề cập đến một điểm cuối index thuần túy. app.add_url_rule() liên kết tên điểm cuối 'index' với /url để url_for ('index') hoặc url_for('blog.index') đều hoạt động, tạo ra cùng một URL / theo cách nào đó.
Index sẽ hiển thị tất cả các bài Post, gần đây nhất trước tiên. Một JOIN được sử dụng để thông tin tác giả từ bảng người dùng có sẵn trong kết quả.

```flaskr/blog.py```
```
@bp.route('/')
def index():
    db = get_db()
    posts = db.execute(
        'SELECT p.id, title, body, created, author_id, username'
        ' FROM post p JOIN user u ON p.author_id = u.id'
        ' ORDER BY created DESC'
    ).fetchall()
    return render_template('blog/index.html', posts=posts)
```
```flaskr/templates/blog/index.html```
```
{% extends 'base.html' %}

{% block header %}
  <h1>{% block title %}Posts{% endblock %}</h1>
  {% if g.user %}
    <a class="action" href="{{ url_for('blog.create') }}">New</a>
  {% endif %}
{% endblock %}

{% block content %}
  {% for post in posts %}
    <article class="post">
      <header>
        <div>
          <h1>{{ post['title'] }}</h1>
          <div class="about">by {{ post['username'] }} on {{ post['created'].strftime('%Y-%m-%d') }}</div>
        </div>
        {% if g.user['id'] == post['author_id'] %}
          <a class="action" href="{{ url_for('blog.update', id=post['id']) }}">Edit</a>
        {% endif %}
      </header>
      <p class="body">{{ post['body'] }}</p>
    </article>
    {% if not loop.last %}
      <hr>
    {% endif %}
  {% endfor %}
{% endblock %}
```
Một chút kiến thức với jinja sẽ giúp bạn hiểu về các vòng lặp trong đoạn code trên nhé.
Chức năng trang chủ để hiển thị Post đã hoàn thành nhưng chúng ta chưa có bài viết nào để hiển thị cả, hãy xây dựng một form create post nhé.
Trước hết là tạo form để tạo post. Trước hết hãy yêu cầu user đăng nhập để có thể sử dụng tính năng này(dùng login_required)
<a name="createtemplate"></a>
#### 5.5 Mẫu tạo bài đăng

```flaskr/blog.py```
```
@bp.route('/create', methods=('GET', 'POST'))
@login_required
def create():
    if request.method == 'POST':
        title = request.form['title']
        body = request.form['body']
        error = None

        if not title:
            error = 'Title is required.'

        if error is not None:
            flash(error)
        else:
            db = get_db()
            db.execute(
                'INSERT INTO post (title, body, author_id)'
                ' VALUES (?, ?, ?)',
                (title, body, g.user['id'])
            )
            db.commit()
            return redirect(url_for('blog.index'))

    return render_template('blog/create.html')
```
```flaskr/templates/blog/create.html```
```
{% extends 'base.html' %}

{% block header %}
  <h1>{% block title %}New Post{% endblock %}</h1>
{% endblock %}

{% block content %}
  <form method="post">
    <label for="title">Title</label>
    <input name="title" id="title" value="{{ request.form['title'] }}" required>
    <label for="body">Body</label>
    <textarea name="body" id="body">{{ request.form['body'] }}</textarea>
    <input type="submit" value="Save">
  </form>
{% endblock %}
```
<a name="updatetemplate"></a>
#### 5.6 Mẫu cập nhật

Cả chế độ Update và delete sẽ cần tìm nạp một post theo id và kiểm tra xem tác giả có khớp với user đã đăng nhập hay không. Để tránh trùng lặp mã, bạn có thể viết một hàm để lấy post và gọi nó từ mỗi lần xem.
```flaskr/blog.py```
```
def get_post(id, check_author=True):
    post = get_db().execute(
        'SELECT p.id, title, body, created, author_id, username'
        ' FROM post p JOIN user u ON p.author_id = u.id'
        ' WHERE p.id = ?',
        (id,)
    ).fetchone()

    if post is None:
        abort(404, f"Post id {id} doesn't exist.")

    if check_author and post['author_id'] != g.user['id']:
        abort(403)

    return post
```
- ```abort()``` sẽ đưa ra một ngoại lệ đặc biệt trả về mã trạng thái HTTP. Nó cần một thông báo tùy chọn để hiển thị cùng với lỗi, nếu không, một thông báo mặc định sẽ được sử dụng. 404 có nghĩa là "Not Found" và 403 có nghĩa là "Forbidden". (401 có nghĩa là “Unauthorized”, nhưng bạn chuyển hướng đến trang login thay vì trả lại trạng thái đó.)
- ```check_author``` được định nghĩa để hàm có thể được sử dụng để lấy một post mà không cần kiểm tra tác giả. Điều này sẽ hữu ích nếu bạn viết một lượt xem để hiển thị từng post trên một trang, nơi người dùng không quan trọng vì họ không sửa đổi bài đăng.
```flaskr/blog.py```
```
@bp.route('/<int:id>/update', methods=('GET', 'POST'))
@login_required
def update(id):
    post = get_post(id)

    if request.method == 'POST':
        title = request.form['title']
        body = request.form['body']
        error = None

        if not title:
            error = 'Title is required.'

        if error is not None:
            flash(error)
        else:
            db = get_db()
            db.execute(
                'UPDATE post SET title = ?, body = ?'
                ' WHERE id = ?',
                (title, body, id)
            )
            db.commit()
            return redirect(url_for('blog.index'))

    return render_template('blog/update.html', post=post)
```
- Không giống như các chế độ xem bạn đã viết cho đến nay, hàm update có một đối số là id. Điều đó tương ứng với <int: id> trong route. URL thực sẽ giống như /1/update. Flask sẽ nắm bắt giá trị 1, đảm bảo nó là int và chuyển nó làm đối số id. Nếu bạn không chỉ định int: và thay vào đó là <id>, nó sẽ là một chuỗi. Để tạo URL cho trang update, url_for () cần được chuyển id để nó biết cần điền gì vào: url_for('blog.update', id=post ['id']). Đây cũng là tệp index.html ở trên.
- Chế độ xem tạo và update trông rất giống nhau. Sự khác biệt chính là dạng xem update sử dụng đối tượng bài đăng và truy vấn UPDATE thay vì INSERT. Với một số cấu trúc thông minh, bạn có thể sử dụng một chế độ xem và template cho cả hai hành động, nhưng đối với tutorial này, rõ ràng hơn là giữ chúng riêng biệt.

```flaskr/templates/blog/update.html```
```
{% extends 'base.html' %}

{% block header %}
  <h1>{% block title %}Edit "{{ post['title'] }}"{% endblock %}</h1>
{% endblock %}

{% block content %}
  <form method="post">
    <label for="title">Title</label>
    <input name="title" id="title"
      value="{{ request.form['title'] or post['title'] }}" required>
    <label for="body">Body</label>
    <textarea name="body" id="body">{{ request.form['body'] or post['body'] }}</textarea>
    <input type="submit" value="Save">
  </form>
  <hr>
  <form action="{{ url_for('blog.delete', id=post['id']) }}" method="post">
    <input class="danger" type="submit" value="Delete" onclick="return confirm('Are you sure?');">
  </form>
{% endblock %}
```
- Template này có hai dạng. Đầu tiên đăng dữ liệu đã chỉnh sửa lên trang hiện tại(/<id>/update). Form khác chỉ chứa một nút và chỉ định một thuộc tính hành động sẽ đăng lên dạng xem xóa. Nút này sử dụng một số JavaScript để hiển thị hộp thoại xác nhận trước khi gửi.

- Template {{request.form['title'] hoặc post['title']}} được sử dụng để chọn dữ liệu xuất hiện trong form. Khi form chưa được gửi, dữ liệu post ban đầu sẽ xuất hiện, nhưng nếu dữ liệu post không hợp lệ đã được đăng, bạn muốn hiển thị dữ liệu đó để user có thể sửa lỗi, do đó, request.form sẽ được sử dụng thay thế. yêu cầu là một biến khác tự động có sẵn trong các templates.
<a name="deletetemplate"></a>
#### 5.7 Mẫu xóa
    
Chế độ xem delete không có tempalte riêng, nút xóa là một phần của update.html và đăng lên URL/ <id>/delete. Vì không có template, nó sẽ chỉ xử lý phương thức POST và sau đó chuyển hướng đến index.
```flaskr/blog.py```
```
@bp.route('/<int:id>/delete', methods=('POST',))
@login_required
def delete(id):
    get_post(id)
    db = get_db()
    db.execute('DELETE FROM post WHERE id = ?', (id,))
    db.commit()
    return redirect(url_for('blog.index'))
```
<a name="updatetemplate"></a>
#### 5.8 Nâng cấp giao diện
Blog của bạn gần như đã hoàn thành tuy nhiên hãy để ý đến base.html có một đường dẫn đến file css. Hãy thêm style.css để cập nhật giao diện cho blog của mình.
    
```style.css```
```
html { font-family: sans-serif; background: #eee; padding: 1rem; }
body { max-width: 960px; margin: 0 auto; background: white; }
h1 { font-family: serif; color: #377ba8; margin: 1rem 0; }
a { color: #377ba8; }
hr { border: none; border-top: 1px solid lightgray; }
nav { background: lightgray; display: flex; align-items: center; padding: 0 0.5rem; }
nav h1 { flex: auto; margin: 0; }
nav h1 a { text-decoration: none; padding: 0.25rem 0.5rem; }
nav ul  { display: flex; list-style: none; margin: 0; padding: 0; }
nav ul li a, nav ul li span, header .action { display: block; padding: 0.5rem; }
.content { padding: 0 1rem 1rem; }
.content > header { border-bottom: 1px solid lightgray; display: flex; align-items: flex-end; }
.content > header h1 { flex: auto; margin: 1rem 0 0.25rem 0; }
.flash { margin: 1em 0; padding: 1em; background: #cae6f6; border: 1px solid #377ba8; }
.post > header { display: flex; align-items: flex-end; font-size: 0.85em; }
.post > header > div:first-of-type { flex: auto; }
.post > header h1 { font-size: 1.5em; margin-bottom: 0; }
.post .about { color: slategray; font-style: italic; }
.post .body { white-space: pre-line; }
.content:last-child { margin-bottom: 0; }
.content form { margin: 1em 0; display: flex; flex-direction: column; }
.content label { font-weight: bold; margin-bottom: 0.5em; }
.content input, .content textarea { margin-bottom: 1em; }
.content textarea { min-height: 12em; resize: vertical; }
input.danger { color: #cc2f2e; }
input[type=submit] { align-self: start; min-width: 10em; }
```
Hãy thử chạy Flask và thử các tính năng.

Note: Hãy để ý đến ```(venv)``` và ```FLASK_APP```.

<a name="projectinstallable"></a>
V. Project Installable - Cài đặt dự án
Dự án gần như đã hoàn thành, tuy nhiên đó là ở trên máy của chúng ta mà thôi, vậy muốn nó chạy được trên máy người khác thì phài làm sao?
Chúng ta phải cài đặt lại từ đầu thì mất quá nhiều thời gian. Hãy tìm cách mô tả và cài đặt dự án để nó có thể cài đặt được ở mọi nơi.
Với tutorial việc giới thiệu phần này là muộn. Với những dự án sau này, các bạn hãy bắt đầu nó từ khi bắt đầu dự án nhé.
Hãy xem lại cấu trúc của dự án nhé.
[1. Describe - Mô tả dự án]

```setup.py```
```
from setuptools import find_packages, setup

setup(
    name='flaskr',
    version='1.0.0',
    packages=find_packages(),
    include_package_data=True,
    zip_safe=False,
    install_requires=[
        'flask',
    ],
)
```
- Các gói cho Python biết những thư mục gói nào (và các tệp Python mà chúng chứa) cần bao gồm. find_packages () tự động tìm các thư mục này, do đó bạn không cần phải gõ chúng ra. Để bao gồm các tệp khác, chẳng hạn như thư mục tĩnh và mẫu, dữ liệu include_package_data được thiết lập. Python cần một tệp khác có tên MANIFEST.in để cho biết dữ liệu khác này là gì.

```MANIFEST.in```
```
include flaskr/schema.sql
graft flaskr/static
graft flaskr/templates
global-exclude *.pyc
```
- Điều này yêu cầu Python sao chép mọi thứ trong thư mục static và templates cũng như tệp schema.sql, nhưng loại trừ tất cả các tệp bytecode.

[2. Install - Cài đặt dự án]

Hãy tìm cách upload project của bạn lên Github nhé.
Bây giờ hãy clone project của bạn về một nơi khác:

```
$ cd Flask-Tutorial
$ Flask-Tutorial> cd venv/Scripts
$ Flask-Tutorial\venv\Scripts> activate
$ Flask-Tutorial> pip install -e .
```
- Điều này yêu cầu pip tìm setup.py trong thư mục hiện tại và cài đặt nó ở chế độ có thể chỉnh sửa hoặc phát triển. Chế độ có thể chỉnh sửa có nghĩa là khi bạn thực hiện các thay đổi đối với mã cục bộ của mình, bạn sẽ chỉ cần cài đặt lại nếu bạn thay đổi siêu dữ liệu về dự án, chẳng hạn như các phụ thuộc của dự án.

Hãy kiểm tra và so sánh với project trên máy:
```
$ Flask-Tutorial>pip list
```
```
Package      Version Location
------------ ------- -----------------------------------------
click        8.0.3
colorama     0.4.4
Flask        2.0.2
flaskr       1.0.0   c:\users\admin\flask-clone\flask-tutorial
itsdangerous 2.0.1
Jinja2       3.0.2
MarkupSafe   2.0.1
pip          21.2.3
setuptools   57.4.0
Werkzeug     2.0.2
```
```flask run``` và kiểm tra nó. Đảm bảo rằng bạn đã khai báo FLASK_APP nhé.
Vậy là bạn có thể sử dụng được project của mình ở nhiều nơi khác nhau rồi. Tuy nhiên vẫn còn nhiều công đoạn nữa để project có thể đến tay người dùng được.
<a name="test"></a>
VI. Test - Thử nghiệm
Viết các bài kiểm tra đơn vị cho ứng dụng của bạn cho phép bạn kiểm tra xem mã bạn đã viết có hoạt động theo cách bạn mong đợi hay không. Flask cung cấp một ứng dụng khách thử nghiệm mô phỏng các yêu cầu đến ứng dụng và trả về dữ liệu phản hồi.
<a name="installtest"></a>
1. Cài đặt thử nghiệm

(venv)$ Flask-Tutorial> pip install pytest coverage
(venv)$ Flask-Tutorial> mkdir tests

<a name="setuptest"></a>
2. Thiết lập thử nghiệm
Mã kiểm tra nằm trong thư mục kiểm tra. Thư mục này nằm bên cạnh gói flaskr, không phải bên trong nó. Tệp tests / conftest.py chứa các chức năng thiết lập được gọi là đồ đạc mà mỗi thử nghiệm sẽ sử dụng. Kiểm tra trong các mô-đun Python bắt đầu bằng test_ và mỗi hàm kiểm tra trong các mô-đun đó cũng bắt đầu bằng test_.

Mỗi bài kiểm tra sẽ tạo một tệp cơ sở dữ liệu tạm thời mới và điền một số dữ liệu sẽ được sử dụng trong các bài kiểm tra. Viết tệp SQL để chèn dữ liệu đó.

```tests/data.sql```
```
INSERT INTO user (username, password)
VALUES
  ('test', 'pbkdf2:sha256:50000$TCI4GzcX$0de171a4f4dac32e3364c7ddc7c14f3e2fa61f2d17574483f7ffbb431b4acb2f'),
  ('other', 'pbkdf2:sha256:50000$kJPKsz6N$d2d4784f1b030a9761f5ccaeeaca413f27f2ecb76d6168407af962ddce849f79');

INSERT INTO post (title, body, author_id, created)
VALUES
  ('test title', 'test' || x'0a' || 'body', 1, '2018-01-01 00:00:00');
```
Ứng dụng cố định sẽ gọi nhà máy và vượt qua test_config để định cấu hình ứng dụng và cơ sở dữ liệu để thử nghiệm thay vì sử dụng cấu hình phát triển cục bộ của bạn.

```tests/conftest.py```
```
import os
import tempfile

import pytest
from flaskr import create_app
from flaskr.db import get_db, init_db

with open(os.path.join(os.path.dirname(__file__), 'data.sql'), 'rb') as f:
    _data_sql = f.read().decode('utf8')


@pytest.fixture
def app():
    db_fd, db_path = tempfile.mkstemp()

    app = create_app({
        'TESTING': True,
        'DATABASE': db_path,
    })

    with app.app_context():
        init_db()
        get_db().executescript(_data_sql)

    yield app

    os.close(db_fd)
    os.unlink(db_path)


@pytest.fixture
def client(app):
    return app.test_client()


@pytest.fixture
def runner(app):
    return app.test_cli_runner()
```
- ```tempfile.mkstemp()``` tạo và mở một tệp tạm thời, trả về bộ mô tả tệp và đường dẫn đến tệp đó. Đường dẫn DATABASE bị ghi đè nên nó trỏ đến đường dẫn tạm thời này thay vì thư mục cá thể. Sau khi thiết lập đường dẫn, các bảng cơ sở dữ liệu được tạo và dữ liệu thử nghiệm được chèn vào. Sau khi thử nghiệm kết thúc, tệp tạm thời được đóng và xóa.

- TESTING cho Flask biết rằng ứng dụng đang ở chế độ thử nghiệm. Flask thay đổi một số hành vi bên trong để dễ kiểm tra hơn và các tiện ích mở rộng khác cũng có thể sử dụng cờ để kiểm tra chúng dễ dàng hơn.

- Ứng dụng khách gọi app.test_client() với đối tượng ứng dụng được tạo bởi ứng dụng fixture. Các thử nghiệm sẽ sử dụng máy khách để thực hiện các yêu cầu đối với ứng dụng mà không cần chạy máy chủ.

- Vật cố định người chạy tương tự như khách hàng. app.test_cli_runner() tạo một trình chạy có thể gọi các lệnh Click đã đăng ký với ứng dụng.

- Pytest sử dụng các đồ đạc bằng cách khớp tên hàm của chúng với tên của các đối số trong các hàm kiểm tra. Ví dụ: hàm test_hello mà bạn sẽ viết tiếp theo có một đối số khách hàng. Pytest đối sánh điều đó với hàm cố định máy khách, gọi nó và chuyển giá trị trả về cho hàm kiểm tra.

<a name="factorytest"></a>
2.1 Thử nghiệm nhà máy ứng dụng

Không có nhiều điều để kiểm tra về chính nhà máy. Hầu hết mã sẽ được thực thi cho mỗi bài kiểm tra, vì vậy nếu có điều gì đó không thành công, các bài kiểm tra khác sẽ thông báo.

Hành vi duy nhất có thể thay đổi là vượt qua cấu hình kiểm tra. Nếu cấu hình không được thông qua, phải có một số cấu hình mặc định, nếu không cấu hình sẽ được ghi đè.

```tests/test_factory.py```
```
from flaskr import create_app


def test_config():
    assert not create_app().testing
    assert create_app({'TESTING': True}).testing


def test_hello(client):
    response = client.get('/hello')
    assert response.data == b'Hello, World!'
```
<a name="databasetest"></a>
2.2 Thử nghiệm cơ sở dữ liệu
Trong ngữ cảnh ứng dụng, get_db sẽ trả về cùng một kết nối mỗi khi nó được gọi. Sau ngữ cảnh, kết nối sẽ được đóng lại.

```tests/test_db.py```
```
import sqlite3

import pytest
from flaskr.db import get_db


def test_get_close_db(app):
    with app.app_context():
        db = get_db()
        assert db is get_db()

    with pytest.raises(sqlite3.ProgrammingError) as e:
        db.execute('SELECT 1')

    assert 'closed' in str(e.value)

def test_init_db_command(runner, monkeypatch):
    class Recorder(object):
        called = False

    def fake_init_db():
        Recorder.called = True

    monkeypatch.setattr('flaskr.db.init_db', fake_init_db)
    result = runner.invoke(args=['init-db'])
    assert 'Initialized' in result.output
    assert Recorder.called
```
- Lệnh init-db sẽ gọi hàm init_db và xuất ra một thông báo.
- Thử nghiệm này sử dụng thiết bị cố định Monkeypatch của Pytest để thay thế hàm init_db bằng một hàm ghi lại rằng nó đã được gọi. Vật cố định người chạy mà bạn đã viết ở trên được sử dụng để gọi lệnh init-db theo tên.

<a name="authenticationtest"></a>
2.3 Thử nghiệm xác thực
Đối với hầu hết các chế độ xem, người dùng cần phải đăng nhập. Cách dễ nhất để thực hiện việc này trong các thử nghiệm là thực hiện yêu cầu ĐĂNG đối với chế độ xem đăng nhập với ứng dụng khách. Thay vì viết nó ra mọi lúc, bạn có thể viết một lớp với các phương thức để làm điều đó và sử dụng một vật cố định để chuyển nó cho máy khách cho mỗi lần kiểm tra.

```tesst/conftest.py```
```
class AuthActions(object):
    def __init__(self, client):
        self._client = client

    def login(self, username='test', password='test'):
        return self._client.post(
            '/auth/login',
            data={'username': username, 'password': password}
        )

    def logout(self):
        return self._client.get('/auth/logout')


@pytest.fixture
def auth(client):
    return AuthActions(client)
```
- 361 / 5000
Kết quả dịch
Với phần cố định auth, bạn có thể gọi auth.login () trong thử nghiệm để đăng nhập với tư cách là người dùng thử nghiệm, được chèn vào như một phần của dữ liệu thử nghiệm trong ứng dụng cố định.

Chế độ xem đăng ký sẽ hiển thị thành công trên GET. Trên POST với dữ liệu biểu mẫu hợp lệ, nó sẽ chuyển hướng đến URL đăng nhập và dữ liệu của người dùng phải có trong cơ sở dữ liệu. Dữ liệu không hợp lệ nên hiển thị thông báo lỗi. 

```tests/test_auth.py```
```
import pytest
from flask import g, session
from flaskr.db import get_db


def test_register(client, app):
    assert client.get('/auth/register').status_code == 200
    response = client.post(
        '/auth/register', data={'username': 'a', 'password': 'a'}
    )
    assert 'http://localhost/auth/login' == response.headers['Location']

    with app.app_context():
        assert get_db().execute(
            "SELECT * FROM user WHERE username = 'a'",
        ).fetchone() is not None


@pytest.mark.parametrize(('username', 'password', 'message'), (
    ('', '', b'Username is required.'),
    ('a', '', b'Password is required.'),
    ('test', 'test', b'already registered'),
))
def test_register_validate_input(client, username, password, message):
    response = client.post(
        '/auth/register',
        data={'username': username, 'password': password}
    )
    assert message in response.data
```
- client.get () thực hiện yêu cầu GET và trả về đối tượng Phản hồi do Flask trả về. Tương tự, client.post () thực hiện một yêu cầu ĐĂNG, chuyển đổi dữ liệu dict thành dữ liệu biểu mẫu.

- Để kiểm tra xem trang có hiển thị thành công hay không, một yêu cầu đơn giản được đưa ra và kiểm tra mã trạng thái 200 OK. Nếu hiển thị không thành công, Flask sẽ trả về mã lỗi 500 Internal Server Error.

- tiêu đề sẽ có tiêu đề Vị trí với URL đăng nhập khi chế độ xem đăng ký chuyển hướng đến chế độ xem đăng nhập.

- dữ liệu chứa phần thân của phản hồi dưới dạng byte. Nếu bạn mong đợi một giá trị nhất định hiển thị trên trang, hãy kiểm tra xem giá trị đó có trong dữ liệu hay không. Các byte phải được so sánh với các byte. Nếu bạn muốn so sánh văn bản, hãy sử dụng get_data (as_text = True) để thay thế.

- pytest.mark.parametrize yêu cầu Pytest chạy cùng một hàm kiểm tra với các đối số khác nhau. Bạn sử dụng nó ở đây để kiểm tra các thông báo lỗi và đầu vào không hợp lệ khác nhau mà không cần viết cùng một mã ba lần.

- Các bài kiểm tra cho chế độ xem đăng nhập rất giống với các bài kiểm tra cho chế độ đăng ký. Thay vì kiểm tra dữ liệu trong cơ sở dữ liệu, phiên phải được đặt user_id sau khi đăng nhập.
```test/test_auth.py```
```
def test_login(client, auth):
    assert client.get('/auth/login').status_code == 200
    response = auth.login()
    assert response.headers['Location'] == 'http://localhost/'

    with client:
        client.get('/')
        assert session['user_id'] == 1
        assert g.user['username'] == 'test'


@pytest.mark.parametrize(('username', 'password', 'message'), (
    ('a', 'test', b'Incorrect username.'),
    ('test', 'a', b'Incorrect password.'),
))
def test_login_validate_input(auth, username, password, message):
    response = auth.login(username, password)
    assert message in response.data

def test_logout(client, auth):
    auth.login()

    with client:
        auth.logout()
        assert 'user_id' not in session
```
- Sử dụng máy khách trong một khối với cho phép truy cập các biến ngữ cảnh như phiên sau khi phản hồi được trả về. Thông thường, việc truy cập phiên bên ngoài một yêu cầu sẽ gây ra lỗi.

- Kiểm tra đăng xuất ngược lại với đăng nhập. phiên không được chứa user_id sau khi đăng xuất.

<a name="blogtest"></a>
2.4 Thử nghiệm blog
Tất cả các lượt xem blog đều sử dụng thiết bị xác thực mà bạn đã viết trước đó. Gọi auth.login () và các yêu cầu tiếp theo từ máy khách sẽ được đăng nhập với tư cách người dùng thử nghiệm.

Chế độ xem chỉ mục sẽ hiển thị thông tin về bài đăng đã được thêm vào với dữ liệu thử nghiệm. Khi đăng nhập với tư cách tác giả, cần có một liên kết để chỉnh sửa bài viết.

Bạn cũng có thể kiểm tra thêm một số hành vi xác thực trong khi kiểm tra chế độ xem chỉ mục. Khi chưa đăng nhập, mỗi trang sẽ hiển thị các liên kết để đăng nhập hoặc đăng ký. Khi đăng nhập, có một liên kết để đăng xuất.
```tests/test_blog.py```
```
import pytest
from flaskr.db import get_db


def test_index(client, auth):
    response = client.get('/')
    assert b"Log In" in response.data
    assert b"Register" in response.data

    auth.login()
    response = client.get('/')
    assert b'Log Out' in response.data
    assert b'test title' in response.data
    assert b'by test on 2018-01-01' in response.data
    assert b'test\nbody' in response.data
    assert b'href="/1/update"' in response.data
```
- Người dùng phải đăng nhập để truy cập vào chế độ xem tạo, cập nhật và xóa. Người dùng đã đăng nhập phải là tác giả của bài đăng để truy cập cập nhật và xóa, nếu không trạng thái 403 Forbidden sẽ bị trả về. Nếu bài đăng với id đã cho không tồn tại, cập nhật và xóa sẽ trả về 404 Not Found.
```tests/test_blog.py```
```
@pytest.mark.parametrize('path', (
    '/create',
    '/1/update',
    '/1/delete',
))
def test_login_required(client, path):
    response = client.post(path)
    assert response.headers['Location'] == 'http://localhost/auth/login'


def test_author_required(app, client, auth):
    # change the post author to another user
    with app.app_context():
        db = get_db()
        db.execute('UPDATE post SET author_id = 2 WHERE id = 1')
        db.commit()

    auth.login()
    # current user can't modify other user's post
    assert client.post('/1/update').status_code == 403
    assert client.post('/1/delete').status_code == 403
    # current user doesn't see edit link
    assert b'href="/1/update"' not in client.get('/').data


@pytest.mark.parametrize('path', (
    '/2/update',
    '/2/delete',
))
def test_exists_required(client, auth, path):
    auth.login()
    assert client.post(path).status_code == 404
```
- Chế độ xem tạo và cập nhật sẽ hiển thị và trả về trạng thái 200 OK cho một yêu cầu GET. Khi dữ liệu hợp lệ được gửi trong một yêu cầu ĐĂNG, tạo sẽ chèn dữ liệu bài đăng mới vào cơ sở dữ liệu và cập nhật sẽ sửa đổi dữ liệu hiện có. Cả hai trang sẽ hiển thị thông báo lỗi trên dữ liệu không hợp lệ.

```tests/test_blog.py```
```
def test_create(client, auth, app):
    auth.login()
    assert client.get('/create').status_code == 200
    client.post('/create', data={'title': 'created', 'body': ''})

    with app.app_context():
        db = get_db()
        count = db.execute('SELECT COUNT(id) FROM post').fetchone()[0]
        assert count == 2


def test_update(client, auth, app):
    auth.login()
    assert client.get('/1/update').status_code == 200
    client.post('/1/update', data={'title': 'updated', 'body': ''})

    with app.app_context():
        db = get_db()
        post = db.execute('SELECT * FROM post WHERE id = 1').fetchone()
        assert post['title'] == 'updated'


@pytest.mark.parametrize('path', (
    '/create',
    '/1/update',
))
def test_create_update_validate(client, auth, path):
    auth.login()
    response = client.post(path, data={'title': '', 'body': ''})
    assert b'Title is required.' in response.data

def test_delete(client, auth, app):
    auth.login()
    response = client.post('/1/delete')
    assert response.headers['Location'] == 'http://localhost/'

    with app.app_context():
        db = get_db()
        post = db.execute('SELECT * FROM post WHERE id = 1').fetchone()
        assert post is None
```
- Chế độ xem xóa sẽ chuyển hướng đến URL chỉ mục và bài đăng sẽ không còn tồn tại trong cơ sở dữ liệu.
<a name="runtest"></a>
3. Chạy thử nghiệm

```(venv)$ Flask-Tutorial>pytest```
Nếu nó không hoạt động hãy thử:

```(venv)$ Flask-Tutorial>converage run -m pytest```
Bạn sẽ thấy một gì đó tương tự tại terminal
```
collected 24 items                                                                                    

tests\test_auth.py ........                                                                    [ 33%] 
tests\test_blog.py ............                                                                [ 83%] 
tests\test_db.py ..                                                                            [ 91%] 
tests\test_factory.py ..                                                                       [100%] 

======================================== 24 passed in 8.88s ========================================= 
======================================== test session starts ======================================== 
platform win32 -- Python 3.9.7, pytest-6.2.5, py-1.10.0, pluggy-1.0.0
```
Kiểm tra lại coverage report tại terminal:

```(venv)$Flask-Tutorial> coverage report```

```
(venv) PS C:\Users\Admin\Flask-Tutorial> coverage report
Name                    Stmts   Miss  Cover
flaskr\__init__.py         23      0   100%
flaskr\auth.py             60      0   100%
flaskr\blog.py             58      0   100%
flaskr\db.py               25      0   100%
tests\conftest.py          33      0   100%
tests\test_auth.py         30      0   100%
tests\test_blog.py         59      0   100%
tests\test_db.py           19      0   100%
tests\test_factory.py       7      0   100%
-------------------------------------------
TOTAL                     314      0   100%
```
Báo cáo HTML cho phép bạn xem dòng nào được bao gồm trong mỗi tệp:
```(venv)$ Flask-Tutorial>coverage html```
- Điều này tạo ra các tệp trong thư mục htmlcov. Mở htmlcov / index.html trong trình duyệt của bạn để xem báo cáo.