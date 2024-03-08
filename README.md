#  LECTURE 1 : TDARG - ASSERT
**I.Thư viện stdarg**
- Cung cấp các phương thức để làm việc với các hàm có số lượng input parameter không cố định.
- Các hàm như printf và scanf là ví dụ điển hình 
**Stddarg Function**
- va_list: là một kiểu dữ liệu để đại diện cho danh sách các đối số biến đổi.
- va_start: Bắt đầu một danh sách đối số biến đổi. Nó cần được gọi trước khi truy cập các đối số biến đổi đầu tiên.
- va_arg: Truy cập một đối số trong danh sách. Hàm này nhận một đối số của kiểu được xác định bởi tham số thứ hai
- va_end: Kết thúc việc sử dụng danh sách đối số biến đổi. Nó cần được gọi trước khi kết thúc hàm.

```c
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
printf("MUX:%d",MUL(4,2,2,2,2));
return 0;
}
```
OUTPUT
```c
MUX:16
```
**I.Thư viện assert**
- Cung cấp macro assert. 
- Macro này được sử dụng để kiểm tra một điều kiện. 
- Nếu điều kiện đúng (true), không có gì xảy ra và chương trình tiếp tục thực thi.
- Nếu điều kiện sai (false), chương trình dừng lại và thông báo một thông điệp lỗi.
- Dùng trong debug, dùng #define NDEBUG để tắt debug

- Điều kiện đúng
 ```c
#include <stdio.h>
#include <assert.h>
int main() {
    int x = 5;

    assert(x == 5);

    // Chương trình sẽ tiếp tục thực thi nếu điều kiện là đúng.
    printf("X is: %d", x);
    
    return 0;
}
```
```c
X is: 5
```

-Điều kiện sai

```c
#include <stdio.h>
#include <assert.h>

int main() {
    int x = 5;

    assert(x == 10);

    // Chương trình sẽ tiếp tục thực thi nếu điều kiện là đúng.
    printf("X is: %d", x);
    
    return 0;
}
```
```c
Assertion failed: x == 10, file main.c, line 7
```
**Các lỗi**
- Lỗi truy cập mảng không an toàn.
- Lỗi chia cho số 0.
- Chia số nguyên cho số nguyên, kết quả là số thực.

EX1
```c
#include <assert.h>

#define ASSERT_IN_RANGE(val, min, max) assert((val) >= (min) && (val) <= (max))

void setLevel(int level) {
    ASSERT_IN_RANGE(level, 1, 10);
    // Thiết lập cấp độ
}
```

