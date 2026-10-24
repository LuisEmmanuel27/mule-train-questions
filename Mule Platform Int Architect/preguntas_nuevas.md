# Most Likely Questions · Mule-Arch-201 (MCPA)

## [Cuestionario](cuestionario.md) · [Respuestas alternas](respuestas_alter.md)

> **Qué es esto:** 60 preguntas con su respuesta correcta y la justificación.
> - **Parte A (1–25):** preguntas del banco actual de 152 (actualizado en oct-2026) que **no** vienen en tu cuestionario.
> - **Parte B (26–60):** preguntas de tu cuestionario confirmadas en el banco actual.
> - **Parte C (61+):** preguntas de práctica nuevas que fuiste agregando y que no estaban en tu cuestionario ni aquí.
> - **Parte D (74–103):** 30 preguntas de práctica (con opciones a–d) sobre los temas nuevos de Mule-Arch-201 que no cubren los bancos: CloudHub 2.0, Flex Gateway, API Governance, Anypoint MQ, entre otros.
> - Todas con la pregunta (**Q**) y la respuesta (**A**) en inglés, y la justificación en español.
>
> 🟡 = la respuesta es la más sólida según la documentación o la lógica MuleSoft, pero algún banco marca otra; está indicado.

---

## Parte A: Preguntas nuevas (no están en tu cuestionario)

> Pregunta y respuesta en inglés, como aparecen en el examen. Algunas preguntas están resumidas porque los sitios no muestran el texto completo, pero conservan los datos clave para que las reconozcas.

1. **Q:** A circuit breaker strategy is planned in order to meet the goal of improved response time and demand on a downstream API. Thresholds are defined for Circuit Open (more than 10 errors/minute for 3 minutes), Circuit Half-Open (1 error/minute) and Circuit Closed (less than 1 error/minute for 5 minutes). Which proposal meets this goal?
   **A:** Add the Circuit Breaker policy to the API instance, and configure the required settings.
   *Justificación:* El Circuit Breaker ya es una política incluida de fábrica en API Manager. Construir una política propia, programarlo en la app o armar alertas con reintentos implica más esfuerzo y no aporta nada.

2. **Q:** An application updates an inventory running only one process at any given time to keep the inventory consistent. Each process takes 200 milliseconds, so the application can handle five requests per second. What happens if the application is scaled horizontally by adding more workers?
   **A:** The application scalability threshold is five requests per second regardless of the horizontal scaling.
   *Justificación:* 1000 ms / 200 ms = 5 rps. Como solo puede correr un proceso a la vez, agregar workers no sube el límite: el cuello de botella es el diseño.

3. **Q:** A Platform Architect inherits a legacy monolithic SOAP-based web service that performs a number of tasks, including showing all policies belonging to a client. The service connects to two back-end systems (a life-insurance administration system and a general-insurance administration system), queries for insurance policy information within each system, aggregates the results, and presents a SOAP-based response to a user interface (UI). The architect wants to break up the monolithic web service to follow API-led conventions. Which part of the service should be put into the process layer?
   **A:** Combining the insurance policy information from the administration systems.
   *Justificación:* Consultar y conectarse a cada backend va en System; presentar la respuesta a la UI va en Experience; agregar y orquestar va en Process.

4. **Q:** An enterprise is embarking on the API-led digital transformation journey, and the central IT team has started to define System APIs. Currently there is no Enterprise Data Model defined within the enterprise, and the definition of a clean Bounded Context Data Model requires too much effort. According to MuleSoft's recommended guidelines, how should the System API data model be defined?
   **A:** The data model of the System APIs should make use of data types that approximately mirror those from the back-end systems.
   *Justificación:* Es el enfoque pragmático del curso: se parece al backend, pero "aproximadamente". No se copian errores tal cual, no se inventa una convención nueva y no se exponen todos los campos.

5. **Q:** A team is planning to enhance an Experience API specification, and they are following API-led connectivity design principles. What is their motivation for enhancing the API?
   **A:** A Canonical Data Model is being adopted that impacts several types of data included in the API.
   *Justificación:* La especificación (el contrato) solo cambia si cambian los datos que expone. Que la System API de abajo cambie no obliga a cambiar la Experience API (para eso existen las capas). Una política como IP Allowlist no toca el contrato. Y cambiar endpoints a gusto de un consumidor rompe el estándar del C4E.

6. **Q:** An organization wants to create a Center for Enablement (C4E). What should be on the agenda of the first meeting?
   **A:** Define C4E objectives, mission statement, guiding principles, and success criteria (KPIs).
   *Justificación:* Primero se establece el propósito del C4E. La monetización, las buenas prácticas técnicas y el modelo operativo de una división vienen después.

7. **Q:** A large organization with an experienced central IT department is getting started using MuleSoft. It needs to connect a siloed back-end system to a new CRM system. What action would support building an application network using API-led connectivity?
   **A:** Create a System API that exposes the back-end system data through a REST API.
   *Justificación:* El primer paso de API-led es desbloquear el sistema con una System API reutilizable. Conectar el CRM y el backend directamente es punto a punto, y un modelo canónico hecho por un analista no construye la red de aplicaciones.

8. **Q:** An Order API triggers a sequence of other API calls to look up details of an order's items: the Order API calls the OrderItems Process API, which calls the Inventory System API, which queries an unreliable inventory database that sometimes hangs. Where should a timeout of 2 seconds be configured so that the Order API never waits more than 2 seconds for a response from the OrderItems Process API?
   **A:** In the Order API implementation.
   *Justificación:* El timeout lo configura quien no quiere esperar (el cliente), en su HTTP Request hacia OrderItems. Ponerlo más abajo no garantiza los 2 s de la Order API.

