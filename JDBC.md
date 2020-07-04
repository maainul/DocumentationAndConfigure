# MYSQL cmd

> \sql

> \connect root@localhost

> \use (database name)

> show tables;


# JDBC 
![maxresdefault](https://user-images.githubusercontent.com/37740006/86489664-d977dd00-bd86-11ea-9b0d-f950229b74fc.jpg)

1. Introduction and Installing MySQL 
2. Connecting Java Program to MySQL Database
3. Reading Data from MySQL Database
4. Inserting Data into database


## 1. Introduction and Installing MySQL 

#### Create Maven project and add dependencies into pom.xml

https://mvnrepository.com/artifact/mysql/mysql-connector-java

### create class and method




Download MySql from : https://dev.mysql.com/downloads/installer/

If any problem see : https://www.youtube.com/watch?v=BOUMR85B-V0&t=2s

## 2. Connecting Java Program to MySQL Database 

If any problem occurs see this : https://www.youtube.com/watch?v=9rTJa4l8YQ0


To connect to MySQL database from a Java program, you need to do the following steps:

	1. Load the MySQL Connector into your program.

	2. Create a new Connection object from the DriverManager class. 

#### 1. Loading MySQL Connector into your program

To load MySQL Connector into your program you follow three steps below:

First, in NetBeans IDE, from project name, right mouse click and choose properties menu item. 

The project properties dialog will appear.

![mysql-jdbc-project-properties](https://user-images.githubusercontent.com/37740006/86494950-177dfc80-bd99-11ea-8b6d-fb392de00d8e.jpg)

![2 mysql-jdbc-choose-library](https://user-images.githubusercontent.com/37740006/86494971-295f9f80-bd99-11ea-8017-eb299fbfac89.jpg)

![3 mysql-jdbc-add-jar](https://user-images.githubusercontent.com/37740006/86494986-33819e00-bd99-11ea-9ab6-568ac3e9e197.jpg)

![4 jar-file-added](https://user-images.githubusercontent.com/37740006/86494997-42685080-bd99-11ea-9be7-4f91e3503b58.jpg)

#### Create Class DBConnection and method createConnection

```.java
package mainul;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class DBConnection {

	public static void main(String[] args) {
		DBConnection obj = new DBConnection();
		obj.createConnection();
	}

	public void createConnection() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
			Connection con = DriverManager
					.getConnection("jdbc:mysql://localhost:3306/mydb?autoReconnect=true&useSSL=false", "root", "root");
			Statement stmt = con.createStatement();
			ResultSet rs = stmt.executeQuery("select * from emp");
			while (rs.next())
				System.out.println(rs.getInt(1) + "  " + rs.getString(2) + "  " + rs.getString(3));
			con.close();
		} catch (Exception e) {
			System.out.println(e);
		}
	}
}
```
### Way 2
```.java

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;


public class DBConnection {

	public static void main(String[] args) {
		DBConnection obj = new DBConnection();
		obj.createConnection();
	}
	public void createConnection() {
		// creates three different Connection objects
		Connection conn1 = null;
		try {
			// connect way #1
			String url1 = "jdbc:mysql://localhost:3306/mydb?autoReconnect=true&useSSL=false";
			String user = "root";
			String password = "root";

			conn1 = DriverManager.getConnection(url1, user, password);
			if (conn1 != null) {
				System.out.println("Connected to the database");
			}

		} catch (SQLException ex) {
			System.out.println("An error occurred. Maybe user/password is invalid");
			ex.printStackTrace();
		}
	}
}
```
## 3. Reading Data from MySQL Database

create table in MYsql

And add this code into the Class

```.java

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class MYSqlConnection {

	public static void main(String[] args) {
		MYSqlConnection obj = new MYSqlConnection();
		obj.createConnection();
	}

	public void createConnection() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
			Connection con = DriverManager
					.getConnection("jdbc:mysql://localhost:3306/mydb?autoReconnect=true&useSSL=false", "root", "root");
			
			Statement stmt = con.createStatement();
			ResultSet rs = stmt.executeQuery("select * from users");
			while (rs.next())
				System.out.println(rs.getString("name"));
			
			con.close();
		} catch (Exception e) {
			System.out.println(e);
		}
	}
}

```
## 4. Inserting Data into database