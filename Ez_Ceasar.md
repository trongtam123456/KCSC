## Đề 
> Ceasar is basic, right?
## Giải 
- Sau khi tải được file và mở lên em thấy đoạn code như sau 
```text
import string
import random

alphabet = string.ascii_letters + string.digits + "!{_}?"

flag = 'KCSC{s0m3_r3ad4ble_5tr1ng_like_7his}'
assert all(i in alphabet for i in flag)

key = random.randint(0, 2**256)

ct = ""
for i in flag:
    ct += (alphabet[(alphabet.index(i) + key) % len(alphabet)])

print(f"{ct=}")

# ct='ldtdMdEQ8F7NC8Nd1F88CSF1NF3TNdBB1O'
```
- Giải thích 1 tí : Đoạn strings flag sẽ được mã hoá và lưu vào ct
- Bây giờ em sẽ viết code giải mã xem thử ct được mã hoá từ chuỗi nào 
```text
import string
import random

alphabet = string.ascii_letters + string.digits + "!{_}?"

flag = 'ldtdMdEQ8F7NC8Nd1F88CSF1NF3TNdBB1O'
assert all(i in alphabet for i in flag)

key = random.randint(0, 2**256)

ct = ""
for i in flag:
    ct += (alphabet[(alphabet.index(i) + key) % len(alphabet)])

print(f"{ct=}")

# ct='ldtdMdEQ8F7NC8Nd1F88CSF1NF3TNdBB1O'

```
- Vấn đề đưa ra là nó chỉ có 1 lần nên em sẽ đưa nó vào vòng lặp 26 lần tương ứng với 26 kí tự
```text
import string
import random
for i in range(0, 26):
	alphabet = string.ascii_letters + string.digits + "!{_}?"

	flag = 'ldtdMdEQ8F7NC8Nd1F88CSF1NF3TNdBB1O'
	assert all(i in alphabet for i in flag)

	key = random.randint(0, 2**256)

	ct = ""
	for i in flag:
    		ct += (alphabet[(alphabet.index(i) + key) % len(alphabet)])

	print(f"{ct=}")

# ct='ldtdMdEQ8F7NC8Nd1F88CSF1NF3TNdBB1O'
```
- Đây là kết quả 
```text
ct='kcscLcDP7E6MB7Mc0E77BRE0ME2SMcAA0N'
ct='zrHr0rS4hTg1Qh1raThhQ6Ta1Tc71rPPa2'
ct='meueNeFR9G8OD9Oe2G99DTG2OG4UOeCC2P'
ct='91c1v1nzRoQwlRw1KoRRlBoKwoMCw1kkKx'
ct='qiyiRiJV}K_SH}Si6K}}HXK6SK8YSiGG6T'
ct='5X}XrXjvNkMshNsXGkNNhxkGskIysXggGt'
ct='PHXHbH8fx9wc6xcHq9xx6h9qc9sicH55qd'
ct='kcscLcDP7E6MB7Mc0E77BRE0ME2SMcAA0N'
ct='RJZJdJ!hz{ye8zeJs{zz8j{se{ukeJ77sf'
ct='IAQA9A1}q2p!Zq!Aj2qqZa2j!2lb!AYYj{'
ct='KCSC{C3as4r_1s_Cl4ss1c4l_4nd_C00l}'
ct='6Y?YsYkwOlNtiOtYHlOOiylHtlJztYhhHu'
ct='BtJt2tU6jVi3Sj3tcVjjS8Vc3Ve93tRRc4'
ct='0S8SmSeqIfHncInSBfIIcsfBnfDtnSbbBo'
ct='ogwgPgHT{I!QF{Qg4I{{FVI4QI6WQgEE4R'
ct='BtJt2tU6jVi3Sj3tcVjjS8Vc3Ve93tRRc4'
ct='EwMw5wX9mYl6Vm6wfYmmV{Yf6Yh_6wUUf7'
ct='OGWGaG7ew8vb5wbGp8ww5g8pb8rhbG44pc'
ct='b8j8C8uGYvXDsYD8RvYYsIvRDvTJD8rrRE'
ct='HzPz8z0_p1o9Yp9zi1ppY?1i91ka9zXXi!'
ct='kcscLcDP7E6MB7Mc0E77BRE0ME2SMcAA0N'
ct='MEUE}E5cu6t?3u?En6uu3e6n?6pf?E22na'
ct='KCSC{C3as4r_1s_Cl4ss1c4l_4nd_C00l}'
ct='KCSC{C3as4r_1s_Cl4ss1c4l_4nd_C00l}'
ct='PHXHbH8fx9wc6xcHq9xx6h9qc9sicH55qd'
ct='}5g5z5rDVsUApVA5OsVVpFsOAsQGA5ooOB'

```
> Flag : KCSC{C3as4r_1s_Cl4ss1c4l_4nd_C00l}