# Học NodeJs

<span style="color: red; font-size: 16px">**Bài 1: Nhập môn lập trình backend**</span>

# 1. Mô hình Client - Server

-   Là mô hình để các máy tính giao tiếp và truyền đạt dữ liệu với nhau
-   Client và Server có vai trò khác nhau => Dựa vào đó để phân biệt 2 thằng này

-   Client: Máy khách(PC: personal computer: laptop, máy bàn ,điện thoại ...)

    -   Là ông gửi yêu cầu đi

-   Server: Máy chủ (Thực chất cũng là PC nhưng mạnh mẽ hơn, chịu được dữ liệu lớn)

    -   Vai trò: Lưu trữ dữ liệu (Bản chất việc viết html, css, code,... trên máy tính thì máy tính chính là một server: VD trong VScode có nút live server khi code html)
    -   Ông nào tiếp nhận yêu cầu, xử lí trả về cho client thì được gọi là server
    -   EngineX, Apaches: Là những phần mềm để chạy web server(tạo ra chức năng đón nhận và phản hồi yêu cầu)
    -   Node, PHP
    -   Trong trường hợp ứng dụng là lớn hoặc rất lớn, người ta sẽ tách database ra một server riêng và lúc này server cũ lại tương tác với server của database => Lại tạo ra một mô hình client server

-   Khi Client truy cập vào một trang web thì sẽ có một yêu cầu (request message) được gửi đi đến server => Server nhận được yêu cầu này và xử lí thành các file html css image, ... rồi trả ngược lại(phản hồi: response) về phía Client => Client có trình duyệt và render ra website mà client truy cập

# 2. Domain(Tên miền)

-   Là địa chỉ website
-   Cấu trúc:
    -   Tên_miền.hậu_tố (VD: facebook.com)
    -   Miền_phụ.tên_miền.hậu_tố (VD: mail.google.com)
-   Hậu tố:
    -   1 từ: .com, .org, ...
    -   2 từ: .com.vn, edu.vn, ...
    -   Nếu hậu tố có một từ thì hậu tố đó là: Top level domain (TLD)
    -   Nếu hậu tố có hai từ thì Top level domain là thằng đầu tiên từ bên trái vào => Tiếp đến là second level domain(SLD)
-   Cấp của một domain sẽ nhỏ dần theo chiều từ nhỏ qua trái => Máy chủ quản lí domain sẽ theo mô hình phân cấp (hình cây)
-   Lẽ ra đứng trước top level domain còn có một thằng . (dấu chấm: gọi là root)
-   Root => TLD => SLD => DN => SDN
-   DNS: Domain name system
-   Thực tế Domain có tác dụng giúp dễ nhớ địa chỉ web thôi, nếu muốn truy cập trang web thì chỉ cần truy cập trực tiếp vào địa chỉ ip

<span style="color: red; font-size: 16px">**Bài 2: Http protocol**</span>

-   Khái niệm: Http protocol là cách thức mà website được truyền tải qua internet
-   Giả sử khi thực hiện truy cập vào một trang web, điều đầu tiên trình duyệt nó sẽ gửi đi một yêu câu(trang web được lưu trữ trên máy chủ), những hình ảnh, text, video, ... trong trang web sẽ được lưu trữ trong cơ sở dữ liệu của máy chủ.
-   Dựa vào url mà máy chủ biết nên trả về cái gì(trả về mã html trong source code của chúng ta)
-   Quản lí trong tab network(F12 trình duyệt) vào mục all
    -   Nếu request code gửi về đầu 200: Thành công, đầu 300: việc được cache hoặc không có sự thay đổi, những cái liên quan tới chuyển hướng
    -   remote address: là địa chỉ của máy chủ 172.67.162.2:443 (phần trước : là địa chỉ còn sau dấu : là port, có thể hiểu địa chỉ chính là con đường tới nhà chúng ta và port chính là số nhà => nó sẽ đi đến chính xác nơi mà ta lưu trữ dữ liệu)
    -   response headers: Phản hồi sau khi yêu cầu(chỉ có sau khi yêu câu gửi đi được xử lí)
    -   request headers: Những yêu cầu gửi đi
