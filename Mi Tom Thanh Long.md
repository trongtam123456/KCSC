## Giải
- Sau khi truy cập được trang web mì tôm thanh long với đường dẫn: `http://103.162.14.116:10002/`
- Thứ đầu tiên em nghĩ ngay đến là tìm đường dẫn đi đến flag
- Em bắt đầu lục source code nhưng vẫn không có 
- Hết cách em dùng đến công cụ dirsearch 
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
- Có thể thấy có rất nhiều đường dẫn nhưng ta chỉ cần chú ý đến các đường dẫn truy cập được
- Có 1 file flag.txt nên em vào thử `http://103.162.14.116:10002/flag.txt`
> Flag : KCSC{Lan_Dau_Tien_Trai_Thanh_Long_Co_Trong_KCSC:))}