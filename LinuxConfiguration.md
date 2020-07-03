
# How to install MYsql in Ubantu

>>sudo apt-get update

>>sudo apt-get install mysql-server

>>systemctl status mysql

>>sudo mysql -u root

>>mysql>

>>UPDATE mysql.user SET authentication_string = PASSWORD('rootpassword') WHERE User = 'root';

>>FLUSH PRIVILEGES;

>>SELECT User, Host, authentication_string FROM mysql.user;

>>CREATE DATABASE demodb;

>>SHOW DATABASES;

# Way of creating USER

>>create user 'django'@'localhost' identified by 'anypassword';

>>grant usage on *.* to 'django'@'localhost';

>>grant all privileges on darabasename.* to 'django'@'localhost';


# Remove MYSQL

>>sudo apt-get remove --purge mysql-server mysql-client mysql-common -y

>>sudo apt-get autoremove -y

>>sudo apt-get autoclean

>>rm -rf /etc/mysql


# MYSQL AND DJANGO FOR PROJECT

## PART 1: Create Django Project

>>sudo apt-get update

>>sudo apt-get upgrade

>>sudo apt-get install python3-dev (only one time in life )

>>sudo apt-get install python3-dev libmysqlclient-dev(only one time in life)

>>mkdir folder_name

>>virtualenv -p python3 .

>>source bin/activate

>>pip install django

>>pip install mysqlclient

>>mkdir src

>>cd src

>>django-admin startproject test_proj .

>>python manage.py makemigrations

>>python manage.py migrate

>>python manage.py runserver

## PART 2: MYSQL

>>sudo mysql -u root

>>CREATE DATABASE demodb;

>>FLUSH PRIVILEGES;

>>SELECT User, Host, authentication_string FROM mysql.user;

>>SHOW DATABASES;

## PART 3:Create USER for Django for Permission

>>create user 'django'@'localhost' identified by 'anypassword';

>>grant usage on *.* to 'django'@'localhost';

>>grant all privileges on demode.* to 'django'@'localhost';

## PART 4: Edit Settings.py from project

>>ALLOWED_HOSTS = ['127.0.0.1']
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
