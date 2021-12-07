<h1>Iteration 2: Identifying Structures to Support Primary Functionality</h1>

This section contains the results of the activites that are performed in each of the steps of ADD in the first iteration of the design process. 
 
The pdf file with the full report on iteration 1 can be found here. <--- INSERT LINK TO FOLDER 1 


<h2>Step 1: Review Inputs</h2>

For the revision of inputs, refer to step 1 in iteration 1. 

<h2>Step 2: Establish Iteration Goal by Selecting Drivers</h2>

The goal of this iteration is to identify elements that support the primary functionality of the application. The following use cases were selected as the drivers for this iteration.
<ul>
  <li>UC-1: Manage Listings</li>
  <li>UC-2: Reservations</li>
  <li>UC-6: Login</li>
  <li>UC-8: Search Listings</li>
</ul>

![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%202/Figure%201.%20Context%20model%20of%20the%20web%20application.JPG "Context Model") <br>

<h2>Step 3: Choose One or More Elements of the System to Refine</h2>

The elements that will be refined are located in the server side of the web reference architecture. 
The main focus will be on the UI Process modules, which control the flow of system use cases. 
Since the car rental system is heavily reliant on user interaction, refining this module is critical to supporting the primary function of the system.

<h2>Step 4: Choose One or More Design Concepts that Satisfy the Selected Drivers</h2>

Design Decisions and Location  | Rationale
------------- | -------------
Create a Domain Model for the application  | A domain model is used to find the major entities and their relationships within a domain. 
Identify Domain Objects that map to functional requirements  | Domain objects are used to capture functional elements.
Decompose Domain Objects into general and specialized components | The domain objects capture sets of functionality. Components are considered modules. 
Use Laravel Framework and Eloquent  | Laravel is used to build custom web applications and content management systems using PHP. <br> Laravel provides support for MySQL. It provides transactions to store and retrieve objects from the database. Laravel includes a built-in object to relational mapping (ORM) is called Eloquent <br>  Other PHP frameworks that support MySQL are Codeigniter and Medoo. Laravel was chosen because of its modularity and security. It also upscale to handle more user traffic. 

<h2>Step 5: Instantiate Architectural Elements, Allocate Responsibilities, and Define Interfaces</h2>

Design Decisions and Location  | Rationale
------------- | -------------
Create initial domain model  | Components that participate in primary use cases are modeled in an initial domain model. 
Map the system use cases to domain objects  | System use cases are used to identify domain objects.
Decompose domain objects across the layers  | All functionalities are supported with the modules (ie. components in the pattern).
Connect modules using Laravel.  | This framework is designed for users to follow the MVC pattern and provides built-in support for inversion of control principle (IoC).
Associated frameworks with a module in the data layer | Eloquent applies ORM to capture objects in the database. 

<h2>Step 6: Sketch Views and Record Design Decisions</h2>

![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%202/Figure%202.%20Initial%20domain%20model.JPG "Title is optional")
<br>Above is the initial domain model.

![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%202/Figure%203.%20Domain%20objects%20associated%20with%20use%20cases.JPG "Title is optional")
<br>The domain objects associated with the use cases are shown in the model above. The individual functionality of these objects will be described in this iteration.

![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%202/Figure%204.%20Modules%20that%20support%20the%20primary%20use%20cases.JPG "Title is optional")
<br>The modules that support the primary use cases are shown above.


Elements of Modules that support primary use case  | Responsibilities
------------- | -------------
SignupForm  | User interface to input necessary fields (name, username, password, email etc.) for signup
SigninForm  | User interface to input necessary fields (username, password) for signin
ReservationForm  | User interface to input necessary fields (name, vehicle, start and end date etc.) for making or deleting reservation
ViewListing  | User interface to view all listings
ListingsForm | User interface to input necessary fields (name, username, password etc.) for signup
SignupRequest  | Send user request to sign up to server-side logic
SigninRequest  | Send user request to sign in to server-side logic
ReservationRequest  | Send user request to make/delete reservation to server-side logic
ListingRequest  | Send user request to make listings to server-side logic
ViewListingRequest  | Send user request to view listings to server-side logic
validateSignup  | Check user input validity (check for existing user) and process signup request.
validateSignin  | Check user input validity (check for correct username and password) and process sign in request
validateReservation | Check user input validity (check vehicle availability for specified date and time to make reservation, or check for pre-existing reservation to delete reservation) and process reservation request
reservationConfirmation  | When reservation is processed, send a confirmation email with details of the action to the user.
retrieveListings | Check user sign-in status. If user is signed in, provide vehicle list.
createListings  | Create new vehicle listings. 
userInfo  | Store all users information.
reservationInfo  | Store all reservations.
listingInfo  | Store all listings. 
database  | All tables are stored in external database

The table above captures elements in the diagram which shows modules that support the primary use cases and provides a description of their functionality.<br>


