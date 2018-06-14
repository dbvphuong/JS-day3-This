# JS-day3-This
# 1 this & Object prototype
## 1.1 this
###  This là phép gán được thực hiện khi hàm được gọi, giá trị của nó phụ thuộc vào ngữ cảnh hàm được gọi. This dùng để trỏ tới 1 đối tượng nào đó, dùng để tham chiếu(cách lấy dữ liệu) ở đối tượng chứa mã lệnh đang được thực thi.
### This trỏ tới function f() là sai.
### This trỏ tới scope của function là sai. Vì f() và g() là 2 function riêng biệt.

## So sánh các dạng gọi hàm như code:
#### function fn() {
}
#### fn(); // cách gọi 1- cách gọi hàm cơ bản
#### var o = {
####  method: fn
}
#### o.method(); // cách gọi 2- gán 1 giá trị bằng biến
#### fn.call(); // cách gọi 3- dùng hàm call()
#### new fn(); // cách gọi 4
