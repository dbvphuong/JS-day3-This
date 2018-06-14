# JS-day3-This
# 1 this & Object prototype  
## 1.1 this
This là phép gán được thực hiện khi hàm được gọi, giá trị của nó phụ thuộc vào ngữ cảnh hàm được gọi. This dùng để trỏ tới 1 đối tượng nào đó, dùng để tham chiếu(cách lấy dữ liệu) ở đối tượng chứa mã lệnh đang được thực thi.  
This trỏ tới function f() là sai.this trỏ tới window.  
This trỏ tới scope của function là sai mà trỏ đến window.2 scope ko liên kết gì với nhau.  

## So sánh các dạng gọi hàm như code:
function fn() {  
}  
fn(); // cách gọi 1- cách gọi hàm cơ bản  
 var o = {  
  method: fn  
}  
 o.method(); // cách gọi 2- gán 1 giá trị bằng biến  
 fn.call(); // cách gọi 3- dùng hàm call()  cấu trúc: function.call(đối tượng this,tham số 1 của hàm, tham số 2 của hàm,..)
 new fn(); // cách gọi 4 - chuyển sang object.  
 
 ## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
 function f() {  
  console.log(this.a);  
}  
var a = 2;  
f(); // ??  
