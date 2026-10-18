# Preguntas más probables · Mule-Arch-201 (MCPA)

## [Cuestionario](cuestionario.md) · [Respuestas alternas](respuestas_alter.md)

> **Qué es esto:** 60 preguntas con su respuesta correcta y la justificación.
> - **Parte A (1–25):** preguntas del banco actual de 152 (actualizado en oct-2026) que **no** vienen en tu cuestionario.
> - **Parte B (26–60):** preguntas de tu cuestionario confirmadas en el banco actual.
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
    **A:** Implement a system API named customerManagement which has all the functionalities wrapped in it as various operations/resources.
    *Justificación:* Una API por capacidad o entidad de negocio, no una por operación. Además, poner "CRMZ" en el nombre acopla la API al backend.

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

---

### Fuentes

- [pass4success – Mule-Arch-201](https://www.pass4success.com/salesforce/exam/mulesoft-platform-architect-i)
- [pass4future – Mule-Arch-201](https://www.pass4future.com/questions/salesforce/mulesoft-platform-architect-i)
- [exams4sure – preguntas 1–45 (págs. 1–5)](https://www.exams4sure.com/MuleSoft-Platform-Architect-I-practice-questions-1.html)
- [exams4success – vista previa](https://www.exams4success.com/mulesoft-platform-architect-i/practice-questions)
- [marks4sure – demo](https://www.marks4sure.com/MuleSoft-Platform-Architect-I-exam.html)
- [MuleSoft Docs – CloudHub Networking Guide (puertos 8081/8082/8091/8092)](https://docs.mulesoft.com/cloudhub/cloudhub-networking-guide)
