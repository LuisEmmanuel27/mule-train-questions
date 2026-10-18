# Preguntas más probables · Mule-Arch-201 (MCPA)

## [Cuestionario](cuestionario.md) · [Respuestas alternas](respuestas_alter.md)

> **Qué es esto:** 60 preguntas con su respuesta correcta y la justificación.
> - **Parte A (1–25):** preguntas del banco actual de 152 (actualizado en oct-2026) que **no** vienen en tu cuestionario.
> - **Parte B (26–60):** preguntas de tu cuestionario confirmadas en el banco actual. Entre paréntesis va su número en `cuestionario.md`.
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

26. **4 capacidades de Anypoint Platform** (#2) → **Design & Development, Runtime Execution & Hosting, Operations & Management, Consumer Engagement.**
    Es la lista oficial del curso.

27. **Retail con miles de tiendas, JDBC con archivos temporales, out-of-file-space** (#13) → **Aumentar el tamaño del worker o workers.** 🟡
    Es un problema de disco del worker: un worker más grande tiene más disco. El autoscaling se dispara por CPU o memoria, no por disco. Brainscape marca "aumentar el número".

28. **API 3.1.1 → 3.2.0, mismo endpoint: ¿qué hace el cliente?** (#15 / #44) → **Solo cambia su código si quiere usar las funciones nuevas.**
    Es un cambio MINOR: compatible hacia atrás.

29. **Solo partners conocidos con Client ID Enforcement: ¿cuándo usar un proxy?** (#17) → **Cuando la implementación no es una app Mule.**
    Sin un Mule runtime no hay autodiscovery.

30. **¿Qué hace efectivo el modelo operativo de IT?** (#26) → **Crear activos reutilizables + hacerlos descubribles (self-service) + obtener feedback activo y métricas de uso.**
    Es el ciclo completo producción → consumo → feedback.

31. **CRM-Z con 4 funciones de cliente** (#32) → **Una sola System API `customerManagement` con todas las operaciones.**
    Una API por capacidad de negocio, no una por operación ni con el nombre del backend.

32. **¿Cuándo un C4E federado en vez de centralizado?** (#34) → **Cuando el desarrollo ya está organizado en varias iniciativas o grupos independientes.**

33. **Order API con picos de 4x, CPU > 90 % y backend sano** (#35) → **Autoscaling horizontal por CPU > 70 %.**
    Agrega workers solo durante el pico; lo vertical no mejora el throughput hacia JMS.

34. **¿Qué conectores soportan transacciones?** (#37) → **Database, JMS y VM.**

35. **¿Qué NO caracteriza un integration test?** (#40) → **Que corra justo después de compilar y empaquetar.**
    Eso es un unit test; el integration test necesita la app desplegada y los sistemas accesibles.

36. **¿Cómo se combinan consumer, client e implementación?** (#48) → **El consumer crea un client, que envía invocaciones a una API, procesadas por una implementación.**

37. **Order API con mucha lógica de integración que usa Product API (relación Customer/Supplier)** (#50) → **Un anti-corruption layer en la Order API.**
    Protege el modelo interno de la Order API.

38. **¿Qué caracteriza a los unit tests de Mule?** (#52) → **Se escriben con MUnit y corren en un runtime embebido, sin conectividad externa.**

39. **Automatización con Platform APIs, CLI y Maven** (#57) → **Por defecto, la CLI y el Maven plugin NO vienen dentro del Mule runtime.**

40. **¿Qué NO se puede aplicar efectivamente con una política?** (#61) → **Protección contra DoS.** 🟡
    El ataque ya llegó al runtime; la defensa va en el borde (Edge, WAF).

41. **Reflejar Rate Limiting en el RAML** (#67) → **Agregar los headers de respuesta `X-RateLimit-*` con descripción, tipo y ejemplo.**

42. **Estado de una transacción en un proceso largo y asíncrono en varios workers** (#68) → **Persistent Object Store.**

43. **Requisito clave al usar un IdP externo para Client Management** (#70) → **Los clientes deben enviar access tokens emitidos por ese mismo IdP.**

44. **¿Dónde se define y aplica una política?** (#73) → **En API Manager, para una instancia específica, y solo se aplica a esa instancia.**

45. **FQDNs en el Shared Worker Cloud** (#76) → **Se determinan por el nombre de la app, sin importar la región.** 🟡
    Es lo que marcan pass4success y examcatalog.

46. **System API sobre un backend con problemas de escalabilidad (opciones sin Spike Control)** (#79) → **SLA-based Rate Limiting.**

47. **Runtimes customer-hosted con el control plane de MuleSoft (híbrido)** (#80) → **Las apps siguen corriendo aunque no puedan comunicarse con el control plane.**

48. **¿Para qué sirve auto-discovery?** (#83) → **Hace que API Manager conozca la implementación para que pueda aplicar políticas.**

49. **No poner timeout a un downstream sin SLA** (#84) → **No se puede ofrecer un SLA para la API upstream.**

50. **Invocar una API en STAGING con Client ID Enforcement** (#86) → **Con el client ID y secret obtenidos en Exchange para la instancia de STAGING.**

51. **¿Qué dan las métricas de invocación?** (#91) → **Datos de invocaciones pasadas para identificar anomalías y patrones de uso.**

52. **¿Cuándo se necesita un Dedicated Load Balancer?** (#92) → **Para TLS mutuo con balanceo del lado del servidor.**

53. **Quote of the Day con caché en CloudHub Object Store** (#93) → **Un despliegue en CloudHub con 3 workers que comparten el estado.**
    El Object Store es por app y por región.

54. **KPI del C4E visible en las APIs de la plataforma** (#94) → **El número de especificaciones RAML/OAS publicadas en Exchange.**

55. **Política MENOS probable en una Process API** (#95) → **JSON Threat Protection.**
    Ya se aplicó en la capa Experience (ver la #9).

56. **EDM exitoso: ¿en qué capas se reutiliza?** (#11) → **Process y System.**

57. **Pruebas antes de staging, sin backend y con datos mockeados suficientes** (#27) → **Unit tests (Whitebox).**
    Es MUnit con mocks; es la respuesta de los bancos.

58. **Partners acceden desde Partner-subnet con el menor impacto posible** (#43) → **Un API proxy por cada API, desplegado en los runtimes de Partner-subnet.**

59. **Minimizar el impacto en los clientes cuando cambia una Process API** (#88) → **Cambiar la implementación manteniendo el RAML sin cambios siempre que se pueda.**

60. **Funciones de un runtime plane hospedado por MuleSoft, pero en Azure** (#33) → **Anypoint Runtime Fabric.**

---

### Fuentes

- [pass4success – Mule-Arch-201](https://www.pass4success.com/salesforce/exam/mulesoft-platform-architect-i)
- [pass4future – Mule-Arch-201](https://www.pass4future.com/questions/salesforce/mulesoft-platform-architect-i)
- [exams4sure – preguntas 1–45 (págs. 1–5)](https://www.exams4sure.com/MuleSoft-Platform-Architect-I-practice-questions-1.html)
- [exams4success – vista previa](https://www.exams4success.com/mulesoft-platform-architect-i/practice-questions)
- [marks4sure – demo](https://www.marks4sure.com/MuleSoft-Platform-Architect-I-exam.html)
- [MuleSoft Docs – CloudHub Networking Guide (puertos 8081/8082/8091/8092)](https://docs.mulesoft.com/cloudhub/cloudhub-networking-guide)
