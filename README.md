# SOFE3650FinalProject
Final project for Software Design and Architecture

<h1>Online Community-Based Car Reservation Platform</h1>

<h2>Authors</h2>

    Anish Patel 100751489  
    David Fung 100767734  
    Nathan Yohannes 100749914  
    Saaruca Kugarajh 100751441  

<h2>Project Proposal</h2>

    The Project Proposal PDF contains a brief overview of the project. 
    It also contains a list of functional and non-functional requirements for the software.

<h2>Project Progress Report</h2>
The Project Progress Report PDF contains following artifacts:


* [Use Case Model](System%20Requirements/Use%20Case%20Model.pdf)
    * Shows the most relevant use cases for the project and is further described in a table
* [Quality Attributes](System%20Requirements/Quality%20Attributes.pdf)
    * The five most relevant quality attributes are also presented in a table with a description and associated use case
* [System Constraints](System%20Requirements/System%20Constraints.pdf)
    * The derived system constraints on the system were collected and shown in a table


<h1>Iteration 1: Establishing an Overall System Structure</h1>

This section contains the results of the activites that are performed in each of the steps of ADD in the first iteration of the design process. 
 
The pdf file with the full report on iteration 1 can be found here. <--- INSERT LINK TO FOLDER 1

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

PUT IMAGE HERE

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


