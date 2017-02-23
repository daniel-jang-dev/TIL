##Step 1: Generate a new Spring Boot project

>The first step is to generate a new Spring Boot project at [https://start.spring.io](https://start.spring.io). 
>We need at least the Web plugin to let Spring Boot serve the Angular2 application.

>Click on Generate Project to download the zip file with your new Spring Boot project. 
>Extract the zip file somewhere on your computer. 
>Then open a command prompt and go to the newly created project directory.

##Step 2: Split the project into seperate modules

    cd c:\ng2boot
    mkdir backend frontend\src\main
    move src backend
    copy pom.xml backend

> top level pom.xml
  
    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.jdriven.ng2boot</groupId>
    <artifactId>parent</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>

    <name>parent</name>
    <description>The ng2boot parent project</description>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.4.2.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
    </properties>

    <modules>
        <module>frontend</module>
        <module>backend</module>
    </modules>
    </project>  

> pom.xml in backend directory

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
 
    <artifactId>backend</artifactId>
 
    <name>backend</name>
    <description>The ng2boot backend project</description>
 
    <parent>
        <groupId>com.jdriven.ng2boot</groupId>
        <artifactId>parent</artifactId>
        <version>0.0.1-SNAPSHOT</version>
    </parent>
 
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
 
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>
 
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
    </project>
    
>copy, paste and edit pom.xml to frontend directory

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <artifactId>frontend</artifactId>

    <name>frontend</name>
    <description>The ng2boot frontend project</description>

    <parent>
        <groupId>com.jdriven.ng2boot</groupId>
        <artifactId>parent</artifactId>
        <version>0.0.1-SNAPSHOT</version>
    </parent>

    <build>
        <plugins>
        </plugins>
    </build>
    </project>

##Step 3: Add the Angular2 application to the project

    npm config set loglevel error
    npm install -g angular-cli
    cd frontend\src\main
    ng new --skip-git --directory frontend ng2boot
    
##Step 4: Configure Maven to build the Angular2 application

>We will use the frontend-maven-plugin to build the Angular 2 application with Maven. 
First, let’s add the plugin to the fronted pom in the build/plugins section.

    <plugins>
	    <plugin>
	        <groupId>com.github.eirslett</groupId>
	        <artifactId>frontend-maven-plugin</artifactId>
	        <version>1.3</version>

	        <configuration>
	            <nodeVersion>v6.9.1</nodeVersion>o
	            <npmVersion>4.0.3</npmVersion>
	            <workingDirectory>src/main/frontend</workingDirectory>
	        </configuration>

	        <executions>
	            <execution>
	                <id>install node and npm</id>
	                <goals>
	                    <goal>install-node-and-npm</goal>
	                </goals>
	            </execution>

	            <execution>
	                <id>npm install</id>
	                <goals>
	                    <goal>npm</goal>
	                </goals>
	            </execution>

	            <execution>
	                <id>npm run build</id>
	                <goals>
	                    <goal>npm</goal>
	                </goals>

	                <configuration>
	                    <arguments>run build</arguments>
	                </configuration>
	            </execution>
	        </executions>
	    </plugin>
    </plugins>
>Edit package.json and add the build script to the end of the scripts section as shown below. 
>This build script will delegate the actual building to angular-cli.

    "scripts": {
        "start": "ng serve",
        "lint": "tslint \"src/**/*.ts\"",
        "test": "ng test",
        "pree2e": "webdriver-manager update",
        "e2e": "protractor",
        "build": "ng build"
      }

  >Edit angular-cli.json and change the outDir in the apps section.

    "apps": [
      {
        "root": "src",
        "outDir": "../../../target/frontend",
        "assets": [
          "assets",
          "favicon.ico"
        ],
        "index": "index.html",
        "main": "main.ts",
        "test": "test.ts",
        "tsconfig": "tsconfig.json",
        "prefix": "app",
        "mobile": false,
        "styles": [
          "styles.css"
        ],
        "scripts": [],
        "environments": {
          "source": "environments/environment.ts",
          "dev": "environments/environment.ts",
          "prod": "environments/environment.prod.ts"
        }
      }
    ]
    
##Step 5: Let Spring Boot serve the Angular2 application

>Add the packaged Angular2 application to the resources by adding the snippet below to the build section in frontend pom.xml. 
>The given targetPath will put it in /static on the classpath and Spring Boot will serve it from there.

    <resources>
      <resource>
        <directory>target/frontend</directory>
        <targetPath>static</targetPath>
      </resource>
    </resources>
    
>Because the Spring Boot backend is in another module, we will need to add a dependency to the Angular2 application. 
>Edit the backend pom file and add the following to the list of dependencies.

    <dependency>
      <groupId>com.jdriven.ng2boot</groupId>
      <artifactId>frontend</artifactId>
      <version>${project.version}</version>
      <scope>runtime</scope>
    </dependency>
    
##Step 6: Fire it up!

    mvn clean install
    cd backend
    mvn spring-boot:run
    
>Wait for the application to start and then point your browser to [http://localhost:8080](http://localhost:8080)

##Step 7: Using the angular-cli development server with your Spring Boot backend
>One of many nice features of angular-cli is the development server. It will serve the Angular2 application, just like Spring Boot. However, every time we save a source file, it will automatically rebuild the application and refresh the browser.

> There is one problem though. Maven (running our backend) and the development server (running our frontend) are seperate processes listening on seperate ports. This prevents Angular2 from making backend requests because it violates the Same Origin Policy of our web browser. Web browsers only allow backend requests to the same origin that the web application making the requests was downloaded from.

> Thankfully, we can let angular-cli act as a proxy for our Spring Boot backend. The Angular2 application will send backend requests to thedevelopment server, which will forward them to Spring Boot. Now, the Angular2 application can make backend requests to the same origin it came from.


>Edit package.json and change the start script to add the proxy configuration.

    "scripts": {
      "start": "ng serve --proxy-config proxy.conf.json",
      "lint": "tslint \"src/**/*.ts\"",
      "test": "ng test",
      "pree2e": "webdriver-manager update",
      "e2e": "protractor",
      "build": "ng build"
    }
>The start script now references proxy.conf.json. Create that file, with the following content:

    {
      "/api": {
        "target": "http://localhost:8080",
        "secure": false
      }
    }
>This configuration assumes all backend requests will be made to (sub paths of) /api. 

>Now, when you run in the frontend\src\main\frontend directory,

    npm start  

>the development server will run your Angular2 application. 
>It can be reached at [http://localhost:4200](http://localhost:4200). 


>Don’t forget you have to start your backend seperately. 
>You can do this by running  in the backend directory.

    mvn spring-boot:run
    
>It can be reached at [http://localhost:8080](http://localhost:8080). 
