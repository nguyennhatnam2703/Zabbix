
# Giám sát server Ubuntu 18.04 bằng zabbix-gent

# 1.Các bước cài đặt zabbix-gent trên Ubuntu 18.04

## Bước 1:Tải về các gói cài đặt:

- `wget https://repo.zabbix.com/zabbix/4.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_4.4-1%2Bxenial_all.deb`

## Bước 2: Giải nén và cài đặt:

- `sudo dpkg -i zabbix-release_4.4-1+xenial_all.deb`

## Bước 3: Update các gói phần mềm và cài zabbix-agent:

- `sudo apt-get update`

- `sudo apt-get install zabbix-agent -y`

## Bước 4: Sửa file cấu hình zabbix-agent

- Sửa lại file /etc/zabbix/zabbix_agentd.conf với các tham số như sau:

-    ``` 
     Server=<IP_ZABBIX_SERVER>
     ServerActive=<IP_ZABBIX_SERVER>
     Hostname=<ZABBIX_SERVER_HOSTNAME>
	 
	 ```
	 
## Bước 5: Khởi động dịch vụ zabbix-agent

-   ```
    systemctl start zabbix-agent
    systemctl enable zabbix-agent
    
    ```
# 2.Add host trên zabbix web	

- Đầu tiên vào Configuration > Host > Create host. Sau đó điền các thông tin host,các thông tin bắt buộc bao gồm có:

 + Hostname: Tên host hiển thị trên Zabbix Web

 + Groups: Gán 1 hoặc nhiều nhóm cho host

 + Agent interfaces: là địa chỉ IP để monitor của host

- ![]( /image/un1.PNG)

- sau đó chọn template:

- ![]( /image/cen2.PNG)

- Kết quả khi add thành công:

- ![]( /image/un2.PNG)

# Tham khảo:

- [1] https://news.cloud365.vn/zabbix-giam-sat-server-ubuntu-16-04-bang-zabbix-agent/
	 

