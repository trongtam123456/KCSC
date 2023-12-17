## Đề
> Very easy vbs !!!
## Giải 
- Sau khi tải xuống được 1 file nén code.zip
- Nhưng khi giải nén thì nó bắt nhập mật khẩu
- Đọc đề thì em thấy không đề cập đến mật khẩu 
- Nên em nghĩ phải `cờ rắc` nó rồi
- Em định dùng hashcat để crack mà mỗi tội em không biết sử dụng =)))
- Nên em thay thế bằng cách dùng john 
>  zip2john code.zip > hash.txt
- Câu lệnh này chuyển file code.zip thành hash rồi đưa vào file hash.txt
- Em sử dụng wordlist rockyou để brute force nó
```text
└─$ sudo john --wordlist=/usr/share/wordlists/rockyou.txt hash
Using default input encoding: UTF-8
Loaded 1 password hash (PKZIP [32/64])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
kma9239          (code.zip/code.vbs)     
1g 0:00:00:01 DONE (2023-12-17 15:58) 0.5882g/s 3830Kp/s 3830Kc/s 3830KC/s knia10129..km2742
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
```
- Có thể thấy mật khẩu là kma9239
- Giờ thì giải nén thôi
- Sau khi giải nén em được 1 file code.vbs
- Lại đến với vấn đề không mở được trên linux nên em dùng cat đọc đỡ
> cat code.vbs
```text
Dim http : Set http = CreateObject("MSXML2.ServerXMLHTTP.6.0")
Dim url : url = "http://api.bitly.com/v3/shorten?login=YOUR_BITLY_USERNAME&apiKey=YOUR_BITLY_API_KEY&longUrl=https://pastebin.pl/view/a60d3da5"

http.Open "GET", url, False
http.setRequestHeader "Content-Type", "text/xml"
http.send ""

If http.Status = 200 Then
    Dim response : response = http.responseText
    Dim shortUrl : shortUrl = ParseJson(response)("data")("url")
    WScript.Echo "Shortened URL: " & shortUrl
Else
    WScript.Echo "Error: " & http.Status & " - " & http.statusText
End If

Function ParseJson(json)
    Dim objJson : Set objJson = CreateObject("MSJSON.Parser")
    Set ParseJson = objJson.Parse(json)
End Function

```
- Ở đây em thấy 1 đường link : `https://pastebin.pl/view/a60d3da5`
- Truy cập vào lại có mã hoá base64 `S0NTQ3tWYjRfaDAxX2xvciIiX2FlX3RoMG5nX2M0bV89KCgofQ==`
- Decode ra flag 
> Flag : KCSC{Vb4_h01_lor""_ae_th0ng_c4m_=(((}