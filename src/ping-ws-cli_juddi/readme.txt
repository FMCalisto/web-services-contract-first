This is a Java Web Service client using UDDI to lookup the endpoint address.

The client uses the wsimport tool (included with the JDK since version 6)
to generate classes that can invoke the web service and
perform the Java to XML data conversion.

The client needs access to the WSDL file,
either using HTTP or using the local file system.

The UDDI client is configured by the uddi.xml file,
but some values are defined in the client program.


Instructions using Maven:
------------------------

You must start UDDI server and hello-ws first.

The default WSDL file location is ${basedir}/src/wsdl .
The WSDL URL location can be specified in pom.xml
/project/build/plugins/plugin[artifactId="jaxws-maven-plugin"]/configuration/wsdlUrls

The jaxws-maven-plugin is run at the "generate-sources" Maven phase (which is before the compile phase).

To generate stubs using wsimport:
  mvn generate-sources

To compile:
  mvn compile

To run using exec plugin:
  mvn exec:java

To generate launch scripts for Windows and Linux:
  (appassembler:assemble is attached to install phase)
  mvn install

To run using appassembler plugin:
  On Windows:
    target\appassembler\bin\ping-ws-cli_juddi.bat http://localhost:9090 Ping
  On Linux:
    ./target/appassembler/bin/ping-ws-cli http://localhost:9090 Ping


To configure the project in Eclipse:
-----------------------------------

If Eclipse files (.project, .classpath) exist:
    'File', 'Import...', 'General'-'Existing Projects into Workspace'
    'Select root directory' and 'Browse' to the project base folder.
    Check if everything is OK and 'Finish'.

If Eclipse files do not exist:
    'File', 'Import...', 'Maven'-'Existing Maven Projects'.
    'Browse' to the project base folder.
    Check that the desired POM is selected and 'Finish'.

To run:
    Select the main class and click 'Run' (the green play button).
    Specify arguments using 'Run Configurations'


--
Revision date: 2016-03-14
leic-sod@disciplinas.tecnico.ulisboa.pt