9. **Q:** An organization has built an application network following the API-led connectivity approach. It wants to protect the network from malicious external API clients by using JSON Threat Protection policies. In which API layer are these policies most commonly applied?
   **A:** The experience layer.
   *Justificación:* Experience es la capa expuesta a clientes externos. Process y System solo reciben tráfico interno ya validado (por eso tu #95 dice que es la política menos probable en Process).

10. **Q:** An established communications company is beginning its API-led connectivity journey. It has an established Enterprise Data Model (EDM) and has identified Experience, Process and System APIs for a self-service account management mobile app: Customer SAPI, Customer Lookup PAPI, Mobile Account Management EAPI and Service SAPI. Which API would NOT be served by the Enterprise Data Model?
    **A:** Mobile Account Management EAPI.
    *Justificación:* Las Experience APIs se adaptan a su consumidor (la app móvil). El EDM aplica a Process y System, igual que en tu #11.

11. **Q:** A customer wants to monitor and gain insights about the number of requests coming in a given time period, as well as to measure key performance indicators (response times, CPU utilization, number of active APIs). Which tool provides these data insights?
    **A:** Anypoint Monitoring.
    *Justificación:* Reúne métricas de apps y APIs (peticiones, tiempos, CPU). Functional Monitoring sirve para pruebas funcionales, Runtime Alerts solo genera alertas y API Manager gestiona políticas.

12. **Q:** A developer from the Central IT team has created an initial version of the RAML definition in Design Center for an OAuth 2.0-protected System API and published it to Exchange. Another developer from LoB IT discovered the System API in Exchange and would like to leverage it in the Process API. What is the MuleSoft-recommended approach for the Process API to invoke the System API?
    **A:** The Process API uses the REST Connect Connector autogenerated in Exchange for the System API.
    *Justificación:* Exchange genera un conector (REST Connect) a partir del RAML publicado; es la forma recomendada de reutilizarlo. Las demás opciones (importar un módulo OAuth, usar HTTP Request con URLs en YAML o editar el POM a mano) son manuales.

13. **Q:** A developer for a transportation organization is implementing exactly-once processing functionality in a Reservation Mule application to process and store passenger records. The application will be deployed to multiple CloudHub workers/replicas, and several external systems could send duplicate passenger records. Which type of simple storage mechanism in Anypoint Platform allows the Reservation Mule application to update and share data between the CloudHub workers/replicas exactly once, with minimal development effort?
    **A:** Persistent Object Store.
    *Justificación:* Se comparte entre los workers de CloudHub y sobrevive reinicios. El Object Store en memoria o no persistente es local a cada worker o volátil, y el de Runtime Fabric no aplica a CloudHub.

14. **Q:** Which statement is true about Spike Control policy and Rate Limiting policy?
    **A:** All requests are rejected after the limit is reached in Rate Limiting policy, whereas the requests are queued in Spike Control policy after the limit is reached.
    *Justificación:* Esa es la diferencia clave. Las demás opciones son falsas: Rate Limiting puede aplicarse a todo el clúster, no hace falta Rate Limiting para proteger Experience APIs, y solo la versión *SLA-based* necesita contrato.

15. **Q:** A Platinum customer uses the U.S. control plane and deploys applications to CloudHub in Singapore with a default log configuration. The compliance officer asks where the logs and monitoring data reside.
    **A:** Logs and monitoring data are held in the United States.
    *Justificación:* Los logs y el monitoreo los almacena el control plane, que está en EE. UU., aunque el runtime esté en Singapur. Por eso, para cumplir con una jurisdicción, deben alinearse **ambos planos** (tu #45).

16. **Q:** A Mule application implements an API. The HTTP Listener's connector configuration has HTTPS enabled and the port is hard-coded. The application is deployed to an Anypoint VPC and uses the CloudHub 1.0 Shared Load Balancer for all incoming traffic. Which port must be assigned to the HTTP Listener so the application properly receives HTTPS invocations routed through the Shared Load Balancer?
    **A:** 8082 🟡
    *Justificación:* La documentación oficial dice que el SLB envía 443 → 8082 (`${https.port}`). El 8092 es el puerto *interno* (`mule-worker-internal`), solo para tráfico dentro de la VPC o con un balanceador propio. **Ojo:** pass4success marca 8092 sin verificarlo. Si la pregunta menciona *mule-worker-internal* o un balanceador propio, la respuesta es 8092.

17. **Q:** A company is building an application network using MuleSoft's recommendations for the various API layers. What is the main (default) role of a Process API?
    **A:** To orchestrate and coordinate calls to other APIs in order to automate a business process.
    *Justificación:* Process orquesta y aplica la lógica de negocio. Exponer sistemas es tarea de System y adaptar datos a un canal es tarea de Experience.

18. **Q:** An online store's marketing team has noticed an increase in customers leaving online baskets without checking out. They want to view metrics from all the APIs involved in the checkout process at the same time. Which Anypoint Platform feature should be used?
    **A:** Custom dashboards (Anypoint Monitoring).
    *Justificación:* Los dashboards integrados muestran una app o API a la vez; los personalizados combinan métricas de varias en una sola vista.

19. **Q:** A Rate Limiting policy is applied to an API implementation to protect the back-end system. Recently, there have been surges in demand that cause some API client POST requests to be rejected, resulting in errors. How should the policies be changed to reduce the number of client errors while still protecting the back-end system?
    **A:** Remove the Rate Limiting policy and add a Spike Control policy. 🟡
    *Justificación:* Spike Control suaviza las ráfagas (encola y reintenta) en lugar de rechazar, y sigue protegiendo el backend. Si se mantiene Rate Limiting, los rechazos continúan. Algunos bancos marcan "keep Rate Limiting and add SLA-based Spike Control".

20. **Q:** An organization requires several APIs to be secured with OAuth 2.0, using PingFederate as the client provider (identity provider for client management) across two child business groups. What must be done so that API consumers can access these API instances?
    **A:** The API consumer creates a client application and requests access to the API instance in Anypoint Exchange, and the API administrator approves the request. 🟡
    *Justificación:* Aunque el client provider sea externo, el flujo de acceso sigue pasando por Exchange: la plataforma registra el cliente en PingFederate. No se solicita acceso directamente en Ping ni se crean contratos a mano.

21. **Q:** A security team has a guideline that NO HTTP traffic is allowed for a production environment deployed on a dedicated Anypoint VPC in CloudHub 1.0. Which TWO options support this requirement?
    **A:** Enable HTTPS on the HTTP Listener configuration **+** Remove the HTTP entry from the VPC firewall rules.
    *Justificación:* El protocolo se controla en el listener (HTTPS) y en el firewall de la VPC. Las políticas, como IP blocklist o una política personalizada, no bloquean el protocolo HTTP.

22. **Q:** Which THREE tools automate the deployment of Mule applications?
    **A:** Anypoint Platform CLI, Anypoint Platform APIs, Mule Maven plugin. 🟡
    *Justificación:* Son las tres herramientas de automatización que menciona la documentación oficial. Runtime Manager y Anypoint Studio son interfaces manuales, y API Community Manager es un portal. **Ojo:** exams4sure marca Runtime Manager + CLI + APIs; lo correcto según la documentación es CLI + APIs + Maven.

23. **Q:** An auto manufacturer with a mature CI/CD practice wants to automate the packaging and deployment of Mule applications to CloudHub, customer-hosted Mule runtimes, and Anypoint Runtime Fabric. Which MuleSoft-provided tool or component facilitates this?
    **A:** Mule Maven plugin.
    *Justificación:* Está hecho para pipelines de CI/CD: empaqueta y despliega a los tres destinos. La CLI y las APIs pueden desplegar, pero no empaquetan.

24. **Q:** A client wants to send daily changes of Salesforce Account and Case records to AWS DynamoDB as a single JSON document. Only 5 of the 219 Account attributes and 8 of the Case attributes are needed. Which API design best supports this data model?
    **A:** Create a System API for Account exposing only the 5 required attributes and a System API for Case exposing only the 8 required attributes, then a Process API combines them into the 13-attribute JSON sent to DynamoDB.
    *Justificación:* Hay una System API por entidad, cada una solo con lo necesario, y la combinación va en Process. Copiar todos los atributos o crear un EDM para esto sería un desperdicio.

25. **Q:** An eCommerce company is adding a new Product Details feature to its website. Product data is updated only once or twice a year, and the database responds slowly under high volume. What action retrieves the product details with the lowest response time, fault tolerance, and consistent data?
    **A:** Use an object store to store and retrieve the product details originally read from a database, and return them within the API response.
    *Justificación:* El Object Store es un caché persistente y compartido entre workers: es rápido, tolera fallos y es consistente. El Cache scope es local a cada worker, Anypoint MQ no sirve para esto y leer siempre de la BD es lento.

---

## Parte B: De tu cuestionario, confirmadas en el banco actual

> Entre paréntesis va el número en `cuestionario.md`, solo como referencia. Aquí ya tienes todo lo que necesitas.

26. **Q:** What are 4 important Platform Capabilities offered by Anypoint Platform? *(#2)*
    **A:** API Design and Development, API Runtime Execution and Hosting, API Operations and Management, API Consumer Engagement.
    *Justificación:* Es la lista oficial del curso. Versionado y deprecación son prácticas, no capacidades de la plataforma.

27. **Q:** A retail company with thousands of stores has an API to receive data about purchases and insert it into a single database. Each store sends a batch of purchase data about every 30 minutes. The API implementation uses a database bulk insert with a custom JDBC driver, and is deployed to a single CloudHub worker. The JDBC driver processes the data into several temporary disk files on the worker before sending it to an analytics engine. Sometimes a request fails with an out-of-file-space message from the JDBC driver; when resubmitted, it succeeds. What is the best way to try to resolve this throughput issue? *(#13)*
    **A:** Increase the size of the CloudHub worker(s). 🟡
    *Justificación:* Es un problema de disco del worker, y un worker más grande tiene más disco. El autoscaling se dispara por CPU o memoria, no por disco. Brainscape marca "Increase the number of CloudHub workers".

28. **Q:** An API has been updated in Anypoint Exchange by its API producer from version 3.1.1 to 3.2.0 following accepted semantic versioning practices, and the changes have been communicated via the API's public portal. The API endpoint does NOT change in the new version. How should the developer of an API client respond to this change? *(#15 / #44)*
    **A:** The API client code ONLY needs to be changed if it needs to take advantage of new features.
    *Justificación:* 3.1.1 → 3.2.0 es un cambio MINOR: compatible hacia atrás. No hace falta regresión completa ni correr versiones en paralelo.

29. **Q:** An organization wants to make sure only known partners can invoke the organization's APIs, so it wants to enforce a Client ID Enforcement policy in API Manager. In what type of API implementation does MuleSoft recommend adding an API proxy to enforce the policy, rather than embedding it directly in the application's JVM? *(#17)*
    **A:** A Non-Mule application.
    *Justificación:* Sin un Mule runtime no hay autodiscovery, así que las políticas solo se pueden aplicar a través de un proxy.

30. **Q:** Which of the below, when used together, makes the IT Operational Model effective? *(#26)*
    **A:** Create reusable assets, make them discoverable so that LOB teams can self-serve and browse the APIs, and get active feedback and usage metrics.
    *Justificación:* Es el ciclo completo producción → consumo → feedback. Sin las métricas de uso, el modelo queda incompleto.

31. **Q:** A legacy CRM system called CRM-Z offers these functions: customer creation, amend details of an existing customer, retrieve details of a customer, suspend a customer. How should System APIs be designed for it? *(#32)*
    **A:** Implement a system API named customerManagement which has all the functionalities wrapped in it as various operations/resources. 🟡
    *Justificación:* Una API por capacidad o entidad de negocio, no una por operación. Además, poner "CRMZ" en el nombre acopla la API al backend. Es lo que recomienda el curso de MuleSoft: una sola API por entidad, con las operaciones como recursos (`POST /customers`, `PATCH /customers/{id}`, `GET /customers/{id}`…). **Ojo:** pass4test y otros bancos marcan "createCustomer, amendCustomer, retrieveCustomer y suspendCustomer" como APIs separadas; según la documentación, eso es fragmentar de más.

32. **Q:** A company has started to create an application network and is now planning to implement a Center for Enablement (C4E) organizational model. What key factor would lead the company to decide upon a federated rather than a centralized C4E? *(#34)*
    **A:** When development is already organized into several independent initiatives or groups.
    *Justificación:* Un C4E federado se apoya en los equipos o LOBs independientes que ya existen.

33. **Q:** A retail company's Order API uses a JMS queue to submit orders to a backend order management service. Normal load is handled by two CloudHub workers of 0.2 vCore each, with CPU well below 70%. Several times a year the Order API gets 4x the average orders, pushing CPU above 90% and order submission time above 30 seconds. The backend is NOT the cause. What is the MOST resource-efficient way to configure the CloudHub deployment to cope with this? *(#35)*
    **A:** Use a horizontal CloudHub autoscaling policy that triggers on CPU utilization greater than 70%.
    *Justificación:* Los picos son ocasionales, así que escalar de forma permanente desperdicia recursos. Escalar verticalmente deja los mismos 2 workers y casi no mejora el throughput hacia JMS. Escalar horizontalmente agrega workers solo durante el pico.

34. **Q:** What Anypoint Connectors support transactions? *(#37)*
    **A:** Database, JMS, VM.
    *Justificación:* Son los conectores transaccionales (single resource y XA). HTTP, File y SFTP no soportan transacciones.

35. **Q:** What is most likely NOT a characteristic of an integration test for a REST API implementation? *(#40)*
    **A:** The test runs immediately after the Mule application has been compiled and packaged.
    *Justificación:* Eso describe un unit test. El integration test necesita la app desplegada y los sistemas accesibles.

36. **Q:** How are an API implementation, API client, and API consumer combined to invoke and process an API? *(#48)*
    **A:** The API consumer creates an API client, which sends API invocations to an API such that they are processed by an API implementation.
    *Justificación:* Es la definición del curso. El consumer es la persona u organización, el client es el software que llama a la API y la implementation es la que procesa la petición.

37. **Q:** An Order API must be designed that contains significant amounts of integration logic and involves the invocation of the Product API. The power relationship between Order API and Product API is one of "Customer/Supplier", because the Product API is used heavily throughout the organization and is developed by a dedicated team in the office of the CTO. What strategy should be used to deal with the API data model of the Product API within the Order API? *(#50)*
    **A:** Implement an anti-corruption layer in the Order API that transforms the Product API data model into internal data types of the Order API.
    *Justificación:* La Order API tiene mucha lógica propia. El ACL protege su modelo interno de los cambios en Product API sin pedirle nada al equipo de Product.

38. **Q:** What correctly characterizes unit tests of Mule applications? *(#52)*
    **A:** They are typically written using MUnit to run in an embedded Mule runtime that does not require external connectivity.
    *Justificación:* Es la definición de unit test en Mule.

39. **Q:** What is true about automating interactions with Anypoint Platform using tools such as Anypoint Platform REST APIs, Anypoint CLI, or the Mule Maven plugin? *(#57)*
    **A:** By default, the Anypoint CLI and Mule Maven plugin are NOT included in the Mule runtime, so are NOT available to be used by deployed Mule applications.
    *Justificación:* Las demás opciones son falsas: las APIs no se limitan a CloudHub, no se pueden aplicar políticas a las APIs de la plataforma y no existen permisos separados para la CLI y para las APIs.

40. **Q:** What CANNOT be effectively enforced using an API policy in Anypoint Platform? *(#61)*
    **A:** Guarding against Denial of Service attacks. 🟡
    *Justificación:* La política se ejecuta dentro del runtime, y cuando un ataque DoS llega ahí ya consumió recursos. La defensa va en el borde (Anypoint Security Edge, WAF). En cambio, las credenciales, el logging y la protección del backend sí se pueden manejar con políticas.

41. **Q:** How can the application of a rate limiting API policy be accurately reflected in the RAML definition of an API? *(#67)*
    **A:** By refining the response definitions by adding the x-ratelimit-* response headers with description, type, and example.
    *Justificación:* El cliente recibe esos headers en la respuesta, así que el contrato debe documentarlos.

42. **Q:** What is the most performant out-of-the-box solution in Anypoint Platform to track transaction state in an asynchronously executing long-running process implemented as a Mule application deployed to multiple CloudHub workers? *(#68)*
    **A:** Persistent Object Store.
    *Justificación:* Es nativo y compartido entre workers. Redis no viene incluido, y WeakHashMap y los archivos son locales a cada worker.

43. **Q:** What is a key requirement when using an external Identity Provider for Client Management in Anypoint Platform? *(#70)*
    **A:** To invoke OAuth 2.0-protected APIs managed by Anypoint Platform, API clients must submit access tokens issued by that same Identity Provider.
    *Justificación:* La política OAuth valida los tokens contra el IdP configurado como client provider.

44. **Q:** What is true about where an API policy is defined in Anypoint Platform and how it is then applied to API instances? *(#73)*
    **A:** The API policy is defined in API Manager for a specific API instance, and then ONLY applied to the specific API instance.
    *Justificación:* Las políticas se configuran por instancia. Así, cada instancia (por ejemplo, cada entorno) puede tener las suyas.

45. **Q:** What best describes the Fully Qualified Domain Names (FQDNs), also known as DNS entries, created when a Mule application is deployed to the CloudHub Shared Worker Cloud? *(#76)*
    **A:** The FQDNs are determined by the application name chosen, IRRESPECTIVE of the region. 🟡
    *Justificación:* Es lo que marcan pass4success y examcatalog: el nombre de la app es globalmente único y es lo que define el DNS. La comunidad está dividida con "app name + organization".

46. **Q:** A System API is designed to retrieve data from a backend system that has scalability challenges. What API policy can best safeguard the backend system? *(#79)*
    **A:** SLA-based rate limiting.
    *Justificación:* De las opciones (IP whitelist, OAuth, Client ID), es la única que limita volumen. Spike Control sería lo ideal, pero no aparece entre las opciones.

47. **Q:** What is true when using customer-hosted Mule runtimes with the MuleSoft-hosted Anypoint Platform control plane (hybrid deployment)? *(#80)*
    **A:** API implementations can run successfully in customer-hosted Mule runtimes, even when they are unable to communicate with the control plane.
    *Justificación:* El runtime funciona de forma autónoma. Además, es el runtime el que inicia la conexión con el control plane (no al revés), y el Shared Load Balancer solo existe en CloudHub.

48. **Q:** What best explains the use of auto-discovery in API implementations? *(#83)*
    **A:** It makes API Manager aware of API implementations and hence enables it to enforce policies.
    *Justificación:* Liga la app desplegada con su instancia en API Manager.

49. **Q:** When designing an upstream API and its implementation, the development team has been advised to NOT set timeouts when invoking a downstream API, because that downstream API has no SLA that can be relied upon. This is the only downstream API dependency of that upstream API. Assume the downstream API runs uninterrupted without crashing. What is the impact of this advice? *(#84)*
    **A:** An SLA for the upstream API CANNOT be provided.
    *Justificación:* Sin timeout y con un downstream sin SLA, el upstream no puede garantizar ningún tiempo de respuesta.

50. **Q:** A developer is building a client application to invoke an API deployed to the STAGING environment that is governed by a client ID enforcement policy. What is required to successfully invoke the API? *(#86)*
    **A:** The client ID and secret obtained from Anypoint Exchange for the API instance in the STAGING environment.
    *Justificación:* Se obtienen al registrar la client app y solicitar acceso a esa instancia en Exchange.

51. **Q:** What do the API invocation metrics provided by Anypoint Platform provide? *(#91)*
    **A:** Data on past API invocations to help identify anomalies and usage patterns across various APIs.
    *Justificación:* Son métricas históricas; no dan ROI ni predicciones.

52. **Q:** What condition requires using a CloudHub Dedicated Load Balancer? *(#92)*
    **A:** When server-side load-balanced TLS mutual authentication is required between API implementations and API clients.
    *Justificación:* El Shared Load Balancer no soporta mTLS ni certificados propios; el DLB sí.

53. **Q:** An organization is implementing a Quote of the Day API that caches today's quote. What scenario can use the CloudHub Object Store via the Object Store connector to persist the cache's state? *(#93)*
    **A:** When there is one CloudHub deployment of the API implementation to three CloudHub workers that must share the cache state.
    *Justificación:* El Object Store de CloudHub es por aplicación y por región: se comparte entre los workers de la misma app, no entre regiones, business groups ni runtimes on-prem.

54. **Q:** What is a key performance indicator (KPI) that measures the success of a typical C4E that is immediately apparent in responses from the Anypoint Platform APIs? *(#94)*
    **A:** The number of API specifications in RAML or OAS format published to Anypoint Exchange.
    *Justificación:* Es un KPI del C4E que se obtiene directamente de las APIs de Exchange.

55. **Q:** What API policy would LEAST likely be applied to a Process API? *(#95)*
    **A:** JSON threat protection.
    *Justificación:* A la Process API la llaman Experience APIs internas, que ya validaron el payload externo (ver la #9).

56. **Q:** A company has created a successful enterprise data model (EDM). The company is committed to building an application network by adopting modern APIs as a core enabler of its IT operating model. At what API tiers (experience, process, system) should the company require reusing the EDM when designing modern API data models? *(#11)*
    **A:** At the process and system tiers.
    *Justificación:* Las Experience APIs se adaptan a cada consumidor; el EDM aplica a Process y System (igual que la #10).

57. **Q:** A set of tests must be performed prior to deploying API implementations to a staging environment. Due to data security and access restrictions, untested APIs cannot be granted access to the backend systems, so mocked data must be used instead. The mocked data is sufficient to entirely test the API implementations with no active connections to the backend systems. What type of tests should be used to incorporate this mocked data? *(#27)*
    **A:** Unit tests (Whitebox).
    *Justificación:* Antes de staging, sin backend y con mocks suficientes: eso es MUnit. Es la respuesta de los bancos; no la confundas con Functional.

58. **Q:** Mule applications that implement a number of REST APIs are deployed to their own subnet that is inaccessible from outside the organization. External business partners need to access these APIs, which are only allowed to be invoked from a separate partner subnet (Partner-subnet) that is accessible from the public internet. Anypoint Platform and Mule runtimes are already deployed in Partner-subnet and can already access the APIs. What is the most resource-efficient solution, with the least impact on other applications currently using the APIs? *(#43)*
    **A:** Implement (or generate) an API proxy Mule application for each of the APIs, then deploy the API proxies to the Mule runtimes.
    *Justificación:* No se tocan las implementaciones existentes (impacto mínimo) y las APIs quedan expuestas desde la subred permitida.

59. **Q:** The implementation of a Process API must change. What is a valid approach that minimizes the impact of this change on API clients? *(#88)*
    **A:** Implement required changes to the Process API implementation so that, whenever possible, the Process API's RAML definition remains unchanged.
    *Justificación:* Mientras el contrato no cambie, los clientes no se enteran del cambio.

60. **Q:** An organization wants MuleSoft-hosted runtime plane features (such as HTTP load balancing, zero downtime, and horizontal and vertical scaling) in its Azure environment. What runtime plane minimizes the organization's effort to achieve these features? *(#33)*
    **A:** Anypoint Runtime Fabric.
    *Justificación:* Runtime Fabric corre sobre Azure (AKS o VMs) y ofrece capacidades parecidas a las de CloudHub. CloudHub (1.0) solo corre en AWS.

## Parte C: Preguntas de práctica adicionales

> Preguntas nuevas que no estaban en tu cuestionario ni en las Partes A y B.

61. **Q:** The asset version 2.0.0 of the Order API is successfully published in Exchange and configured in API Manager with the Autodiscovery API ID correctly linked to the API implementation. A new GET method is added to the existing API specification, and after updates, the asset version of the Order API is 2.0.1. What happens to the Autodiscovery API ID when the new asset version is updated in API Manager?
    **A:** The API ID does not change, so no changes to the API implementation are needed for the new asset version in the API Autodiscovery global element.
    *Justificación:* El API ID pertenece a la **instancia** en API Manager, no a la versión del asset. Si solo actualizas la versión del asset (2.0.0 → 2.0.1) en esa misma instancia, el ID se queda igual y el elemento de Autodiscovery de la app sigue funcionando sin cambios. Las opciones que dicen que el ID cambia, o que hay que poner la nueva versión en el Autodiscovery, son falsas: el Autodiscovery solo guarda el API ID y el flow, no la versión.

62. **Q:** Which TWO statements are true about the technology architecture of an Anypoint Virtual Private Cloud (VPC)?
    **A:** CIDR blocks are used **+** Ports 8081 and 8082 are used. 🟡
    *Justificación:* Una Anypoint VPC se crea definiendo un bloque CIDR (su rango de IPs privadas). Según la documentación oficial, los únicos puertos expuestos al público son 8081 (HTTP) y 8082 (HTTPS); 8091/8092 solo funcionan dentro de la VPC. El balanceo de carga no lo hace la VPC, sino el Shared o el Dedicated Load Balancer de CloudHub, y el round-robin reparte entre los **workers** de una app, no entre aplicaciones distintas. **Ojo:** el banco (pass4test) marca "CIDR blocks + port 6091 desde internet", pero el puerto 6091 no aparece en la documentación de CloudHub. Si en el examen sale con estas mismas opciones, lo seguro es CIDR; para la segunda, la documentación respalda 8081/8082.

63. **Q:** An API implementation is deployed to CloudHub. What conditions can be alerted on using the default Anypoint Platform functionality, where the alert conditions depend on the API invocations to an API implementation?
    **A:** When the number of API invocations is below a threshold.
    *Justificación:* Las alertas de API en API Manager y Anypoint Monitoring se basan en métricas de las invocaciones: cantidad de peticiones (por encima o por debajo de un umbral), tiempo de respuesta, códigos de error y violaciones de políticas. No hay alertas de fábrica por geografía del cliente, por uso de TLS/SSL ni por invocar el DNS interno. **Ojo:** no la confundas con tu #72, que pregunta por el *end-to-end request processing*; ahí la respuesta es el tiempo de respuesta sobre un umbral.

64. **Q:** When should idempotency be taken into account?
    **A:** When preventing duplicate processing from multiple sent requests.
    *Justificación:* Una operación idempotente produce el mismo resultado aunque se reciba varias veces. Importa cuando hay reintentos, timeouts o clientes que reenvían la misma petición; en Mule se resuelve, por ejemplo, con el Idempotent Message Validator y un Object Store. Las peticiones concurrentes o las entidades bloqueadas son problemas de concurrencia y bloqueo, y guardar resultados previos para reutilizarlos es caché, no idempotencia.

65. **Q:** A European company has customers all across Europe, and the IT department is migrating from an older platform to MuleSoft. The main requirements are that the new platform should allow redeployments with zero downtime and deployment of applications to multiple runtime versions, provide security and speed, and utilize Anypoint MQ as the message service. Which runtime plane should the company select based on the requirements without additional network configuration?
    **A:** MuleSoft-hosted runtime plane (CloudHub).
    *Justificación:* La clave es *without additional network configuration*. CloudHub ya trae de fábrica el redeploy sin downtime, permite elegir la versión del runtime por aplicación y usa Anypoint MQ sin configurar red extra (también hay control plane y CloudHub en la región de la UE). Runtime Fabric (en VMs/Bare Metal o en Kubernetes propio) y los runtimes customer-hosted también pueden lograrlo, pero exigen montar y configurar tu propia infraestructura y red.

66. **Q:** When can CloudHub Object Store v2 be used?
    **A:** To store key-value pairs with keys up to 300 characters. 🟡
    *Justificación:* Según la FAQ oficial de Object Store v2, la clave puede medir hasta 1024 bytes en UTF-8 (unos 1024 caracteres ASCII), así que 300 caracteres caben sin problema. Cada valor puede pesar hasta **10 MB**, por eso falla la opción de payloads de más de 15 MB. Además, **Mule 4 solo soporta Object Store v2**, no v1. **Ojo:** la misma FAQ dice que el número de claves por app es ilimitado, así que la opción "unlimited number of key-value pairs" también es cierta según la documentación actual. El banco (pass4test) marca la de los 300 caracteres; en el examen elige esa.

67. **Q:** A large company wants to implement IT infrastructure in its own data center, based on the corporate IT policy requirements that data and metadata reside locally. Which combination of Mule control plane and Mule runtime plane(s) meets the requirements?
    **A:** Anypoint Platform Private Cloud Edition for the control plane and customer-hosted Mule runtimes for the runtime plane.
    *Justificación:* Los **datos** viven en el runtime plane y los **metadatos** (configuración, logs, métricas, políticas) en el control plane, así que ambos deben estar en el data center. El control plane on-prem es **Private Cloud Edition (PCE)**. Si cualquiera de los dos planos lo hospeda MuleSoft (el control plane en la nube, o CloudHub como runtime), algo sale del data center. Es la misma lógica de tu #28 del cuestionario, con otras opciones.

68. **Q:** A Mule 4 API has been deployed to CloudHub and a Basic Authentication - Simple policy has been applied to all API methods and resources. However, the API is still accessible by clients without using authentication. How is this possible?
    **A:** The Autodiscovery element is not present in the deployed Mule application.
    *Justificación:* Sin Autodiscovery, la app no queda ligada a su instancia en API Manager y el runtime no descarga ni aplica las políticas, así que el API queda abierto. La versión de Exchange en el APIkit Router no afecta las políticas. Basic Auth - Simple no usa client applications ni contratos. Y si un worker se reinicia, vuelve a descargar las políticas al arrancar.

69. **Q:** An IT Security Compliance Auditor is assessing which nonfunctional requirements (NFRs) are already being implemented to meet security measures. The Web API has: Rate-Limiting SLA, Basic Authentication - LDAP, JSON Threat Protection, and IP Allowlist policies applied. Which TWO NFRs are enforced?
    **A:** The API invocations are coming from a known subnet range **+** Username/password supported to validate login credentials.
    *Justificación:* Relaciona cada política con su NFR: **IP Allowlist** → solo se acepta tráfico de un rango de IPs o subred conocido; **Basic Auth - LDAP** → valida usuario y contraseña contra el LDAP. Las demás opciones caen por detalle: JSON Threat Protection protege contra ataques con **JSON**, no con XML (eso sería XML Threat Protection). Ninguna de las políticas enmascara datos sensibles. Y el Rate Limiting SLA limita peticiones por cliente, pero no fija un objetivo de rendimiento como "1,000 requests per second".

70. **Q:** A large lending company has developed an API to unlock data from a database server and web server. The API has been deployed to an Anypoint VPC on CloudHub 1.0. The database server and web server are in the customer's secure network and are not accessible through the public internet. The database server is in the customer's AWS VPC, whereas the web server is in the customer's on-premises corporate data center. How can access be enabled for the API to connect with the database server and the web server?
    **A:** Set up VPC peering with the AWS VPC and a VPN tunnel to the customer's on-premises corporate data center.
    *Justificación:* La regla es: **VPC peering** conecta VPC con VPC (Anypoint VPC ↔ AWS VPC del cliente), y la **VPN** (IPsec) conecta la Anypoint VPC con un data center on-premises. No existe "peering con un data center", así que las opciones que lo proponen son falsas. Un transit gateway hacia on-prem a través de la AWS VPC no es la forma estándar de conectar CloudHub 1.0 con on-premises.

71. **Q:** A business process is being implemented within an organization's application network. The architecture group proposes using a more coarse-grained application network design with relatively fewer APIs deployed compared to a more fine-grained design. Overall, which factor typically increases with a more coarse-grained design for this business process implementation and deployment?
    **A:** The complexity of each API implementation.
    *Justificación:* Con menos APIs, cada una concentra más lógica, así que su implementación es más compleja. Las demás opciones **disminuyen** con un diseño coarse-grained: hay menos assets descubribles en Exchange, menos conexiones entre APIs y menos uso de red (menos saltos). Es el espejo de tu #53 del cuestionario: fine-grained → más assets descubribles; coarse-grained → APIs más complejas.

72. **Q:** Which scenario is suited for MUnit tests instead of integration tests?
    **A:** For read-only interactions to any dependencies (such as other web APIs).
    *Justificación:* Viene casi literal del curso MCPA. En los unit tests con MUnit, las interacciones de **solo lectura** con dependencias (otras APIs) pueden invocar los endpoints reales, mientras que las de **escritura** se deben mockear. Las demás opciones describen integration tests: "no requiere conocer detalles de implementación" es black-box (los unit tests son white-box), "no se permite mockear" excluye a MUnit y SoapUI es una herramienta externa. **Ojo:** la explicación del sitio defiende la B, pero la respuesta que marca, y la del curso, es la A.

73. **Q:** An existing Quoting API is defined in RAML and used by REST clients for interacting with the quoting engine. Currently there is a resource defined in the RAML that allows the creation of quotes; however, a new requirement was just received to allow for the updating of existing quotes. Which TWO actions need to be taken to facilitate this change so it can be processed?
    **A:** Update the RAML with new method details for the update request **+** Update the API implementation to accommodate the new update request.
    *Justificación:* Agregar un método (PUT/PATCH) cambia el **contrato**, así que se actualiza el RAML, y la **implementación** debe procesar la nueva petición. Es un cambio compatible hacia atrás (versión MINOR): no hay que deprecar versiones ni recrear client applications. Las políticas son NFRs y no habilitan endpoints. Va en línea con tu #39 del cuestionario: el RAML cambia cuando cambia la estructura de la petición o la respuesta.

---

## Parte D: Temas nuevos de Mule-Arch-201 (práctica)

> 30 preguntas escritas al estilo del examen para cubrir los temas que no aparecen en los bancos: CloudHub 2.0, Flex Gateway, API Governance, automated policies, Anypoint MQ, monitoreo avanzado, Anypoint Security, entre otros. **No vienen de un banco de preguntas**: están hechas con base en tu `guia_estudio.md` (Parte VI y temas sin cobertura), la documentación de MuleSoft y el módulo de mantenimiento de la certificación en Trailhead. Responde primero y luego revisa la respuesta.

74. **Q:** A Mule application is deployed to a CloudHub 2.0 private space. External API clients must invoke it over HTTPS on port 443. The HTTP Listener connector configuration hard-codes the port value. Which port must be assigned to the HTTP Listener so the application receives the requests routed through the CloudHub 2.0 ingress?
    - a) 8082
    - b) 8092
    - c) 8081
    - d) 443

    **Respuesta:** c) 8081
    *Justificación:* En CloudHub 2.0 no existen el Shared Load Balancer ni la distinción 8082/8092. El ingress recibe en 443, termina el TLS y reenvía a la app por `${http.port}` (8081). La trampa es contestar 8082 como en CloudHub 1.0; siempre revisa si la pregunta dice 1.0 o 2.0.

75. **Q:** An organization is moving its Mule applications to a CloudHub 2.0 private space. The applications must reach systems located in several of the organization's AWS VPCs, as well as an on-premises data center already connected to AWS. The network team wants a single, highly available hub instead of managing many point-to-point connections. What should be configured?
    - a) VPC peering between the private space and each AWS VPC
    - b) A Transit Gateway attachment for the private space
    - c) A Dedicated Load Balancer with mapping rules to each VPC
    - d) A shared space with outbound firewall rules to each VPC

    **Respuesta:** b) A Transit Gateway attachment for the private space
    *Justificación:* En CloudHub 2.0, el VPC peering y Direct Connect de CloudHub 1.0 ya no se usan; los reemplaza **Transit Gateway**, que es HA por diseño y conecta varias VPCs (y on-prem a través de AWS). El DLB no existe en 2.0, y un shared space no tiene conectividad privada ni firewall configurable.

76. **Q:** A security team requires that all traffic to a Mule application deployed in a CloudHub 2.0 private space be encrypted end to end, including the hop between the platform's ingress load balancer and the application replicas. What must be done?
    - a) Enable Last-Mile Security in the deployment's ingress settings and configure the HTTP Listener for HTTPS with a certificate
    - b) Deploy a Dedicated Load Balancer with two-way TLS enabled in front of the private space
    - c) Apply a TLS enforcement policy to the API instance in API Manager
    - d) Configure the HTTP Listener on port 8092 so traffic uses the internal HTTPS channel

    **Respuesta:** a) Enable Last-Mile Security...
    *Justificación:* Por defecto, el ingress de CloudHub 2.0 termina el TLS y manda el tráfico a la réplica por HTTP. **Last-Mile Security** cifra también ese último tramo, y la app escucha en HTTPS con un certificado del TLS context del private space. El DLB y el 8092 son de CloudHub 1.0, y no hay una política de API Manager que haga esto.

77. **Q:** A System API is deployed to a CloudHub 2.0 private space. Security guidelines state that it must only be invoked by Process APIs deployed in the same private space and must never be reachable from the public internet. What is the most appropriate configuration?
    - a) Deploy the System API to a shared space and apply an IP Allowlist policy
    - b) Invoke the System API through its internal endpoint and disable its public endpoint
    - c) Configure the Process APIs to call the System API using the mule-worker-internal DNS name on port 8091
    - d) Put a Dedicated Load Balancer in front of the System API with a whitelist of the Process APIs' IPs

    **Respuesta:** b) Invoke the System API through its internal endpoint and disable its public endpoint
    *Justificación:* En un private space, cada app tiene un endpoint interno (`<app>.internal-<space-id>.<region>.cloudhub.io`), el tráfico se queda dentro del private space y la app puede no tener endpoint público. `mule-worker-internal` con 8091 es de CloudHub 1.0, y un shared space no tiene red privada.

78. **Q:** A Mule application deployed to CloudHub 1.0 uses persistent VM queues to reliably hand off messages between flows running on multiple workers. The application is being migrated to CloudHub 2.0 and must keep the same reliability. What should replace the persistent VM queues?
    - a) Persistent VM queues enabled from the Runtime Manager deployment settings
    - b) Object Store v2 with a polling flow
    - c) Anypoint MQ queues
    - d) Transient VM queues with Mule clustering enabled

    **Respuesta:** c) Anypoint MQ queues
    *Justificación:* CloudHub 2.0 **no soporta persistent VM queues**, y la documentación indica usar **Anypoint MQ** como mensajería confiable entre réplicas. El Object Store no es una cola (sería un parche con polling), y las colas VM transitorias pierden los mensajes si la réplica se reinicia.

79. **Q:** A company wants a MuleSoft-managed, container-based runtime plane where it does not manage any infrastructure. The applications require an isolated private network, static outbound IP addresses for backend allowlisting, inbound firewall rules, and a custom domain with mutual TLS. Which option meets these requirements?
    - a) CloudHub 2.0 private space
    - b) CloudHub 2.0 shared space
    - c) Anypoint Runtime Fabric on Amazon EKS
    - d) Customer-hosted Mule runtimes in a hybrid deployment

    **Respuesta:** a) CloudHub 2.0 private space
    *Justificación:* Red aislada, IPs estáticas, firewall configurable y TLS context con mTLS son características del **private space**. El shared space no tiene ninguna de ellas. Runtime Fabric e híbrido sí cumplen técnicamente, pero obligan al cliente a administrar la infraestructura, que es justo lo que no quiere.

80. **Q:** An organization runs dozens of Node.js and Java Spring Boot microservices in its own Kubernetes cluster. The architect must apply rate limiting and JWT validation policies managed from Anypoint Platform, adding minimal latency and without building or maintaining Mule proxy applications. What should be used?
    - a) A Mule API proxy application deployed for each microservice
    - b) Anypoint Flex Gateway deployed in the Kubernetes cluster (as an ingress controller or sidecar)
    - c) API Autodiscovery configured inside each microservice
    - d) Rewrite the microservices as Mule applications so policies can be embedded

    **Respuesta:** b) Anypoint Flex Gateway deployed in the Kubernetes cluster
    *Justificación:* **Flex Gateway** (ahora también llamado Omni Gateway) es un gateway ligero basado en Envoy para APIs **no Mule**, con muy baja latencia, y en Kubernetes se despliega como ingress o sidecar. Un proxy Mule por servicio funciona, pero agrega latencia y mantenimiento. El Autodiscovery solo existe dentro de un Mule runtime.

81. **Q:** A DevOps team wants every Flex Gateway configuration and API policy to be stored as code in a Git repository and applied automatically through its CI/CD pipeline. No changes should be made through a user interface. How should Flex Gateway be run?
    - a) In Connected Mode, applying policies from API Manager
    - b) As a Managed Flex Gateway on CloudHub 2.0
    - c) As a Mule API proxy with properties externalized in Git
    - d) In Local Mode, using declarative YAML configuration files

    **Respuesta:** d) In Local Mode, using declarative YAML configuration files
    *Justificación:* En **Local Mode**, la configuración y las políticas viven en archivos YAML declarativos, ideales para GitOps y CI/CD. En **Connected Mode** el gateway se administra desde la UI de Runtime Manager y API Manager. Regla rápida: "Git, CI/CD, sin UI" → Local Mode; "administrar desde API Manager" → Connected Mode.

