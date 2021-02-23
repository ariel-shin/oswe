## Code Review Principles 

### Application features and business rules
* Understand all the features currently provided by the application and capture all business restrictions/rules related to them
* Future proof security decisions / be mindful of potential future functionality

### Context
* Context is the "Holy Grail" of secure code inspection and risk assessment
* What type of data is being manipulated or processed? 
* What would the damage to the company be if this data was compromised?

### Sensitive Data
* Make note of account numbers and passwords that are sensitive to the application.
* Categorize data entities based on the sensitivity to determine the impact of any kind of data loss in the application 

### User roles and access rights
* Understand the type of users allowed to access the application
* Is it externally facing or internal to "trusted" users? 
* Understand the different privilege levels present in the application 
* Enumerate different security violations/privilege escalation attacks that can be applicable to the application

### Application type
* Is the application browser-based? Desktop based standalone application? Web service? Mobile application? Hybrid? 

### Code
* Look out for language best practices from a security and performance perspective

### Design
* Understand company standards and guidelines and apply them to the code review
* Where are the application properties/configuration parameters stored? 
* How is the business class identified for any feature/URL?
What type of classes get executed for any processing any request? (e.g. centralized controller, command classes, view pages, etc.)
* How is the view rendered to the users for any request?

## Code Review Checklist
* Data validation
* Authentication
* Session Management
* Authorization 
* Cryptography
* Error Handling
* Logging
* Security Configuration
* Network Architecture
