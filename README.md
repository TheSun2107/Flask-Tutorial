# Flask-Tutorial
Bài viết này được lấy từ <a href="https://flask.palletsprojects.com/">trang chủ</a> của Flask.
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
<a name="Huongdan"></a>
Phần này Flask hướng dẫn sử dụng các thành phần chính khi xây dựng ứng dụng.
Các bạn có thể xem trực tiếp trên trang chủ Flask.
## IV. Hướng dẫn
Trong hướng dẫn này mình sử dụng HDH Windows 10 và Visual Studio Code(1.61.2)
<a name="Bocucduan"></a>
### 1. Bố cục dự án
#### Đầu tiên hãy cài đặt Python nhé:

Phiên bản python mình sử dụng: <a href="https://www.python.org/downloads/release/python-397/">Python 3.9.7</a>

#### Khởi tạo thư mục chính:
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
<a name="Thietlapungdung"></a>
### 2. Thiết lập ứng dụng
Như mình đã giới thiệu bài viết này là tutorial chính thức của Flask, nên hãy làm theo Flask để đạt được sự tối ưu nhất cho ứng dụng.

#### Khởi tạo thư mục chứa ứng dụng

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

#### Khởi chạy ứng dụng lần đầu tiên:
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

<a name="Sudungcosodulieu"></a>
### 3. Sử dụng cơ sở dữ liệu
Ứng dụng sẽ sử dụng SQLite để lưu trữ người dùng( user) và bài đăng( post). SQLite tiện lợi vì nó được tích hợp sẵn trong Python. Tuy nhiên nó sẽ chậm một chút nếu các yêu cầu ghi vào cơ sở dữ liệu xảy ra đồng thời. Với ứng dụng nhỏ sẽ không nhận ra điều này tuy nhiên khi ứng dụng trở nên lớn hơn, bạn sẽ muốn chuyển qua một cơ sở dữ liệu khác.

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
 
 #### Blueprint: Mẫu
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

#### Đầu tiên hãy tạo một trang đăng nhập và đăng kí

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
- @bp.route('/register'..) Tạo một liên kết với URL và hàm xử lý nó.
- Nếu người dùng đã gửi biểu mẫu với request.method là 'POST' thì hãy bắt đầu xác thực input.
- request.form sẽ lấy giá trị người dùng nhập vào gồm "username" và "password" Nếu thành công sẽ ghi người dùng mới vào cơ sở dữ liệu.
- db.execute() sẽ đảm bảo rằng SQL của bạn khỏi hình thức tấn công SQL Injection.
- create_password_hash() để bảo mật không lưu password dưới dạng text trong cơ sở dữ liệu.
- Lỗi sqlite3.IntegrityError sẽ xảy ra nếu tên người dùng đã tồn tại, điều này sẽ được hiển thị cho người dùng dưới dạng một lỗi xác thực khác.
- Sau đó user được chuyển đến trang đăng nhập với url_for(). Điều này tốt hơn là viết URL trực tiếp vì nó cho phép bạn thay đổi URL sau này mà không cần thay đổi tất cả mã liên kết đến nó. redirect () tạo phản hồi chuyển hướng đến URL đã tạo.
- Nếu xác thực không thành công, lỗi sẽ được hiển thị cho người dùng. flash() lưu trữ các thông báo có thể được truy xuất khi hiển thị template.
- Khi người dùng ban đầu điều hướng đến auth / register hoặc có lỗi xác thực, một trang HTML có biểu mẫu đăng ký sẽ được hiển thị.