82. **Q:** An organization wants to protect several non-Mule REST APIs with Anypoint Platform policies using a lightweight gateway. However, it has no team to install, patch, scale, or troubleshoot gateway infrastructure. What should the architect recommend?
    - a) Self-managed Flex Gateway on Linux virtual machines
    - b) A Mule API proxy deployed to customer-hosted Mule runtimes
    - c) Flex Gateway in Local Mode as a Docker container
    - d) Managed Flex Gateway, hosted by MuleSoft on CloudHub 2.0

    **Respuesta:** d) Managed Flex Gateway, hosted by MuleSoft on CloudHub 2.0
    *Justificación:* **Managed Flex Gateway** es la versión de Flex que administra MuleSoft en CloudHub 2.0 (se crea en un private space): MuleSoft se encarga de infraestructura, escalado y parches. Las demás opciones requieren que el cliente administre servidores o contenedores.

83. **Q:** Which statement about Anypoint Flex Gateway is true?
    - a) It can only protect APIs implemented as Mule applications
    - b) It requires a Mule API proxy application to enforce policies on non-Mule APIs
    - c) Custom policies can be developed in Rust and compiled to WebAssembly using the Policy Development Kit
    - d) It can only be deployed to CloudHub 2.0

    **Respuesta:** c) Custom policies can be developed in Rust and compiled to WebAssembly...
    *Justificación:* Las políticas personalizadas de Flex se escriben en **Rust/WebAssembly** con el **PDK**. Flex protege cualquier API HTTP (Mule o no), no necesita un proxy Mule y corre en Linux, Docker, Kubernetes o de forma administrada en CloudHub 2.0 o RTF.

