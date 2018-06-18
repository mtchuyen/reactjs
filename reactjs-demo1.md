#ReactJS

lear reactjs

## Step

### 1, Nhúng thư viện ReactJS vào html
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

Hãy tạo một component có tên là Hello.

```javascript
class Hello extends React.Component {
    render() {
        return <h1>Hello my friend!</h1>;
    }
}
```
Sau đó bạn định nghĩa các methods cho component. Trong ví dụ của chúng ta, chỉ có một method và được gọi là `render()`.

Trong hàm `render()` sẽ trả về những gì mà bạn muốn hiển thị trên trang. Trong trường hợp trên, chúng ta muốn nó hiển thị một thẻ `h1` với text `Hello my friend!`

Để ứng dụng của chúng ta hiển thị trên màn hình, chúng tôi cần phải sử dụng `ReactDOM.render()`:

```javascript
ReactDOM.render(
    <Hello />, 
    document.getElementById("root")
);
```
Đầy đủ code trong thẻ tab `<body></body>` như sau:

```javascript
<div id="demo4">
    <script type="text/babel">
        class Hello extends React.Component {
            render() {
                return <h1>Hello my friend!</h1>;
            }
        }
        ReactDOM.render(
                <Hello />,
                document.getElementById("demo4")
        );

    </script>
</div>
```

Bạn có thể tạo ra một component bằng các gọi phương thức `createClass` của đối tượng React, điểm bắt đầu khi tiếp cận với thư viện này.

Component ta sẽ thực hiện khai báo như sau:

```javascript
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

```javascript
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

```javascript
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

Cách để đưa props vào một component nhìn rất giống cách mà chúng ta khai báo attribute cho một HTML element.

```javascript
<App text={text} />
```
Lý do chúng ta sử dụng cặp ngoặc nhọn `{}` là vì chúng ta cần nói cho JSX biết rằng đó là một Javascript expression.

Một khi `App` component được cài đặt như thế này, nó có thể truy xuất vào biến text mà ta đã khai báo ở trên thông qua lời gọi `this.props.text`.

Tuy nhiên, nó không thể trực tiếp thay đổi dữ liệu. Từ góc nhìn của component, props của nó là bất biến (immutable). Nó chỉ là thông tin được cài đặt cho component.

```javascript
var textBt = "Click the button";

var Form = React.createClass({
    render: function(){
        return (
            <div>
                <h3>{this.props.text}</h3>
                <input type="submit" />
            </div>
        );
    }
});
var App = React.createClass({
    render: function(){
        return (
            <div>
                <h1> Welcome to my app!</h1>
                <Form text={this.props.text}/>
            </div>
        );
    }
});
ReactDOM.render(<App text={textBt}/>,  document.getElementById("app"));

```

***props*** được truyền vào trong `App` component trong phương thức `ReactDOM.render()`. Sau đó `App` component có thể truy xuất biến `text` thông qua lời gọi `this.props.text`. Nó cũng có thể truyền dữ liệu xuống component con của nó như chúng ta thấy cách mà `Form` component được `App` component cài đặt props trong ví dụ.

Khi dữ liệu đến được `Form` component, chúng ta thấy đây là điểm kết thúc, dữ liệu sẽ được render ra thẻ `h3` như trên.


***Props children***:

```
ReactDOM.render(<Demo demoprop="Demo Prop">Test props children</Demo>, 
```
Component:

```javascript
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

Một cách khác để storing dữ liệu trong React là state. Không giống như `props` (bất biến dưỡi góc nhìn của component), state có thể thay đổi (mutable).

Ta có thể hiểu ***Props*** là thuộc tính thì ***State*** chính là trạng thái của nó.

Vì thế nếu bạn muốn dữ liệu trong ứng dụng thay đổi, ví dụ như dựa trên tương tác người dùng, thì dữ liệu phải được lưu trữ trong component state.

***State*** là private và được quản lý bởi chỉ duy nhất một component, nó không thể truyền xuống cho component con. Nếu bạn muốn truyền xuống cho component con thì bạn phải truyền nó như là một props.

***Cài đặt state***

Để cài đặt state, đơn giản chúng ta cài đặt hàm `getInitialState()` vào component, và trả về bất cứ gì bạn muốn cài đặt trong state của component đó.

***Thay đổi state***

Để thay đổi state, đơn giản ta gọi hàm `this.setState()`, và truyền vào state mới như là một tham số.



Ta sẽ init 1 state và new 1 function addString nhằm nuối chuỗi khi thực hiện click button

```javascript
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

```javascript
var App = React.createClass({
    getInitialState: function(){
        return {
            active: true
        }
    },
    handleClick: function(){
        this.setState({
            active: !this.state.active
        });
    },
    render: function(){
        var buttonSwitch = this.state.active ? "On" : "Off";
        return (
            <div>
                <p>Click the button!</p>
                <input type="submit" onClick={this.handleClick} />
                <p>{buttonSwitch}</p>
            </div>
        );
    }
});

React.render(<App />,  document.getElementById("app"));
```

Chúng ta hook một event listener vào trong button, ở trên là `onClick`. Khi nó được trigger, chúng ta gọi hàm `handleClick`, cái mà đã được cài đặt trước đó, và luôn sẵn sàng được gọi thông qua từ khóa `this`.

Trong hàm `handleClick`, chúng ta gọi `this.setState()`, cái mà sẽ thay đổi trạng thái của component.


***Chúng ta nên giữ state ở đâu?***

Bạn nên cố gắng giữ số lượng các stateful component ít nhất có thể, và thậm chí giữ tối thiểu lượng dữ liệu trong state. Nếu component cấp dưới cần truy xuất dữ liệu từ state, thì hãy truyền nó thông qua props.

> Stateful component thì luôn luôn là higher level, trong khi Stateless component thường là lower level trong hệ thống phân cấp.

Để hình dung việc state được giữ ở đâu, bạn hãy hỏi bản thân một vài câu hỏi, những câu hỏi này được lấy từ React docs:

- Xác định mỗi component mà render thông tin gì đó dựa trên state.
- Tìm một component mà nó chủ sở hữu chung của các component khác (một component nằm bên trên tất cả các component khác trong hệ thống phân cấp thì cần có state)
- Hoặc là những component là chủ sở hữu chung hoặc là những component nằm trên hệ thống phân cấp sẽ nên giữ state.
- Nếu bạn không thể tìm ra component nào phù hợp, hãy tạo một component mới đơn giản giữ nhiệm vụ lưu trữ state và đặt nó đâu đó nằm bên trên các component là chủ sở hữu chung trong hệ thống phân cấp.


## Referrer

[Demo React JS Trên Client](https://viblo.asia/p/demo-react-js-tren-client-3P0lPO1pZox)

[Học ReactJS trong 15 phút (Phần 1)](https://kipalog.com/posts/Hoc-ReactJS-trong-15-phut--Phan-1)

[Học React.js trong 5 phút!](https://viblo.asia/p/hoc-reactjs-trong-5-phut-E375zRwq5GW)


