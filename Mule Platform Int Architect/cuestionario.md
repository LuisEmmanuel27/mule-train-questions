# Cuestionario de prueba

## [Respuestas](respuestas.md)

---

1. True or False. We should always make sure that the APIs being designed and developed are self-servable even if it needs more man-day effort and resources.

   1. FALSE
   2. TRUE
2. What are 4 important Platform Capabilities offered by Anypoint Platform?

   1. API Versioning, API Runtime Execution and Hosting, API Invocation, API Consumer Engagement
   2. API Design and Development, API Runtime Execution and Hosting, API Versioning, API Deprecation
   3. API Design and Development, API Runtime Execution and Hosting, API Operations and Management, API
      Consumer Engagement
   4. API Design and Development, API Deprecation, API Versioning, API Consumer Engagement
3. What Anypoint Platform Capabilities listed below fall under APIs and API Invocations/Consumers category?
   Select TWO

   1. API Operations and Management
   2. API Runtime Execution and Hosting
   3. API Consumer Engagement
   4. API Design and Development
4. Select the correct Owner-Layer combinations from below options

   1. A.
      1. App Developers owns and focuses on Experience Layer APIs
      2. Central IT owns and focuses on Process Layer APIs
      3. LOB IT owns and focuses on System Layer APIs
   2. B.
      1. Central IT owns and focuses on Experience Layer APIs
      2. LOB IT owns and focuses on Process Layer APIs
      3. App Developers owns and focuses on System Layer APIs
   3. C.
      1. App Developers owns and focuses on Experience Layer APIs
      2. LOB IT owns and focuses on Process Layer APIs
      3. Central IT owns and focuses on System Layer APIs
5. Which layer in the API-led connectivity focuses on unlocking key systems, legacy systems, data sources etc and exposes the functionality?

   1. Experience Layer
   2. Process Layer
   3. System Layer
6. A Mule application exposes an HTTPS endpoint and is deployed to three CloudHub workers that do not use static IP addresses. The Mule application expects a high volume of client requests in short time periods. What is the most cost-effective infrastructure component that should be used to serve the high volume of client requests?

   1. customer-hosted load balancer
   2. The CloudHub shared load balancer
   3. An API proxy
   4. Runtime Manager autoscaling
7. What are the major benefits of MuleSoft proposed IT Operating Model?

   1. A .

      1. Decrease the IT delivery gap
      2. Meet various business demands without increasing the IT capacity
      3. Focus on creation of reusable assets first. Upon finishing creation of all the possible assets then inform the LOBs
         in the organization to start using them
   2. B .

      1. Decrease the IT delivery gap
      2. Meet various business demands by increasing the IT capacity and forming various IT departments
      3. Make consumption of assets at the rate of production
   3. C .

      1. Decrease the IT delivery gap
      2. Meet various business demands without increasing the IT capacity
      3. Make consumption of assets at the rate of production
8. Which of the following best fits the definition of API-led connectivity?

   1. API-led connectivity is not just an architecture or technology but also a way to organize people and processes for efficient IT delivery in the organization
   2. API-led connectivity is a 3-layered architecture covering Experience, Process, and System layers
   3. API-led connectivity is a technology that enabled us to implement Experience, Process, and System layer
      based APIs
9. A system API has a guaranteed SLA of 100 ms per request. The system API is deployed to a primary environment as well as to a disaster recovery (DR) environment, with different DNS names in each environment. An upstream process API invokes the system API and the main goal of this process API is to respond to client requests in the least possible time. In what order should the system APIs be invoked, and what changes should be made in order to speed up the response time for requests from the process API?

   1. In parallel, invoke the system API deployed to the primary environment and the system API deployed to the DR environment, and ONLY use the first response
   2. In parallel, invoke the system API deployed to the primary environment and the system API deployed to the DR environment using a scatter-gather configured with a timeout, and then merge the responses
   3. Invoke the system API deployed to the primary environment, and if it fails, invoke the system API deployed to the DR environment
   4. Invoke ONLY the system API deployed to the primary environment, and add timeout and retry logic to avoid intermittent failures
10. The application network is recomposable: it is built for change because it ‘bends but does not break’

    1. TRUE
    2. FALSE
