# Static-Variable
- Là biến chỉ khởi tạo 1 lần duy nhất và tồn tại suốt thời gian mà chương trình chạy.
~~~cpp
#include <stdio.h>

void count()
{
  static int a = 0;
  a++;
  printf("Gia tri cua a: %d", a);
}

int main()
{
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
## Vậy biến toàn cục và biến static khác nhau ở chỗ nào ?
- Biến toàn cục (Global variable): Đây là biến được khai báo bên ngoài bất kì hàm nào và có thể truy cập mọi nơi trong chương trình. Biến toàn cục tồn tại suốt thời gian chạy của chương trình và "có thể sửa chữa giá trị từ bất kì hàm nào" => điều này dẫn đến việc quản lí dữ liệu.
