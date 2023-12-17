## Đề 
> nc 103.162.14.116 14002
## Giải 
- Sau khi kết nối với máy chủ 
- Nó bắt mình nhập giá trị lớn nhất mà họ random ra 
- Em viết code py để xử lý giá trị tìm tìm số lớn nhất 
- Sau đó up nó lên bằng thư viện os
- Nhưng quên mất 1 điều, mỗi lần kết nối là máy chủ sẽ random 1 list khác nhau 
- Sau n*3.14 phút ngồi mò google em biết được 1 thư viện pwn 
- Đây là code của em (code dùng code gpt nên chữ tiếng anh hơi nhiều)
```text
import re
from pwn import *

# Thông tin máy chủ
server_ip = "103.162.14.116"
server_port = 14002

try:
    # Kết nối đến máy chủ
    conn = remote(server_ip, server_port)
    
    print(f"Đã kết nối đến {server_ip}:{server_port}")

    while True:
        # Nhận dữ liệu từ máy chủ
        received_data = conn.recvline().decode()
        print(received_data)
        # Kiểm tra nếu không còn dữ liệu
        if not received_data:
            break
        
        # a là dữ liệu nhận được từ máy chủ
        a = received_data
        input_string = a

        # Sử dụng biểu thức chính quy để trích xuất mảng số từ chuỗi
        match = re.search(r'\[([^]]+)\]', input_string)

        if match:
            # Lấy chuỗi con chứa mảng số từ match
            array_string = match.group(1)
    
            # Chuyển chuỗi số thành danh sách các số nguyên
            arr = [int(num) for num in re.findall(r'\d+', array_string)]
    
            # Tìm giá trị lớn nhất trong mảng
            max_value = max(arr)
            
            # In thông tin
            print("Mảng các số:", arr)
            print("Giá trị lớn nhất là:", max_value)
            
            # Gửi giá trị lớn nhất lại cho máy chủ
            conn.sendline(str(max_value))
            		
except Exception as e:
    print("Đã xảy ra lỗi:", e)
    print(conn.sendline(str(max_value)))

finally:
    # Đóng kết nối
    conn.close()
```
- Sau khi kết nối với máy chủ nó sẽ nhận dữ liệu và xử lý tìm giá trị lớn nhất 
- Sau đó up lên lại máy chủ rồi tiếp tục vòng lặp 
- Đây là kết quả sau khi chạy(do quá nhiều dữ liệu nên em chỉ show ra khúc tìm flag)
```text
4409314, 383897527401332947858244268684745, 769715236999241159561622308475458, 430375137478587619996860329964351, 125998789259376296715685254652887, 894459429560992323986149610332015, 886958058833007593438697657331666, 976403466545807743854370985231661, 576738595551364265627608303321585, 120972197954787127701149847761346, 845931629090618236675325404905174, 503700653161868019813726314879465, 95788786140185506707257602481860, 857000329486212962103723422524773, 746053579641363671598210900126242]

Mảng các số: [323138834142363917320096146325799, 159988245405555674353939882687129, 864647197260136848039389621873321, 86426601283113113105820349380110, 980145409799886963024575704757854, 302537308485112641351475383503603, 865264885937449007493421251892006, 948366820847413329380131667523223, 500992052291261491363169328704447, 280472678170535447325392914181012, 931794141853848968753138680184773, 791405340336540115540929039758049, 344128465789337325331883302211550, 549323020678417275972631513797365, 10176351870596273027784382981631, 438389762332989695340506772470367, 931250628798555302842930453493972, 37155850776733469056631410057098, 604485734037725433558198694409314, 383897527401332947858244268684745, 769715236999241159561622308475458, 430375137478587619996860329964351, 125998789259376296715685254652887, 894459429560992323986149610332015, 886958058833007593438697657331666, 976403466545807743854370985231661, 576738595551364265627608303321585, 120972197954787127701149847761346, 845931629090618236675325404905174, 503700653161868019813726314879465, 95788786140185506707257602481860, 857000329486212962103723422524773, 746053579641363671598210900126242]
Giá trị lớn nhất là: 980145409799886963024575704757854
max = CORRECT!

Flag: b'KCSC{Ezzz_Programmingggg}'

Đã xảy ra lỗi: 
/home/trongtam/Prog1: Max.py:48: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  print(conn.sendline(str(max_value)))
None
[*] Closed connection to 103.162.14.116 port 14002
```
> Flag : KCSC{Ezzz_Programmingggg}