84. **Q:** An enterprise has APIs running behind AWS API Gateway, Azure API Management, and Mule runtimes. The C4E wants all these APIs to be automatically discovered and published to a single catalog in Anypoint Exchange as part of the existing CI/CD pipelines. What should be used?
    - a) API Catalog CLI, as part of Universal API Management
    - b) API proxies created in API Manager for each non-Mule API
    - c) API Community Manager
    - d) Anypoint Visualizer

    **Respuesta:** a) API Catalog CLI, as part of Universal API Management
    *Justificación:* **Universal API Management** extiende el gobierno de Anypoint a APIs en cualquier gateway o nube. La pieza de **descubrimiento** es el **API Catalog CLI**, que publica las APIs existentes en Exchange desde CI/CD. Visualizer solo muestra apps que corren en Mule, y ACM es un portal para consumidores.

85. **Q:** A C4E wants to automatically verify that every API specification published to Anypoint Exchange follows company standards, such as naming conventions, mandatory HTTPS, and OWASP API Security Top 10 rules, and to notify API owners when an API does not comply. What should the C4E use?
    - a) Automated policies applied in API Manager
    - b) Anypoint API Governance with rulesets applied through a governance profile
    - c) Mandatory API design review meetings before publishing
    - d) A custom API policy that validates the specification at runtime

    **Respuesta:** b) Anypoint API Governance with rulesets applied through a governance profile
    *Justificación:* **API Governance** revisa las APIs contra **rulesets** (reglas de MuleSoft u otras propias publicadas en Exchange), reporta la conformidad y notifica a los dueños cuando el perfil está activo. Las automated policies son políticas de runtime, no validan especificaciones. Una revisión manual no es automática.

