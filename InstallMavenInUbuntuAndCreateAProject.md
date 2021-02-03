# Install Maven in Ubuntu

```
mainul@mainul-EliteBook:~$ export PATH=/home/mainul/code/apache-maven-3.6.3/bin:${PATH}

mainul@mainul-EliteBook:~$ mvn -version
```

```
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)

Maven home: /home/mainul/code/apache-maven-3.6.3
Java version: 11.0.9.1, vendor: Ubuntu, runtime: /usr/lib/jvm/java-11-openjdk-amd64
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.8.0-40-generic", arch: "amd64", family: "unix"
```

# Create Director for New Maven Application 

```
mainul@mainul-EliteBook:~$ cd code/

mainul@mainul-EliteBook:~/code$ mkdir mavenProjects

mainul@mainul-EliteBook:~/code$ ls

master/        mavenProjects/ 
```

```
mainul@mainul-EliteBook:~/code$ cd mavenProjects/

mainul@mainul-EliteBook:~/code/mavenProjects$ mkdir myapp

mainul@mainul-EliteBook:~/code/mavenProjects$ cd myapp/
```
# Create A Project

```
mainul@mainul-EliteBook:~/code/mavenProjects/myapp$ mvn archetype:generate
```
