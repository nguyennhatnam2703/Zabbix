
# Cấu hình zabbix gửi cấu hình qua mail

# Cài đặt SSMTP trên Centos 7

- Bước 1: Cài đặt phần mềm SSMTP
 `sudo yum update -y`
 `sudo yum install ssmtp mailx -y`
 
- Bước 2: Cấu hình các tham số của SSMTP

   `vi /etc/ssmtp/ssmtp.conf`

  ```
	root=Tên tài khoản@gmail.com
    mailhub=smtp.gmail.com:465
    rewriteDomain=domain local
    hostname=zabbix server hostname
    UseTLS=Yes
    UseSTARTTLS=Yes
    AuthUser=địa chỉ email
    AuthPass=pass email
	``` 
	
- Bước 3: Bật tính năng cho phép các truy cập kém an toàn

  + Truy cập vào link sau và bật tính năng: https://myaccount.google.com/lesssecureapps	
  
  ![]( /image/email1.png)

- Bước 4: Test thử gửi mail bằng dịch vụ SSMTP

 `echo "Hello toi la nam" | ssmtp <GMAIL_ADDRESS>`
 
  ![]( /image/email2.PNG)
  
# Cấu hình trên Zabbix Server

- Bước 1: Đăng nhập vào Zabbix Web  

  ![]( /image/email3.PNG)
  
- Bước 2: Cấu hình Media Types

  ![]( /image/email4.png) 

  ![]( /image/email5.png)

- Bước 3: Cấu hình gửi mail cảnh báo như sau:

 ![]( /image/email6.PNG)
 
 + Name: Đặt một tên bất kì bạn muốn để phân biệt với các loại media types khác
 + SMTP server: smtp.gmail.com
 + SMTP port: 465
 + SMTP helo: gmail.com
 + SMTP email: điền địa chỉ sẽ gửi email cảnh báo tới người dùng
 + Username/Password: Thông tin đăng nhập của SMTP email
 
- Bước 4: Enable Config Action 

  ![]( /image/email7.PNG)
  
- Bước 5: Sau khi enable, ta cấu hình User nhận email

  + Nhập địa chỉ email ta muốn gửi cảnh báo đến và chọn add
  
  + ![]( /image/email8.PNG)
  
  + Cuối cùng ta chọn Update để hoàn tất
  
  + ![]( /image/email9.PNG)
  
 # Test cảnh báo

- Khi client kết nối tới server bị ngắt kết nối

  ![]( /image/email10.PNG)

- Khi server khởi động trở lại

  ![]( /image/email11.PNG)  
  
- Thông báo khi loadavg vượt quá mức cảnh báo.

  ![]( /image/email12.PNG)  
  
  ( trung bình 1.5 process xử lý trong 5 phút)
  

    