# HTML coding style guide

## Table of contents

+ [Indentation](#indentation)
+ [Doctype](#doctype)
+ [Be consistent in single quote, double quote](#be-consistent-in-single-quote-double-quote)
+ [Language attribute](#language-attribute)
+ [Character encoding](#character-encoding)
+ [IE compatibility mode](#ie-compatibility-mode)
+ [CSS and JavaScript includes](#css-and-javascript-includes)
+ [Self-closing](#self-closing)
+ [Optional closing tags](#optional-closing-tags)
+ [Semantic tags](#semantic-tags)
+ [Attribute order](#attribute-order)
+ [Boolean attribute](#boolean-attribute)
+ [Attribute value](#attribute-value)
+ [IDs vs. Classes](#ids-vs-classes)
+ [Paragraphs](#paragraphs)
+ [Tables](#tables)
+ [Input label](#input-label)
+ [Reducing markup](#reducing-markup)
+ [Accessibility](#accessibility)
+ [References](#references)


### Indentation

Sử dụng thụt đầu dòng với khoảng cách - đó là cách để bảo vệ những đoạn mã trả về như nhau ở mọi môi trường.
(Ưa thích: 4 spaces)


### Doctype

Thực thi chế độ tiêu chuẩn và trả về đồng nhất hơn ở mọi trình duyệt có thể với `doctype` đơn giản này tại lúc khởi đầu của mỗi trang HTML.

``` html
<!DOCTYPE html>
```


### Be consistent in single quote, double quote

Hãy đồng nhất khi sử dụng dấu nháy đơn hoặc dấu nháy kép cho thuộc tính.
(Ưa thích: dấu nháy kép "")


### Language attribute

Đặc tả một thuộc tính `lang` trên thành phần html gốc. Giúp cho các công cụ tổng hợp giọng nói xác định
phát âm đang sử dụng là gì, các công cụ dịch thuật xác định được qui tắc đang sử dụng là gì.

``` html
<html lang="en-us">
    <!-- ... -->
</html>
```


### Character encoding

Nhanh chóng và dễ dàng đảm bảo trả về đúng nội dung của bạn bằng việc khai báo một bảng mã ký tự rõ ràng. Khi làm như vậy, bạn có thể tránh sử dụng những thực thể ký tự trong HTML của bạn, cung cấp mã hóa cho nó phù hợp với tài liệu. (thường là UTF-8)

``` html
<head>
    <meta charset="UTF-8">
</head>
```


### IE compatibility mode

Trình duyệt IE hỗ trợ việc sử dụng thẻ `<meta>` có khả năng tương thích tài liệu để mô tả phiên bản của trình duyệt IE mà trang web nên được trả về là gì. Trừ trường hợp có yêu cầu khác nếu không, nó là hữu ích nhất để hướng dẫn trình duyệt IE sử dụng chế được hỗ trợ mới nhất với `edge mode`

``` html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```


### CSS and JavaScript includes

Theo đặc tả của HTML5, thường thì không cần phải chỉ rõ thuộc tính `type` khi chèn tập tin css hay javascript vào, như `text/css` và `text/javascript` là tương ứng mặc định của nó.

``` html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- JavaScript -->
<script src="code-guide.js"></script>
```


### Self-closing

Không thêm dấu gạch chéo (dấu xuyệt trái) vào những thành phần tự đóng như `img`, `link`, `input`, `meta` v.v...

__Bad__

``` html
<input type="text" name="input" />
<img src="logo.png" alt="Logo Company" />
```

__Good__

``` html
<input type="text" name="input">
<img src="logo.png" alt="Logo Company">
```


### Optional closing tags

Đừng bỏ qua việc đóng thẻ tùy chọn như `</li>`, `</body>`


### Semantic tags

HTML5 cung cấp cho chúng ta rất nhiều thành phần ngữ nghĩa mục đích để mô tả chính xác các nội dung. Chắc chắn rằng bạn hiểu ngữ nghĩa của các thành phần mà bạn đang sử dụng

__Bad__

``` html
<div id="main">
    <div class="article">
        <div class="header">
            <h1>Blog post</h1>
            <p>Published: <span>21st Feb, 2015</span></p>
        </div>
        <p>Lorem ipsum dolor sit amet</p>
    </div>
</div>
```

__Good__

``` html
<main>
    <article>
        <header>
            <h1>Blog post</h1>
            <p>Published: <time datetime="2015-02-21">21st Feb, 2015</time></p>
        </header>
        <p>Lorem ipsum dolor sit amet</p>
    </article>
</main>
```


### Attribute order

Thuộc tính HTML nên đến trong thứ tự đặc biệt này cho dễ dàng đọc mã:

1. `class`
2. `id`, `name`
3. `data-*`
4. `src`, `for`, `type`, `href`, `value`
5. `title`, `alt`
6. `role`, `aria-*`

``` html
<a class="..." id="..." data-toggle="modal" href="#">
    Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```


### Boolean Attribute

Thuộc tính boolean là một thuộc tính không cần phải khai báo giá trị. XHTML yêu cầu bạn phải khai báo 1 giá trị, nhưng HTML không yêu cầu như vậy.

``` html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
    <option value="1" selected>1</option>
</select>
```


### Attribute Value

Sử dụng dấu nháy để bao quanh tất cả giá trị của thuộc tính trong HTML, mặc dù dấu nháy là tùy chọn trong HTML5. Điều này duy trì sự đồng nhất giữa các giá trị của thuộc tính chứa khoảng trắng và không chưa khoảng trắng.

__Bad__

``` html
<form class="registration module" action=/register method=POST>
```

__Good__

``` html
<form class="registration module" action="/register" method="POST">
```


### IDs vs Classes

Các thành phần HTML được xác định bằng việc sử dụng các thuộc tính id và class. Một ID là một xác định cho thành phần đặc biệt, không có thành phần nào khác trên trang sử dụng cùng ID.

Sự độc đáo này cho phép các thành phần `<label>` liên kết chúng với 1 input đặc biệt và là đường dẫn để chuyển đến một vị trí di chuyển cụ thể trên một trang

Các class không là duy nhất. Những class giống nhau có thể được sử dụng trên nhiều thành phần trong 1 trang, và 1 thành phần đơn có thẻ có 1 hoặc hơn 1 class, trong một danh sách được giới hạn bởi khoảng trắng

``` html
<ul id="categories">
    <li class="category">Jackets</li>
    <li class="category specials">Accessories</li>
    <li class="category">Shoes</li>
</ul>
```


### Paragraphs

Tránh sử dụng thẻ `<br>` để tách rời các đoạn văn hay các dòng của đoạn text. Sử dụng thẻ `<p>` thay vì với việc mở và đóng các thẻ phù hợp.


### Tables

Bảng không nên được sử dụng cho việc chia bố cục của trang, chỉ nên sử dụng chúng khi bạn cần hiển thị bảng biểu.

Sử dụng thành phần `<thead>` và `<tbody>` để chỉ rõ hàng nào chứa tiêu đề của cột để khi 1 người dùng in ra trang web và bảng đó chạy trên trang khác thì trình duyệt có thể hiển thị `<thead>` trên mỗi trang cho dễ dàng đọc hơn. Nhớ sử dụng thuộc tính `scope` trên thành phần `<th>` để chỉ ra khi nào thì tiêu đề áp dụng cho các hàng hoặc cột.

``` html
<table>
    <thead>
        <tr>
            <th scope="col">Name</th>
            <th scope="col">Age</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John Doe</td>
            <td>33</td>
        </tr>
    </tbody>
</table>
```


### Input Label

Tất cả các trường input nên được liên kết với 1 thành phần `<label>`.Thuộc tính của thành phần `<label>`nên chứa id tương ứng với trường input. Điều này có nghĩa là trường input sẽ nhận trạng thái focus khi người dùng kích vào thành phần `<label>` và cũng như là cho phép đọc màn hình cho những người khiếm thị đọc 1 mô tả phù hơp với trường input đó.

__Bad__


``` html
<label>Home Address</label>
<input type="text">
```

__Good__

``` html
<label for="home-address">Home Address</label>
<input id="home-address" type="text">

<!-- Or -->

<label>
    <span>Home address</span>
    <inputtype="text">
</label>
```


### Reducing markup

Bất cứ khi nào có thể, tránh những thành phần mẹ dư thừa khi viết HTML. Nhiều lúc điều này yêu cầu phải lặp đi lặp lại và tái cấu trúc, nhưng sản xuất ra ít HTML hơn.

__Bad__

``` html
<span class="avatar">
    <img src="photo.jpg" alt="image">
</span>
```

__Good__

``` html
<img class="avatar" src="photo.jpg" alt="image">
```


### Accessibility

Khả năng tiếp cận không nên là một cách giải quyết đến sau. Bạn không phải là 1 chuyên gia WCAG để đi cải tiến website, nhưng bạn có thể bắt đầu ngay lập tức bằng việc sửa những thứ nhỏ mà lại tạo ra sự khác biệt lớn, chẳng hạn như:

+ Học sử dụng thuộc tính `alt` đúng.
+ Đảm bảo liên kết và các nút của bạn được đánh dấu như vậy
+ Không dựa hoàn toàn vào màu sắc để truyền đạt thông tin.
+ Ghi nhãn rõ ràng cho các điều khiển của biểu mẫu.

__Bad__

``` html
<h1><img src="logo.png" alt="Logo"></h1>
```

__Good__

``` html
<h1><img src="logo.png" alt="My Company, Inc."></h1>
```


### References

+ [Code Guide by @mdo](http://codeguide.co/#html)
+ [Some HTML, CSS and JS best practices](https://github.com/bendc/frontend-guidelines)
+ [Isobar Front-end Code Standards](http://isobar-idev.github.io/code-standards/)




