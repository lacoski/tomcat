# Cấu hình MySQL

## Change MySQL default character-set to UTF8 on Ubuntu Server

Một Character set là tập symbols và encodings, giá trị mặc định của MySQL là: latin1_swedish_ci

### Bước 1
Connect MySQL qua MySQL command line/Workbench:
```mysql
show variables like '%collation%';
```
Ta cần set giá cho *collation_database* và *collation_server* sang **utf8_general_ci**

### Bước 2: Edit MySQL config file
```
vim /etc/my.cnf
```
paste đoạn mã dưới đây sau dòng *[mysqld]*:
```
# UTF8 character-set
init_connect = 'SET collation_connection = utf8_unicode_ci'
init_connect = 'SET NAMES utf8'
character-set-server = utf8
collation-server = utf8_unicode_ci
skip-character-set-client-handshake
```

### Bước 3: Restart MySQL server
```
sudo service mysql restart
```
Thực hiện lại bước 1 để xem kết quả.
