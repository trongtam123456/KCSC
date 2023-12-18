## Giải
- Sau khi truy cập được trang web mì tôm thanh long với đường dẫn: `http://103.162.14.116:10002/`
- Thứ đầu tiên em nghĩ ngay đến là tìm đường dẫn đi đến flag
- Em bắt đầu lục source code nhưng vẫn không có 
- Hết cách em phải dùng đến cách brute force xem thử có đường dẫn nào hay không
- Sau 1 hồi tra gg thì em biết được công cụ mang tên dirsearch.
> dirsearch -u http://103.162.14.116:10002/ 
```text

Extensions: php, aspx, jsp, html, js | HTTP method: GET | Threads: 25 | Wordlist size: 11460

Output File: /home/trongtam/reports/http_103.162.14.116_10002/__23-12-17_09-38-51.txt

Target: http://103.162.14.116:10002/

[09:38:51] Starting: 
[09:38:59] 403 -  282B  - /.ht_wsr.txt                                      
[09:38:59] 403 -  282B  - /.htaccess.orig                                   
[09:38:59] 403 -  282B  - /.htaccess.save
[09:38:59] 403 -  282B  - /.htaccess.bak1
[09:38:59] 403 -  282B  - /.htaccess_extra                                  
[09:38:59] 403 -  282B  - /.htaccessBAK                                     
[09:38:59] 403 -  282B  - /.htaccessOLD2
[09:38:59] 403 -  282B  - /.htaccessOLD                                     
[09:38:59] 403 -  282B  - /.htaccess_orig
[09:38:59] 403 -  282B  - /.html                                            
[09:38:59] 403 -  282B  - /.htm                                             
[09:38:59] 403 -  282B  - /.htpasswd_test                                   
[09:38:59] 403 -  282B  - /.htpasswds                                       
[09:38:59] 403 -  282B  - /.htaccess_sc                                     
[09:38:59] 403 -  282B  - /.htaccess.sample                                 
[09:38:59] 403 -  282B  - /.httr-oauth                                      
[09:39:57] 200 -  346B  - /flag.txt                                         
[09:40:02] 301 -  326B  - /images  ->  http://103.162.14.116:10002/images/  
[09:40:02] 403 -  282B  - /images/                                          
[09:40:03] 403 -  282B  - /includes/                                        
[09:40:03] 301 -  328B  - /includes  ->  http://103.162.14.116:10002/includes/
[09:40:25] 301 -  325B  - /pages  ->  http://103.162.14.116:10002/pages/    
[09:40:25] 403 -  282B  - /pages/                                           
[09:40:40] 403 -  282B  - /server-status                                    
[09:40:40] 403 -  282B  - /server-status/
                                                                             
Task Completed                                                                                                                                                             
```
- Có thể thấy có rất nhiều đường dẫn nhưng hầu hết trả về 403
- Chỉ có các đường dẫn truy cập được như flag.txt, /images, /includes, /pages truy cập lần lượt thì flag xuất hiện tại /flag.txt
`http://103.162.14.116:10002/flag.txt`
> Flag : KCSC{Lan_Dau_Tien_Trai_Thanh_Long_Co_Trong_KCSC:))}