11. A company has created a successful enterprise data model (EDM). The company is committed to building an application network by adopting modern APIs as a core enabler of the company’s IT operating model. At what API tiers (experience, process, system) should the company require reusing the EDM when designing modern API data models?

    1. At the experience and process tiers
    2. At the experience and system tiers
    3. At the process and system tiers
    4. At the experience, process, and system tiers
12. Due to a limitation in the backend system, a system API can only handle up to 500 requests per second. What is the best type of API policy to apply to the system API to avoid overloading the backend system?

    1. Rate limiting
    2. HTTP caching
    3. Rate limiting - SLA based
    4. Spike control
13. A retail company with thousands of stores has an API to receive data about purchases and insert it into a single database. Each individual store sends a batch of purchase data to the API about every 30 minutes. The API implementation uses a database bulk insert command to submit all the purchase data to a database using a custom JDBC driver provided by a data analytics solution provider. The API implementation is deployed to a single CloudHub worker. The JDBC driver processes the data into a set of several temporary disk files on the CloudHub worker, and then the data is sent to an analytics engine using a proprietary protocol. This process usually takes less than a few minutes. Sometimes a request fails. In this case, the logs show a message from the JDBC driver
    indicating an out-of-file-space message. When the request is resubmitted, it is successful. What is the best way to try to resolve this throughput issue?

    1. se a CloudHub autoscaling policy to add CloudHub workers
    2. Use a CloudHub autoscaling policy to increase the size of the CloudHub worker
    3. Increase the size of the CloudHub worker(s)
    4. Increase the number of CloudHub workers
14. An API implementation returns three X-RateLimit-* HTTP response headers to a requesting API client. What type of information do these response headers indicate to the API client?

    1. The error codes that result from throttling
    2. A correlation ID that should be sent in the next request
    3. The HTTP response size
    4. The remaining capacity allowed by the API implementation
15. An API has been updated in Anypoint exchange by its API producer from version 3.1.1 to 3.2.0 following accepted semantic versioning practices and the changes have been communicated via the APIs public portal. The API endpoint does NOT change in the new version. How should the developer of an API client respond to this change?

    1. The API producer should be requested to run the old version in parallel with the new one
    2. The API producer should be contacted to understand the change to existing functionality
    3. The API client code only needs to be changed if it needs to take advantage of the new features
    4. The API clients need to update the code on their side and need to do full regression
16. A company requires Mule applications deployed to CloudHub to be isolated between non-production and production environments. This is so Mule applications deployed to non-production environments can only access backend systems running in their customer-hosted non-production environment, and so Mule applications deployed to production environments can only access backend systems running in their customer-hosted production environment. How does MuleSoft recommend modifying Mule applications, configuring environments, or changing infrastructure to support this type of per-environment isolation between Mule applications and backend systems?

    1. Modify properties of Mule applications deployed to the production Anypoint Platform environments to prevent access from non-production Mule applications
    2. Configure firewall rules in the infrastructure inside each customer-hosted environment so that only IP addresses from the corresponding Anypoint Platform environments are allowed to communicate with corresponding backend systems
    3. Create non-production and production environments in different Anypoint Platform business groups
    4. Create separate Anypoint VPCs for non-production and production environments, then configure connections to the backend systems in the corresponding customer-hosted environments
17. An organization wants to make sure only known partners can invoke the organization’s APIs. To achieve this security goal, the organization wants to enforce a Client ID Enforcement policy in API Manager so that only registered partner applications can invoke the organization’s APIs. In what type of API implementation does MuleSoft recommends adding an API proxy to enforce the Client ID Enforcement policy, rather than embedding the policy directly in the application’s JVM?

    1. A Mule 3 application using APIkit
    2. A Mule 3 or Mule 4 application modified with custom Java code
    3. A Mule 4 application with an API specification
    4. A Non-Mule application