-   tab header chỉ nói lên những yêu cầu và phản hồi dạng "thông tin demo" (kiểu như mặt ngoài của phong bì thư)
-   phần chi tiết sẽ nằm ở phần tab response(nó nhận được dữ liệu đồng thời
    khi thằng reponse headers có dữ liệu). Đây là mã html dạng dữ liệu thuần
    túy (chuỗi) => Nó không thể hiển thị ra website , tuy nhiên trình duyệt được
    lập trình riêng để đọc hiểu các dữ liệu kiểu này => Nó sẽ tiến hành đọc và
    render ra trình duyệt

-   Bài tập:
    -   **Câu 1**: Website (HTML, CSS, Javascript, JSON, XML, static files, …) được truyền tải qua internet với giao thức nào?
        -   Trả lời: Giao thức Http
    -   **Câu 2**: Cách thức dữ liệu được gửi đi với giao thức HTTP được gọi là gì?
        -   Trả lời: Giao thức
    -   **Câu 3**: Cấu trúc tổng quát của HTTP response gồm những thành phần nào?
        -   Trả lời: gồm header và body
    -   **Câu 4**: Phát biểu nào sau đây là đúng khi nói về mã phản hồi của giao thức HTTP?
        -   Trả lời: Mã mang thông tin đầu 1xx, mã thành công đầu 2xx, mã chuyển hướng đầu 3xx, mã lỗi client đầu 4xx, mã lỗi server đầu 5xx
    -   **Câu 5**: Website truyền tải dữ liệu qua giao thức HTTP giữa máy khách và máy chủ theo mô hình nào?
        -   Trả lời: Mô hình client server

