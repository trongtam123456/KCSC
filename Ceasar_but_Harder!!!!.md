## Giải 
- Sau khi tải xuống em được 1 file chứa code python như sau:
```text
import string
import random

flag = "KCSC{s0m3_r3ad4ble_5tr1ng_like_7his}" 

alphabet = string.ascii_letters + string.digits + "!{_}?"
assert all(i in alphabet for i in flag)

#xoá 3 phần tử trong alphabet
for i in range(3):
    k = random.randint(0, len(alphabet))
    alphabet = alphabet[:k] + alphabet[k+1:]
#key ngẫu nhiên từ 0 đến 2^512
key = random.randint(0, 2**512)

ct = ""
for i in flag:
    ct += (alphabet[(alphabet.index(i) + key) % len(alphabet)])

print(f"{ct=}")

# ct='2V9VnRcNosvgMo4RoVfThg8osNjo0G}mmqmp'
```
- Mặc dù key hơi lớn nhưng ta chỉ cần bruteforce 3 vị trí cần xoá và decrypt dựa trên alphabet mới đó
```text
import string
import random

target_flag = "KCSC{s0m3_r3ad4ble_5tr1ng_like_7his}"  # Test flag
encrypted_text = '2V9VnRcNosvgMo4RoVfThg8osNjo0G}mmqmp'
found_flags = []
character_set = string.ascii_letters + string.digits + "!{_}?"
set_length = len(character_set)

for first_idx in range(set_length):
    first_set = character_set[:first_idx] + character_set[first_idx + 1:]
    
    for second_idx in range(first_idx + 1, set_length):
        second_set = first_set[:second_idx] + first_set[second_idx + 1:]

        for third_idx in range(second_idx + 1, set_length):
            third_set = second_set[:third_idx] + second_set[third_idx + 1:]

            for key in range(len(third_set)):
                decrypted_flag = ''
                for char in encrypted_text:
                    if char not in third_set:
                        continue
                    decrypted_flag += (third_set[(third_set.index(char) - key) % len(third_set)])

                if 'KCSC{' in decrypted_flag:
                    found_flags.append(decrypted_flag)

for flag in found_flags:
    print(flag)

```
- Sau khi chạy sẽ có nhiều kết quả nhưng chỉ cần kiên nhẫn là có flag 
> Flag : KCSC{y0u_be4t_My_C3A54R_bu7_HoW!!?!}
