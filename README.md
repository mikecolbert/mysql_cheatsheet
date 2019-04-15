# mysql_cheatsheet
List of common SQL commands for managing MySQL

---

Create / Delete / Switch / Show Database(s): 
```
CREATE DATABASE new_database_name;

USE new_database_name;

SHOW DATABASES;

DROP DATABASE new_database_name;

```



Users and Privileges:
```
CREATE USER 'database_name_mgr'@'%' IDENTIFIED BY 'new_password';

# '%' indicates the user can log in from anywhere. If you want to limit logins to localhost, replace '%' with 'localhost'. 
# I think you could also add an IP address or IP network id or range.*


GRANT ALL PRIVILEGES ON database_name.* TO 'database_name_mgr'@'%';

# *.* - all tables in all databases
# database1.* - all tables in database 1
# database1.table1 - only table1 in database1

# ALL PRIVILEGES can be replace with any combination of the following:
# ALL PRIVILEGES – grants all privileges to the MySQL user
# CREATE – allows the user to create databases and tables
# DROP - allows the user to drop databases and tables
# DELETE - allows the user to delete rows from specific MySQL table
# INSERT - allows the user to insert rows into specific MySQL table
# SELECT – allows the user to read the database
# UPDATE - allows the user to update table rows

# (example) GRANT SELECT, INSERT ON database_name.table1 TO '*new_database_name_usr'@'%';


DROP USER 'user_to_drop'@'host'

# host could be %, localhost, or some IP address/range.


FLUSH PRIVILEGES;
# force MySQL to reload users and permissions after changes have been made

```



Tables:
```
SHOW TABLES;

DESCRIBE table_name;

CREATE TABLE new_tablename IF NOT EXISTS (
id int UNIQUE AUTO_INCREMENT NOT NULL PRIMARY KEY,  
field1 varchar(128) NOT NULL, 
field2 varchar(256), 
field3 int(11) NOT NULL, 
field4 int(11)
)AUTO_INCREMENT=1;

DROP TABLE table_name;




```
