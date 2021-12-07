<h1>Iteration 2: Identifying Structures to Support Primary Functionality</h1>

This section presents the results of the activities that are performed for iteration 2 of the ADD process. 
 


<h2>Step 1: Review Inputs</h2>

For the revision of inputs, refer to step 1 in iteration 1. 

<h2>Step 2: Establish Iteration Goal by Selecting Drivers</h2>

This iteration will focus on QA-4: User authentication ensures 99.999% of unauthorized login attempts are detected and prevented.


<h2>Step 3: Choose One or More Elements of the System to Refine</h2>

Since this iteration will focus on the availability quality attribute, the elements that will be refined will be located in the application server.

<h2>Step 4: Choose One or More Design Concepts That Satisfy the Selected Drivers</h2>

Design Decisions and Location  | Rationale and Assumptions
------------- | -------------
Introduce an intrusion detection system  | By comparing network traffic or service request patterns within a system to a set of malicious patterns stored in a database, the system is able detect unusual login behaviour. 

<h2>Step 5: Instantiate Architectural Elements, Allocate Responsibilities, and Define Interfaces</h2>

Design Decisions and Location  | Rationale
------------- | -------------
Intrusion detection system is implemented in the application server  | Even distribution throughout the system, applied to all login attempts. 
Heartbeat used to identify suspicious behaviour | Messages are sent at regular intervals. Any irregularities in the messages can easily be detected.
Alerts used to describe attacks  | Alerts can provide information such as time or occurrence, time of detection, target, classification, etc. This can be used to detect patterns of attack.

<h2>Step 6: Sketch Views and Record Design Decisions</h2>

<h3>Deployment Diagram</h3>

![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%203/Figure%201.%20The%20refined%20deployment%20diagram%20that%20implements%20intrusion%20detection%20to%20the%20system.JPG "Context Model") <br>
Above is the refined deployment diagram that implements intrusion detection to the system.<br>
UML sequence diagram to support UC-6 (login) and QA-4 (security). Illustrates communication between physical nodes. Method names are temporary and may be changed in further iterations. <br>

Element  | Responsibility 
------------- | -------------
Heartbeat System | Creates messages at a regular interval. Any irregularities that are detected in these messages can identify suspicious behaviour.
Alerts Information Logger | Receives and stores alerts from the Intrusion Detection System. Stores the provided information about any detected intrusion, such as the time or occurrence of the detection, target, classification, etc. Tracks the gathered information to detect and identify patterns of attack

<br>

Below is a UML sequence diagram to illustrate UC-6 communication. <br>

![picture alt](https://github.com/anishp22/SOFE3650FinalProject/blob/main/Iteration%203/Figure%202.%20The%20UML%20sequence%20diagram%20to%20illustrate%20UC-6%20communicaton.JPG "Context Model") <br>

Element | Method | Description
------------- | ------------- | -------------
User Interface | loginInfo(username, password) | Accept user input of username and password
User Interface  | allowLogin() | If intrusion is not detected, the user is logged in. If intrusion is detected, user login is halted. 
Application Server  | requestLogin() | The username and password is sent as a login request. 
Application Server | detectIntrusion() | States if an intrusion is detected.
Heartbeat | heartbeat(Request)  | When a login attempt is made, heartbeat is requested. 
Intrusion Detection System | sendHeartbeat()  | Heartbeat at regular intervals is received to analyze. 
Intrusion Detection System | validateLogin() | Checks for valid user input.
Intrusion Detection System | alertInfo(loginAttempt, intrusionTime, detectionTime,  target, status) | Retrieve all information for the intrusion attempt.
AlertInformationLogger | logAlert(loginAttempt, intrusionTime, detectionTime, target, status) | Logs all information on the intrusion attempt.

<h2>Step 7: Perform Analysis of Current Design and Review Iteration Goal and Achievement of Design Purpose</h2>


Not Addressed  | Partially Addressed | Completely Addressed | Design Decision Made During the Iteration
------------- | ------------- | ------------- | ------------- 
|  |  QA-1 |              |  No relevant decisions made.
|  |  QA-2 |              |  No relevant decisions made.
|  |  QA-3 |              |  No relevant decisions made.
|  |  QA-4 |              |  By implementing an intrusion detection system, we ensure that unauthorized login attempts are detected. Furthermore, we can use the alerts feature to track the time and date, target, and classification of the login attempt. Specific technologies were not chosen, thus this driver is marked partially addressed.
|  |  QA-5 |              |  No relevant decisions made.
|  |  CON-1 |              |  No relevant decisions made.
|  |  CON-3 |              |  No relevant decisions made.
| CRN-3 |  |              |  The new concern that arises from this is how changes will be implemented to the system when a pattern of intrusion is detected. 

