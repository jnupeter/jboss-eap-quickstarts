log4j: How to Define a Module Dependency and Use log4j in an Application
=======================================================================
Author: Bartosz Baranowski  
Level: Beginner  
Technologies: JBoss Modules  
Summary: Demonstrates how to use modules to control class loading for 3rd party logging frameworks  
Target Product: EAP  
Product Versions: EAP 6.1, EAP 6.2  
Source: <https://github.com/jboss-developer/jboss-eap-quickstarts/>  

What is it?
-----------

This simple JSF 2.0 application shows how to use container defined modules to limit the size of the application package. It also shows how to use 
common versions of certain classes at runtime.

Applications must often depend on third-party libraries. By default, Java EE packages allow you to include dependencies in a deployable unit which can lead to uncontrolled growth of the deployable unit. This can be avoided by the use of container defined modules. A module is nothing more than a container managed binary dependency which is shared by all deployed applications. For more informatin on class loading and modules please refer to "About Modules and the New Modular Class Loading System used in JBoss EAP 6" in the [Development Guide for JBoss Enterprise Application Platform](https://access.redhat.com/site/documentation/en-US/JBoss_Enterprise_Application_Platform).

This example is very simple. It declares dependency on the Apache Log4j module which allows it to use a custom logging framework. This is achieved with a simple addition to the xml file: `src/main/webapp/WEB-INF/jboss-deployment-structure.xml`. For more information about this file please refer to the the [Development Guide for JBoss Enterprise Application Platform](https://access.redhat.com/site/documentation/en-US/JBoss_Enterprise_Application_Platform).


System requirements
-------------------

The application this project produces is designed to be run on Red Hat JBoss Enterprise Application Platform 6.1 or later. 

All you need to build this project is Java 6.0 (Java SDK 1.6) or later, Maven 3.0 or later.

 
Configure Maven
---------------

If you have not yet done so, you must [Configure Maven](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_MAVEN.md#configure-maven-to-build-and-deploy-the-quickstarts) before testing the quickstarts.


Start the JBoss Server
-------------------------

1. Open a command prompt and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the server:

        For Linux:   JBOSS_HOME/bin/standalone.sh
        For Windows: JBOSS_HOME\bin\standalone.bat

 
Build and Deploy the Quickstart
-------------------------

_NOTE: The following build command assumes you have configured your Maven user settings. If you have not, you must include Maven setting arguments on the command line. See [Build and Deploy the Quickstarts](../README.md#build-and-deploy-the-quickstarts) for complete instructions and additional options._

1. Make sure you have started the JBoss Server as described above.
2. Open a command prompt and navigate to the root directory of this quickstart.
3. Type this command to build and deploy the archive:

        mvn clean install jboss-as:deploy

4. This will deploy `target/jboss-log4j.war` to the running instance of the server.


Access the application 
---------------------

The application will be running at the following URL: <http://localhost:8080/jboss-log4j/>.


Undeploy the Archive
--------------------

1. Make sure you have started the JBoss Server as described above.
2. Open a command prompt and navigate to the root directory of this quickstart.
3. When you are finished testing, type this command to undeploy the archive:

        mvn jboss-as:undeploy

Run the Quickstart in JBoss Developer Studio or Eclipse
-------------------------------------
You can also start the server and deploy the quickstarts from Eclipse using JBoss tools. For more information, see [Use JBoss Developer Studio or Eclipse to Run the Quickstarts](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/USE_JDBS.md#use-jboss-developer-studio-or-eclipse-to-run-the-quickstarts) 


Debug the Application
------------------------------------

If you want to debug the source code or look at the Javadocs of any library in the project, run either of the following commands to pull them into your local repository. The IDE should then detect them.

        mvn dependency:sources
        mvn dependency:resolve -Dclassifier=javadoc
