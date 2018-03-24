# Deploy project Tomcat
---
## Triển khai project lên tomcat
### Bước 1: Thiết lập database
__Truy cập db__
```
mysql -u root
```
Tạo DB mới
```
mysql> create database <Project-Database>;
Query OK, 1 row affected (0.00 sec)
```
> Thoát trạng thái cmd mysql (ctrl + D)

__Chạy script sinh DB__
```
mysql -u root -p <Project-Database> < <Project-Database>.sql
```
__Truy cập lại DB__
```
mysql -u root
```
Kiểm tra db vừa sinh ra
```
mysql> use <Project-Database>
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
```
Kiểm tra table
```
mysql> show tables;
+---------------------------+
| Tables_in_<Project-Database> |
+---------------------------+
| hibernate_gen_id          |
| topic                     |
| user                      |
+---------------------------+
3 rows in set (0.00 sec)
```

### Bước 2: Thiết lập project
__Chuyển project đã đóng gói vào thư mục webapps__
```
cp <Project>.war /opt/apache-tomcat-9.0.6/webapps/
```
Khởi động lại dịch vụ
```
./bin/shutdown.sh
./bin/startup.sh
```
__Cấu hình kết nối db (nếu sai)__
```
/opt/apache-tomcat-9.0.6/webapps/<Project>/WEB-INF/classes/application.yml
```
> Đổi lại DB và passwd cho chính xác db mong muốn

Khởi động lại

```
./bin/shutdown.sh
./bin/startup.sh
```

__Truy cập site__
```
http://ip/<Project>/
```

> LƯU Ý: Check log để biết trạng thái hoạt động web