18. A company uses a hybrid Anypoint Platform deployment model that combines the EU control plane with customer-hosted Mule runtimes. After successfully testing a Mule API implementation in the Staging
    environment, the Mule API implementation is set with environment-specific properties and must be promoted to the Production environment. What is a way that MuleSoft recommends configuring the Mule API implementation and automating its promotion to the Production environment?

    1. Bundle properties files for each environment into the Mule API implementation’s deployable archive, then promote the Mule API implementation to the Production environment using Anypoint CLI or the Anypoint Platform REST APIsB.
    2. Modify the Mule API implementation’s properties in the API Manager Properties tab, then promote the Mule API implementation to the Production environment using API Manager
    3. Modify the Mule API implementation’s properties in Anypoint Exchange, then promote the Mule API implementation to the Production environment using Runtime Manager
    4. Use an API policy to change properties in the Mule API implementation deployed to the Staging environment and another API policy to deploy the Mule API implementation to the Production environment
19. A system API is deployed to a primary environment as well as to a disaster recovery (DR) environment, with different DNS names in each environment. A process API is a client to the system API and is being rate limited by the system API, with different limits in each of the environments. The system API’s DR environment provides only
    20% of the rate limiting offered by the primary environment. What is the best API fault-tolerant invocation strategy to reduce overall errors in the process API, given these conditions and constraints?

    1. Invoke the system API deployed to the primary environment; add timeout and retry logic to the process API to avoid intermittent failures; if it still fails, invoke the system API deployed to the DR environment
    2. Invoke the system API deployed to the primary environment; add retry logic to the process API to handle intermittent failures by invoking the system API deployed to the DR environment
    3. In parallel, invoke the system API deployed to the primary environment and the system API deployed to the DR environment; add timeout and retry logic to the process API to avoid intermittent failures; add logic to the
       process API to combine the results
    4. Invoke the system API deployed to the primary environment; add timeout and retry logic to the process API to avoid intermittent failures; if it still fails, invoke a copy of the process API deployed to the DR environment
20. In which layer of API-led connectivity, does the business logic orchestration reside?

    1. System Layer
    2. Experience Layer
    3. Process Layer
21. Once an API Implementation is ready and the API is registered on API Manager, who should request the access to the API on Anypoint Exchange?

    1. None
    2. Both
    3. API Client
    4. API Consumer
22. Traffic is routed through an API proxy to an API implementation. The API proxy is managed by API Manager and the API implementation is deployed to a CloudHub VPC using Runtime Manager. API policies have been applied to this API. In this deployment scenario, at what point are the API policies enforced on incoming API client requests?

    1. At the API proxy
    2. At the API implementation
    3. At both the API proxy and the API implementation
    4. At a MuleSoft-hosted load balancer
23. An API client calls one method from an existing API implementation. The API implementation is later updated. What change to the API implementation would require the API client’s invocation logic to also be updated?

    1. When the data type of the response is changed for the method called by the API client
    2. When a new method is added to the resource used by the API client
    3. When a new required field is added to the method called by the API client
    4. When a child method is added to the method called by the API client
24. An organization has created an API-led architecture that uses various API layers to integrate mobile clients with a backend system. The backend system consists of a number of specialized components and can be accessed via a REST API. The process and experience APIs share the same bounded-context model that is different from the backend data model. What additional canonical models, bounded-context models, or anti-corruption layers are best added to this architecture to help process data consumed from the backend system?

    1. Create a bounded-context model for every layer and overlap them when the boundary contexts overlap, letting API developers know about the differences between upstream and downstream data models
    2. Create a canonical model that combines the backend and API-led models to simplify and unify data models, and minimize data transformations.
    3. Create a bounded-context model for the system layer to closely match the backend data model, and add an anti-corruption layer to let the different bounded contexts cooperate across the system and process layers
    4. Create an anti-corruption layer for every API to perform transformation for every data model to match each
       other, and let data simply travel between APIs to avoid the complexity and overhead of building canonical models
25. Which of the following sequence is correct?

    1. API Client implementes logic to call an API»_space; API Consumer requests access to API»_space; API Implementation routes the request to»_space; API
    2. API Consumer requests access to API»_space; API Client implementes logic to call an API»_space; API routes the request to»_space; API Implementation
    3. API Consumer implementes logic to call an API»_space; API Client requests access to API»_space; API Implementation routes the request to»_space; API
    4. API Client implementes logic to call an API»_space; API Consumer requests access to API»_space; API routes the request to»_space; API Implementation
