

# Tìm hiểu về Zabbix

# Mục đích ra đời

- để giảm thiểu tối đa các sự cố làm gián đoạn hoạt động của hệ thống mạng.
- tối ưu được hiệu năng hoạt động của hệ thống mạng để đảm bảo được các yêu cầu sử dụng của người dùng.

# Zabbix là gì? 
- Zabbix là một công cụ mã nguồn mở giải quyết cho ta các vấn đề về giám sát.
- Zabbix được sáng lập bởi Alexei Vladishev và hiện nay đang được phát triển và hỗ trợ bởi Zabbix SIA.
- Zabbix được viết và phát hành dưới bản quyền General Public License GPL phiên bản 2


# Một số tính năng của zabbix

- Khả năng giám sát:zabbix có cấu hình tập trung,các thông tin giám sát được tập trung vào một cơ sở dữ liệu.

- Khả năng mở rộng: các thí nhiệm cho thấy nó có khả năng xử lý quản trị  tới 100.000 thiết bị và máy chủ.Số lượng thông tin,dịch vụ giám sát có thể lên dến
  1000.000 .

- Hỗ trợ giám sát thời gian thực:zabbix có thể cảnh báo ngay tới người quản trị viên khi hệ thống được giám sát có sự cố qua mail hoặc sms..Hơn nữa zabbix còn
có hồ sơ về thông tin giám sát.

- khả năng hiển thị kết quả bằng đồ thị,biểu đồ giúp người dùng có thể dễ dàng giám sát.

- khả năng nhập và xuất cơ sơ dữ liệu thông qua XML

- khả năng tự động phát hiện: người dùng có thể tạo ra các luật dựa trên nó zabbix có thể tự động phát hiện ra các địa chỉ IP,các dịch vụ hoặc các thiết bị
SNMP để thực hiện việc giám sát.

- tính linh hoạt:zabbix hỗ trợ ipv4 và ipv6, zabbix agent có khả năng cài đặt trên nhiều nền tảng khác nhau.

- zabbix có khả năng giám sát các thiết bị không hỗ trợ cài đăt zabbix agent: zabbix có khả năng sát các thiết bị hỗ trợ IPMI, SMNPv123.

- khả năng bảo mật: zabbix cung cấp khả năng chứng thực của địa chỉ IP.
 

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

# Cơ chế hoạt động

- zabbix có thể thu thập dữ liệu dựa vào agent hoặc snmp sau đó đẩy về zabbix server để xử lý.

- Zabbix server dựa vào dữ liệu nhận được để tính toán, vẽ biểu đồ và cảnh báo cho người dùng dựa vào các trigger được định nghĩa.

- Sau khi dữ liệu được zabbix server phân tích xong sẽ được đẩy vào lưu trữ trong Database.

- Zabbix Web dùng để hiển thị các dữ liệu thông qua biểu đồ để theo dõi.

## Sự khác biệt giữa zabbix passive check và zabbix active check

- zabbix thực hiện lấy thông tin từ agent dựa trên cấu hình item tương ứng dữ liệu cần thu thập.Có hai loại item chính là active item và passive item.

 `zabbix passive check` là gì
-  một zabbix item được coi như thuộc tính bị động sẽ có đặc điểm đó là công việc chủ động request kiếm thông tin monitor thuộc về zabbix server.
-  Zabbix Server sẽ request thông tin cần tìm kiếm đến các Agent theo các khoảng thời gian (interval time) đã được cấu hình trong item tương ứng, lấy thông 
  tin monitor và báo cáo lại về hệ thống ngay lập tức. Server khởi tạo kết nối, Agent luôn ở chế động lắng nghe kết nối từ Server.
- Tiến trình:
  + Server mở kết nối TCP đến Zabbix Agent
  + Server gửi ưu cầu thu thập thông tin với item tương ứng. Ví dụ : "agent.ping"
  + Agent nhận ưu cầu, phân tích, thu thập dữ liệu và gửi trả về Server. Với item "agent.ping", kết quả trả về ở đây sẽ là "0" hoặc "1".
  + Kết nối TCP đóng lại
- Nội dung gói tin "Server request" : agent.ping\n
- Nội dung gói tin "Agent response" : <HEADER><DATALEN>1

  `zabbix active check` là gì
- một zabbix item được coi như thuộc tính bị động sẽ có đặc điểm đó là công việc chủ động request kiếm thông tin monitor thuộc về zabbix agent.
- Kiểu kiếm tra này hay dùng khi Zabbix Server không thể kết nối trực tiếp đến Zabbix Agent (có thể do chính sách firewall...).
- Hoạt động của zabbix active check:
  + Đầu tiên Zabbix Agent sẽ chủ động gửi request đến Zabbix Server nhằm lấy thông tin về các Item được Server chỉ định sẵn 
  + Sau khi lấy được danh sách item thì Agent sẽ xử lý động lập rồi gửi tuần tự thông tin về cho Server
  + Server sẽ không khởi tạo kết nối nào mà chỉ trả lời request item list và nhận lại thông tin được trả về. 
  + tuy nhiên nhược điểm lớn nhất là nếu Agent treo hoặc chết thì Server sẽ không nhận được bất kỳ kết nối nào.
 
 - Phân tích thêm ở mức kỹ thuật:
 
 - đầu tiên sẽ lấy danh sách các item cần thiết từ zabbix server:
  + Agent mở kết nối TCP đến zabbix server
  + Agent yêu cầu danh sách item cần thu thập
  + Server phản hồi với danh sách item tương ứng ( danh sách này đã được định sẵn trước đó, gồm item key, delay).
  + Kết nối TCP đóng lại. Agent bắt đầu thu thập thông tin tương ứng với danh sách item nhận được.
  