86. **Q:** API developers want to detect governance violations in their API specifications while they are still designing them, before publishing to Exchange. What is the recommended approach?
    - a) Run Functional Monitoring tests against the API mocking service
    - b) Apply an automated policy to the Sandbox environment
    - c) Wait for the governance dashboard to report nonconformance after publication
    - d) Add the governance rulesets as dependencies of the API specification project in Design Center or Anypoint Code Builder

    **Respuesta:** d) Add the governance rulesets as dependencies...
    *Justificación:* Es la **gobernanza en tiempo de diseño**: si agregas el ruleset como dependencia del proyecto en Design Center o Anypoint Code Builder, las violaciones aparecen mientras editas. El dashboard reporta después de publicar, y las políticas o el Functional Monitoring no validan especificaciones.

87. **Q:** A new security standard requires that every API instance in the Production environment, including API instances created in the future, enforce Client ID Enforcement and JSON Threat Protection. What is the most efficient way to meet this requirement?
    - a) Apply both policies manually to each API instance and add them to the deployment checklist
    - b) Include both policies in each API specification's RAML so they are applied at deployment
    - c) Configure both as automated policies in API Manager for the Production environment
    - d) Apply both policies to the Experience API instances only

    **Respuesta:** c) Configure both as automated policies in API Manager for the Production environment
    *Justificación:* Las **automated policies** se aplican a **todas** las instancias de un entorno, incluidas las futuras. Una política normal solo aplica a la instancia donde se configura. El RAML no aplica políticas, y hacerlo a mano no escala ni garantiza que se aplique a las APIs nuevas.

