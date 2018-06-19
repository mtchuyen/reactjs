# ReactJS

learn reactjs

## Jsx

- JSX = Javascript + XML
- Nó là phần mở rộng của javascript nhưng có cú pháp viết như xml
- JSX không phải một ngôn ngữ template, JSX chỉ đơn giản là một cú pháp thay thế JavaScript, mặc dù cú pháp đó là đặc trưng của React

## JSX Elements

Một đơn vị căn bản của JSC được gọi là một `JSX element`

Đây là một ví dụ của một `JSX element`:
```javascript
<h1>Hello world</h1>
```

Bạn có thể thấy `JSX element` trông giống hệt HTML. Chỉ có điểm khác đó là nó được viết trong file ***.js*** chứ không phải `.html`.

JSX có thể được lưu vào trong 1 biến, truyền nó vào function hoặc lưu trong một object hoặc mảng

Cú pháp:
```javascript
const navBar = <nav>I am a nav bar</nav>;
```

hay:

```javascript
 const theExample = (
   <a href="https://www.example.com">
     <h1>
       Click me!
     </h1>
   </a>
 );
 ```
 `JSX element` phải có chính xác một element bao ngoài nó (như ví dụ trên là `<a>...</a>`)
 
 Ví dụ sau đây là sai:
 ```javascript:
 const paragraphs = (
  <p>I am a paragraph.</p> 
  <p>I, too, am a paragraph.</p>
);
```
2 element ngang hàng nhưng không có element nào bao cả 2 cái.

### Render element
`ReactDOM.render()` là cách phổ biến nhất để render ra JSX.

- Tham số đầu tiên là một JSX expression. Nó sẽ tạo ra một cây tương ứng với node DOM, sau đó thêm cây này vào DOM.
- Tham số thứ 2 sẽ là nơi mà bạn muốn tham số đầu tiên được xuất hiện.

Ví dụ:
```javascript
ReactDOM.render(<h1>Hello world</h1>, document.getElementById('app'));
```

Một điều đặc biệt về `ReactDOM.render()` đó là nó chỉ cập nhật những thành phần DOM có sự thay đổi. Nghĩa là nếu bạn gọi hàm render 2 lần mà không có sự thay đổi gì cả, thì hàm render thứ 2 sẽ không làm gì cả
```javascript
const hello = <h1>Hello world</h1>;
// This will add "Hello world" to the screen:
ReactDOM.render(hello, document.getElementById('app'));

// This won't do anything at all:
ReactDOM.render(hello, document.getElementById('app'));
```


## Referrel
- [Basic ReactJs (P1)](https://viblo.asia/p/basic-reactjs-p1-4dbZNDdq5YM)
- [Jsx và event trong reactjs](https://viblo.asia/p/jsx-va-event-trong-reactjs-WkwGnJmDG75g)
- [Series hướng dẫn reactJs (P.1)](https://huongdanreactjs.wordpress.com/2018/03/18/series-huong-dan-reactjs/)
- [Series hướng dẫn ReacJs (P.2)](https://huongdanreactjs.wordpress.com/2018/03/19/series-huong-dan-reacjs-p-2/)

