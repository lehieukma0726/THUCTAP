# Mô hình Graph monitor (Grafana + InfluxDB + Telegraf)
## I.Cài đặt grafana,InfluxDB,Telegraf
- Ở đây ta cài đặt grafana,influxDB,telegraf trên CentOS 7. Dưới đây sẽ là mô hình mà chúng ta cài đặt để thực hiện 
![](images/mohinh.png)

- **Grafana** là công cụ được tin tưởng và yêu thích bởi cộng đồng, là nền tảng phân tích tất cả các loại metric.
- **Grafana** cho phép truy vấn, visualize (hiển thị), cảnh báo và giúp bạn hiểu metric dù chúng được lưu ở bất kì đâu. Tạo, khám phá và chia sẻ dashboard với nhóm của bạn và thúc đẩy văn hóa luồng dữ liệu.
- **Telegraf** là một agent để collecting và reporting metrics và data được viết bởi Go.Nó có thể tích hợp để collect nhiều loại nguồn dữ liệu khác nhau của metrics, events, và logs trực tiếp từ containers và system mà nó chạy trên đó
- **InfluxDB** là một **Time Series Database** (là database được tối ưu hóa để xử lý dữ liệu chuỗi thời gian, các dãy số được lập chỉ mục theo thời gian. )
- **InfluxDB** được sử dụng để lưu các dữ liệu cho các trường hợp liên quan đến một lượng lớn time-stamped data, bao gồm DevOps monitoring, log data, application metrics, IoT sensor data, và real-time analytics. Nó có thể tự động xóa các dữ liệu cũ, không cần thiết và cung cấp một ngôn ngữ giống SQL để tương tác với dữ liệu.

## Cài đặt InfluxDB, Telegraf và Grafana
### InfluxDB :
![](images/influxdb.PNG)
### Telegraf :
![](images/telegraf.PNG)
### Grafana :
![](images/grafana.PNG)

## II . Cấu hình

### Cấu hình influxDB :
- Thiết lập username và password trong influxDB. 
![](images/influxdb.1.PNG)
Ở đây tạo user là lehieu và pass là 123.

### Cấu hình telegraf :
- Ta vào thư mục telegraf.conf và chỉnh sửa trên tệp tin :
![](images/telegraf.1.PNG)
- Ta cần chú ý tới url =  [“htttp://localhost:8086”] là địa chỉ truy cập của influxdb
![](images/telegraf.2.PNG)
database là telegraf.
![](images/telegraf.3.PNG)
Tài khoản và mật khẩu ta tạo ở trên influxDB để khi khởi động influxDB thì telegraf có thể tiến hành đấy metric lên influxDB thông qua cổng 8086
Sau đó restart lại influxDB và telegraf
- Update repository trên máy và cài đặt Grafana:
```
apt-get update -y
apt-get install grafana -y
```
- File cấu hình cài đặt của grafana thường ở file `:/etc/grafana/grafana.ini `
Chạy lệnh sau để khởi động grafana cùng hệ thống:
`systemctl enable grafana-server.service`
## III . Thực hiện trên grafana :
- Truy cập Grafana trên trình duyệt http://ip_add:3000. Login user admin and pass admin .
Khi đấy sẽ vào Home Dashboard tiến hành add data source
![](images/grafana.1.PNG)
- Ở đây ta tiến hành điền thông tin ở các trường, ở phần user và pass thì điền user+pass đã tạo trên influxDB. Sau đấy save lại ta sẽ nhận được thông báo dữ liệu InfluxDB đã được thêm vào máy chủ Grafana.
- Hiện có các kiểu panel: Graph, Singlestat, Dashlist, Table và Text, …
![](images/grafana.5.PNG)
- Query Editor cho thấy khả năng của DS và cho phép truy vấn các metric mà nó chứa. Sử dụng Query Editor để dựng lên một hoặc nhiều truy vấn (cho một hoặc nhiều chuỗi dữ liệu) trong cơ sở dữ liệu thời gian thực.
![](images/grafana.6.png)
### Import Dashboard
- Sau đây sẽ thực hiện import dashboard,nguồn dữ liệu được lấy từ telegraf,thu thập metric từ telegraf rồi đẩy nguồn dữ liệu lên influxDB
- Sau khi thêm Influxdb làm nguồn dữ liệu vào máy chủ grafana, tiếp theo sẽ nhập bảng điều khiển grafana dựa trên thiết lập plugin đầu vào Telegraf .
![](images/grafana.2.png)
Ở đây ta sẽ chọn import để nhập dữ liệu từ database của influxDB lên telegraf .Từ bảng kế tiếp ta sẽ nhập thêm các trường dữ liệu vào và tùy chọn nhập dữ liệu là influxDB.
- Dưới dây ở trên telegraf nhận được metric từ database và hiển thị lên telegraf
![](images/grafana.3.PNG)

![](images/grafana.4.PNG)
- Ở đây ta có thể nhìn thấy dạng dữ liệu thông qua dạng đồ thị, cho hiển thị các thông tin về CPU , RAM , DISK 1 cách chân thực nhất qua các thông số ở phần Quick Overview và trực quan bằng phần đồ thị ở dưới .
- Qua quá trình trên ta có thể thấy được từ telegrab sẽ thu thập các dữ liệu từ hệ thống các thông tin như CPU,RAM,DISK,NET … .Sau đó sẽ đẩy toàn bộ dữ liệu lên infuluxDB để tối ưu hóa dữ liệu thông qua các trường thời gian.Sau cùng của quá trình thì ta sẽ hiển thị các thông tin thu thập được từ quá trình trên lên Grafana để hiển thị thông qua dạng trực quan cũng như đồ thị thông số cụ thể .



