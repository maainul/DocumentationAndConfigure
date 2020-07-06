
# How to install MYsql in Ubantu

> sudo apt-get update

> sudo apt-get install mysql-server

> systemctl status mysql

> sudo mysql -u root

> mysql>

> SELECT user,authentication_string,plugin,host FROM mysql.user;

```
+------------------+------------------------------------------------------------------------+-----------------------+-----------+
| user             | authentication_string                                                  | plugin                | host      |
+------------------+------------------------------------------------------------------------+-----------------------+-----------+
| debian-sys-maint | $A$005$on^'Xj_%ama
| mysql.infoschema | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| mysql.session    | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| mysql.sys        | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| root             |                                                                        | auth_socket           | localhost |
+------------------+------------------------------------------------------------------------+-----------------------+-----------+
```

If you find that root is empty then update root table password.


> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yourpassword';

> FLUSH PRIVILEGES;

> SELECT user,authentication_string,plugin,host FROM mysql.user;
```
+------------------+------------------------------------------------------------------------+-----------------------+-----------+
| user             | authentication_string                                                  | plugin                | host      |
+------------------+------------------------------------------------------------------------+-----------------------+-----------+
| debian-sys-maint | $A$005$on^'Xj_%ama
| mysql.infoschema | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| mysql.session    | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| mysql.sys        | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| root             | *81F5E21E35407D884A6CD4A731AEBFB6AF209E1B                              | mysql_native_password | localhost |
+------------------+------------------------------------------------------------------------+-----------------------+-----------+
```

> exit

## Create a New user(if needed)

> sudo mysql

> mysql -u root -p

> CREATE USER 'sammy'@'localhost' IDENTIFIED BY 'password';

> GRANT ALL PRIVILEGES ON *.* TO 'sammy'@'localhost' WITH GRANT OPTION;

> exit

## Test Your Mysql

> systemctl status mysql.service

> sudo mysqladmin -p -u root version

> CREATE DATABASE demodb;

> SHOW DATABASES;


# Remove MYSQL

> sudo apt-get remove --purge mysql-server mysql-client mysql-common -y

> sudo apt-get autoremove -y

> sudo apt-get autoclean

> rm -rf /etc/mysql


# MYSQL AND DJANGO FOR PROJECT

## PART 1: Create Django Project

> sudo apt-get update

> sudo apt-get upgrade

> sudo apt-get install python3-dev (only one time in life )

> sudo apt-get install python3-dev libmysqlclient-dev(only one time in life)

>>mkdir folder_name

> virtualenv -p python3 .

> source bin/activate

> pip install django

> pip install mysqlclient

> mkdir src

> cd src

> django-admin startproject test_proj .

> python manage.py makemigrations

> python manage.py migrate

> python manage.py runserver

## PART 2: MYSQL

> sudo mysql -u root

> CREATE DATABASE demodb;

> FLUSH PRIVILEGES;

> SELECT User, Host, authentication_string FROM mysql.user;

> SHOW DATABASES;

## PART 3:Create USER for Django for Permission

> create user 'django'@'localhost' identified by 'anypassword';

> grant usage on *.* to 'django'@'localhost';

> grant all privileges on demode.* to 'django'@'localhost';

#  PART 4: Edit Settings.py from project

> ALLOWED_HOSTS = ['127.0.0.1']
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'demodb', 
        'USER': 'django',
        'PASSWORD': 'django-user-password',
        'HOST': 'localhost',
        'PORT': '8000',
    }
}
```
