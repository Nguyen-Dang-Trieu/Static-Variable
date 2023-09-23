# Static-Variable
- Là biến chỉ khởi tạo 1 lần duy nhất và tồn tại suốt thời gian mà chương trình chạy.

**Example 1:**
~~~cpp
#include <stdio.h>

void count(){
  static int a = 0;
  a++;
  printf("Gia tri cua a: %d", a);
}

int main(){
  count();
  count();
  count();
  return 0;
}
~~~

Hiển thị ra màn hình:
~~~cpp
   Gia trị cua a: 1
   Gia tri cua a: 2
   Gia tri cua a: 3
~~~

**Example 2:**
~~~cpp
#include <stdio.h>

void count(){
  static int a = 1;
  printf("Gia tri cua a: %d", a);
  a++;
}

int main(){

  while(1){
    count();
  }
  return 0;
}
~~~

Hiển thị ra màn hình:
- **TH:** `Không sử dụng static`.
~~~cpp
   Gia trị cua a: 1
   Gia tri cua a: 1
   Gia tri cua a: 1
   ...
~~~
- **TH:** `Sử dụng static`.
~~~cpp
   Gia trị cua a: 1
   Gia tri cua a: 2
   Gia tri cua a: 3
   ...
~~~
## Vậy Global variable và Static variable khác nhau ở chỗ nào ?
- `Biến toàn cục (Global variable)`: Đây là biến được khai báo bên ngoài bất kì hàm nào và có thể truy cập mọi nơi trong chương trình. Biến toàn cục tồn tại suốt thời gian chạy của chương trình và `có thể sửa chữa giá trị từ bất kì hàm nào` => điều này dẫn đến việc quản lí dữ liệu.
- `Biến static`: Đây là biến được khai báo trong hàm hoặc khối mã, tồn tại trong suốt thời gian mà chương trình chạy. Tuy nhiên, `phạm vi của biến static chỉ nằm trong hàm và khối mã đã khai báo` => điều này có nghĩa rằng biến static không thể truy cập ngoài hàm và khối mã đó.
  
## Static function
   `Static functions in C` are functions that are restricted to the same file in which they are defined. `The functions in C are by default global`. If we want to limit the  scope of the function, we use the `keyword static` before the function. Doing so, restricts the scope of the function in other files, and the function remains callable only in the file in which it is defined.

***Example 1:*** Program to Call a Global Function Inside Another File.
Tạo 2 file: *first_file.c* và *second_file.c*

**first_file.c**
~~~cpp
int tong(int a,int b){
  return (a + b);
}
~~~
**second_file.c**
~~~cpp
#include <stdio.h>

int tong(int,int);

int main(){
   int sum = tong(4,5);
   printf("Tong sum = %d",sum);
   return 0;
}
//Note: Để chạy được second_file.c thì ta cần phải liên kết vs first_file.c nếu không sẽ báo lỗi là undefined reference to 'tong'
~~~
`Out put:`
~~~cpp
Tong sum = 9
~~~
`Explanation:`
Since addition is a global non-static function, it can be called from the same file or different file. Thus the above program is executed successfully

***Example 2:*** Program to call a static function inside Another File.
**first_file.c**
~~~cpp
static int tong(int a,int b){
  return (a + b);
}
~~~
**second_file.c**
~~~cpp
#include <stdio.h>

int tong(int,int);

int main(){
   int sum = tong(4,5);
   printf("Tong sum = %d",sum);
   return 0;
}
~~~
`Out put:`
~~~cpp
undefined reference to 'tong'
~~~
`Explanation:`
Static functions are restricted to the file in which they are created, and cannot be called from other file. Since we are creating the static function `tong()` in `first_file.c` and calling it from `second_file.c`, compiler is throwing the error *"undefined reference to 'tong'"*.

### Why the Static Functions are Required?
- It is used to limit the scope of a function in a C program.
- It is used for reusing the same function name in other files.

# Storage
Trong C, biến Static được lưu ở BSS hoặc DATA.
<p align="center">
    <img src="./Images/Static.png" width="600px" alt="">
</p>
<img src="./Images/Static.png" alt="Image 1" width="200" height="150"/><img src="link_to_image_2.png" alt="Image 2" width="200" height="150"/>
