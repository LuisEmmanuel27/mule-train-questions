# Respuestas y explicaciones

1. `i.`

The `pom.xml` file must be modified because it contains all the configuration required for building and deploying the Mule application using Maven, including dependencies and deployment parameters (such as CloudHub settings).

Without updating this file, Maven does not have the necessary information to properly package and deploy the application.

- pom.xml = build + dependencies + deployment config
- It´s the central file for all the project configuration.

2. `iv.`

To implement a publish/subscribe model in Anypoint MQ, messages must be published to a message exchange, not directly to a queue.

An exchange can route a single message to multiple queues, and each queue can be consumed independently by different systems.

By binding multiple queues to the same exchange, each queue receives a copy of the message, ensuring all subscribing systems get the event.

3. `iii.`

Mutual TLS (mTLS) requires **both sides (client and server) to authenticate each other.**

The keystore contains the server’s certificate and private key, used to prove its identity.

The truststore contains the certificates of trusted clients, used to validate incoming client certificates.

Without both configurations, mutual authentication cannot occur.

4. `i.`

Each Mule application has its own isolated Object Store, so another application cannot access it using the Object Store Connector.

To interact with another application's Object Store v2 (including deleting values), you must use the Object Store v2 REST API, which allows external access via HTTP methods like **DELETE**.

5. `iii.`

Selecting “Insecure” in the HTTP Listener disables the TLS configuration entirely.

This means:
- No TLS context is applied
- No HTTPS (encryption) is used
- The listener falls back to plain HTTP only
- So the listener will only accept HTTP requests, not HTTPS.

6. `i.`

A webhook is an HTTP callback mechanism that allows a server to notify a client immediately when an event occurs.

Instead of the client polling for changes, the server pushes the update in real time via an HTTP request (usually POST).

This makes webhooks ideal for event-driven, asynchronous notifications.

7. `ii.`

Even if the TLS configuration is set to None, when making an HTTPS request, Mule still relies on the default JRE truststore to validate the server’s certificate.

If the certificate of the target API is signed by a CA that exists in the JRE truststore, the HTTPS connection will succeed. Otherwise, it will fail during the TLS handshake.

8. `iii.`

To unit test modules created with the XML SDK, Mule requires the MUnit Extensions Maven plugin, which provides specific support for testing custom modules built with XML SDK.

This plugin enables invoking and validating XML SDK operations within MUnit test cases, something that the standard MUnit Maven plugin alone does not support.

9. `iii.`

10. `iv.`

When a property is defined inside the `<secureProperties>` section in the Mule Maven Plugin for CloudHub 2.0, it is treated as a secure property.

In CloudHub 2.0, secure properties are **masked in Runtime Manager**, meaning their values are hidden (e.g., shown as `****`) in the UI and logs to prevent exposure.

11. `iii.`

In Maven, phases are executed in a specific, non-negotiable order. When you run a command like mvn deploy, Maven automatically executes every preceding phase in this exact hierarchy:

Core Sequence Breakdown
- Validate: Ensures the project structure is correct.
- Initialize: Sets up build properties.
- Compile: Transforms source code into bytecode.
- Test: Runs unit tests (crucial before packaging).
- Package: Converts the compiled code into a distributable format (e.g., a .jar or .mule file).
- Verify: Runs checks on the package to ensure quality/integrity.
- Install: Moves the package to your Local Repository (.m2 folder).
- Deploy: Uploads the final artifact to a Remote Repository (like Anypoint Exchange or Nexus).

The logic is simple: you cannot Install or Deploy an artifact until it has been Verified, and you cannot Verify it until it has been Packaged.

12. `iv.`

In Mule 4, when using asynchronous messaging protocols like Anypoint MQ, the `correlationId` is not automatically propagated across different applications. To maintain distributed tracing and observability, the Tracing Module provides the **With CorrelationID** scope. This component allows a developer to explicitly override or set the `correlationId` for all operations executed within that scope (such as the `Publish` operation). This ensures that the specific Order ID is attached to the outgoing message's metadata, allowing Anypoint Monitoring and logs to track the entire transaction lifecycle across multiple Mule applications.

13. `iii.`

14. `iii.`

When invoking multiple REST APIs in parallel, standard ACID transactions are not applicable. The Scatter-Gather router is used to trigger these requests concurrently. To handle failures and maintain data consistency, the Saga Pattern is implemented by defining compensating actions for each route. If one or more routes fail within the Scatter-Gather, the orchestrator identifies which operations succeeded and executes their corresponding "undo" or "rollback" HTTP requests in sequence to ensure the system returns to a consistent state.