<span style="color: red; font-size: 16px">**Bài 3:SSR & CSR (Server side render & client side render**</span>

-   Phía dữ liệu trả về được render
-   Phân biệt một trang web sử dụng SSR hay CSR

    -   Sử dụng chuột phải + view page source, nếu những gì nhìn thấy trên trang web đều có trong dữ liệu trả về thì trang web này được sử dụng server side render

-   Server side rendering:

    -   Bạn request một trang web, server xử lý nội dung thành HTML, return lại cho browser hiển thị lại lên màn hình
    -   Ưu điểm: do trả về các content từ phía server nên tốt cho việc SEO
    -   Request đầu tiến sẽ nhanh hơn client side rendering do trả về trực tiếp mã html => trình duyệt có thể đọc và render ra ngay
    -   Nhược điểm: các lần request sau vẫn nặng

-   Client side rendering:

    -   Ban đầu nó cũng có một chút xử lí server side rendering, nhưng server chỉ trả về một thẻ div(hoặc thẻ main) trống, hoặc rất ít code
        => Lúc này trình duyệt phải bật js để render(append) ra các thẻ html để render ra trang web
    -   Ưu điểm: tăng trải nghiệm người dùng do các lần render sau rất nhanh
    -   Nhược điểm: Không hỗ trợ SEO
        -   Lần đầu render chậm hơn do phải đọc file js rồi nhận mã html từ đó trình duyệt mới bắt đầu thực hiện render ra màn hình

-   Trang web kết hợp cả Server side rendering và client side rendering bằng cách sử dụng Server side rendering khi cần yếu tố SEO, và những chỗ không cần thì sử dụng thăng còn lại

<span style="color: red; font-size: 16px">**Bài 4:Install Node**</span>

-   NodeJs là một nền tảng js được xây dựng trên chrom v8 js engine(Bời js là một ngôn ngữ thông dịch, nó có thể chạy mà không cần phải build ra thành các mã nhị phân và chrom v8 js engine sẽ giúp chúng ta chạy file js trên trình duyệt)
-   NodeJs cũng như js, nó có thể chạy trực tiếp trên server nhờ thằng chrom v8 js engine

<span style="color: red; font-size: 16px">**Bài 5:Install ExpressJS**</span>

-   Các bước khởi tạo Nodejs
    -   trỏ vào tên folder và chạy: npm init

<span style="color: red; font-size: 16px">**Bài 6:Install Nodemon and inspector**</span>

-   Nodemon: lắng nghe sự thay đổi trong code của chúng ta và tự động chạy lại
    -   Cài trong sự phát triển: npm i nodemon --save-dev

<span style="color: red; font-size: 16px">**Bài 7: Add git repo**</span>

<span style="color: red; font-size: 16px">**Bài 8: install Morgan**</span>

-   Quan sát các log request từ client lên node server

<span style="color: red; font-size: 16px">**Bài 9: Template engine (handlebars)**</span>

-   Giúp ta viết ra những file chứa html ở những nơi khác gọn gàng hơn, có thể chia layout và đạt được
    hiệu quả giống như việc viết html bình thường
-   Cài đặt package: npm i express-handlebars

-   Ví dụ:

    -   Ta có cấu trúc thư mục sau:
        -   src
            -   resources
                -   scss
                -   views
                    -   layouts
                        -   main.hbs
                    -   partials
                        -   footer.hbs
                        -   header.hbs
                    -   home.hbs
                    -   news.hbs
        -   index.js

-   Code:

```html
<!-- main.hbs -->
<html>
    <head>
        <meta charset="utf-8" />
        <title>Example App</title>
    </head>
    <body>
        <div class="app">
            {{> header}}
            <div class="main">{{{body}}}</div>
            {{> footer}}
        </div>
    </body>
</html>
```

```html
<!-- footer.hbs -->
<h1>this is footer</h1>
<!-- header.hbs -->
<h1>this is header</h1>
```

```html
<!-- home.hbs -->
<h1>Example App: Home</h1>
<!-- news.hbs -->
<h1>News</h1>
```

```js
// index.js
const express = require('express');
const morgan = require('morgan');
const { engine } = require('express-handlebars');
const path = require('path');

const app = express();
const port = 3000;

// template engine
app.engine('.hbs', engine({ extname: '.hbs' }));
app.set('view engine', '.hbs');
app.set('views', path.join(__dirname, 'resources/views'));

// http logger
app.use(morgan('combined'));

app.get('/', (req, res) => {
    res.render('home');
});

app.get('/news', (req, res) => {
    res.render('news');
});

app.listen(port, () => {
    console.log('localhost:' + port);
});
```

<span style="color: red; font-size: 16px">**Bài 10: Static file and Scss**</span>

-   Cấu trúc thư mục:
-   Ta có cấu trúc thư mục sau: - src - public - imgs - girl.jpg
    => Từ trình duyệt ta có thể truy cập như sau để lấy ảnh: http://localhost:3000/imgs/girl.jpg

```js
app.use(express.static(path.join(__dirname, 'public')));
// lưu ý: Lúc này path của chúng ta đang xuất phát từ public rồi nhé :>
```

<span style="color: red; font-size: 16px">**Bài 11: Bootstrap**</span>

<span style="color: red; font-size: 16px">**Bài 12: Basic routing**</span>

-   Đây là cách đơn giản để định nghĩa ra một tuyến đường để truy cập vào trang web của mình

```js
app.get('/', (req, res) => {
    res.render('home');
});
```

-   req: request (yêu cầu): Chứa các thông tin mà ứng dụng gửi lên server
-   res: response (phản hồi): Khi server nhận được yêu cầu thì nó sẽ xử lí và nó sẽ chọc vào database để lấy dữ liệu và trả về cho client
    -   Dùng để customize những gì được phản hồi (Có thể tùy chọn những gì trả về từ server)
    -   Việc mà quyết định trả về mã status code hay response là gì (Có thể sử dụng biến res)

<span style="color: red; font-size: 16px">**Bài 13: GET method**</span>

-   Đây là một phương thức trong giao thức http
-   Khi chúng ta click vào một thẻ a hay truy cập vào một trang web nào đó thì mặc định trình duyệt
    sẽ gửi đi một phương thức là GET(Trình duyệt tự request lên server)
-   Trong phương thức GET thì Server sẽ phân biệt được thông qua path đằng sau domain (route) để
    phân biệt request gửi lên server là gì

<span style="color: red; font-size: 16px">**Bài 14: Query parameters**</span>

-   Là khái niệm giúp chúng ta có thể truyền giữ liệu thông qua chính cái url
-   Ví dụ: "https://www.google.com/search?q=f8&ref=edu&author=sondn"
    -   Cái param đầu tiên bắt đầu từ dấu ?, nhưng param sau cách nhau bởi dấu &
    -   Mọi method như GET, POST, PUT, ... Đều có thể sử dụng query parameter, tuy nhiên nó
        thường được sử dụng nhiều nhất với GET vì đây là cách đơn giản nhất để truyền dữ liệu
        những phương thức còn lại có hỗ trợ cách truyền dữ liệu khác

<span style="color: red; font-size: 16px">**Bài 15: Form default behavior(hành vi mặc định của form trong html**</span>

```js
app.get('/search', (req, res) => {
    res.render('search');
});
```

```html
<div style="padding: 0 30px" class="mt-5">
    <form>
        <div class="mb-3">
            <label for="search" class="form-label">Nhập để tìm kiếm</label>
            <input placeholder="Nhập từ khóa..." name="q" class="form-control" id="search" />
        </div>
        <button type="submit" class="btn btn-primary">Tìm kiếm</button>
    </form>
</div>
```

-   Khi chúng ta bấm submit thì trình duyệt tự động gửi request GET lên server
-   Lúc này URL tự động đổi thành `http://localhost:3000/search?${inputName}=${inputValue}`
    Và trong trường hợp này nó sẽ là: http://localhost:3000/search?q=a (Nếu nhập a vào ô input)
-   Tương tự nếu nhiều input có name khác nhau
-   Mặc định thằng form sẽ có một attribute là method="GET"
-   Nếu muốn khi bấm submit thì form sẽ gửi yếu cầu post, put hay path thì ghi vào method tương ứng,
    Nhớ phải định nghĩa tuyến đường cho nó nhé!
-   Ví dụ muốn method là post thì phải định nghĩa

```js
app.post('/search', (req, res) => {
    res.render('search');
});
```

=> Lúc này khi submit form thì nó sẽ gọi một request POST lên server,
và kể từ lúc này ta refresh lại trang thì nó vẫn luôn gọi lên server request POST
cho đến khi để con trỏ chuột lên url và ấn enter(để trình duyệt load lại) thì nó trở về GET

**Lưu ý**: Khi bấm submit thì mặc định form sẽ tìm kiếm ở url hiện tại trên trình duyệt, nó chỉ thêm phần param đằng sau.

=> Vậy muốn đang ở trang hiện tại, khi bấm submit thì nó sẽ sang url khác thì làm thế nào?

-   Trong form có một attribute là action="", Nó sẽ quyết định nơi submit của chúng ta, Nếu không có attribute này thì mặc định nó là vậy, còn nếu chỉ định action thì nó sẽ submit nơi chúng ta mong muốn

-   Ví dụ: Ta đang ở trên url: http://localhost:3000/search

```html
<div style="padding: 0 30px" class="mt-5">
    <form method="GET" action="/news">
        <div class="mb-3">
            <label for="search" class="form-label">Nhập để tìm kiếm</label>
            <input placeholder="Nhập từ khóa..." name="q" class="form-control" id="search" />
        </div>
        <button type="submit" class="btn btn-primary">Tìm kiếm</button>
    </form>
</div>
```

=> Sau khi bấm submit thì url sẽ là: http://localhost:3000/news?q=check

check chính là giá trị tìm kiếm trong ô input

<span style="color: red; font-size: 16px">**Bài 16: POST Method**</span>

-   Sử dụng khi muốn gửi dữ liệu từ phía client lên server
-   Trong GET method, khi bấm submit một form thì toàn bộ dữ liệu sẽ được đưa lên thanh url => không an toàn nếu như người dùng nhập mật khẩu

=> Lúc này cần sử dụng POST method

```js
app.post('/search', (req, res) => {
    console.log(req.body); //undefined (Sử dụng khi dùng POST method)
    res.send('');
});
```

-   Tạo sao khi log req.body lại ra undefined nhưng dùng req.query lại được

=> Trước tiên cần hiểu luồng code chạy, nó sẽ chạy như sau:

-   (Web brower => midleware => controller => web browser)
-   Thằng GET được express hỗ trợ sẵn cái midleware rồi còn POST thì không
    => Cần tích hợp middleware khi sử dụng POST như sau: (Thằng express đã hỗ trợ)

```js
// Khi submit mặc định bằng html
app.use(express.urlencoded());
// Khi sử dụng Js submit, hoặc thư viện nào đó viết bằng JS (XMLHttpRequest/ fetch/ axios/...)
app.use(express.json());
```

=> Lúc này đã có xuất hiện req.body

-   Tuy nhiên xuất hiện một waring: "body-parser deprecated undefined extended: provide extended option"

=> Fix: bằng cách thêm extended cho urlencoded

```js
app.use(express.urlencoded({ extended: true }));
```

**Note**:

-   Trong quá trình xử dụng thì ta dùng phương thức GET để gửi yêu cầu lên server ý muốn nói rằng "Tôi cần lấy data về client, server trả cho tôi đi".

-   Phương thức POST thì "Tôi mang data từ client lên cho ông đây server, lưu lại đi".

<span style="color: red; font-size: 16px">**Bài 17: Mô hình MVC**</span>

-   MVC là từ viết tắt bởi 3 từ Model – View – Controller. Đây là mô hình thiết kế sử dụng trong kỹ thuật phần mềm. Mô hình source code thành 3 phần, tương ứng mỗi từ. Mỗi từ tương ứng với một hoạt động tách biệt trong một mô hình.

-   View: được hiểu là thành phần chỉ chứa nội dung hiển thị (html)
-   Model: Là thành phần tương tác với resource(lấy ra dữ liệu)
-   Controller: là thành phần trung chuyển giữa view và modal

=> Cách hoạt động của mô hình MVC: khi người dùng gõ một trình duyệt vào trong website thì nó sẽ gửi request tới server bằng http => Đi lên web server => Routes (chính là tầng định tuyến) => Thằng Routes này sẽ thực hiện một hành vi dispatcher (hành vi gọi tới controller)
=> Controller sẽ tương tác với model để lấy ra dữ liệu => Gọi tới View tương ứng và xử lí kết hợp với dữ liệu đã được lấy => Trả về cho phía client qua web server (bằng http protocol) => Brower nhận được và trả ra website

=> Mô hình MVC bóc tách rõ ràng các thành phần chính

<span style="color: red; font-size: 16px">**Bài 18: [MVC] Routes & Controllers**</span>

-   Hosting là nơi lưu trữ
-   local host & hosting: đều là server

-   Giải thích mô hình MVC

    -   Việc truy cập vào một trang web từ máy tính là mình đang thực hiện gửi một resquest lên web server
    -   Khi chúng ta start ứng dụng lên thì node sẽ chọc vào index.js và nạp toàn bộ file đó vào trong bộ nhớ ram
    -   Ứng dụng của chúng ta đã có thằng express hỗ trợ nên việc sử dụng app.methodName(routes, ...) là đang thực hiện tới bước routes
    -   Khi ứng dụng của chúng ta kiếm tra thấy url đang match với phương thức mà chúng ta định nghĩa trong routes thì nó sẽ thực thi function handler
    -   action => dispatcher => function handler(controller)

-   Tổ chức lại file theo mô hình MVC:
-   Cấu trúc file:
    -   src
        -   app
            -   controllers
                -   NewController.js
                -   SiteController.js
            -   public(chứa css, image, ...)
            -   resources
                -   Scss
                -   views
                    -   layouts
                        -   main.hbs
                    -   partials
                        -   footer.hbs
                        -   header.hbs
                    -   news.hbs
                    -   search.hbs
            -   routes
                -   index.js
                -   news.js
                -   site.js
    -   index.js

```js
// NewController.js
class NewsController {
    // [GET]/ news
    index(req, res) {
        res.render('news');
    }
    // [GET]/ news/:slug
    show(req, res) {
        res.send('New Details');
    }
}

module.exports = new NewsController();

// SiteController.js
class SiteController {
    // [GET]/
    index(req, res) {
        res.render('home');
    }

    // [GET]/search
    search(req, res) {
        res.render('search');
    }
}

module.exports = new SiteController();

// routes/index.js
const newsRouter = require('./news');
const siteRouter = require('./site');

function route(app) {
    app.use('/news', newsRouter);
    app.use('/', siteRouter);
}

module.exports = route;

// routes/news.js
const express = require('express');
const router = express.Router();
const newsController = require('../app/controllers/NewsController');

router.use('/:slug', newsController.show);
router.use('/', newsController.index);

module.exports = router;

// routes/site.js
const express = require('express');
const router = express.Router();
const siteController = require('../app/controllers/SiteController');

router.use('/search', siteController.search);
router.use('/', siteController.index);

module.exports = router;

// src/index.js
// require from library
const express = require('express');
const morgan = require('morgan');
const { engine } = require('express-handlebars');
const path = require('path');
const route = require('./routes');
const app = express();
const port = 3000;

// file static as css, img, ... is started at public/...
app.use(express.static(path.join(__dirname, 'public')));
// Khi submit mặc định bằng html
app.use(express.urlencoded({ extended: true }));
// Khi sử dụng Js submit, hoặc thư viện nào đó viết bằng JS (XMLHttpRequest/ fetch/ axios/...)
app.use(express.json());

// template engine
app.engine('.hbs', engine({ extname: '.hbs' }));
app.set('view engine', '.hbs');
app.set('views', path.join(__dirname, 'resources/views'));

// http logger
app.use(morgan('combined'));

// Routes init
route(app);

// listen port
app.listen(port, () => {
    console.log('localhost:' + port);
});
```

-   File Site sẽ là nơi chứa những page không có slug path nào nữa
-   Ví dụ trong news còn có details news => Nó sẽ được tách trong một tệp riêng
-   Code được cập nhật lên github

<span style="color: red; font-size: 16px">**Bài 19: Cài đặt MongoDB**</span>

<span style="color: red; font-size: 16px">**Bài 20: Prettier - Code formatter**</span>

-   Lint-staged: Giúp chạy một command được add vào git
-   husky: Cung cấp những cái hooks: Khi sử dụng git chúng ta có những hành động như là push, commit, ...
    => Lúc này nó sẽ làm một việc gì đó

<span style="color: red; font-size: 16px">**Bài 21: (MVC) Model**</span>

-   Các bước

    -   Install mongoose
    -   Connect to DB
    -   Create Model

-   MongoDB conpass nó là một client để giúp connect tới server mongoDB
-   MongoDB không lưu dữ liệu dưới dạng bảng mà lưu ở dạng documents(json)
-   Install Mongoose: Object Model Driver: là trình điều khiển(hãy tưởng tượng nó đứng giữa node và mongoDB để làm việc dễ dàng hơn).
-   Trong MySQL mỗi một trường đều có cấu trúc dữ liệu như nhau, tuy nhiên trong thằng MongoDB, mỗi document có thể có cấu trúc dữ liệu khác nhau.
    => Thằng mongoose sẽ đối tượng hóa document để tạo nên các field chặt chẽ hơn(Nên để các documents có cấu trúc giống nhau)
-   Mongoose được thiết kế để làm việc trong môi trường bất đồng bộ, nó có thể làm việc với callback và promise

<span style="color: red; font-size: 16px">**Bài 22: Install JSON viewer and review**</span>

-   Chức năng: Xem file Json dễ nhìn hơn là json thuần túy.
-   Phân biệt giữa app.get và app.use
    -   app.use(VD: app.use("/news", newsRouter)) Sử dụng use khi tất cả tuyến đường sẽ đưuọc match khi bắt đầu bằng /news, Nếu là /news/abc... thì vẫn truy cập được bình thường
    -   app.get(VD: router.get('/details', newsController.show);) Sử dụng để gửi yêu cầu GET khi url match cố định với /details

<span style="color: red; font-size: 16px">**Bài 23: [CRUD] Read from DB**</span>

-   Khi render dữ liệu có object => Chúng ta không thể truy cập trực tiếp vào các property của nó được do lỗi bảo mật

=> Cần chỉnh sửa lại object trước khi thực hiện render

<span style="color: red; font-size: 16px">**Bài 24: Course detail page**</span>

<span style="color: red; font-size: 16px">**Bài 25: [CRUD] Create new course**</span>

<span style="color: red; font-size: 16px">**Bài 26: [CRUD] Update course**</span>

-   GET: Gửi yêu cầu lên server, yêu cầu server trả lại dữ liệu cho client
-   POST: Gửi yêu cầu lên server, yêu cầu server lưu lại dữ liệu(Tạo mới dữ liệu)
-   PUT/ PATCH: Thường được dùng để chỉnh sửa dữ liệu

    -   PUT: replace từng document
    -   PATCH: Sửa từng field
    -   detete: Xóa

-   method trong form chỉ hỗ trợ method là POST hoặc GET, nếu khác 2 cái này thì mặc định nó là GET

=> download npm install method-override để overide lại khi sử dụng các method khác 2 method được quy định

<span style="color: red; font-size: 16px">**Bài 27: [CRUD] Delete course**</span>

<span style="color: red; font-size: 16px">**Bài 28: Soft delete?**</span>

-   Kĩ thuật xóa mềm: Chỉ mất đi ở mặt giao diện nhưng trong DB vẫn có
-   Khi nào sử dụng kĩ năng xóa mềm:
    -   Khi cần đối soát, truy vết
    -   Liên quan tới đơn hàng, tiền tệ, tài liệu nhạy cảm
-   Các chức năng cần phát triển với soft delete
    -   delete(soft)
    -   restore
    -   force delete
-   Cài đặt thư viện mongoose soft delete: npm i mongoose-delete

-   Create => POST
-   Update => PUT, PATCH
-   Delete => DELETE
-   Read => GET

<span style="color: red; font-size: 16px">**Bài 29: Deleted count documents**</span>

<span style="color: red; font-size: 16px">**Bài 30: "Select all" with checkbox**</span>

-   Lưu ý: Không được sử dụng form trong một form khác nhé ;>
-   Khi chúng ta không biết hành vi xác định của form là gì thì để POST method

<span style="color: red; font-size: 16px">**Bài 31: Middleware**</span>

-   Là phần mềm trung gian (đứng giữa các thành phần trong mô hình phần mềm)
-   Brower(Client) ==== Request ====> Server(Node)
-   Brower(Client) <=== Reponse ===== Server(Node)

=> Các thành phần đứng giữa 2 thành phần và có nhiệm vụ như một "bác bảo vệ" là middleware

-   Ví dụ dễ hiểu hơn:
-   Nhà ========> Bác bảo vệ 1(middleware): Bác bảo vệ 2(middleware)... :Sự kiện
-   Nhà <======== Sự kiện

1. Soát vé (Chức năng của bác bảo vệ, tương tự như một middleware) => validation
2. Không cho phép vào
3. Cho phép vào (validation passed => Cho vào)
4. Thay đổi/ Chỉnh sửa

-   Một ví dụ cụ thể về middleware
-   Thứ tự của các middleware là quan trọng
-   middleware của path này không bao giờ ảnh hưởng đến path khác

```js
app.get(
    '/middleware',
    // Có thể có nhiều function là tương ứng với một middleware
    function (req, res, next) {
        if (['ve_thuong', 've_vip'].includes(req.params.ve)) {
            // Sửa đổi gì đó trước khi cho chạy tới middleware tiếp theo
            req.face = 'gach gach gach!!!';
            return next(); // hàm next có vai trò chuyển tiếp tới middleware tiếp theo, nếu không có thì nó vẫn sẽ mãi ở middleware này
        }
        res.status(403).json({
            message: 'Access denied',
        });
    },
    function (req, res, next) {
        res.json({
            message: 'Successfully',
            face: req.face,
        });
    }
);
```

-   Các ví dụ trên là middleware áp dụng lên một path cụ thể => Nếu muốn nó áp dụng lên toàn bộ trang web thì làm như sau:
    -   Bình thường các middleware sẽ được tách ra thành các file riêng, Khi muốn sử dụng thì chỉ cần import vào

```js
// Ta có một function (middleware)
// app.use không định nghĩa một path nên bất kì phương thức cùng với path bất kì đều phải lọt vào đây
app.use(bacBaoVe);
// app.use("middleware", bacBaoVe);     => Nếu nó định nghĩa một path thì bất kì phương thức (get, post, ...) có path trùng đều phải lọt vào đây
function bacBaoVe(req, res, next) {
    if(["ve_thuong", "ve_vip"].includes(req.params.ve)) {
        // Sửa đổi gì đó trước khi cho chạy tới middleware tiếp theo
        req.face = "gach gach gach!!!";
        return next(); // hàm next có vai trò chuyển tiếp tới middleware tiếp theo, nếu không có thì nó vẫn sẽ mãi ở middleware này
    }
    res.status(403).json({
        message: "Access denied"
    })
},
```

=> Ứng dụng của middleware - Chức năng xác thực, phân quyền, để chia sẻ các giá trị của biến tới tất cả các views

<span style="color: red; font-size: 16px">**Bài 32: Sort Middleware**</span>

-   Khi sử dụng res.locals... thì biến đó sẽ nằm trong views => Chúng ta có thể sử dụng từ views

<span style="color: red; font-size: 16px">**Bài 33: Sort query helper**</span>

<span style="color: red; font-size: 16px">**Bài 34: Auto increment id field**</span>

-   Sử dụng thư viện mongoose sequence
