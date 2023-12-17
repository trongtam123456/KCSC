## Giải 
## Cách 1
- Sau khi tải về em được 1 file chall.exe
- Vì trên linux không mở được file exe nên em dùng strings để đọc sơ lược 
> strings chall.exe
```text
Nh4p. v40` f149 v4` nh4n' [3N73R]
S0NTQ3tDaDQwYF9NfF98bjlgX0QzTidfVjAxJ183N1wvX0tDU0N9
Great!!!
Sai roi. Hay thu lai
Argument domain error (DOMAIN)
Argument singularity (SIGN)
Overflow range error (OVERFLOW)
Partial loss of significance (PLOSS)
Total loss of significance (TLOSS)
The result is too small to be represented (UNDERFLOW)
Unknown error
_matherr(): %s in %s(%g, %g)  (retval=%g)
Mingw-w64 runtime failure:
Address %p has no image-section
  VirtualQuery failed for %d bytes at address %p
  VirtualProtect failed with code 0x%x
  Unknown pseudo relocation protocol version %d.
  Unknown pseudo relocation bit size %d.
.pdata

```
- Tại đoạn `S0NTQ3tDaDQwYF9NfF98bjlgX0QzTidfVjAxJ183N1wvX0tDU0N9` có vẻ như nó được mã hoá 
- Thử giải mã bằng base64
```text
┌──(trongtam㉿kali)-[~/Downloads]
└─$ echo "S0NTQ3tDaDQwYF9NfF98bjlgX0QzTidfVjAxJ183N1wvX0tDU0N9" | base64 -d
KCSC{Ch40`_M|_|n9`_D3N'_V01'_77\/_KCSC} 
```
> Flag : KCSC{Ch40`_M|_|n9`_D3N'_V01'_77\/_KCSC} 
## Cách 2
- Em mở file chall.exe bằng ida64
```text
int __fastcall main(int argc, const char **argv, const char **envp)
{
  char Str1[256]; // [rsp+20h] [rbp-60h] BYREF

  _main();
  puts("Nh4p. v40` f149 v4` nh4n' [3N73R]");
  while ( 1 )
  {
    if ( !gets(Str1) )
      return 0;
    if ( !strcmp(Str1, "S0NTQ3tDaDQwYF9NfF98bjlgX0QzTidfVjAxJ183N1wvX0tDU0N9") )
      break;
    puts("Sai roi. Hay thu lai");
  }
  return printf("Great!!!");
}
```
- Đây có vẻ là chương trình viết ngôn ngữ C
- Tuy chưa học nhưng dựa vào những câu lệnh cơ bản có thể thấy nếu dữ liệu nhập vào khác với chuỗi nào đó thì in ra `sai rồi, thử lại`
- Vì vậy chỉ cần decode được strings `S0NTQ3tDaDQwYF9NfF98bjlgX0QzTidfVjAxJ183N1wvX0tDU0N9` là có flag 
> Flag : KCSC{Ch40`_M|_|n9`_D3N'_V01'_77\/_KCSC}