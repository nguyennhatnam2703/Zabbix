
# Cài đặt Zabbix Server:

- Bước chuẩn bị:
  sudo systemctl disable firewalld
  
  sudo systemctl stop firewalld
  
  sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
  
  sudo setenforce 0
   
- Bước 1: Cài đặt database và 1 số gói phụ trợ, ở đây tôi sử dụng MySQL

  yum update -y
  
  yum install php php-devel php-bcmath php-pear php-gd php-mbstring php-mysql php-xml -y
  
- Cài đặt MySQL 

  yum install wget
  wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
  
  rpm -ivh mysql-community-release-el7-5.noarch.rpm
  
  yum install mysql-server -y
  
  systemctl start mysqld
  
  systemctl enable mysqld 

- Đặt mật khẩu cho user root của MySQL

  mysql_secure_installation <<EOF
  
  Y
  
  nam
  
  nam
  
  Y
  
  Y
  
  Y
  
  Y
  
  EOF

- Bước 2: Login vào database để tạo user, phân quyền…
- mysql -u root -p
- Tạo database, phân quyền:

create database zabbix;

grant all privileges on zabbix.* to 'zabbix'@'localhost' identified by 'zabbix';

exit

- Bước 3: Cài đặt gói Zabbix cần thiết

- rpm -Uvh https://repo.zabbix.com/zabbix/4.4/rhel/7/x86_64/zabbix-release-4.4-1.el7.noarch.rpm
- yum install zabbix-server-mysql -y
- yum install zabbix-web-mysql -y

- Bước 4: Import database Zabbix nếu sử dụng MySQL
 zcat /usr/share/doc/zabbix-server-mysql*/create.sql.gz | mysql -uzabbix -p zabbix
 
- Bước 5: Config database trong file /etc/zabbix/zabbix_server.conf 
 DBHost=localhost
DBName=zabbix
DBUser=zabbix
DBPassword=zabbix

- service zabbix-server start
systemctl enable zabbix-server

- Bước 6: Chỉnh sửa các tham số cho web frontend trong file /etc/httpd/conf.d/zabbix.conf
  + Truy cập file /etc/httpd/conf.d/zabbix.conf và uncomment ở dòng timezone và chỉnh sửa lại timezone
  php_value max_execution_time 300
  php_value memory_limit 128M
  php_value post_max_size 16M
  php_value upload_max_filesize 2M
  php_value max_input_time 300
  php_value max_input_vars 10000
  php_value always_populate_raw_post_data -1
  php_value date.timezone Asia/Ho_Chi_Minh
  
- Bước 7: Khởi động lại dịch vụ
  systemctl restart zabbix-server
  systemctl restart httpd
  systemctl enable zabbix-server httpd  
  
- Bước 8: Truy cập vào địa chỉ http://<IP_Zabbix_Server>/zabbix/
  ![]( /image/z1.PNG)
-   Tiếp tục chọn Next Step;
  ![]( /image/z2.PNG)
- Cấu hình để Zabbix kết nối tới database ( pass la pass giong voi mysql)
  ![]( /image/z3.PNG)
- Đặt hostname của Zabbix Server. Có thể bỏ qua bước này
  ![]( /image/z4.PNG)
  
- Sau đó chọn Finish

  ![]( /image/z6.PNG)
  
# tham khao
-  https://news.cloud365.vn/zabbix-cai-dat-zabbix-server-phien-ban-4-4-tren-centos7/?fbclid=IwAR3fF2ildx8MORPW4hs9uCDcxuTllbOMLGlGkoiTPTi7X2I8k0i1Dzt1suk
  
  
