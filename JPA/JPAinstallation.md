###Step1: Verify your Java Installation

    \>java –version

###Step 2: Set your Java Environment

    Set JAVA_HOME to C:\ProgramFiles\java\jdk1.7.0_60
    Append the String "C:\Program Files\Java\jdk1.7.0_60\bin" to the end of the system variable PATH.

###Step3: Installing JPA

* You can go through the JPA installation by using any of the JPA Provider from this tutorial, E.g. Eclipselink, Hibernate. Let us follow the JPA installation using Eclipselink. For JPA programming we require to follow the specific folder framework therefore it is better to use IDE.

* Download Eclipse IDE form following link https://www.eclipse.org/downloads/ Choose the EclipseIDE for JavaEE developer that is Eclipse indigo.

* Installing JPA using Eclipselink: Eclipselink is a library therefore we cannot add it directly to Eclipse IDE. For installing JPA using Eclipselink you need to follow the following steps.

  * Create a new JPA project by selecting File->New->JPA Project in the Eclipse IDE as follows:
  * You will get a dialog box named New JPA Project. Enter project name ‘tutorialspoint_JPA_Eclipselink’, check the jre version and click next:
  * Click on download library (if you do not have the library) in the user library section:
  
  * Select the latest version of Eclipselink library in the Download library dialog box and click next as follows:
  
  * Accept the terms of license and click finish for download library as follows:
  
  * You will find the process of downloading a file as follows:
  
  * After downloading, select the downloaded library in the user library section and click finish as follows:
  
  * Finally you get the project file in the Package Explorer in Eclipse IDE. Extract all files, you will get the folder and file hierarchy as follows:

* Adding MySQL connector to Project

  * Go to Project properties -> Java Build Path by right click on it. You will get a dialog box as follows: Click on Add External Jars.

  * Go to the jar location in your system memory, select and click on open as follows:

  * Click ok on properties dialog. You will get the MySQL-connector Jar into your project. Now you are able to do database operations using MySQL.
