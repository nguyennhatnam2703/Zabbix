
# Tích hợp Zabbix vào Grafana

# 1.Grafana là gì ?

- Grafana là một công cụ hiển thị biểu đồ monitor phổ biến.

- Grafana hỗ trợ các data source, phục vụ việc query metric, hiển thị lên dashboard..

# 2.Cài đặt Grafana cho Zabbix.

- Bước 1: Cài đặt EPEL-repo : ` yum install epel-release `

- Bước 2: Tải về các gói cài đặt: ` wget https://dl.grafana.com/oss/release/grafana-6.4.4-1.x86_64.rpm `

- Bước 3: Giải nén gói cài đặt: ` sudo yum localinstall grafana-6.4.4-1.x86_64.rpm `

- Bước 4: Cài đặt Grafana: ` sudo yum install grafana `

- Bước 5:  Khởi động dịch vụ:

  + ```
      systemctl daemon-reload
      systemctl start grafana-server
      systemctl enable  grafana-server
	  
	```
- Bước 6: Truy cập vào dashboard Grafana: ` Truy cập theo địa chỉ: http://<IP_GRAFANA>:3000 `.

  + tài khoản mặc định ban đầu là admin/admin.

# 3.Thêm source zabbix

- Bước 1: Trong giao diện dashboard ta thêm plugin

  + ![]( /image/g1.PNG)
  
- Bước 2: Cài đặt Plugin đồ họa cho Zabbix

  + ```
     grafana-cli plugins install alexanderzobnin-zabbix-app

     systemctl restart grafana-server
	 
	```
- Bước 3: Trong danh sách các plugin ta tìm đến plugin là Zabbix

  + ![]( /image/g2.png)
  
- Bước 4: enable plugin Zabbix.

  + ![]( /image/g3.png)
  
- Bước 5: Add thêm data source

  + ![]( /image/g4.png)

  + ![]( /image/g5.png)
  
  + ![]( /image/g6.png)
  
  + Trong giao diện add, ta điền các thông số cần thiết của source, sau đó chọn Save and test:

  + ![]( /image/gra4.PNG)

  + Sau đó save và test:

  + ![]( /image/g7.png)

- Bước 6: Sau khi thêm source thành công ta thử import template vào để quan sát biểu đồ

  + ![]( /image/g8.png)

  + Quan sát biểu đồ monitor thu được: 

  + ![]( /image/g9.PNG)   
  
# Tham khảo:

- [1] https://news.cloud365.vn/zabbix-tich-hop-zabbix-vao-grafana/

- [2] https://mdungblog.wordpress.com/2018/08/31/huong-dan-cai-dat-do-hoa-grafana-cho-zabbix/
  	

  
