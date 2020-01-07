
# Giám sát Windown Server bằng zabbix-agent

- Mục tiêu: Bài viết này sẽ hướng dẫn bạn cách cài đặt zabbix-agent trên Windown Server 2012 để tiến hành các hoạt động theo dõi tình trạng tài nguyên của 
 Windown Server 2012.
  
 
# 1.Các bước cài đặt zabbix-agent trên Windown Server 2012

## Bước 1: Tải về gói cài đặt zabbix-agent
  
 + Link tải: https://www.zabbix.com/download_agents?__cf_chl_captcha_tk__=d3fd4382a41cb5d2361b3beb3b7c084185c901e6-1578368235-0-Aeq5J_kswwhDRWDYPgfgdgIvOET6N81MWsmQ-EI7OyE2I-Sfgt483Uzq6Z1zDmqahoQYkEaDNllHkZr4ko46_rdtWuGuMx18hc-QcBoF_W420jA-Nj7dqYvlazUdDFQTB3mKDCFe_MMXtDEcAGNFi7sqhrPtS7tc1y-1xpuy1BpWuc0TIYWTJEAFIk9yj0uo-c4Eeq5u0_8fh4Q6eewQdsPg6b9c8ziwsd-mJjpLPVW1ZxIM8-Mx4PYz3KwxXQgdT87RmYXMx2G7bRP2Xqx-RHM-B6eGJNNBKeUrrpbn67aNqn1Zl8mpsRuSpQjNWl2E6xhb6eO6Y_PEqi-DAbSlVdWTW2Lnq7PoYHR4pz2eCudmBaylzsSnK46u1uHE8uUi9Q

 + ở đây tôi dow bản zabbix-agent 4.4- win( msi)
  
  ![]( /image/w3.PNG)
  
## Bước 2: Tiến hành cài đặt và cấu hình
 
 - sau khi tải về thì tôi tải về và click vào file tải về thì nó sẽ ra giao diện như sau:
   
  ![]( /image/w14.PNG)

 - Sau đó bạn cứ next liên tục thì khi đến phần điền thông tin cấu hình thì bạn điền như sau:
   
   + Server= < địa chỉ IP của zabbix-server>
   + ServerActive=< địa chỉ IP của zabbix-server>
   + Hostname=< hostname của zabbix-agent>
   
 - Sau đó bạn có thể kiểm tra lại thông tin cấu hình ở file `zabbix-agent.conf`
   
   ![]( /image/w16.PNG)   
   
## Bước 3:Thiết lập zabbix-agent khỏi đồng cùng hệ thống:

  - Ta thiết lập dịch vụ khởi động cùng hệ thống Windown:
    
	+ Start Windown > Run > "services.msc" ( ta cd.. 2 lần )> Chọn service "zabbix agent" > Chuột phải rồi chon properties > Start type chọn automatic
	
	+ ![]( /image/w4.PNG)
	
	+ với cách trên thì bạn có thể bật tắt dịch vụ zabbix-agent.
	
## Bước 4: Mở port firewall cho port 10050

   - Tìm kiếm phần Windows Firewall with advance security

     + ![]( /image/w5.PNG)

   - Tạo rule theo chiều inbound
   
     + ![]( /image/w6.PNG)
  
   - Tạo rule cho port

     + ![]( /image/w7.png)
   
   - Sử dụng TCP port 10050
    
   + ![]( /image/w8.png)

   - Cho phép kết nối

     + ![]( /image/w9.png)

   - Tích hết vào các rule

     + ![]( /image/ww.png)

   - Đặt tên cho rule
     
    + ![]( /image/w10.png)

## Bước 5: Add host trên zabbix web

  - Đầu tiên vào Configuration > Host. Sau đó điền các thông tin host,các thông tin bắt buộc bao gồm có:
   
   + Hostname: Tên host hiển thị trên Zabbix Web
   + Groups: Gán 1 hoặc nhiều nhóm cho host
   + Agent interfaces: là địa chỉ IP để monitor của host 
   
   + ![]( /image/w13.PNG)
   
  - Sau đó chọn template cho host Windows sau đó chọn Add:
  
   + ![]( /image/w11.PNG)
   
## Kết quả khi add thành công:

  - ![]( /image/w12.PNG)

# Tổng kết:

  - Như vậy tôi đã hướng dẫn cài đặt thành công zabbix-agent trên Windown Server 2012.Ở dưới tôi có để các nguồn mà tôi tham khảo,các bạn có thể tìm hiểu ở
  đó để biết thêm chi tiết.Chúc các bạn thành công!!!
  
# Tham khảo:

 - [1] https://news.cloud365.vn/zabbix-giam-sat-windows-server-bang-zabbix-agent/

 - [2] https://cuongquach.com/cai-dat-zabbix-agent-tren-windows-client.html 

  
   
  
   
   
