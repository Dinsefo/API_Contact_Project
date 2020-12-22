# API_Contact_Project
Production Support and Developer on Mulesoft V3, V4, Datapower, APIC and others IBM products.

#Project Statment
- To develop full CRUD operations with incremental updates.
- To design API support the API and data model.
- Accessable to customer facing and high visibility.

#Input date model
- Json format - data model
- src/main/resources/api/Example-Model/ContactNoIDExample.raml

#Project activity
- Collect the prerequesit requirement
- Design API Speccification
- Develope API  -- Interface
- Develop Mule Application  -- Implementation
- Deploye to the Repository
 
#Tables
## Identification Table
-CREATE TABLE IF NOT EXISTS Identification(
    ->   cont_id    INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    ->   FirstName  VARCHAR(255) NOT NULL,
    ->   LastName   VARCHAR(255) NOT NULL,
    ->   DOB        DATE,
    ->   Gender     CHAR(1),
    ->   Title      VARCHAR(255));
## Address Table
-CREATE TABLE IF NOT EXISTS Address(
    ->   addrs_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    ->   cont_id INTEGER NOT NULL REFERENCES Identification(cont_id),
    ->   Type       VARCHAR(255) NOT NULL,
    ->   Number     VARCHAR(255) NOT NULL,
    ->   Street     VARCHAR(255) NOT NULL,
    ->   Unit       VARCHAR(255) NOT NULL,
    ->   City       VARCHAR(255) NOT NULL,
    ->   State      VARCHAR(2) NOT NULL,
    ->   Zipcode    VARCHAR(10)  NOT NULL);
## Communication Table
-CREATE TABLE IF NOT EXISTS Communication(
    ->   comm_id    INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    ->   cont_id    INTEGER NOT NULL REFERENCES Identification(cont_id),
    ->   Type       VARCHAR(255) NOT NULL,
    ->   Value      VARCHAR(255) NOT NULL,
    ->   Preferred  BIT(1) NULL DEFAULT 0 );

#API Service/Methods
## Parameter value
       - "ID" for Identification -- cont_id
       - "ID" for Address        -- comm_id
       - "ID" for Communication  -- addrs_id
# GET - http://localhost:8089/contactid/"ID"
# POST - http://localhost:8089/contactid
# PUT  - http://localhost:8089/contactid/"ID"
# DELETE - http://localhost:8089/contactid/"ID"
