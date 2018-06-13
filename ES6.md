# ES

ES là viết tắt của ECMAScript

## ECMAScript ES6 là gì?

ES6 là chữ viết tắt của ECMAScript 6, là phiên bản mới nhất của chuẩn ECMAScript. ECMAScript do hiệp hội các nhà sản xuất máy tính Châu Âu đề xuất làm tiêu chuẩn của ngôn ngữ Javascript. Bạn cứ nghĩ xem hiện nay có khá nhiều trình duyệt Browser ra đời và nếu mỗi Browser lại có cách chạy Javascript khác nhau thì các trang web không thể hoạt động trên tất cả các trình duyệt đó được, vì vậy cần có một chuẩn chung để bắt buộc các browser phải phát triển dựa theo chuẩn đó.

Như các bạn biết thời buổi ngày nay công nghệ thay đổi liên tục tới chóng mặt và các trình duyệt cũng không đứng ngoài để ngắm nhìn làn sóng của sự thay đổi này. Chrome, Firefore, IE, Edge... liên tục ra các phiên bản mới để thêm tính năng cũng như khắc phục lỗi. Và từ những sự cải tiến này các nhà sản xuất trình duyệt nhận thấy có những hạn chế trong tiêu chuẩn ECMAScript đang sử dụng và đòi hỏi cần có sự thay đổi trong chính tiêu chuẩn này. Kết quả của nó đó là ra đời các tiêu chuẩn mới ECMAScript, nói đúng hơn là phiên bản mới cho tiêu chuẩn ECMAScript. Phiên bản phổ biến của ECMASCript đang được nhiều trình duyệt hỗ trợ hiên nay là ES phiên bản thứ 5 (5th edition) hay ES5. 


## Babel Là Gì

Babel là một công cụ chuyển đổi mã lệnh JavaScript hay JavaScript transpiler, được dùng với mục đích chuyển đổi mã lệnh JavaScript được viết dựa trên tiêu chuẩn ECMAScript phiên bản mới về phiên bản cũ hơn trước đó.

JavaScript đã có sẵn các quy tắc để lập trình, tuy nhiên do JavaScript chủ yếu được chạy trên môi trường trình duyệt và mỗi trình duyệt khác nhau như Chrome, Firefox, Internet Explore, Safari... có những quy định riêng để viết JavaScript. Điều này dẫn đến không chỉ có duy nhât một quy định (ngôn ngữ) JavaScript và nếu như bạn code tuân theo "ngôn ngữ" JavaScript của một trình duyệt thì khi chạy trên trình duyệt khác hoàn toàn có khả năng code của bạn sẽ không chạy như ý muốn. Do đó chuẩn ECMAScript được ra đời để hạn chế sự khác biệt giữa các "ngôn ngữ" JavaScript khác nhau được định nghĩa bởi các trình duyệt.

trường hợp như các bạn viết code JavaScript dựa trên ES6 thì có nhiều khả năng code của bạn chạy không đúng hoặc thậm chí là không chạy được trên các trình duyệt khác nhau. Để khắc phục tình huống này thì sẽ cần có một công cụ chuyển đổi mã lệnh JavaScript viết dựa trên ES6 về ES5. Và Babel được cho ra đời để đáp ứng nhu cầu trên.

## Cài Đặt và Sử Dụng Babel Trên Browser

Chúng ta sẽ cần nhúng thư viện Babel (JavaScript) vào trang web thông qua thẻ `<script>`. Ví dụ sau sử dụng thư viện Babel đã được tinh giản (minified) từ CDN server:
```
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

Sau đó bạn cần đặt code JavaScript được viết theo ES6 trong thẻ `<script type="text/babel">`:
```
<div id="output"></div>

<script type="text/babel">
const getMessage = () => "Hello World";
document.getElementById('output').innerHTML = getMessage();
</script>

```
Lưu ý rằng thuộc tính `type` trong thẻ mở `<script>` ở trên là "text/babel" thay vì "text/javascript".

Khi tải trang, thư viện ***Babel*** sẽ chuyển đổi mã lệnh viết trong thẻ `<script type="text/babel">` về mã JavaScript viết theo ES5 qua đó trình duyệt có thể hiểu được.



##Referrer:

[Tìm Hiểu cơ bản về ES6](https://viblo.asia/p/tim-hieu-co-ban-ve-es6-DKBedxBZedX)
