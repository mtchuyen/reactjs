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

Lưu ý: Khi sửa dụng render React. bắt buộc phải tồn tại 1 thành phần cha bao các thành phần con còn lại. Nếu không React sẽ không chạy.


### 3, Component lồng nhau:

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