26. Which of the below, when used together, makes the IT Operational Model effective?

    1. Create reusable assets, Do marketing on the created assets across the organization, and Arrange time to time LOB reviews to ensure assets are being consumed or not
    2. Create reusable assets, Make them discoverable so that LOB teams can self-serve and browse the APIs, Get active feedback and usage metrics
    3. Create reusable assets, and make them discoverable so that LOB teams can self-serve and browse the APIs
27. A set of tests must be performed prior to deploying API implementations to a staging environment. Due to data security and access restrictions, untested APIs cannot be granted access to the backend systems, so instead mocked data must be used for these tests. The amount of available mocked data and its contents is sufficient to entirely test the API implementations with no active connections to the backend systems. What type of tests should be used to incorporate this mocked data?

    1. Integration tests
    2. Performance tests
    3. Functional tests (Blackbox)
    4. Unit tests (Whitebox)
28. A company wants to move its Mule API implementations into production as quickly as possible. To protect access to all Mule application data and metadata, the company requires that all Mule applications be deployed to the company's customer-hosted infrastructure within the corporate firewall. What combination of runtime plane and control plane options meets these project lifecycle goals?

    1. Manually provisioned customer-hosted runtime plane and customer-hosted control plane
    2. MuleSoft-hosted runtime plane and customer-hosted control plane
    3. Manually provisioned customer-hosted runtime plane and MuleSoft-hosted control plane
    4. iPaaS provisioned customer-hosted runtime plane and MuleSoft-hosted control plane
29. Version 3.0.1 of a REST API implementation represents time values in PST time using ISO 8601 hh:mm:ss format. The API implementation needs to be changed to instead represent time values in CEST time using ISO 8601 hh:mm:ss format. When following the semver.org semantic versioning specification, what version should be assigned to the updated API implementation?

    1. 3.0.2
    2. 4.0.0
    3. 3.1.0
    4. 3.0.1
30. What is the main change to the IT operating model that MuleSoft recommends to organizations to improve innovation and clock speed?

    1. Drive consumption as much as production of assets; this enables developers to discover and reuse assets from other projects and encourages standardization
    2. Expose assets using a Master Data Management (MDM) system; this standardizes projects and enables developers to quickly discover and reuse assets from other projects
    3. Implement SOA for reusable APIs to focus on production over consumption; this standardizes on XML and WSDL formats to speed up decision making
    4. Create a lean and agile organization that makes many small decisions everyday; this speeds up decision making and enables each line of business to take ownership of its projects
31. An Anypoint Platform organization has been configured with an external identity provider (IdP) for identity management and client management. What credentials or token must be provided to Anypoint CLI to execute commands against the Anypoint Platform APIs?

    1. The credentials provided by the IdP for identity management
    2. The credentials provided by the IdP for client management
    3. An OAuth 2.0 token generated using the credentials provided by the IdP for client management
    4. An OAuth 2.0 token generated using the credentials provided by the IdP for identity management
32. Say, there is a legacy CRM system called CRM-Z which is offering below functions: <br/> 1. Customer creation <br/> 2. Amend details of an existing customer <br/> 3. Retrieve details of a customer <br/> 4. Suspend a customer.
    1. Implement a system API named customerManagement which has all the functionalities wrapped in it as various operations/resources.
    2. Implement different system APIs named createCustomer, amendCustomer, retrieveCustomer and suspendCustomer as they are modular and has seperation of concerns.
    3. Implement different system APIs named createCustomerInCRMZ, amendCustomerInCRMZ, retrieveCustomerFromCRMZ and suspendCustomerInCRMZ as they are modular and has seperation of concerns

33. An organization wants MuleSoft-hosted runtime plane features (such as HTTP load balancing, zero downtime, and horizontal and vertical scaling) in its Azure environment. What runtime plane minimizes the organization's effort to achieve these features?

    1. Anypoint Runtime Fabric
    2. Anypoint Platform for Pivotal Cloud Foundry
    3. CloudHub
    4. A hybrid combination of customer-hosted and MuleSoft-hosted Mule runtimes
