# upload-file-manager
## Prerequisites

* Java 8
* Maven 3
* spring boot 2.7.6
* mysql 8
* spring data
* spring test

## Description
Create a Spring Boot application that will allow to upload XML files via REST API, validate them against an XSD schema, parse the
data from them and store it in the database.
The workflow looks like this:
1. A user sends an XML file via REST API.
2. The file is parsed and validated, its content goes to the table in the DB.
3. The content of the DB can be presented by the GUI, in the form of a table with possibility of sorting, paging & filtering
   (creating a REST API for "front-end team" to prepare such GUI is enough ).
   XML files have the following format (you can create several files for testing based on this example):
```xml
<?xml version="1.0" encoding="UTF-8"?>
<epaperRequest>
    <deviceInfo name="Browser" id="test@comp">
    <screenInfo width="1280" height="752" dpi="160" />
        <osInfo name="Browser" version="1.0" />
    <appInfo>
        <newspaperName>abb</newspaperName>
        <version>1.0</version>
    </appInfo>
</deviceInfo>
<getPages editionDefId="11" publicationDate="2017-06-06" />
</epaperRequest>
```

Please extract the content from newspaperName and width, height, dpi from screenInfo tag to the database. The upload time
and filename should also be stored in the database.

Technology stack:
Java >= 8, Maven, Spring Boot, PostgreSQL or Mysql / MariaDB or MongoDB

## Run the System
We can easily run the whole with only a single command:
```bash
docker-compose up
```

Docker will pull the MySQL and Spring Boot images (if our machine does not have it before).

The services can be run on the background with command:
```bash
docker-compose up -d
```

## Stop the System
Stopping all the running containers is also simple with a single command:
```bash
docker-compose down
```

If you need to stop and remove all containers, networks, and all images used by any service in <em>docker-compose.yml</em> file, use the command:
```bash
docker-compose down --rmi all
```
