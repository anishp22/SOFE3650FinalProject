<h1>Iteration 1: Establishing an Overall System Structure</h1>

This section contains the results of the activites that are performed in each of the steps of ADD in the first iteration of the design process. 
 
The pdf file with the full report on iteration 1 can be found here. <--- INSERT LINK TO FOLDER 1

<h3>System Constraints</h3>

A set of constraints on the overall system and deployment were collected and presented in the table below. 

ID  | Constraint
------------- | -------------
CON-1  | The database should be accessible using a web browser
CON-2  | A minimum of 1000 users should be supported.
CON-3  | Network connection can have low bandwidth but should be reliable
CON-4  | The database should be created using MySQL

<h3>Architectural Concerns</h3>

ID  | Concern
------------- | -------------
CRN-1  | Establishing an initial system structure
CRN-2  | Leverage the team’s knowledge on cloud database services that can support relational databases (ie. MySQL)

<h2>Step 1: Review Inputs</h2>

The following inputs were reviewed on their significance for iteration 1 to select a general architecture of the system.

Category  | Details
------------- | -------------
Design Purpose  | Design the optimal peer-to-peer sharing model for a car rental website. 
Primary Functional Requirements  | UC-1: Manage Listings <br> UC-2: Reservations <br> UC-6: Login <br> UC-8: Search Listings

<h3>Quality Attribute Scenarios</h3>

Scenario ID  | Importance to the Customer  | Difficulty of Implementation According to the Architect
------------- | -------------  | -------------
QA-1  | Med  | High
QA-2  | High   | Med
QA-3  | Med   | High
QA-4  | High   | High
QA-5  | Med   | High
QA-6  | Low  | Med

From this list, QA-1,2,3 4 and 5 are selected as drivers.

Constraints
All constraints mentioned in the progress report are included as drivers.

Architectural Concerns
All concerns mentioned in Architectural Concerns are included as drivers.



<h2>Step 2: Establish Iteration Goal by Selecting Drivers</h2>


This iteration is driven by a general architectural concern, but the following drivers that may influence the general structure of the system should also be acknowledged:<br>
<ul>
    <li> QA-1: Performance </li>
    <li> QA-2: Usability </li>
    <li> QA-3: Availability </li>
    <li> QA-4: Security </li>
    <li> QA-5: Modifiability </li>
    <li> CON-1: System should be accessible using a web browser on different platforms (OSX, Windows, Linux) </li>
    <li> CON-2: A minimum of 1000 users should be supported </li>
    <li> CON-4: Database should be created using MySQL </li>
    <li> CRN-1: Establishing an initial system structure </li>
</ul>

<h2>Step 3: Choose One or More Elements of the System to Refine</h2>

![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%201/Figure%201.%20Context%20diagram%20for%20car%20reservation%20system.JPG "Context Diagram")

The element to be refined is the Car Reservation System Server and the Database as shown in the context diagram. 
The refinement of these elements will be done through decomposition.

<h2>Step 4: Choose One or More Design Concepts That Satisfy the Selected Drivers</h2>

Design Decisions and Location  | Rationale
------------- | -------------
Logically structure the system using the web application reference architecture.  | The web application architecture allows the car reservation system to be deployed without installing anything on the client machine, and uses a minimum of client-side resources. This architecture will also be more portable and can be used on many devices and operating systems.
Discarded alternatives: Rich Client Application  | This reference architecture requires it to be installed on the user’s PC and does not run on a web browser. This means that the architecture would be less portable and available on many devices, and is not necessary since a rich user interface is not necessary.
Discarded alternatives: Rich Internet Application  | This reference architecture is limited to accessing local resources due to security concerns. This decision was discarded because our system needs to access a public database for hosts and customers to post listings and make car reservations.
Discarded alternatives: Service Application  | This reference architecture does not provide a user interface and is non-interactive. This decision was discarded because our system needs a user interface for customers and hosts to use to navigate through and interact with the website.
Discarded alternatives: Mobile Applications  | Mobile applications architecture refers to applications for handheld devices. This alternative was discarded because this application was not made specifically for handheld devices. It should be accessible through other devices as well.
The database system should use a relational database service that operates in the cloud with no local storage  | Since the web applications must be built with scalability in mind, an online relational database service can offer storage scalability, availability, and high throughput.
Physically structure the application using the three-tier deployment  | A three-tier deployment is a very common web application layout that implements a database, which is necessary for this application. 
Build the user interface of the client application using Bootstrap, a CSS framework supporting Javascript via plugins | This framework is commonly used to build web applications. It optimizes the application performance and development speed.
Deploy the application using the Apache technology  | This application is accessed using a web browser. 