34. A company has started to create an application network and is now planning to implement a Center for Enablement (C4E) organizational model. What key factor would lead the company to decide upon a federated rather than a centralized C4E?

    1. When there are a large number of existing common assets shared by development teams
    2. When various teams responsible for creating APIs are new to integration and hence need extensive training
    3. When development is already organized into several independent initiatives or groups
    4. When the majority of the applications in the application network are cloud based
35. A retail company is using an Order API to accept new orders. The Order API uses a JMS queue to submit orders to a backend order management service. The normal load for orders is being handled using two (2) CloudHub workers, each configured with 0.2 vCore. The CPU load of each CloudHub worker normally runs well below 70%. <br/> However, several times during the year the Order API gets four times (4x) the average number of orders. This causes the CloudHub worker CPU load to exceed 90% and the order submission time to exceed 30 seconds. The cause, however, is NOT the backend order management service, which still responds fast enough to meet the response SLA for the Order API. What is the MOST resource-efficient way to configure the Mule application's CloudHub deployment to help the company cope with this performance challenge?

    1. Permanently increase the size of each of the two (2) CloudHub workers by at least four times (4x) to one (1) vCore
    2. Use a vertical CloudHub autoscaling policy that triggers on CPU utilization greater than 70%
    3. Permanently increase the number of CloudHub workers by four times (4x) to eight (8) CloudHub workers
    4. Use a horizontal CloudHub autoscaling policy that triggers on CPU utilization greater than 70%
36. A REST API is being designed to implement a Mule application. What standard interface definition language can be used to define REST APIs?

    1. Web Service Definition Language (WSDL)
    2. OpenAPI Specification (OAS)
    3. YAML
    4. AsyncAPI Specification
37. What Anypoint Connectors support transactions?

    1. Database, JMS, VM
    2. Database, JMS, HTTP
    3. Database, JMS, VM, SFTP
    4. Database, VM, File
38. What Mule application can have API policies applied by Anypoint Platform to the endpoint exposed by that Mule application?

    1. A Mule application that accepts requests over HTTP/1.x
    2. A Mule application that accepts JSON requests over TCP but is NOT required to provide a response
    3. A Mule application that accepts JSON requests over WebSocket
    4. A Mule application that accepts gRPC requests over HTTP/2
39. An API implementation is updated. When must the RAML definition of the API also be updated?

    1. When the API implementation changes the structure of the request or response messages
    2. When the API implementation changes from interacting with a legacy backend system deployed on-premises to a modern, cloud-based (SaaS) system
    3. When the API implementation is migrated from an older to a newer version of the Mule runtime
    4. When the API implementation is optimized to improve its average response time
40. What is most likely NOT a characteristic of an integration test for a REST API implementation?
    1. The test needs all source and/or target systems configured and accessible
    2. The test runs immediately after the Mule application has been compiled and packaged
    3. The test is triggered by an external HTTP request
    4. The test prepares a known request payload and validates the response payload

41. An organization uses one specific CloudHub (AWS) region for all CloudHub deployments. How are CloudHub workers assigned to availability zones (AZs) when the organization's Mule applications are\ndeployed to CloudHub in that region?

    1. Workers belonging to a given environment are assigned to the same AZ within that region
    2. AZs are selected as part of the Mule application's deployment configuration
    3. Workers are randomly distributed across available AZs within that region
    4. An AZ is randomly selected for a Mule application, and all the Mule application's CloudHub workers are\nassigned to that one AZ

42. When could the API data model of a System API reasonably mimic the data model exposed by the corresponding backend system, with minimal improvements over the backend system's data model?

    1. When there is an existing Enterprise Data Model widely used across the organization
    2. When the System API can be assigned to a bounded context with a corresponding data model
    3. When a pragmatic approach with only limited isolation from the backend system is deemed appropriate
    4. When the corresponding backend system is expected to be replaced in the near future

