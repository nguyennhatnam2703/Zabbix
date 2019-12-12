
# Tìm hiểu về Zabbix

# Mục đích ra đời
- Giám sát mạng có vị trí rất quan trọng trong một công ty và nó còn đặc biệt quan trọng hơn đối với các công ty làm việc dựa vào các dịch vụ công nghệ thông tin.
- Hệ thống giám sát có thể tìm và giúp đỡ giải quyết việc tải trang web snail-paced, mất mát email, hoạt động của người truy vấn và truyền tải file, nguyên nhân 
 do quá tải, sự cố server...
- Zabbix ra đời nhằm giải quyết cho ta các vấn đề về giám sát.

# Zabbix là gì? Chức năng của nó ?
- Zabbix là một công cụ mã nguồn mở giải quyết cho ta các vấn đề về giám sát.
- Zabbix là phần mềm sử dụng các tham số của một mạng, tình trạng và tính toàn vẹn của Server cũng như các thiết bị mạng.
- Zabbix sử dụng một cơ chế thống báo linh hoạt cho phép người dùng cấu hình email hoặc sms để cảnh báo dựa trên sự kiện được ta thiết lập sẵn.
- Ngoài ra Zabbix cung cấp báo cáo và dữ liệu chính xác dựa trên cơ sở dữ liệu.

# Ưu điểm của Zabbix

- Giám sát cả Server và thiết bị mạng
- Dễ dàng thao tác và cấu hình
- Hỗ trợ máy chủ Linux, Solaris, FreeBSD..
- Đáng tin cậy trong việc chứng thực người dùng
- Linh hoạt trong việc phân quyền người dùng
- Giao diện web đẹp mắt
- Thông báo sự cố qua email và SMS
- Mã nguồn mở và chi phí thấp

# Các thành phần cơ bản của Zabbix

- Zabbix server
  + Zabbix Server có thể kiểm tra các dịch vụ mạng từ xa thông qua các báo cáo của Agent gửi về cho Zabbix Server và từ đó nó sẽ lưu trữ tất cả các cấu hình 
  cũng như là các số liệu thống kê.

- Zabbix Proxy
  + Là phần tùy chọn của Zabbix. Nó có nhiệm vụ thu nhận dữ liệu, lưu trong bộ nhớ đệm và chuyển đến Zabbix Server.
  + Đây là một tùy chọn nên bạn có thể cài nó hoặc không nhưng nó sẽ rất hữu ích với hột hệ thống lớn. Nó sẽ giúp giảm tải cho Zabbix Server.
  + Zabbix Proxy là một giải pháp lý tưởng cho việc giám sát tập trung của các địa điểm từ xa, chi nhánh công ty, các mạng lưới không có quản trị viên nội bộ.

- Zabbix Agent:
  + Zabbix Agent được cài đặt trên các thiết bị mà ta cần giám sát. Nó sẽ có nhiệm vụ thu thập thông tin và gửi nó về Zabbix Server.

- Web interface:
  + Web interface giúp ta có thể truy cập để theo dõi các thiết bị ở bất kỳ đâu. Nó là một phần của zabbix server.
  
- Database sử dụng MariaDB, MySQL, PostgresSQL để lưu trữ dữ liệu thu thập được. 
 










# Tham khảo
- https://news.cloud365.vn/zabbix-cai-dat-zabbix-server-phien-ban-4-4-tren-centos7/?fbclid=IwAR3fF2ildx8MORPW4hs9uCDcxuTllbOMLGlGkoiTPTi7X2I8k0i1Dzt1suk
- https://news.cloud365.vn/zabbix-giam-sat-server-centos-7-bang-zabbix-agent/?fbclid=IwAR0N5VbXVoqIFuVAfZsLzJ-MSIvaoofSmvh7alcpzIXWNbjqg2hBRGzr6rI
- https://techblog.vn/tong-quan-ve-zabbix
- https://github.com/quangln94/Linux/tree/master/Monitoring/Zabbix
- https://www.facebook.com/groups/quantrimang365/permalink/808013262983356/
- https://viblo.asia/p/cai-dat-zabbix-tren-server-ubuntu-1604-p1-V3m5WbwylO7?__cf_chl_captcha_tk__=babc6d4aa514be86e8f1df0768a286574218f2ab-1575598404-0-AU_6YpLNZOZogGUB4T8YwCiDQghreF6ClK-Hhf4Gj7fwuOympyWJWQLL0mQIe8GUu8Z192KxEPvBmAYYqB2BpWAb9-1O6ErSq7CBdsE4ndQ5x9d8GTL2FYk1ZqNpzXmUKz-Nbf4wGwX-46ozXzLpg9tIv_BvVt7pm3uGx8mxjk6xcL72MmfdIQPedes76JYyJ8BdIPiHaIxsAp0sqIadlxOmm56LQ4FQSzoE8-jG6ud7uhaB53EZ_6wEYltuvcImPc8EyXyc5jWvXms4Jb74bB_6M0ke-8ybvkQ2mysTL1AB2qrxG4kFx5mphBadSUWMmEkGufFI0HasPs70BzbeNeP_ySMSihGMUpZd1Hk-27s4SUVpvPSgbU1JxUukWEJmIxTwrN7qckCPEseo6AjrLoXFcXn9Nxgwi6Bdl7ixqxCFtWIxjoH1mMM4LnMwH7ZFFw
