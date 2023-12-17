## Đề 
> nc 103.162.14.116 14005
## Giải 
- Bài này thì nó tương tự bài tìm số lớn nhất lúc nãy 
- Nhưng chỉ khác là dữ liệu bây giờ là phải xử lý n để tính tổng theo cấp số cộng
```text
For example, let's go through the first few terms of the sequence:
        a[0] = 1 
        a[1] = 1 + a[0] = 1 + 1 = 2
        a[2] = 2 * a[1] = 2 * 2 = 4
        a[3] = 3 + a[2] = 3 + 4 = 7
        a[4] = 4 * a[3] = 4 * 7 = 28
        a[5] = 5 + a[4] = 5 + 28 = 33
```
- Em vẫn dùng thư viện pwn như lúc đầu 
- Đây là code của em 
```text
from pwn import *
import re

def tinh_toan_a_n(n):
    if n == 0:
        return 1
    
    a = 1
    for i in range(1, n + 1):
        if i % 2 == 0:
            a *= i
        else:
            a += i
    
    return a

# Kết nối đến máy chủ
p = remote('103.162.14.116', 14005)

# Nhận dữ liệu ban đầu cho đến khi có dấu nhắc
while True:
    p.recvuntil(b'n = ')
    value = int(p.recvline()[:-1].decode(), 10)
    print("VALUE : ", value)
    p.sendlineafter(b'=', str(tinh_toan_a_n(value)))
```
- Sau khi chạy ta sẽ có được flag 
- Do dữ liệu sau khi ra flag là up lên nó sẽ báo lỗi nên em phải chạy thêm dòng DEBUG ở sau nữa 
> python3 prog4.py DEBUG
```text
[DEBUG] Received 0x10 bytes:
    b'n = 4\n'
    b'>> a[4] = '
VALUE :  4
[DEBUG] Sent 0x3 bytes:
    b'28\n'
[DEBUG] Received 0xb bytes:
    b'CORRECT!!!\n'
[DEBUG] Received 0x10 bytes:
    b'n = 1\n'
    b'>> a[1] = '
VALUE :  1
[DEBUG] Sent 0x2 bytes:
    b'2\n'
[DEBUG] Received 0xb bytes:
    b'CORRECT!!!\n'
[DEBUG] Received 0x2e bytes:
    b'Flag: KCSC{KOREGA_REQUIEM_DA!!!_WWHaaaaaa___}\n'

```
> Flag : KCSC{KOREGA_REQUIEM_DA!!!_WWHaaaaaa___}