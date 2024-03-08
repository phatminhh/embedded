#  LECTURE 1 : TDARG - ASSERT
**I.Thư viện stdarg**
- Cung cấp các phương thức để làm việc với các hàm có số lượng input parameter không cố định.
- Các hàm như printf và scanf là ví dụ điển hình 
**Stddarg Function**
- va_list: là một kiểu dữ liệu để đại diện cho danh sách các đối số biến đổi.
- va_start: Bắt đầu một danh sách đối số biến đổi. Nó cần được gọi trước khi truy cập các đối số biến đổi đầu tiên.
- va_arg: Truy cập một đối số trong danh sách. Hàm này nhận một đối số của kiểu được xác định bởi tham số thứ hai
- va_end: Kết thúc việc sử dụng danh sách đối số biến đổi. Nó cần được gọi trước khi kết thúc hàm.

```
#include <stdio.h>
#include<stdarg.h>
int MUL(int arr,...){
int val=1;
va_list ap;
va_start(ap,arr);
for (int i = 0; i < arr; i++)
{
val *= va_arg(ap,int);
}
va_end(ap);
return val;
}
int main(int argc, char const *argv[])
{
printf("%d",MUL(4,2,2,2,2));
return 0;
}
```
