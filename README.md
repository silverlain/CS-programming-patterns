# programming-patterns

MVC---
Stands for Model/View/Controller.
Is a software architectural pattern for implementing UI.
Divides given software application into three parts.
Very popular for web applications.
Model directly manages the data, logic, rules of application and also stores retrieved data for view.
View is an informational output of Model such as a chart or diagram to user.
Controller acccepts user input and manipulates the Model state (ex. edit document) or View (ex. scroll down in document).

Business Delegate---
Is a programming pattern often used in J2EE for multi-tiered, distributed systems.
Deals with the issue of presentation-tier clients (devices, web clients, etc.) directly interfacing with business service APIs.
Direct interfacing causes client/presentation-tier components to become vulnerable to changes in business services.
Direct interfacing hurts network performance when presentation-tier makes too many calls to business service API over network.
Hiding implementation details of the business service such as lookup and access minimizes coupling (ex. Client requests BusinessDelegate to provide access to underlying business service -> BusinessDelegate uses a LookupService to locate and create the required BusinessService component -> The BusinessService then can be used to invoke business methods on behalf of the Client when requested via BusinessDelegate).
The BusinessDelegate can obtain String versions of the handles for the BusinessService and cache it to later use to reconnect to the BusinessService being used when the handle was created, avoiding new lookups. Note that Handle objects are implemented by the container provider and may not be portable across containers from different vendors.
Clients may need to implement caching mechanisms for business service information in order to achieve this.
Overall, the benefits are to reduce coupling and improve manageability and shield clients from knowledge of implementation, exception handling, failure recovery, and thread synchronization specifics. The downsides are that it introduces an additional layer between the Client and the business service, and may hide remoteness of the service to the Client developers if the Business Delegate appears to be a local one. The developer may tend to make numerous method invocations to perform a single task which increases network traffic.


Value Object---

Session Facade---

Composite Entity---

Service Locator---

Data Access Object---