15. `i.`

When using XML SDK for creating custom message processors, all operations are public by default and can be used by any Mule application that imports them. There is no way to make an operation private or protected in XML SDK.

16. `iv.`

To perform structural validation of a JSON payload against a predefined schema within a Mule flow, the JSON Module must be used. The Validate Schema operation allows the developer to specify the location of a `.json` schema file (typically stored in `src/main/resources`). If the payload does not conform to the schema, the operation throws a `JSON:SCHEMA_NOT_HONORED` error, which can then be handled by the application's error handling strategy. This approach is superior to manual DataWeave checks because it automatically validates data types, required fields, and constraints defined in the official JSON Schema standard.

17. `iii.`

To minimize operational overhead and costs in Anypoint Platform, multiple API health checks can be grouped into a single Monitor (Schedule). Since the APIs are public, using a Public Location (provided by MuleSoft) avoids the cost and maintenance of setting up a Private Location (which requires a Private Worker Cloud). By including all 10 API endpoints within one functional test suite and running them under a Single Schedule, the operations team reduces the number of monitors to manage and optimizes the consumption of the platform's monitoring quota while still ensuring periodic health verification.

18. `i.`

Since Mule Domain projects are not supported in CloudHub, the standard architectural pattern for sharing common logic (like global error handlers) across multiple applications is the Mule Plugin. By packaging the error handler within a plugin project and adding it as a Maven dependency, the resource becomes available in the application's classpath. However, a critical final step is using the `<import />` configuration element in the consuming Mule application to explicitly load the XML configuration file from the plugin, allowing the application to reference the global error handler by name.

19. `iii.`

The HTTP Listener is designed to support distributed tracing by default. When a request is received, the listener checks for the presence of a correlation ID (typically in the `X-Correlation-ID` header). If the header is present, Mule honors that value and uses it as the `correlationId` for the entire event flow. If no such header is provided, the HTTP Listener automatically generates a new, unique UUID to ensure that every transaction has a traceable identifier from the moment it enters the Mule runtime.

20. `ii.`

In a Mutual TLS (mTLS) configuration, the authentication process is a two-way street that follows a specific order. The protocol starts with the standard TLS handshake where the server identifies itself to the client by sending its certificate. Only after the client validates the server's identity does the server request the client's certificate to verify the caller's identity. This ensures that both parties are authenticated before any sensitive data is exchanged. It is important to note that mTLS provides authentication of the machine/application, not necessarily authorization of the end-user (which is typically handled by OAuth2 or OIDC).

21. `ii.`

The VM Connector offers two types of queues: *Transient* and *Persistent*. Transient queues store messages exclusively in-memory, meaning all in-flight data is lost if the Mule runtime crashes or restarts. In contrast, Persistent queues back up the data to the local disk (or a shared storage in a cluster). In the event of a system failure, the Mule runtime can recover the state of persistent queues upon startup, allowing the consumer flows to pick up and process the messages that were waiting in the queue before the failure occurred.

22. `i.`

MuleSoft's best practices for Secure Properties state that both the encryption key and the sensitive data (such as passwords, client secrets, or tokens) must be unique for each environment. Using a distinct key per environment (e.g., Dev, QA, Prod) ensures that a security breach in a lower environment does not compromise production credentials. This is typically implemented by passing the environment-specific key as a dynamic property (e.g., `-Danypoint.platform.encryption.key=...`) during deployment, ensuring that the decryption process is isolated and secure within each specific runtime context.

23. `iv.`

The Tracing Module provides the *Set Logging Variable operation, which leverages the Mapped Diagnostic Context (MDC)*. When you set a variable in the MDC, it becomes part of the logging context for the current execution thread. This means that every subsequent `Logger` processor in the flow (and its sub-flows) will automatically include these variables in its output, provided the `log4j2.xml` is configured to render MDC properties (usually via `%X`). This is a best practice because it eliminates the need to manually reference flow variables in every single logger, ensuring consistent observability with minimal effort.

24. `iv.`

When configuring the HTTP Request Connector to use the Authorization Code grant type, several mandatory properties must be defined to handle the multi-step handshake. The Authorization URL and Access Token URL are required to direct the user and exchange codes, respectively. Additionally, the Client ID and Client Secret identify the application. Crucially, the Local Authorization URL defines the endpoint where the Mule app listens for the code, while the External Callback URL is the address the OAuth provider uses to redirect the user back. These parameters ensure the Mule runtime can successfully orchestrate the complex redirection and token acquisition process required by this specific grant type.

