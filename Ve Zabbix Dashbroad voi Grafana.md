# Hướng dẫn vẽ Zabbix Dashboard với Grafana

- Bước 1: Để tạo một Dashboard bạn click vào biểu tượng dấu cộng
  
  + ![]( /image/da1.png)
  
- Bước 2: Tiếp theo bạn add một panel mới:

  +![]( /image/da2.png)

  Ở đây có 3 sự lựa chọn:
  
  + Add query: chọn thông tin để hiển thị
  + Choose Visualization: Chọn loại hình thức hiển thị: Gauge,Graph,Singlestat,...
  + Convert to row: Tạo row để tập hợp các panel.

- Bước 3: Add query( ở đây bạn có thể  chọn Choose Visualization trước cũng được ) 

  + Querry Mode : Thường là chọn Metrics vì có nhiều thông tin tại đây , tuy nhiên cũng có thể phải chọn các giá trị khác (ví dụ hiển thị tên hostname thì sẽ 
  chọn Text chứ không chọn Metrics)  
  
  + Group: Là Group các thiết bị các bạn đã khai báo bên Zabbix ví dụ Zabbix Servers , User_WindowsOS … Grafana sẽ tự động hiển thị tất cả các group đã được tạo 
  bên Zabbix tại đây cho các bạn chọn
  
  + Host: Chọn Host muốn hiển thị qua Grafana , danh sách Host cũng sẽ được tự động hiển thị dựa vào Group đã được chọn trước đó.
  
  + Application: Nơi hiện các thông số để hiển thị , 1 tập hợp các group ví dụ : Filesystems sẽ có các thông số liên quan tới ổ đĩa , tổng dung lượng đĩa , còn 
  trống bao nhiêu…v…v  , tương tự với CPU,RAM….
  
  + Item: Chi tiết như RAM trống , tổng RAM ,…. 
  
  + Ví dụ mình muốn hiển thị phần trăm CPU đã sử dụng:
  
  + ![]( /image/da4.PNG)
  
 - Bước 5: Chọn Visualization:

  + Có nhiều loại hình thức hiển thị,ở đây thì mình chọn Gauge:

  + ![]( /image/da6.PNG)

  + Tiếp theo bạn chọn đơn vị:

  + ![]( /image/da7.PNG)

- Bước 6: Để phân biệt các panel thì bạn có thể đổi tên panel:

  + ![]( /image/da8.PNG)

- Kết quả!!

  + ![]( /image/da9.PNG)  
  
