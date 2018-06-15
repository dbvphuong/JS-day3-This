# JS-day3-This
# 1 this & Object prototype  
# 1.1 this
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
 o.method(); // cách gọi 2- dùng phương pháp method  
 fn.call(); // cách gọi 3- dùng hàm call()  cấu trúc: tên function.call(đối tượng this,tham số 1 của hàm, tham số 2 của hàm,..)
 new fn(); // cách gọi 4 - dùng object.  
 
 ## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
 function f() {  
  console.log(this.a);  
}  
var a = 2;  
f(); // ??  

Kết quả là 2.  
Hàm gọi theo cách 1, this trỏ vào đối tượng function f.  

## Cho đoạn code sau, kết quả in ra là gì ?  
function g() {  
  "use strict";  
  console.log(this.b);  
}  
var b = 2;  
g(); // ??  

Kết quả ra undefined(cứ có strict thì this sẽ là undefined)  

## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
function f() {  
  console.log(this.a);  
}  
var o = {  
  a: 2,  
  f: f  
};  
o.f(); // ??  
Kết quả ra là 2. hàm được gọi theo cách 2 .this trỏ đến nơi chứa giá trị a là o.  

## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
function f() {  
  console.log(this.a);  
}  
var o = {  
  a: 2,  
  f: f  
};  
var g = o.f;  
g(); // ??    

Kết quả là undefined.theo cách 1. this trỏ tới window. Vì: o.f= function f.Nên g() là gọi function f =console.log(this.a)<this ở đây không trỏ đến o, vì this phụ thuộc theo cách gọi-cách gọi 1>  


## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
function f() {  
  console.log(this.a);  
}  
var o = {  
  a: 2  
};  
var g = f.apply(o);  
f.call(o); // 2  
g(); // undefined  

Kết quả ra là 2 và undefined. vì dùng hàm call để gọi this trỏ đến o. còn g()=undefined vì gọi theo cách 1 nên this sẽ trỏ đến window.

## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
function f(a) {  
  this.a = a;  
}  
var g = new f(2);  // gán a=2
console.log(g.a); // ???  

Kết quả là 2. cách gọi bằng object. This trỏ vào function f.  


Có 4 cách goi hàm.  
ưu tiên cách 4 nhất, rồi đến 3, rồi đến 2 và cuối cùng là 1.  


# 1.2 Objects  