25. `i.`

When an API is configured to require manual approval for client application registration, the developer must first ensure that SLA Tiers are defined for that API instance or API Group. Without an SLA tier, the "Request Access" button in Exchange may not function as intended for governed APIs. Furthermore, from a security and governance perspective, the person approving or rejecting these requests must hold specific administrative privileges, such as Organization Administrator, API Manager Environment Administrator, or the Manage Contacts permission for that specific API. This combination ensures that access is controlled both by technical constraints (SLA) and organizational authority.

26. `ii.`

27. `i.`

28. `ii.`

By default, the Scatter-Gather router follows an "all-or-nothing" approach; if any route fails, the entire component throws a `MULE:COMPOSITE_ROUTING` error. To implement a partial success pattern, each Flow Reference (or individual route) must be wrapped in a Try scope. Inside this Try scope, an On Error Continue strategy is used to catch the timeout (or any other error). By setting a default value (like an empty string or a default object) within the On Error Continue block, the route technically "succeeds" from the Scatter-Gather's perspective, allowing the router to collect results from all other successful routes and proceed to the next processor.

29. `ii.`

API Manager executes policies in a specific order defined by the administrator. When the HTTP Caching policy is placed first in the chain and a Cache Hit occurs (meaning the requested resource is already stored), the policy immediately generates the HTTP response from the cache and returns it to the client. Because the request is resolved at this stage, the subsequent policies in the chain—such as the OAuth 2.0 access token enforcement—are never triggered or evaluated. This "short-circuit" behavior optimizes performance but requires careful architectural consideration to ensure that sensitive data is not served from the cache to unauthenticated users.

30. `iii.`

A robust health check must validate the actual execution path used by the production traffic. By creating a health check endpoint that reuses the same port and HTTP Listener configuration as the main API, you ensure that if the monitoring tool (like Anypoint Functional Monitoring or a Load Balancer) receives a successful response, the underlying infrastructure (port availability, thread pools, and listener state) is also capable of handling real payment requests. Using a separate port or configuration could lead to "false positives," where the health check appears online while the main API is unreachable due to port-specific issues or listener exhaustion.

31. `iii.`

In a Mule project, the `pom.xml` is the core configuration file for Maven. To successfully deploy an application using Maven commands (such as `mvn deploy`), the developer must configure the mule-maven-plugin section within this file. This configuration includes essential deployment details such as the target runtime version, the worker type, the environment name, and the authentication credentials (often referenced via server IDs in `settings.xml`). Without correctly defining these deployment parameters in the `pom.xml`, Maven would not know where or how to push the packaged JAR file to the Anypoint Platform.

32. `iv.`

In Mule 4, an object is not immediately deleted the millisecond its Entry TTL expires. Instead, there is a background process called the Expiration Run that executes periodically based on the Expiration Interval.
In this specific scenario:
- The entry is stored.
- 10 seconds pass (The entry is now technically "expired" because 10 > 1).
- However, the background cleanup process only runs every 30 seconds 7(Expiration Interval).
- Since the os:retrieve occurs at second 10, the cleanup task hasn't started yet. Therefore, the value "testPayload" is still present in the store and will be successfully retrieved.

33. `iv.`

The API Autodiscovery configuration element acts as the bridge between your Mule application and Anypoint API Manager. Its primary purpose is to link a specific API ID (from API Manager) to a specific flow in your Mule project. The `flowRef` attribute must point to the Global Flow (usually the one generated by APIkit) that contains the HTTP Listener. This is critical because the runtime uses this link to intercept incoming HTTP requests and apply the policies fetched from the control plane before the request reaches your business logic.

34. `ii.`

The keytool utility is a standard Java command-line tool used to manage keys and certificates. To convert a legacy JKS keystore to the modern PKCS12 format, the -importkeystore command is used. The logic follows a "Source to Destination" pattern:

* -srckeystore: Points to the existing JKS file.
* -srcstoretype JKS: Informs the tool that the source is a Java KeyStore.
* -destkeystore: Defines the name of the new file (e.g., keystore.p12).
* -deststoretype PKCS12: Specifies that the new output should be in PKCS12 format.

MuleSoft recommends using PKCS12 for modern applications as it is a cross-platform, industry-standard format, unlike JKS which is proprietary to Java.

35. `i.`