#### Tiếp theo là phần Login

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
- @bp.route('/login') tương tự như register khi người dùng truy cập đường dẫn /auth/login nó sẽ gọi đến hàm xử lý URL đó.
- Người dùng được truy vấn đầu tiên và được lưu trữ trong một biến để sử dụng sau này.
- fetchone() trả về một hàng từ truy vấn. Nếu truy vấn không trả về kết quả, nó sẽ trả về Không có. Sau đó, hàm fetchall() sẽ được sử dụng, nó sẽ trả về một danh sách tất cả các kết quả.
- check_password_hash() băm mật khẩu đã gửi theo cách giống như băm được lưu trữ và so sánh chúng một cách an toàn. Nếu chúng khớp, mật khẩu hợp lệ.
- session là một mệnh lệnh lưu trữ dữ liệu qua các yêu cầu. Khi xác thực thành công, id của người dùng được lưu trữ trong một phiên mới. Dữ liệu được lưu trữ trong một cookie được gửi đến trình duyệt và sau đó trình duyệt sẽ gửi lại dữ liệu đó với các yêu cầu tiếp theo. Flask ký vào dữ liệu một cách an toàn để dữ liệu đó không thể bị giả mạo.

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
- bp.before_app_request() đăng ký một hàm chạy trước hàm xem, bất kể URL nào được yêu cầu. load_logged_in_user kiểm tra xem id người dùng có được lưu trữ trong phiên hay không và lấy dữ liệu của người dùng đó từ cơ sở dữ liệu, lưu trữ trên g.user, kéo dài trong thời gian yêu cầu. Nếu không có id người dùng hoặc nếu id không tồn tại, g.user sẽ là None.
- Để đăng xuất, bạn cần xóa id người dùng khỏi phiên. Sau đó load_logged_in_user sẽ không tải người dùng trong các yêu cầu tiếp theo.

#### Xác thực
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
#### Xử lý các trang hiển thị
Phần trên chúng ta mới xử lý xong việc Flask sẽ làm việc như thế nào với cơ sở dữ liệu, tuy nhiên có một số chỗ cần để ý tới: khi auth yêu cầu trả về register.html, login.html, index.html.
Để hiểu được phần này bạn cần có chút kiến thức về Jinja nữa nhé.
Các file HTML chúng ta sẽ lưu toàn bộ vào folder templates để dễ dàng quản lý.
Hầu hết các trang web sẽ có một cấu trúc cố định và giống nhau khi truy cập từng tính năng trong đó, để giảm thiểu dòng code và tăng tốc cho Flask ta sẽ sử dụng một cấu trúc chung cho trang web là base.html
##### Cấu trúc chung
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
- g tự động có sẵn trong các templates. Dựa trên nếu g.user được đặt (từ load_logged_in_user), tên người dùng và liên kết đăng xuất được hiển thị hoặc các liên kết để đăng ký và đăng nhập được hiển thị. url_for() cũng tự động có sẵn và được sử dụng để tạo URL cho các chế độ xem thay vì viết chúng ra theo cách thủ công.
- Sau tiêu đề trang và trước nội dung, mẫu lặp lại từng thông báo được trả về bởi get_flashed_messages(). Bạn đã sử dụng flash() trong các dạng xem để hiển thị thông báo lỗi và đây là mã sẽ hiển thị chúng.
- {% block title%} sẽ thay đổi tiêu đề được hiển thị trong tab và tiêu đề cửa sổ của trình duyệt.
- {% block header%} tương tự như title nhưng sẽ thay đổi tiêu đề hiển thị trên trang.
- {% block content%} là nơi chứa nội dung của mỗi trang, chẳng hạn như biểu mẫu đăng nhập hoặc một bài đăng trên blog.
##### Trang đăng kí
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
##### Trang đăng nhập
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

Note: Hãy lưu ý phần FLASK_APP nhé.

#### Trang chủ

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
#### Create
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
#### Update
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
- abort() sẽ đưa ra một ngoại lệ đặc biệt trả về mã trạng thái HTTP. Nó cần một thông báo tùy chọn để hiển thị cùng với lỗi, nếu không, một thông báo mặc định sẽ được sử dụng. 404 có nghĩa là "Not Found" và 403 có nghĩa là "Forbidden". (401 có nghĩa là “Unauthorized”, nhưng bạn chuyển hướng đến trang login thay vì trả lại trạng thái đó.)
- check_author được định nghĩa để hàm có thể được sử dụng để lấy một post mà không cần kiểm tra tác giả. Điều này sẽ hữu ích nếu bạn viết một lượt xem để hiển thị từng post trên một trang, nơi người dùng không quan trọng vì họ không sửa đổi bài đăng.
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

- Mẫu {{request.form['title'] hoặc post['title']}} được sử dụng để chọn dữ liệu xuất hiện trong form. Khi form chưa được gửi, dữ liệu post ban đầu sẽ xuất hiện, nhưng nếu dữ liệu post không hợp lệ đã được đăng, bạn muốn hiển thị dữ liệu đó để user có thể sửa lỗi, do đó, request.form sẽ được sử dụng thay thế. yêu cầu là một biến khác tự động có sẵn trong các templates.
#### Delete
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

Note: Hãy để ý đến (venv) và FLASK_APP.