<h2>Step 5: Instantiate Architectural Elements, Allocate Responsibilities, and Define Interfaces</h2>

Design Decisions and Location  | Rationale
------------- | -------------
Remove the optional application facade component for the web application reference architecture  | Users do not need direct access to business logic components, so this feature can be removed to increase simplicity

<h2>Step 6: Sketch Views and Record Design Decisions</h2>

Element  | Responsibility
------------- | -------------
Browser (Client Side) | A web browser running on client machine
Services Server Side  | This layer contains modules that expose services that are consumed by the client
Presentation  | This layer contains modules that control user interaction and use case control flow
Business  | This layer contains modules that control business operations that is processed on the server side
Data  | This layer contains modules that are responsible for data communication and with the database
Cross-Cutting  | These modules have functionality that spans across all layers and includes security, operations management, and communications
UI Modules  | These modules facilitate the user interface and receive user inputs
UI Process Modules  | These modules help to control the flow of the system use cases and navigation between screens
Business Workflow  | These modules are responsible for managing business processes, which may involve the execution of multiple use cases
Business Logic  | This layer contains modules that perform business logic operations that are processed on the server side, and applying business rules on the data
Business Entities  | These entities make up the domain model
Data Access Modules  | This module is responsible for the persistence mechanisms and provide common operations used to retrieve and store information
Helpers and Utilities  | This module contains internal particularities that help with processing of data
Service Agents  | This module helps facilitate some interaction between the business layer and the data layer
Security | These components include cross-cutting functionality that handles security aspects such as authorization and authentication
Operation Management  | Includes cross-cutting functionality such as exception management, logging, and instrumentation, and validation
Communication  | These modules handle communication mechanisms across layers and physical tiers


<h3>Element of the Deployment Diagram</h3>

Element  | Responsibility
------------- | -------------
Client Server  | Hosts the user interface, which is accessible on a web browser running on the client machine.
Application Server  | Hosts the server side logic of the application. Provides web pages for users. Acts as the liaison between the client server and the database.
Database  | Stores the relational database for client information.

<h3>Relationship in the Deployment Diagram</h3>

Relationships  | Description
------------- | -------------
Client Server and Application Server  | Accepts and validates user queries. Format and display retrieved information. 
Application Server and Database  | REST API used to facilitate information transactions (store and retrieve information in the database).

![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%201/Figure%202.%20Module%20view%20of%20web%20reference%20architecture.JPG "Web Reference Architecture") <br>
The diagram above shows a sketch of a module view of the web reference architecture selected for this application that has been adapted accordingly to the design decisions


![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%201/Figure%203.%20Initial%203-tier%20deployment%20pattern%20diagram.JPG "3Tier Deployment Pattern") <br>
The figure above shows the initial 3-tier deployment pattern selected to be used for the system.


<h2>Step 7: Perform Analysis of Current Design and Review Iteration Goal and Achievement of Design Purpose</h2>

Not Addressed  | Partially Addressed | Completely Addressed | Design Decision Made During the Iteration
------------- | ------------- | ------------- | ------------- 
|  | UC-1  |               |  Reference architecture will support the functionality of managing reservations 
| | UC-2  |               |  Reference architecture will support the functionality of making and deleting reservations
|  | UC-6  |               |  Reference architecture will support the functionality of allowing clients to login to the system to access available services
| | UC-8  |               |  Reference architecture will support the functionality of browsing and searching for specific listings
|  | QA-1  |               |  Introduced operation management modules that can collect data on the performance of queries
|QA-2  |   |               |  No relevant decisions made in the overall usability of the application since this iteration focused only on the general architecture and deployment of the application
|  | QA-3  |               |  Identified elements from the deployment pattern that is critical to maintain application uptime
|  | QA-4  |               |  Introduced security modules within cross-cutting functionality that can handle authentication and authorization of accounts
|  | QA-5  |               |  Introduced modules within business layer of the server side that should offer users ability to change and modify parts of their listings
|  | CON-1 |               |  Since the application will be deployed using a web reference architecture, the client can be accessed through a web browser which is available in Windows, OSX, and Linux. Specific technologies used have not been specified. 
CON-2  |   |               |  No relevant decisions have been made on how to achieve the minimum database capacity. 
|  | CON-3 |               |  Apache supports limited bandwidth connections through modifying the configuration file. Specific decisions regarding these modifications are to be made. 
CON-4  |   |               |  No relevant decisions have been made on how the database will be implemented.
 |   |  |      CRN-1        | The web reference architecture and the 3-tier deployment pattern were selected for this application
 |   |CRN-2 |  |       Knowledge of cloud services are used to implement the database. No relevant decisions on specific cloud services have been made.        



