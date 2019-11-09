# Joker
Mock Server for Micro-Service Architecture.

### Motivation 
To provide a robust, light, modular Mock-server implementation for Micro-service architechtures. One stop solution for your Mock needs.

### Design
![Joker Design](https://raw.githubusercontent.com/Rahul-Bhargav/Joker/master/Joker-design.jpg)

#### PBJ (Port Binder Jarvis)
This service lets the developer mock various services present at various ports.  
It can bind to multiple ports at the same time and forward requests to Wayne. This achieved using a mapping of port to the mocked services. 

#### Wayne
The core part of the Mock server which handles the responses that are supposed to be given to a specific request. 
This service responds to the The request Path, Method, Parameters are hashed to form a entry in hash-table with the required response. 
#### Gateway  (The Middle man).
This service acts as a single entry point to configure Joker. It sends the request-response setup to both the PBJ and Wayne. This ensures that all the other services are as modular as they can be. Having a separate gateway also ensures independence from the UI to rest of the architechture. 

#### UI
User Interface for the developer to create and set mock responses. Will connect only to the gate way. More details on this to follow.

#### DBS (Database service)
A lightweight in-memory service to store all the request response pairs, port mappings and has tables. Having an independent DB service will allow developments to be independent of the database implementation and its design.