- Agent gửi trả thông tin đã nhận được:
  + Agent mở kết nối TCP đến zabbix server
  + Agent gửi danh sách các thông tin thu thập được
  + Server xử lý thông tin nhận được và phản ánh trạng thái trở về agent.
  + Kết nối TCP được đóng lại.
 
 
# Các mô hình triển khai
 
  Nhìn chung kiến trúc zabbix cho các hệ thống lớn bao gồm 3 thành phần sau: web server,zabbix server,zabbix web fondend.Ngoài ra còn có hai thành phần nữa là
  zabbix agent và zabbix proxy.
 
- Mô hình tập trung:
  + là mô hình mà một node có thể cài tất cả các thành phần zabbix server,zabbix database,zabbix web fondend.
  + đây là mô hình cơ bản phù hợp với doanh nghiệp nhỏ có số lượng cần giám sát ít.
  
- Mô hình phân tán:
  + mô hình này bao gồm  1 zabbix server cho mỗi chi nhánh.
  + Mô hình này phức tạp trong việc cài đặt và duy trì hoạt động, và không được giám sát tập trung, tuy nhiên có thể kết hợp với mô hình proxy-based.
  + Proxy-based monitoring được triển khai với 01 Zabbix server và nhiều Zabbix proxies, mỗi proxy có thể ở tại một chi nhánh, hoặc 01 data center.
    
 
# Một số khái niệm

- Host: Các thiết bị mà cần giám sát,có thể là server,máy trạm,thiết bị mạng,thiết bị firewall,...Tạo host chính là việc đầu tiên trong cấu hình giám sát
  Zabbix. 

- Items : chính là các đối tượng,dữ liệu cần thu thập trong một host.Có nhiều kiểu item khác nhau,nó phụ thuộc vào các đối tượng giám sát khác nhau.

- Triggers : Là một điều kiện khi thỏa mãn điều kiện của Triggers mà người lập trình đặt ra thì sẽ thực hiện một hành động nào đó tiếp theo.
  Ví dụ: Bạn đang giám sát ram và bạn tạo một trigger cho việc giám sát RAM nếu RAM sử dụng trên 90% thì sẽ thông báo cho người quản trị.
  
- Graphs : Là một sơ đồ giám sát trực quan để người quản trị nhìn các thông tin một cách dễ dàng hơn.

- Template: Là một mẫu chung bao gồm định nghĩa các sẵn các item,trigger,graphs...Nó vô cùng thuận tiện khi triển khai giám sát nhiều host có nhiều thành
 phần cần giám sát giống nhau.
 
 
 










# Tham khảo
- 
- 
- https://techblog.vn/tong-quan-ve-zabbix
- https://github.com/quangln94/Linux/tree/master/Monitoring/Zabbix
- https://www.facebook.com/groups/quantrimang365/permalink/808013262983356/
- https://www.slideshare.net/trongthuy3/luan-van-he-thong-giam-sat-mang-dua-tren-phan-mem-nguon-mo-hay
- https://viblo.asia/p/cai-dat-zabbix-tren-server-ubuntu-1604-p1-V3m5WbwylO7?__cf_chl_captcha_tk__=babc6d4aa514be86e8f1df0768a286574218f2ab-1575598404-0-AU_6YpLNZOZogGUB4T8YwCiDQghreF6ClK-Hhf4Gj7fwuOympyWJWQLL0mQIe8GUu8Z192KxEPvBmAYYqB2BpWAb9-1O6ErSq7CBdsE4ndQ5x9d8GTL2FYk1ZqNpzXmUKz-Nbf4wGwX-46ozXzLpg9tIv_BvVt7pm3uGx8mxjk6xcL72MmfdIQPedes76JYyJ8BdIPiHaIxsAp0sqIadlxOmm56LQ4FQSzoE8-jG6ud7uhaB53EZ_6wEYltuvcImPc8EyXyc5jWvXms4Jb74bB_6M0ke-8ybvkQ2mysTL1AB2qrxG4kFx5mphBadSUWMmEkGufFI0HasPs70BzbeNeP_ySMSihGMUpZd1Hk-27s4SUVpvPSgbU1JxUukWEJmIxTwrN7qckCPEseo6AjrLoXFcXn9Nxgwi6Bdl7ixqxCFtWIxjoH1mMM4LnMwH7ZFFw
