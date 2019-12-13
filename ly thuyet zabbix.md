
# Tìm hiểu về Zabbix

# Mục đích ra đời
- Tìm và giúp đỡ giải quyết việc tải trang web snail-paced, mất mát email, hoạt động của người truy vấn và truyền tải file, nguyên nhân do quá tải, sự cố server… là những tiện ích từ việc giám sát mạng và Zabbix là một trong những công cụ được sinh ra để giải quyết vấn đề 
giám sát.

# Zabbix là gì? 
- Zabbix là một công cụ mã nguồn mở giải quyết cho ta các vấn đề về giám sát.
- Zabbix được sáng lập bởi Alexei Vladishev và hiện nay đang được phát triển và hỗ trợ bởi Zabbix SIA.
- Zabbix được viết và phát hành dưới bản quyền General Public License GPL phiên bản 2

# Chức năng của nó ?
- phần mềm zabbix có thể theo dõi các thông số của mạng và tình trạng của server. 
- Zabbix sử dụng các phương pháp cảnh báo linh hoạt, cho phép bạn cấu hình cảnh báo dựa trên email hoặc SMS cho hầu hết các sự kiện xảy ra, nắm bắt nhanh các sự cố xảy ra của server.
- Zabbix còn hỗ trợ chức năng báo cáo, tổng hợp và dự đoán dữ liệu tốt dựa trên những dữ liệu có sẵn đã được lưu trữ

# Ưu điểm của Zabbix

- Giám sát cả Server và thiết bị mạng
- Dễ dàng thao tác và cấu hình
- Hỗ trợ máy chủ Linux, Solaris, FreeBSD..
- Đáng tin cậy trong việc chứng thực người dùng
- Linh hoạt trong việc phân quyền người dùng
- Giao diện web đẹp mắt
- Thông báo sự cố qua email và SMS
- Mã nguồn mở và chi phí thấp

# Nhược điểm của Zabbix

- Không có giao diện web mobile hỗ trợ
- 

# Yêu cầu tối thiểu phần cứng

- CPU(Central Processing Unit): 2core
- RAM: 1G
- DISK:50G

# Các thành phần cơ bản của Zabbix

- ![]( /image/ctzabbix.png)
- `Zabbix server`
  + Zabbix Server có thể kiểm tra các dịch vụ mạng từ xa thông qua các báo cáo của Agent gửi về cho Zabbix Server và từ đó nó sẽ lưu trữ tất cả các cấu hình 
  cũng như là các số liệu thống kê.

- `Zabbix Proxy`
  + Là phần tùy chọn của Zabbix. Nó có nhiệm vụ thu nhận dữ liệu, lưu trong bộ nhớ đệm và chuyển đến Zabbix Server.
  + Đây là một tùy chọn nên bạn có thể cài nó hoặc không nhưng nó sẽ rất hữu ích với hột hệ thống lớn. Nó sẽ giúp giảm tải cho Zabbix Server.
  + Zabbix Proxy là một giải pháp lý tưởng cho việc giám sát tập trung của các địa điểm từ xa, chi nhánh công ty, các mạng lưới không có quản trị viên nội bộ.

- `Zabbix Agent`:
  + Zabbix Agent được cài đặt trên các thiết bị mà ta cần giám sát. Nó sẽ có nhiệm vụ thu thập thông tin và gửi nó về Zabbix Server.

- `Web interface`:
  + Web interface giúp ta có thể truy cập để theo dõi các thiết bị ở bất kỳ đâu. Nó là một phần của zabbix server.
  
- Database sử dụng MariaDB, MySQL, PostgresSQL để lưu trữ dữ liệu thu thập được. 

# Một số khái niệm

- Host: Là một máy tính, server, vps, chạy các hệ điều hành khác nhau hoặc một thực thể trong hệ thống mạng như là máy in, máy chấm công, máy photo, máy camera có hỗ trợ các giao thức mà monitor zabbix cung cấp

- Templates: Là một bố cục hay một thành phần được tạo ra sẳn để không cần phải lặp đi lặp lại khi gặp đúng 1 trường hợp.

- Items : Đơn giản là một nơi chứa các key như là key memory, key cpu, key hdd… Items được đưa vào trong một templates.

- Triggers : Là một điều kiện khi thỏa mãn điều kiện của Triggers mà người lập trình đặt ra thì sẽ thực hiện một hành động nào đó tiếp theo.

- Graphs : Là một sơ đồ giám sát trực quan để người quản trị nhìn các thông tin một cách dễ dàng hơn.
 










# Tham khảo
- 
- 
- https://techblog.vn/tong-quan-ve-zabbix
- https://github.com/quangln94/Linux/tree/master/Monitoring/Zabbix
- https://www.facebook.com/groups/quantrimang365/permalink/808013262983356/
- https://viblo.asia/p/cai-dat-zabbix-tren-server-ubuntu-1604-p1-V3m5WbwylO7?__cf_chl_captcha_tk__=babc6d4aa514be86e8f1df0768a286574218f2ab-1575598404-0-AU_6YpLNZOZogGUB4T8YwCiDQghreF6ClK-Hhf4Gj7fwuOympyWJWQLL0mQIe8GUu8Z192KxEPvBmAYYqB2BpWAb9-1O6ErSq7CBdsE4ndQ5x9d8GTL2FYk1ZqNpzXmUKz-Nbf4wGwX-46ozXzLpg9tIv_BvVt7pm3uGx8mxjk6xcL72MmfdIQPedes76JYyJ8BdIPiHaIxsAp0sqIadlxOmm56LQ4FQSzoE8-jG6ud7uhaB53EZ_6wEYltuvcImPc8EyXyc5jWvXms4Jb74bB_6M0ke-8ybvkQ2mysTL1AB2qrxG4kFx5mphBadSUWMmEkGufFI0HasPs70BzbeNeP_ySMSihGMUpZd1Hk-27s4SUVpvPSgbU1JxUukWEJmIxTwrN7qckCPEseo6AjrLoXFcXn9Nxgwi6Bdl7ixqxCFtWIxjoH1mMM4LnMwH7ZFFw