Object Store v2 has a hard limit of *10 MB* for the size of a single value. When a Mule application needs to persist large files (over 10MB) across multiple replicas in CloudHub 2.0, the best practice is to use an external storage solution (such as AWS S3, Azure Blob Storage, or an SFTP server). The application should upload the file to this external storage and then store only the metadata (the file's key, URL, or path) in the Object Store. This allows separate executions on different replicas to query the Object Store, retrieve the location, and then download the large file from the shared external source.

36. `iv.`

When integrating custom or legacy Java libraries into a Mule project, the industry best practice is to treat them as Maven dependencies. The process involves:

1. Installing the JAR file into a Maven repository (either a local .m2 repository for development or a remote repository like Nexus, Artifactory, or Anypoint Exchange for team collaboration).
2. Referencing the library in the project's pom.xml file by defining its groupId, artifactId, and version.

This approach ensures that the library is automatically included in the build process, manages transitive dependencies, and follows the "build once, deploy anywhere" principle required for CI/CD pipelines.

37. `iii.`

In Mule 4, the HTTP Listener has two distinct response sections: Responses (for success) and Error Responses (for failures). When a flow ends with an On Error Propagate, the execution is considered a failure. Consequently, the Listener ignores the standard "Response" settings and triggers the "Error Response" settings. Even if you manually set `vars.httpStatus = 200` and change the payload inside the error handler, the Listener will still return a 500 Internal Server Error status code unless the Error Response -> Status Code field in the Listener's configuration is explicitly mapped to that variable. Since the question implies default behavior for the error mapping, the status remains 500, while the body becomes the new payload set in the handler: `'Error in processing your request'`.

38. `iii.`

The Until Successful scope is designed to retry its child processors whenever an error occurs. However, for "non-transient" or permanent errors like **HTTP:UNAUTHORIZED** (401) or **HTTP:FORBIDDEN** (403), retrying is a waste of resources and increases latency. By wrapping the HTTP Request in a **Try scope** with an **On Error Continue** strategy specifically for these error types, you effectively "swallow" the error. Since the Try scope returns a success signal to the Until Successful scope, the retries are immediately aborted after the first failure, thus saving execution time and reducing overall latency.

39. `i.`

A Parent POM is the recommended architectural pattern for standardizing deployment logic across an organization. By defining the mule-maven-plugin configuration in a parent file, you ensure that all child applications use the same deployment standards and plugin versions. Child projects reference this parent and provide their unique values (like `${app.name}`) through properties. This "Inheritance" model simplifies maintenance: if you need to update the Mule runtime version or change a deployment flag for all 50 APIs in your company, you only modify the Parent POM once instead of editing 50 individual projects.

40. `iv.`

41. `ii.` 

The `validation:all` scope is specifically designed to execute all of its nested validation operations, regardless of whether any individual validation fails. Unlike a standard flow where the first error typically stops execution, `validation:all` continues to evaluate every child validator to collect a complete set of validation failures. If one or more validations fail, the scope throws a single `VALIDATION:MULTIPLE` error. This error contains a `parentError` object with a list of all the individual errors captured. This is ideal for front-end applications that need to display all form errors to the user at once (e.g., "invalid email", "invalid date", and "name missing") instead of forcing the user to fix one error at a time.

42. `iv.`

In REST architecture, the `PUT` method is defined as idempotent. This means that making multiple identical requests has the same effect as making a single request. Since the flow uses Until Successful to retry the subflow, and the subflow contains `PUT` operations, the overall process is already reliable and idempotent by design. If a retry occurs, re-sending the same `PUT` request to an upstream system will not result in duplicate records or inconsistent states, unlike a `POST` request (which is typically NOT idempotent). Therefore, no additional architectural changes are required to ensure idempotency.

43. `iii.`

The Cache scope in MuleSoft relies on an Object Store to persist its cached responses. By default, or by providing a custom Object Store configuration, you can define an **Entry TTL (Time To Live)** and an Expiration Interval. Once the TTL for a specific cached entry expires, the next request with the same key will result in a "cache miss," forcing the flow to execute the internal processors again and refresh the cache. While more complex invalidation strategies (like manual clearing via the Object Store connector) are possible, TTL is the only one supported inherently through basic configuration without writing custom logic or additional flows.

44. `iii.`

When an API is scaffolded in Anypoint Studio based on a RAML definition, the APIkit Router performs automatic validation against that contract. In the provided exhibit, the client-id-required trait defines client_id and client_secret as mandatory headers. If a consumer fails to provide these values in the APIkit Console, the request is technically invalid according to the API specification. Since the validation fails at the interface level before any security policy or backend logic is even triggered, the router returns an HTTP 400 Bad Request. An HTTP 403 would only be returned if the headers were present but rejected by a security policy (like Client ID Enforcement) applied in API Manager.

45. `iv.`

In Mule 4, the **Correlation ID** is a built-in property of every event. When an HTTP Listener receives a request, it either adopts the `X-Correlation-ID` header from the incoming request or generates a new UUID if none is provided. This ID stays attached to the event throughout its entire lifecycle (even through asynchronous VM queues or Scatter-Gathers). Crucially, the HTTP Listener is designed to automatically echo this same ID back to the client in the response header `X-Correlation-ID` without any additional configuration, flow-ref, or manual header mapping.

46. `iii.`

When a Scatter-Gather router encounters errors in one or more routes, it throws a `MULE:COMPOSITE_ERROR`. This is a complex object that consolidates all outcomes. To access the specific details of a failed route, you must navigate through the `error.errorMessage.payload` object. This payload contains two collections: `results` (for success) and `failures` (for errors). Because the routes are zero-indexed, Route C corresponds to index 2. Therefore, the correct expression to retrieve the error details for that specific route is `error.errorMessage.payload.failures['2']`.

47. `iii.`

Inbound vs. Outbound Policy Interception:
When developing a custom policy in Mule 4, you must choose the appropriate injection point in the XML template:

- `<http-policy:source>`: Wraps the Message Source (typically the HTTP Listener). Use this for policies that govern how clients access your API.
- `<http-policy:operation>`: Wraps the Message Processor (specifically the HTTP Request operation). Use this for policies that need to intercept, modify, or log outbound calls to downstream systems.

This distinction allows architects to enforce governance not only on how their APIs are consumed but also on how those APIs interact with the rest of the ecosystem.

48. `iv.`

In modern API architecture, tasks that exceed standard timeout windows (typically > 30 seconds) must be handled asynchronously. A Callback (Webhook) implementation involves:

1. The Mule app sends the initial request, including a callback_url.
2. The external system acknowledges receipt and closes the connection.
3. Once the process completes (even 24 hours later), the external system makes an outbound HTTP request to the Mule callback URL to deliver the results.

This approach is superior to Polling (Option 2), which wastes bandwidth and processing power by repeatedly checking for status updates that aren't ready yet.

49. `ii.`

A core principle of unit testing is that each test case must be **independent and isolated**. Chaining tests (Option 1) or passing data between them (Options 3 & 4) creates "flaky" tests where a failure in one component causes a domino effect of failures in unrelated tests.
To test Flow-2 correctly, you should use the Set Event processor within your MUnit test. This allows you to *"mock"* the required state—injecting the specific payload and variables that Flow-2 expects—ensuring the test remains focused only on the logic of Flow-2. This approach guarantees that your test suite is reliable, maintainable, and portable across different environments.

50. `i.`

To capture specific logs from a Mule component like the VM Connector, you must modify the log4j2.xml file. The configuration follows a specific hierarchy:

- Appenders: Define the destination (e.g., RollingFile).
- Loggers: Define the scope and severity.
To target the VM connector specifically, you add an `<AsyncLogger>` (or a synchronous `<Logger>`) referencing the connector's Java package name (`org.mule.extensions.vm`). Setting the level to `ERROR` ensures that only exception data and failure events from that specific connector are captured and sent to the defined appenders.

51. `iii.`

52. `i.`

The VM Connector supports asynchronous, inter‑application communication through in‑memory or persistent queues when applications are deployed under the same Mule domain. By associating both APIs with a shared domain, they can access the same VM queues, allowing one API to publish messages and the other to consume them asynchronously. In an on‑premises clustered environment, these VM queues are shared across the cluster and backed by the cluster’s memory grid, ensuring reliable and decoupled message exchange between the two APIs. Therefore, when the APIs run in the same domain, the VM Connector can be leveraged, making option A correct.

53. `ii.`

The Gatekeeper is a security feature that prevents an API from accepting requests until it has successfully synchronized with API Manager and applied all active policies. When developing locally in Anypoint Studio, if API Autodiscovery is enabled, the runtime will try to reach the Anypoint Platform. If it fails or if policies like an IP Allowlist would block the developer's local IP, the API remains unreachable. By setting the runtime property `-Danypoint.platform.gatekeeper=disabled`, the developer bypasses this check, allowing the API to start and accept local traffic regardless of the status of online policies.

54. `i.`

In a production environment, monitoring goes beyond checking if the Java Virtual Machine (JVM) is running.

1. Liveness Check: Confirms the application is running (Option 4).
2. Readiness Check: Confirms the application and its downstream dependencies (like the MySQL database) are available to fulfill requests (Option 1).

If the MySQL database is down, the System API cannot fulfill its contract. Therefore, the readiness endpoint must perform a "heartbeat" or a lightweight query to the database. If this check fails, the API reports itself as "Not Ready," allowing automated systems (like CloudHub's load balancer or Kubernetes) to redirect traffic to healthy replicas or alert the DevOps team.

55. `iii.`

In MuleSoft's "API-Led Connectivity" model, versioning should be explicitly defined in the API specification. By modifying the `baseUri` in Design Center to include a version variable (e.g., `https://api.example.com/v1`), you ensure that the versioning is part of the API's contract. This allows for:

- Side-by-side deployment: Multiple major versions can coexist because their base paths are distinct.
- Consumer Clarity: Partners can choose which version to target by simply changing the URL prefix.
- Scaffolding Accuracy: When generating the backend implementation, the HTTP Listener will automatically inherit the correct path structure from the RAML, reducing manual configuration errors in Studio.

56. `iii.`

During the TLS (and mTLS) handshake, specifically in the `Client Hello` and `Server Hello` messages, both parties must agree on a **Cipher Suite**. This suite is a set of cryptographic algorithms that determines how the session will be secured. While the **TLS Version** (Option 2) is negotiated at the very beginning, the Cipher Suite exchange specifically focuses on selecting the Encryption Algorithm (like AES) and the hashing method. Without this agreement, the two systems wouldn't know how to encrypt or decrypt the data packets they are about to send to each other.

57. `iv`

A Mule 4 custom policy is essentially a specialized Mule application fragment that consists of two core files:

1. The YAML file: Acting as the "schema" or metadata, it defines the properties (inputs) required by the policy. This file dictates the UI form that appears in Anypoint Platform when a user applies the policy.
2. The XML file: Acting as the "implementation," it contains the actual Mule SDK or XML code that executes the logic (e.g., token validation).

During the build process (using Maven), these files are packaged into a JAR (not a ZIP) and uploaded to Exchange so they can be discovered and applied by API Manager to the target APIs.

58. `i.`

The most efficient way to start a Mule implementation is by leveraging a published API. When you choose to Import a published API in Anypoint Studio:

- The IDE fetches the metadata directly from Anypoint Exchange.
- The developer is prompted to choose a specific Asset Version (e.g., 1.0.1) and API Version (e.g., v1).
- Studio automatically triggers the APIkit Router to create the flow scaffolding, including the main router and individual message processors for every GET, POST, or PUT operation defined in the contract. <br/> This ensures that the implementation stays strictly aligned with the organizational governance and documentation standards established in the design phase.

59. `i.`

MuleSoft applies policies as nested wrappers around the main API flow. The execution logic follows a specific sequence based on the Order assigned in API Manager:

* Request Phase: Policies execute from lowest to highest order number (1, then 2, then 3...).
* The Core: The `execute-next` processor in the highest-order policy triggers the actual API implementation flow.
* Response Phase: After the flow completes, execution flows back through the policies in highest to lowest order (inverse sequence).

Therefore, with Policy A (Order 1) and Policy B (Order 2), the message path is:
`Policy A (Inbound) -> Policy B (Inbound) -> API Flow -> Policy B (Outbound) -> Policy A (Outbound).`

60. `i.`

For customers with the Titanium subscription, Anypoint Monitoring provides advanced observability without requiring manual code changes. The Built-in Dashboards automatically instrument standard connectors like the **Salesforce Connector**.

By navigating to the **Connectors** tab within the application's dashboard, developers and operations teams can instantly view high-level metrics such as throughput and latency specifically for that connector's operations. This is a "zero-config" solution that leverages the underlying telemetry of the Mule runtime.

61. `iii.`

PGP encryption relies on a key pair: a Public Key and a Private Key.

- To **encrypt** data, the sender (Mule 4 app) must use the recipient's Public Key. This ensures that the data is scrambled in a way that only one specific entity can reverse.
- To **decrypt** data, the recipient (Backend) uses its own Private Key, which must never be shared.

In this scenario, the Mule application acts as the sender. Therefore, it only requires the backend's public key to perform the encryption operation. It does not need the private key (which would be a major security risk) nor its own keys unless it also needs to "sign" the message for authenticity.