This is a Java Web Service defined by the WSDL file that generates Java code
(contract-first approach, also called top-down approach).

The service runs in a stand-alone HTTP server.
It throws a Fault in roughly 1/3 of the times.


Instructions using Maven:
------------------------

To run the jUDDI server (required):
  Check if the environment variable CATALINA_HOME is properly set
  On Windows:
    startup
  On Linux:
    startup.sh
  Wait for the following log message: "INFO: Server startup in ... ms"
  Visit http://localhost:9090/juddiv3/ to confirm that the name server is running.

To compile:
  mvn compile

To run using exec plugin:
  mvn exec:java

To generate launch scripts for Windows and Linux:
  (appassembler:assemble is attached to install phase)
  mvn install

To run using appassembler plugin:
  On Windows:
    target\appassembler\bin\ping-ws_juddi http://localhost:9090 Ping http://localhost:8080/ping-ws/endpoint
  On Linux:
    ./target/appassembler/bin/ping-ws_juddi http://localhost:9090 Ping http://localhost:8080/ping-ws/endpoint


When starting, the web service registers itself on the UDDI server.
When stopping, the registration is deleted.

When running, the web service awaits connections from clients.
You can check if the service is running using your web browser 
to see the generated WSDL file:

    http://localhost:8080/ping-ws/endpoint?WSDL

This address is defined when the publish() method is called.

To call the service you will need a web service client,
including code generated from the WSDL.


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