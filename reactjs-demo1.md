#ReactJS

lear reactjs

## Step

### 1, Nhúng thư viện ReactJS vào html
```
<!DOCTYPE html>
<html>
<head>
    <title>Reactjs</title>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/react/15.3.1/react.js"></script>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/react/15.3.1/react-dom.js"></script>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.38/browser.min.js"></script>
</head>
<body>
<div id="demo1">
    <script type="text/babel">
        ReactDOM.render(<h1 className= "abc">Demo ReactJs 1</h1>, document.getElementById("demo1"));
    </script>
</div>

<div id="demo2">
    <script>
        ReactDOM.render(React.createElement("h1", {className: "abc"}, "Demo ReactJs 2"), document.getElementById("demo2"));
    </script>
</div>
</body>
</html>
```

nhờ thư viện `babel-core/5.8.38/browser.js` nên đoạn code `ReactDOM.render` của *demo1* hiện thị được mã HTML trong đoạn script.

Trong *demo2* thì sử dụng thuần của reactjs: React sẽ thực hiện create 1 đối tượng là thẻ h1 với thuộc tính là `class = "abc"` và `content`

### 2, Component 

Bạn có thể tạo ra một component bằng các gọi phương thức `createClass` của đối tượng React, điểm bắt đầu khi tiếp cận với thư viện này.

Component ta sẽ thực hiện khai báo như sau:

```
var Demo = React.createClass({
    render: function(){
        return(
            <h1 className= "abc">Demo ReactJs</h1>
        );
    }
});
```
Thực hiện triệu gọi Component ra ReactDOM
- ReactDOM.render(<Demo/>, document.getElementById("demo"));

OR

- ReactDOM.render(<Demo></Demo>, document.getElementById("demo"));

*Lưu ý:* Khi sửa dụng render React. bắt buộc phải tồn tại 1 thành phần cha bao các thành phần con còn lại. Nếu không React sẽ không chạy.

```
var Button = React.createClass({
    render: function(){
        return (
            <input type="submit" />
        );
    }
});
```

Phương thức `createClass` nhận vào một tham số, là đối tượng mô tả đặc tính của component. Đối tượng này bao gồm tất cả các phương thức để hình thành nên component. Phương thức quan trọng nhất là render, phương thức này được trigger khi component đã sẵn sàng để được render lên trên page.

Trong hàm đó, bạn sẽ trả về một mô tả cho việc bạn muốn React render cái gì lên trên page. Như trong ví dụ ở trên, đơn giản tôi muốn render một button.

Chú ý: Hàm render chính là mô tả cụ thể của UI tại bất cứ thời điểm nào. Vì thế nếu dữ liệu thay đổi, React sẽ take care việc update UI với dữ liệu tương ứng. Các bạn có thể hiểu đơn giản là, khi dữ liệu thay đổi, React sẽ tự động gọi hàm render để update lại UI.

### 3, Component lồng nhau:

Nếu bạn muốn lồng nhiều component vào nhau, bạn sẽ làm điều này trong lệnh return của phương thức render.

```
var Test = React.createClass({
    render: function(){
        return(
            <h1 className= "abc">Test Component ReactJs</h1>
        );
    }
});

var Demo = React.createClass({
    render: function(){
        return(
            <div>
              <h1 className= "abc">Demo ReactJs</h1>
              <Test/>
            </div>
        );
    }
});
React.render(<Demo />,  document.getElementById("app"));
```

### 4, Props

***Props*** là thuộc tính dành cho 1 component và có thể tồn tại nhiều props

```
ReactDOM.render(<Demo demoprop="Demo Prop" />, document.getElementById("demo"));
```
Chúng ta sẽ triệu gọi props vào component

```
<h1 className= "abc">Demo ReactJs {this.props.demoprop}</h1>
```

Ta sửa dụng cặp {} để thực hiện gọi các function trong đó


***Props children***:

```
ReactDOM.render(<Demo demoprop="Demo Prop">Test props children</Demo>, 
```
Component:

```
var Demo = React.createClass({
    render: function(){
        return(
            <div>
              <h1 className= "abc">Demo ReactJs {this.props.demoprop}</h1>
              <h3>Result: {this.props.children}</h3>
              <Test/>
            </div>
        );
    }
});
```

### 5, State
Trái ngược với Props, State lại có thể thay đổi được. Ta có thể hiểu Props là thuộc tính thì State chính là trạng thái của nó Ta sẽ init 1 state và new 1 function addString nhằm nuối chuỗi khi thực hiện click button

```
getInitialState(){
    return {str: "Test state"};
},
addString(){
    this.setState({str: this.state.str + 1});
},
```

Viết 1 button trong component Demo với event onClick sẽ thực hiện gọi hàm addString trong cùng component

```
<button onClick={this.addString}>button</button>
```


## Referrer

[Demo React JS Trên Client](https://viblo.asia/p/demo-react-js-tren-client-3P0lPO1pZox)

[Học ReactJS trong 15 phút (Phần 1)](https://kipalog.com/posts/Hoc-ReactJS-trong-15-phut--Phan-1)