88. **Q:** An automated Rate Limiting policy has been applied to all Mule 4 API instances in an environment. An API owner wants to remove it from one specific API instance and add a Spike Control policy instead. What is true?
    - a) The API owner cannot remove the automated policy from the individual instance but can add the Spike Control policy
    - b) The API owner can remove the automated policy from the instance in API Manager
    - c) Automated policies can only be applied to Flex Gateway instances, so the policy is not enforced on Mule 4 instances
    - d) The automated policy is overridden automatically when a manual policy of the same category is added

    **Respuesta:** a) The API owner cannot remove the automated policy...
    *Justificación:* Una automated policy no se puede quitar desde una instancia individual; solo quien la administra puede cambiar su alcance o eliminarla. El dueño sí puede **agregar** más políticas. Las automated policies aplican tanto a Mule 4 como a Flex.

89. **Q:** An order-processing application publishes order status events (created, paid, shipped) to Anypoint MQ. The consumer must process the events for each order in exactly the order they were published, and duplicates must be avoided. Which Anypoint MQ feature should be used?
    - a) A standard queue with a dead-letter queue
    - b) A message exchange bound to a standard queue
    - c) A standard queue with message delivery delay
    - d) A FIFO queue

    **Respuesta:** d) A FIFO queue
    *Justificación:* Solo las colas **FIFO** garantizan el orden (por grupo de mensajes) y la entrega *exactly once*. Las colas standard son *at least once* y no garantizan el orden. El costo es un throughput menor (~300 TPS). Ojo: las colas FIFO **no** se pueden ligar a un message exchange.

