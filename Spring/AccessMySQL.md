#Accessing data with MySQL

[git repository](https://github.com/spring-guides/gs-accessing-data-mysql.git)

###Build with Maven

>pom.xml
    
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

###Create a new database

    mysql> create database db_example; -- Create the new database
    mysql> create user 'springuser'@'localhost' identified by 'ThePassword'; -- Creates the user
    mysql> grant all on db_example.* to 'springuser'@'localhost'; -- Gives all the privileges to the new user on the newly created database
    
###Create the application.properties file

>src/main/resources/application.properties


    spring.jpa.hibernate.ddl-auto=create
    spring.datasource.url=jdbc:mysql://localhost:3306/db_example
    spring.datasource.username=springuser
    spring.datasource.password=ThePassword

###Create the @Entity model

>src/main/java/hello/User.java

###Create the repository

>src/main/java/hello/UserRepository.java

###Create a new controller for your Spring application

>src/main/java/hello/MainController.java

##Create a new controller for your Spring application

>src/main/java/hello/MainController.java

###If you are using Maven, you can run the application using 
    mvnw spring-boot:run

###Test the application

    $ curl 'localhost:8080/demo/add?name=First&email=someemail@someemailprovider.com'
    $ curl 'localhost:8080/demo/all'