43. Mule applications that implement a number of REST APIs are deployed to their own subnet that is inaccessible from outside the organization. External business partners need to access these APIs, which are only allowed to be invoked from a separate subnet dedicated to partners - called Partner-subnet. This subnet is accessible from the public internet, which allows these external partners to reach it. Anypoint Platform and Mule runtimes are already deployed in Partner-subnet. These Mule runtimes can already access the APIs. What is the most resource-efficient solution to comply with these requirements, while having the least impact on other applications that are currently using the APIs?

    1. Implement (or generate) an API proxy Mule application for each of the APIs, then deploy the API proxies to the\nMule runtimes
    2. Redeploy the API implementations to the same servers running the Mule runtimes
    3. Add an additional endpoint to each API for partner-enablement consumption
    4. Duplicate the APIs as Mule applications, then deploy them to the Mule runtimes

44. An API has been updated in Anypoint Exchange by its API producer from version 3.1.1 to 3.2.0 following accepted semantic versioning practices and the changes have been communicated via the API's public portal. <br/> The API endpoint does NOT change in the new version.\nHow should the developer of an API client respond to this change?
    1. The update should be identified as a project risk and full regression testing of the functionality that uses this API should be run.
    2. The API producer should be contacted to understand the change to existing functionality.
    3. The API producer should be requested to run the old version in parallel with the new one.
    4. The API client code ONLY needs to be changed if it needs to take advantage of new features.

45. What is true about API implementations when dealing with legal regulations that require all data processing to be performed within a certain jurisdiction (such as in the USA or the EU)?
    1. They must avoid using the Object Store as it depends on services deployed ONLY to the US East region.
    2. They must use a Jurisdiction-local external messaging system such as Active MQ rather than Anypoint MQ.
    3. They must te deployed to Anypoint Platform runtime planes that are managed by Anypoint Platform control\nplanes, with both planes in the same Jurisdiction.
    4. They must ensure ALL data is encrypted both in transit and at rest.

46. When must an API implementation be deployed to an Anypoint VPC?
    1. When the API Implementation must invoke publicly exposed services that are deployed outside of CloudHub in a customer-managed AWS instance.
    2. When the API implementation must be accessible within a subnet of a restricted customer-hosted network that does not allow public access.
    3. When the API implementation must be deployed to a production AWS VPC using the Mule Maven plugin.
    4. When the API Implementation must write to a persistent Object Store.

47. An organization uses various cloud-based SaaS systems and multiple on-premises systems. The on-premises\nsystems are an important part of the organization's application network and can only be accessed from within the\norganization's intranet.\nWhat is the best way to configure and use Anypoint Platform to support integrations with both the cloud-based\nSaaS systems and on-premises systems?
    1. Use CloudHub-deployed Mule runtimes in an Anypoint VPC managed by Anypoint Platform Private Cloud\nEdition control plane.
    2. Use CloudHub-deployed Mule runtimes in the shared worker cloud managed by the MuleSoft-hosted Anypoint\nPlatform control plane.
    3. Use an on-premises installation of Mule runtimes that are completely isolated with NO external network\naccess, managed by the Anypoint Platform Private Cloud Edition control plane.
    4. Use a combination of Cloud Hub-deployed and manually provisioned on-premises Mule runtimes managed by\nthe MuleSoft-hosted Anypoint Platform control plane.

48. How are an API implementation, API client, and API consumer combined to invoke and process an API?
    1. The API consumer creates an API implementation, which receives API invocations from an API such that they are processed for an API client.
    2. The API client creates an API consumer, which receives API invocations from an API such that they are processed for an API implementation.
    3. The ApI consumer creates an API client, which sends API invocations to an API such that they are processed by\nan API implementation.
    4. The API client creates an API consumer, which sends API invocations to an API such that they are processed by\nan API implementation

49. An API implementation is being designed that must invoke an Order API, which is known to repeatedly experience downtime.\nFor this reason, a fallback API is to be called when the Order API is unavailable.<br/> What approach to designing the invocation of the fallback API provides the best resilience?
    1. Search Anypoint Exchange for a suitable existing fallback API, and then implement invocations to this fallback API in addition to the Order API.
    2. Create a separate entry for the Order API in API Manager, and then invoke this API as a fallback API if the primary Order API is unavailable.
    3. Redirect client requests through an HTTP 307 Temporary Redirect status code to the fallback API whenever the Order API is unavailable.
    4. Set an option in the HTTP Requester component that invokes the Order API to instead invoke a fallback API whenever an HTTP 4xx or 5xx response status code is returned from the Order API.
50. 