90. **Q:** A Customer Created event must be delivered to three independent applications (Billing, CRM sync, and Marketing). Each application must receive its own copy and process it at its own pace. The publisher must not know about the consumers. What is the recommended Anypoint MQ design?
    - a) Publish to a message exchange bound to three standard queues, one per consuming application
    - b) Publish to a single FIFO queue consumed by all three applications
    - c) Publish three times to three FIFO queues from the publisher
    - d) Publish to one standard queue and let the three applications compete for messages

    **Respuesta:** a) Publish to a message exchange bound to three standard queues...
    *Justificación:* Para pub/sub (un evento, varios consumidores) se usa un **message exchange** ligado a una cola standard por consumidor. Si las tres apps comparten una cola, compiten y cada mensaje lo procesa solo una. Publicar tres veces acopla el publicador a los consumidores, y las FIFO no se pueden ligar a exchanges.

91. **Q:** Some messages in an Anypoint MQ standard queue repeatedly fail to be processed by the consumer because of malformed content, causing them to be redelivered again and again. What should the architect configure so these messages stop blocking processing and can be analyzed later?
    - a) Increase the acknowledgment timeout of the queue to 12 hours
    - b) A dead-letter queue of the same type, region, and environment, with a maximum number of delivery attempts
    - c) Convert the queue to a FIFO queue so the messages are delivered exactly once
    - d) Store the messages in Object Store v2 and delete them from the queue

    **Respuesta:** b) A dead-letter queue...
    *Justificación:* La **dead-letter queue (DLQ)** recibe los mensajes que no se pudieron entregar tras N intentos (10 por defecto). Debe ser del mismo tipo, región, entorno y cuenta que la cola original. Subir el timeout solo retrasa el problema, y una FIFO no arregla un mensaje mal formado.

92. **Q:** An organization uses Okta as an OpenID Connect client provider for its Production APIs, while the Sandbox environment must continue using Anypoint Platform as the client provider. How is this achieved?
    - a) Create a separate Anypoint Platform organization for each environment
    - b) Configure the client provider in each API specification's security scheme
    - c) Configure the external client provider in the root organization and associate it only with the Production environment
    - d) Apply an OAuth 2.0 policy in Sandbox and a Client ID Enforcement policy in Production

    **Respuesta:** c) Configure the external client provider in the root organization...
    *Justificación:* Los client providers externos (Okta, PingFederate, OpenAM, hasta 25) se configuran en la **organización raíz** y se **asocian a entornos**, así que cada entorno puede usar uno distinto. Aun así, los consumidores siguen solicitando acceso en Exchange (ver #20).

93. **Q:** A company wants to launch an external developer portal for partners. The portal must be fully branded, support partner self-registration and user management, and be built on Salesforce Experience Cloud using APIs already published in Anypoint Exchange. What should be used?
    - a) Anypoint Exchange private portal
    - b) API Notebooks published in Exchange
    - c) The Exchange public portal with a custom logo
    - d) API Experience Hub

    **Respuesta:** d) API Experience Hub
    *Justificación:* **API Experience Hub** (la evolución de API Community Manager) es el portal basado en **Salesforce Experience Cloud**: con marca, plantillas, registro y manejo de usuarios. El Exchange public portal solo permite una personalización ligera, y el Exchange privado es interno.

94. **Q:** An architect needs a real-time graphical view of the application network that shows how deployed Mule applications and APIs depend on each other, grouped by Experience, Process, and System layers, and which policies are applied to each API. Which Anypoint Platform capability should be used?
    - a) Anypoint Monitoring custom dashboards
    - b) Anypoint Visualizer
    - c) API Manager analytics
    - d) Anypoint Exchange dependency view

    **Respuesta:** b) Anypoint Visualizer
    *Justificación:* **Visualizer** dibuja la topología de la red de aplicaciones en tiempo real, con vistas **Architecture** (por capa), **Troubleshooting** (con métricas) y **Policies**. Los dashboards muestran métricas, no dependencias, y Exchange muestra dependencias entre assets, no el tráfico real.

95. **Q:** An operations team wants to check every five minutes, from outside the Mule runtime, that a public API returns the expected HTTP status and response payload, and to receive an alert if it does not. Which Anypoint Platform capability is designed for this?
    - a) Functional Monitoring
    - b) A "worker not responding" alert in Runtime Manager
    - c) Log points in Anypoint Monitoring
    - d) A custom metrics dashboard

    **Respuesta:** a) Functional Monitoring
    *Justificación:* **Functional Monitoring** ejecuta pruebas sintéticas periódicas contra endpoints públicos o privados y valida el estatus y el contenido de la respuesta. Es la forma oficial de monitorear una API desde fuera. Las alertas de worker no validan la respuesta, y los log points solo agregan logs.

