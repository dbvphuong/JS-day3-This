# JS-day3-This
# 1 this & Object prototype  
# 1.1 this
This là phép gán được thực hiện khi hàm được gọi, giá trị của nó phụ thuộc vào ngữ cảnh hàm được gọi. This dùng để trỏ tới 1 đối tượng nào đó, dùng để tham chiếu(cách lấy dữ liệu) ở đối tượng chứa mã lệnh đang được thực thi.  
This trỏ tới function f() là sai.this trỏ tới window.  
This trỏ tới scope của function là sai mà trỏ đến window.2 scope ko liên kết gì với nhau.  

## So sánh các dạng gọi hàm như code:
```
function fn() {  
}  
fn(); // cách gọi 1- cách gọi hàm cơ bản 
 var o = {  
  method: fn  
}  
 o.method(); // cách gọi 2- dùng phương pháp method  
 fn.call(); // cách gọi 3- dùng hàm call()  cấu trúc: tên function.call(đối tượng this,tham số 1 của hàm, tham số 2 của hàm,..)
 new fn(); // cách gọi 4 - dùng object.  
 ```
 ## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
```
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
```

Kết quả ra undefined(cứ có strict thì this sẽ là undefined)  

## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
```
function f() {  
  console.log(this.a);  
}  
var o = {  
  a: 2,  
  f: f  
};  
o.f(); // ??
```
Kết quả ra là 2. hàm được gọi theo cách 2 .this trỏ đến nơi chứa giá trị a là o.  

## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
```
function f() {  
  console.log(this.a);  
}  
var o = {  
  a: 2,  
  f: f  
};  
var g = o.f;  
g(); // ??    
```
Kết quả là undefined.theo cách 1. this trỏ tới window. Vì: o.f= function f.Nên g() là gọi function f =console.log(this.a)<this ở đây không trỏ đến o, vì this phụ thuộc theo cách gọi-cách gọi 1>  


## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
```
function f() {  
  console.log(this.a);  
}  
var o = {  
  a: 2  
};  
var g = f.apply(o);  
f.call(o); // 2  
g(); // undefined  
```
Kết quả ra là 2 và undefined. vì dùng hàm call để gọi this trỏ đến o. còn g()=undefined vì gọi theo cách 1 nên this sẽ trỏ đến window.

## Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?  
```
function f(a) {  
  this.a = a;  
}  
var g = new f(2);  // gán a=2
console.log(g.a); // ???  
```
Kết quả là 2. cách gọi bằng object. This trỏ vào function f.  


Có 4 cách goi hàm.  
ưu tiên cách 4 nhất, rồi đến 3, rồi đến 2 và cuối cùng là 1.  


# 1.2 Objects  

#### 6 kiểu nguyên thủy object là:  
- Object.  
- Array.  
- String.  
- Number.  
- Boolean.  
- Function.  

#### Cách để tạo clone object( nghĩa là tạo 1 object mới là bản coppy của object cũ).  
Cú pháp:  
var a= {x:3, x:4};  
var b= Object.assign({},a);
JSON.stringify(b); //  {x:3, x:4}  
Hoặc:  
var a= {x:3, x:4}; 
var b= JSON.parse(JSON.stringify(a))  
JSON.stringify(b); //  {x:3, x:4}  

# 1.3 Iteration  
### Có những cách nào để duyệt các phần tử trong 1 array ? Viết code ví dụ:  
Dùng vòng lặp for.  
vd:  
text;
a=["hay","noi","di","em"];  
 for(i=0; i<a.length; i++){  
 text +=a[i] + " "  
};  
// "hay noi di em"  

### Có những cách nào để duyệt các thuộc tính trong 1 object? Viết code ví dụ:  
Dùng for in  . for(giatriganvao in tenobject)
vd: var object={x:1, y:2, z:3};  
text="";  
for(a in object){  
text += object[a]  
}  


# 1.4 Class Theory  
### Nhớ lại OOP là gì ? các thuộc tính của OOP?  
OOP là lập trình theo hướng đối tượng.  
4 thuộc tính của OOP:  
- Trừu tượng: Các đối tượng được diễn tả trên lập trình bằng các thuộc tính trừu tượng.  
- Kế thừa: các đối tượng con sẽ có các thuộc tính của cha(cha thì không, các con không có các thuộc tính của nhau, và mỗi con chỉ có 1 cha, mỗi cha chỉ có 1 ông).  
- Đóng gói(bảo mật thông tin): không cho phép thay đổi nội dung đối tượng, chỉ các phương thức nội tại mới thay đổi được(ví dụ ông hàng xóm đến xin hạt tiêu, thì người chủ nhà sẽ vào lấy rồi mang ra cửa cho, chứ không cho ông kia vào nhà).  
- Đa hình: là các thuộc tính của đối tượng giống nhau nhưng giá trị của chúng có thể khác nhau(ví dụ như con mèo "kêu" meo meo, con chó "kêu" gâu gâu).  
### So sánh "class" và "instance"  
class là bản vẽ cái bàn còn instance là bố cục cái bàn (gồm có các bộ phận cái bàn)  
### Constructor là gì?  
Cóntructor dùng để định nghĩa giá trị, thuộc tính cho đối tượng ban đầu.(ví dụ dùng từ khóa new object() )  

# 1.5 Prototypes(cha)  
### Xem xét đoạn code sau, em có nhận xét gì ?
var o1 = {  
  a: 2  
}  
var o2 = Object.create(o1); // nghĩa là o2 liên kết với o1, o2 nhận giá trị o1 nhưng không ngược lại.  
console.log(o2.a); // 2  
o1.a = 10;  
console.log(o2.a); // 10  

Nhận xét: o2 chính là con của o1, nếu nó không có giá trị thì sẽ tìm đến cha.  
