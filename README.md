# xml-parsing-rest-api

----------------------------------------------------------------------------------------------------------------------
Technology stack Used : Java 8 , Springboot 2.7.14 , MySql8, Maven , Docker
------------------------------------------------------------------------------------------------------------------------
To Run This XML Parsing API You can either extract the project from  ZIP or You can use Below github link to clone 
project and use below command to run and test

1. **git clone https://github.com/kanishkapanchal1199/xml-parsing-rest-api.git**

2. **cd xml-parsing-rest-api**

3. Import the project as existing maven project in any IDE like(Eclipse or IntelliJ).
4. **IMPORTANT STEP :** Run this maven build command -> **mvn clean install** 
5. In the step Assuming that your machine is having 
   docker and docker compose is  installed on the machine if not follow below link to install docker
   https://docs.docker.com/desktop/install/windows-install/.
6. To Run Rest Application on docker run below command
    <ul>
     <li><b>docker-compose up</b></li> or <li><b>docker-compose up -d</b></li>
   </ul>

7. This command will start and run the application on port 8080.

8. You can refer postman.json collection in project root folder to test purpose.

Note: If on your machine 8080 and 3306 port is already used then change the port to any other port in below files 
Dockerfile,
,docker-compose file
,application.yml file

------------------------------------------------------------------------------------------------------------------------
To Test the REST API you can use POSTMAN tool

1. POST API - To Upload the XML follow below steps
   <ol>
    <li>Select <b>POST</b> http method from postman</li>
    <li>Write this url <b>localhost:8080/xml/upload</b> </li>
    <li>Click on body tab and select form-data to upload xml file</li>
    <li>Select form-data insert key as <b>"file"</b> and change key's setting to <b>file</b> from text.</li>
    <li>After that in value you can browse through your xml file.</li>
    <li>or you can use this curl <b>curl --location 'localhost:8080/xml/upload' --form 'file=@"/D:/newspaper.xml"'</b></li>
    <li> Assuming that you're having  xml file provided in question , this is to validate against xsd and all tags are required .</li>
    <li>If you don't have it then , from project structure you can find the file from <b>resources/static/newspaper.xml.</b> </li>
    <li>Now you can hit the send button to upload the xml file.</li>
   </ol>

<br/>

2. To Get the data from rest API - through post http method
   <ol>
   <li>Select <b>POST</b> http method from postman</li>
   <li>Write this url <b>localhost:8080/xml/xml-content </b></li>
   <li>Click on body tab and from there select <b>raw</b> radio button then use <b>json</b> format </li>
   <li>You can pass"  { } " in raw json request body to get all data without filtering and sorting</li>
   <li>You can pass json in raw
    {"width": 800,
    "height": 600} multiple attributes to filter out the data.</li>
   <li>You can pass json as {
    "page":0,
    "size":15} to get data on 0 th page and total records on that page is 15 . values can be changed over here for 1st page.</li>
   <li>You can pass json as {"sortBy":"newspaperName , width" } to sort by multiple attributes .</li>
   <li>To get specific record by all attribute filter you can pass json as this in raw json format {
    "id": 7,
    "newspaperName": "Times of India",
    "width": 800,
    "height": 600,
    "dpi": 300,
    "uploadTime": "2023-07-28T14:09:19.851",
    "filename": "TimeOfIndia.xml"}</li>
   </ol>
   
<br/>

------------------------------------------------------------------------------------------------------------------------
To run the project without docker locally below steps you can follow : 

1. Import the project into Any IDE. 
2. Assuming to have MySQL database on local machine.
3. You have to create a xml_parsing database with this query **create database xml_parsing;**
4. To run the project locally need to change the application.yml configuration to this
   **url: jdbc:mysql://localhost:3306/xml_parsing?useSSL=false**
5. Now you can build the project with **mvn clean install** command .
6. Run the main XmlParsingRestApiApplication.