96. **Q:** Mule applications deployed to CloudHub 2.0 must send distributed traces and audit logs to the company's existing third-party observability platform (an OpenTelemetry-compatible tool). What should be configured?
    - a) A custom logging flow in each application that calls the observability platform's REST API
    - b) Anypoint Visualizer integration
    - c) Anypoint Monitoring Telemetry Exporter
    - d) Functional Monitoring with an external endpoint

    **Respuesta:** c) Anypoint Monitoring Telemetry Exporter
    *Justificación:* El **Telemetry Exporter** envía trazas y logs de auditoría (y logs, para los destinos soportados) a herramientas externas como Splunk, Azure Monitor o plataformas compatibles con OpenTelemetry, para apps en CloudHub 2.0 y RTF. Programar un flujo de logging propio en cada app es justo lo que se quiere evitar.

97. **Q:** A company deploys its Mule applications to Anypoint Runtime Fabric. It needs WAF capabilities and Denial of Service protection that stop malicious traffic before it reaches the Mule runtimes. What should be used?
    - a) A Rate Limiting policy applied to every API instance
    - b) A JSON Threat Protection automated policy
    - c) An IP Blocklist policy applied in API Manager
    - d) Anypoint Security Edge

    **Respuesta:** d) Anypoint Security Edge
    *Justificación:* **Anypoint Security Edge** (requiere RTF y una licencia de Anypoint Security) actúa en el perímetro, con WAF, protección DoS y límites, **antes** de que el tráfico llegue al runtime. Las políticas de API Manager corren dentro del runtime, y cuando un ataque DoS llega ahí ya consumió recursos (ver #40).

98. **Q:** A healthcare company must reduce the scope of its compliance audits by ensuring that sensitive fields such as patient IDs and card numbers are replaced with values that keep the original format, so downstream systems still work and the original values can be recovered later. The APIs run on Anypoint Runtime Fabric. What should be used?
    - a) Encrypt the fields with the Mule Cryptography module before sending them downstream
    - b) The Anypoint Security tokenization service with tokenization and detokenization policies
    - c) Store the sensitive fields in Object Store v2 with encryption enabled
    - d) A Message Logging policy configured to mask the sensitive fields

    **Respuesta:** b) The Anypoint Security tokenization service...
    *Justificación:* La **tokenización** cambia los datos sensibles por tokens que **conservan el formato**, y se pueden detokenizar después; se usa para reducir el alcance de PCI/PII. Requiere RTF. El cifrado normal no conserva el formato, y enmascarar logs no protege el dato que viaja. (La documentación tiene un aviso de fin de vida para esta función, pero puede salir en el examen.)

99. **Q:** Several mobile and web teams need flexible, read-only queries over customer, order, and product data that is already exposed by existing System and Process APIs. The C4E wants to avoid building a new Process API for every new combination of fields the consumers request. What MuleSoft capability best fits this need?
    - a) A new Experience API for each consumer
    - b) An Enterprise Data Model shared by all APIs
    - c) Anypoint DataGraph
    - d) A Process API with a scatter-gather for every combination

    **Respuesta:** c) Anypoint DataGraph
    *Justificación:* **DataGraph** crea una vista unificada y consultable (GraphQL) sobre las APIs existentes, sin mover los datos, para que los consumidores pidan exactamente los campos que necesitan. Es ideal para **lecturas**; para escrituras en varios sistemas siguen siendo necesarias Process APIs con orquestación.

100. **Q:** Two API clients read the same customer record and then both submit updates. The second update must not silently overwrite the first client's changes, and the API team wants to use standard HTTP mechanisms instead of database locks. What should the API design use?
     - a) Return an ETag with the resource and require the If-Match header on PUT/PATCH, responding 412 Precondition Failed on a mismatch
     - b) Make the PUT method non-idempotent so each update creates a new version
     - c) Apply a Spike Control policy so only one request is processed at a time
     - d) Use the Cache-Control header with max-age=0 on all responses

     **Respuesta:** a) Return an ETag with the resource and require the If-Match header...
     *Justificación:* Es **concurrencia optimista** con HTTP: el `ETag` identifica la versión, y `If-Match` hace que la actualización solo proceda si la versión no cambió; si cambió, el servidor responde **412**. Spike Control no garantiza nada sobre el orden de los datos, y Cache-Control solo controla la caché.

101. **Q:** A Process API automatically retries failed calls to downstream System APIs when a timeout occurs. Which type of request should NOT be retried automatically unless the implementation provides an idempotency mechanism such as an idempotency key?
     - a) GET requests that retrieve a customer
     - b) PUT requests that replace a customer
     - c) DELETE requests that remove a customer
     - d) POST requests that create a new order

     **Respuesta:** d) POST requests that create a new order
     *Justificación:* GET, PUT, DELETE, HEAD y OPTIONS son **idempotentes**: repetirlos deja el mismo estado. **POST no lo es**: reintentarlo puede crear pedidos duplicados. Para reintentarlo de forma segura hace falta una idempotency key o un Idempotent Message Validator.

102. **Q:** A Mule application connects to a production database using a username and password. The security team requires that the password never be stored in plain text in the source repository, and that operations staff without the proper permissions cannot read it in Runtime Manager. What is the recommended approach?
     - a) Hard-code the password in the database connector configuration and restrict access to the Git repository
     - b) Store the password encrypted with the Secure Properties module and supply the decryption key at deployment as a safely hidden property
     - c) Store the password in a properties file bundled for each environment in plain text
     - d) Send the password as a header from the Experience API on every request

     **Respuesta:** b) Store the password encrypted with the Secure Properties module...
     *Justificación:* La buena práctica es **externalizar y cifrar** los secretos (Secure Properties) y entregar la llave en el despliegue como propiedad oculta (*safely hidden*), así no se ve en Runtime Manager. Esto aplica **mínimo privilegio**: solo quien lo necesita puede ver el secreto. Nunca se ponen secretos en el código ni en texto plano.

103. **Q:** An organization is migrating applications from a CloudHub 1.0 Anypoint VPC to a CloudHub 2.0 private space using MuleSoft's upgrade tooling. API clients must keep using the same vanity URLs, and the team wants to shift traffic to the CloudHub 2.0 version gradually while testing. What is true about this approach?
     - a) The CloudHub 1.0 VPC must be deleted before any application can be upgraded
     - b) A new VPN, new CIDR blocks, and new approvals are always required for the private space
     - c) The application upgrade links the CloudHub 1.0 and 2.0 applications and uses the CloudHub 1.0 load balancers to gradually shift traffic, keeping the same URLs
     - d) Applications must be redeployed manually, and clients must switch to the new CloudHub 2.0 URLs

     **Respuesta:** c) The application upgrade links the CloudHub 1.0 and 2.0 applications...
     *Justificación:* La herramienta tiene dos partes. El **VPC upgrade** clona la configuración y las conexiones de red (VPN o Transit Gateway) sin pedir nuevas aprobaciones ni nuevos CIDR, y después deja **bloqueada** la VPC de 1.0. El **application upgrade** liga la app de 1.0 con la de 2.0 y mueve el tráfico poco a poco usando los balanceadores de 1.0, así que las URLs no cambian. La VPC vieja se borra **al final**.

---

### Fuentes

- [pass4success – Mule-Arch-201](https://www.pass4success.com/salesforce/exam/mulesoft-platform-architect-i)
- [pass4future – Mule-Arch-201](https://www.pass4future.com/questions/salesforce/mulesoft-platform-architect-i)
- [exams4sure – preguntas 1–45 (págs. 1–5)](https://www.exams4sure.com/MuleSoft-Platform-Architect-I-practice-questions-1.html)
- [exams4success – vista previa](https://www.exams4success.com/mulesoft-platform-architect-i/practice-questions)
- [marks4sure – demo](https://www.marks4sure.com/MuleSoft-Platform-Architect-I-exam.html)
- [pass4test – MuleSoft Platform Architect I](https://www.pass4test.com/)
- [MuleSoft Docs – CloudHub Networking Guide (puertos 8081/8082/8091/8092)](https://docs.mulesoft.com/cloudhub/cloudhub-networking-guide)
- [MuleSoft Docs – FAQ: Object Store v2](https://docs.mulesoft.com/object-store/osv2-faq)
- [Trailhead – Maintain Your MuleSoft Platform Architect Certification (Summer '25)](https://trailhead.salesforce.com/content/learn/modules/mulesoft-platform-architect-certification-maintenance-summer-25/maintain-your-mulesoft-platform-architect-certification-for-summer-25)
- [DZone – Mule Gateway vs. Flex Gateway vs. Service Mesh](https://dzone.com/articles/mulesoft-anypoint-mule-gateway-vs-anypoint-flex-ga)