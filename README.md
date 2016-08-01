# programming-patterns

[July 2016] MVC---
Stands for Model/View/Controller. Is a software architectural pattern for implementing UI. Divides given software application into three parts. Very popular for web applications. Model directly manages the data, logic, rules of application and also stores retrieved data for view. View is an informational output of Model such as a chart or diagram to user. Controller acccepts user input and manipulates the Model state (ex. edit document) or View (ex. scroll down in document).

[July 2016] Business Delegate---
Is a programming pattern used in J2EE for multi-tiered, distributed systems. Deals with the issue of presentation-tier clients (devices, web clients, etc.) directly interfacing with business service APIs. Direct interfacing causes client/presentation-tier components to become vulnerable to changes in business services. Direct interfacing hurts network performance when presentation-tier makes too many calls to business service API over network. Hiding implementation details of the business service such as lookup and access minimizes coupling (ex. Client requests BusinessDelegate to provide access to underlying business service -> BusinessDelegate uses a LookupService to locate and create the required BusinessService component -> The BusinessService then can be used to invoke business methods on behalf of the Client when requested via BusinessDelegate). The BusinessDelegate can obtain String versions of the handles for the BusinessService and cache it to later use to reconnect to the BusinessService being used when the handle was created, avoiding new lookups. Note that Handle objects are implemented by the container provider and may not be portable across containers from different vendors. Clients may need to implement caching mechanisms for business service information in order to achieve this. Overall, the benefits are to reduce coupling and improve manageability and shield clients from knowledge of implementation, exception handling, failure recovery, and thread synchronization specifics. The downsides are that it introduces an additional layer between the Client and the business service, and may hide remoteness of the service to the Client developers if the Business Delegate appears to be a local one. The developer may tend to make numerous method invocations to perform a single task which increases network traffic.

[August 2016] Value Object---
A small object that represents a simple identity (ex. date range, money, name) whose equality is not based on identity (equal based on values of their fields, not being the same object reference). Value objects should be immutable, since two value objects created equal should remain equal. Value objects may also be immutable to prevent them from being put in an invalid state. In summary, objects are mutable while value objects are immutable, and objects are referenced (obj1=obj2 assings obj1 a reference to obj2) while value objects are copied by value (valobj1=valobj2 makes a copy of the attributes of valobj2 to valobj1). Native support in C#, emulated in Java by making object immutable (since if state of object does not change, passing reference is semantically equivalent to copying value object).

[August 2016] Session Facade---
In multi-tiered J2EE platforms, tight coupling between clients and business objects ("enterprise bean" server-side remote bjects that encapsulate business logic/data such as (1) transient/non-persistent "session bean" objects that represent clients and allow them to invoke its methods to communicate/make requests on the J2EE enterprise server & (2) persistent "entity bean" objects that represent a view of a business entity object in a persistent storage mechanism such as a relational database, object database, legacy application, file, etc. for multiple clients, and and other arbitrary objects that provide services/data) may lead to direct dependence. Direct dependence means the client must implement complex interactions for business object lookups and creations,  must manage the relationships between the participating business objects, and understand the responsibility of transaction demarcation. As client requirements increase, the complexity of interaction increases and the client must grow larger and more complex. This increases rigidity and makes it difficult to implement changes. In addition, too many direct method invocations between client and server objects leads to network problems since enterprise beans are remote objects, and lack of uniform client access strategy can expose business objects to misuse. A sesion facade abstracts the underlying business object interactions and provides a service layer that exposes only the required interfaces, hiding the complexity from the client. It also manages the interactions between the business data and business service objects in the workflow and encapsulates the business logic associated wtih the requirements. As such, the session bean (representing the session facade) manages the relationships between business objects and their life cycle via appropriate creation, locating/look-up, modification, and deletion as required by the workflow. In more complex applications, the session facade may delegate all or parts of this management to a separate object (such as a service locator object). Note that mapping every use case to a session facade results in too many of them and defeats the purpose of having fewer coarse-grained session beans - instead look to consolidate them in a logical partitioning (ex. in banking application, grouping interactions related to managing an account like create new account, change account info, view account info, etc. into a single facade - in this case the facade becomes a highly coarse-grained controllwer with high level methods to facilitate each interaction such as createNewAccount, changeAccount, getAccount). Overall, the advantages are to introduce a business-tier controller layer, expose a uniform interface, reduce coupling, increase manageability, improve performance, reduce fine-grained methods, provide coarse-grained access, centralize security management, centralize transaction control, and expose fewer remote interfaces to clients.

Composite Entity---

Service Locator---

Data Access Object---
