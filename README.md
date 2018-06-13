# reactjs
learn reactjs

## Giới thiệu

React.js là một thư viện Javascript đang nổi lên trong những năm gần đây với xu hướng Single Page Application. Trong khi những framework khác cố gắng hướng đến một mô hình MVC hoàn thiện thì React nổi bật với sự đơn giản và dễ dàng phối hợp với những thư viện Javascript khác. Nếu như AngularJS là một Framework cho phép nhúng code javasscript trong code html thông qua các attribute như ng-model, ng-repeat...thì với react là một library cho phép nhúng code html trong code javascript nhờ vào JSX, bạn có thể dễ dàng lồng các đoạn HTML vào trong JS.

React là một thư viện UI phát triển tại Facebook để hỗ trợ việc xây dựng những thành phần (components) UI có tính tương tác cao, có trạng thái và có thể sử dụng lại được.

Một trong những điểm hấp dẫn của React là thư viện này không chỉ hoạt động trên phía client, mà còn được render trên server và có thể kết nối với nhau. React so sánh sự thay đổi giữa các giá trị của lần render này với lần render trước và cập nhật ít thay đổi nhất trên DOM.

## Khái niệm cơ bản

### Virtual DOM:

Công nghệ DOM ảo giúp tăng hiệu năng cho ứng dụng.

Việc chỉ node gốc mới có trạng thái và khi nó thay đổi sẽ tái cấu trúc lại toàn bộ, đồng nghĩa với việc DOM tree cũng sẽ phải thay đổi một phần, điều này sẽ ảnh hưởng đến tốc độ xử lý.

ReactJS sử dụng Virtual DOM (DOM ảo) để cải thiện vấn đề này. Virtual DOM là một object Javascript, mỗi object chứa đầy đủ thông tin cần thiết để tạo ra một DOM, khi dữ liệu thay đổi nó sẽ tính toán sự thay đổi giữa object và tree thật, điều này sẽ giúp tối ưu hoá việc re-render DOM tree thật.

React sử dụng cơ chế one-way data binding – luồng dữ liệu 1 chiều. Dữ liệu được truyền từ parent đến child thông qua props. Luồng dữ liệu đơn giản giúp chúng ta dễ dàng kiểm soát cũng như sửa lỗi.

Với các đặc điểm ở trên, React dùng để xây dựng các ứng dụng lớn mà dữ liệu của chúng thay đổi liên tục theo thời gian. 

### Props và State:

Props: giúp các component tương tác với nhau, component nhận input gọi là props, và trả thuộc tính mô tả những gì component con sẽ render. Prop là bất biến.

State: thể hiện trạng thái của ứng dụng, khi state thay đồi thì component đồng thời render lại để cập nhật UI.

### Components:

React được xây dựng xung quanh các component, chứ không dùng template như các framework khác.

Trong React, chúng ta xây dựng trang web sử dụng những thành phần (component) nhỏ. Chúng ta có thể tái sử dụng một component ở nhiều nơi, với các trạng thái hoặc các thuộc tính khác nhau, trong một component lại có thể chứa thành phần khác. Mỗi component trong React có một trạng thái riêng, có thể thay đổi, và React sẽ thực hiện cập nhật component dựa trên những thay đổi của trạng thái. Mọi thứ React đều là component. Chúng giúp bảo trì mã code khi làm việc với các dự án lớn. Một react component đơn giản chỉ cần một method render. Có rất nhiều methods khả dụng khác, nhưng render là method chủ đạo.

### JSX

JSX là một dạng ngôn ngữ cho phép viết các mã HTML trong Javascript.
***Đặc điểm:***

- Faster: Nhanh hơn.

> JSX thực hiện tối ưu hóa trong khi biên dịch sang mã Javacsript. Các mã này cho thời gian thực hiện nhanh hơn nhiều so với một mã tương đương viết trực tiếp bằng Javascript.

- Safer: an toàn hơn.

> Ngược với Javascript, JSX là kiểu statically-typed, nghĩa là nó được biên dịch trước khi chạy, giống như Java, C++. Vì thế các lỗi sẽ được phát hiện ngay trong quá trình biên dịch. Ngoài ra, nó cũng cung cấp tính năng gỡ lỗi khi biên dịch rất tốt.

- Easier: Dễ dàng hơn.

> JSX kế thừa dựa trên Javascript, vì vậy rất dễ dàng để cho các lập trình viên Javascripts có thể sử dụng (tham khảo tại https://jsx.github.io/)

## helloworld với reactjs

reactjs cần đến 2 thằng file chính: "react" vs "react-dom". Và một trình biên dịch mã giúp bạn viết ngắn gọn code hơn đó là "babel".

```html
<!DOCTYPE html>
<html>
<head>
	<title>Reactjs</title>
	<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/react/15.3.1/react.js"></script>
	<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/react/15.3.1/react-dom.js"></script>
	<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.38/browser.min.js"></script>
</head>
<body>
	<div id="root">
	</div>
	<script type="text/babel">
		ReactDOM.render(
            <h1>Hello, world!</h1>,
            document.getElementById('root')
    );

    function tick() {
        const element = (
                <div>
                    <h2>It is {new Date().toLocaleTimeString()}.</h2>
                </div>
        );
        ReactDOM.render(
                element,
                document.getElementById('root')
        );
    }
    setInterval(tick, 1000);
	</script>
</body>
</html>
```
Khi chạy file này (mã html) bằng browser, đầu tiên sẽ xuất hiện đoạn text ***Hello, world!***, sau đó 1s hàm `setInterval` sẽ render lại content của page (thể hiện thời gian)
## Referrer:
[Giới thiệu về ReactJS - Phần I (Các khái niệm cơ bản)](https://viblo.asia/p/gioi-thieu-ve-reactjs-phan-i-cac-khai-niem-co-ban-V3m5WzjblO7)
