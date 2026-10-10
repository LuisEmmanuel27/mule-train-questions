# Respuestas alternas cuestionario MCPA

## [Cuestionario](cuestionario.md) · [Respuestas originales](respuestas.md)

> **Criterio usado:** para cada pregunta se prioriza la respuesta que **marca el examen** (la que aparece de forma consistente en los bancos de práctica más citados: ExamTopics, pass4success, examcollection, examcatalog, certifhub, brainscape, marks4sure) y, cuando hay empate o duda, la "lógica MuleSoft" del curso oficial *Anypoint Platform Architecture: Application Networks*. Esa lógica a veces no coincide con lo que harías en un proyecto real; cuando pasa, se indica.
>
> **Leyenda de confianza:**
> - 🟢 Alta: los bancos coinciden y la lógica del curso lo respalda.
> - 🟡 Media: es la respuesta que más se repite, pero hay debate en la comunidad o la redacción es ambigua.
> - 🔴 Cambio: difiere de `respuestas.md`.

---

## Resumen rápido

| # | respuestas.md | respuestas_alter | Estado |
|---|---|---|---|
| **27** | iii. Functional (Blackbox) | **iv. Unit tests (Whitebox)** | 🔴 Cambio |
| 12 | iv. Spike control | iv. Spike control | 🟡 Debatida (algunos dicen Rate limiting) |
| 13 | iii. Aumentar tamaño del worker | iii. Aumentar tamaño del worker | 🟡 Debatida (algunos dicen aumentar número) |
| 21 | iv. API Consumer | iv. API Consumer | 🟡 Debatida |
| 61 | i. DoS | i. DoS | 🟡 Debatida |
| 71 | iv. 8082 | iv. 8082 | 🟡 Debatida |
| 76 | ii. Nombre de la app, sin importar región | ii. | 🟡 Debatida (la comunidad está dividida con la iv) |
| 89 | ii. Alerta "worker not responding" | ii. | 🟡 Debatida (muchos defienden el heartbeat externo) |

Las demás coinciden con tus respuestas y tienen confianza alta.

---

1. **ii. TRUE** 🟢
   La idea central del curso es que las APIs se tratan como **productos** y su consumo debe ser **self-service** (descubribles en Exchange, con documentación, mocking y solicitud de acceso). MuleSoft acepta que esto cueste más al principio porque se recupera con la reutilización.

2. **iii. API Design and Development, API Runtime Execution and Hosting, API Operations and Management, API Consumer Engagement** 🟢
   Son las 4 capacidades de plataforma que lista el curso. Versionado y deprecación son prácticas, no capacidades de plataforma.

3. **i. & iii. API Operations and Management + API Consumer Engagement** 🟢
   El curso las agrupa así: *API implementations* → Design & Development + Runtime Execution & Hosting; *APIs and API invocations* → Operations & Management + Consumer Engagement.

4. **iii. (C)** App Developers → Experience; LOB IT → Process; Central IT → System 🟢
   Central IT conoce y controla los sistemas de registro; LOB IT conoce los procesos de su línea de negocio; los desarrolladores de apps están más cerca del canal.

5. **iii. System Layer** 🟢
   Las System APIs "desbloquean" los sistemas core/legacy y aíslan a los consumidores de su complejidad.

6. **ii. The CloudHub shared load balancer** 🟢
   Ya viene incluido (no tiene costo extra), hace round-robin entre los 3 workers y aguanta picos. El DLB o un LB propio cuestan más; un proxy no balancea; el autoscaling no es un componente de balanceo.

7. **iii. (C)** 🟢
   Cerrar el *IT delivery gap* **sin** aumentar la capacidad de IT y consumir activos al ritmo en que se producen. La A espera a "terminar todos los activos" (anti-patrón) y la B aumenta la capacidad de IT (lo contrario del modelo).

8. **i.** 🟢
   El curso insiste en que API-led no es solo una arquitectura de 3 capas ni una tecnología: también es una forma de **organizar personas y procesos** (el modelo operativo de IT).

9. **i. Invocar en paralelo primario y DR, y usar SOLO la primera respuesta** 🟢
   El objetivo es el **menor tiempo de respuesta posible**, no ahorrar recursos. Lanzar ambas y quedarse con la más rápida minimiza la latencia. Hacer merge (ii) no tiene sentido porque ambas devuelven lo mismo, y las opciones secuenciales (iii, iv) agregan latencia.

10. **i. TRUE** 🟢
    La frase *"bends but does not break"* es casi textual del curso para describir la red de aplicaciones como recomponible.

11. **iii. At the process and system tiers** 🟢
    Confirmado en examcollection y brainscape. Las Experience APIs se adaptan a cada consumidor (móvil, web), así que no se les obliga a usar el EDM. Process y System sí deben reutilizarlo cuando existe un EDM exitoso.

12. **iv. Spike control** 🟡
    Es la que dan los bancos (brainscape). La lógica del curso: *Rate limiting* sirve para cuotas/consumo (rechaza al pasar el límite), mientras que *Spike control* está pensado para **proteger el backend**: suaviza las ráfagas encolando y reintentando las peticiones en lugar de rechazarlas de inmediato. **Ojo:** en otros foros se defiende *Rate limiting* porque el límite es fijo (500 rps). Si en el examen aparece literalmente "protect the backend from overload", ve con Spike control.

13. **iii. Increase the size of the CloudHub worker(s)** 🟡
    El error es **out-of-file-space**: falta disco temporal en el worker. Los workers más grandes tienen más disco (y más memoria). El autoscaling (i, ii) no aplica porque se dispara por CPU/memoria, no por disco, y además el problema es intermitente. **Debate:** algunos bancos (brainscape) marcan "Increase the number of CloudHub workers", con el argumento de que repartir las peticiones concurrentes reduce los archivos temporales por worker. La lectura más directa del síntoma (disco) favorece aumentar el **tamaño**.

14. **iv. The remaining capacity allowed by the API implementation** 🟢
    `X-RateLimit-Limit`, `X-RateLimit-Remaining` y `X-RateLimit-Reset` informan la cuota, lo que queda y cuándo se reinicia.

15. **iii. The API client code only needs to be changed if it needs to take advantage of the new features** 🟢
    3.1.1 → 3.2.0 es un cambio **MINOR**: compatible hacia atrás según semver. No hace falta regresión completa ni correr versiones en paralelo.

16. **iv. Separate Anypoint VPCs for non-prod and prod** 🟢
    Es la recomendación estándar: una VPC por tipo de entorno, cada una conectada (VPN/peering) a su red de backend correspondiente. Los firewalls (ii) ayudan, pero sin VPC los workers compartidos no tienen IPs controlables.

17. **iv. A Non-Mule application** 🟢
    Una app no Mule no puede usar autodiscovery (no corre en un Mule runtime), así que se necesita un **API proxy** para aplicar políticas.

18. **i. Bundle properties files para cada entorno + promover con Anypoint CLI o Anypoint Platform REST APIs** 🟢
    Es la que dan los bancos. Se externalizan las propiedades por entorno (`config-${env}.yaml`) y la promoción se automatiza con CLI/APIs (CI/CD). API Manager, Exchange y las políticas no gestionan propiedades de despliegue.

19. **i. Primario + timeout y retry; si sigue fallando → DR** 🟢
    El DR solo ofrece el 20 % del rate limit, así que no conviene mandarle tráfico en paralelo ni usarlo al primer fallo. Primero se reintenta contra el primario y el DR queda como último recurso. La iv es incorrecta porque invoca una copia del *process* API, no del system API.

20. **iii. Process Layer** 🟢
    La orquestación y la lógica de negocio viven en Process.

21. **iv. API Consumer** 🟡
    En la terminología MuleSoft, el **API consumer** (persona, equipo u organización) es quien solicita acceso en Exchange y registra la client application. El **API client** es el software que hace las llamadas. Es coherente con la pregunta 25 ("API Consumer requests access…"). Hay quien marca "API Client", pero la distinción consumer/client del curso apunta a Consumer.

22. **i. At the API proxy** 🟢
    Cuando hay proxy, las políticas se aplican en el proxy (que es donde está el gateway con autodiscovery). La implementación detrás no las aplica.

23. **iii. When a new required field is added to the method called by the API client** 🟢
    Un campo **requerido** nuevo rompe a los clientes existentes (sus peticiones dejan de ser válidas). Agregar métodos o recursos es compatible. *(Cambiar el tipo de respuesta también es breaking, pero los bancos marcan la iii.)*

24. **iii. Bounded context para la capa System cercano al backend + anti-corruption layer entre System y Process** 🟢
    Process y Experience ya comparten un bounded context; el backend tiene otro modelo. Lo correcto es aislar el modelo del backend en la capa System y traducir con un ACL.

25. **ii. Consumer solicita acceso → Client implementa la llamada → API enruta → API Implementation** 🟢
    Confirmado en examcollection.

26. **ii. Crear activos reutilizables + hacerlos descubribles (self-service) + obtener feedback activo y métricas de uso** 🟢
    Es el ciclo completo producción → consumo → feedback del modelo operativo.

27. **iv. Unit tests (Whitebox)** 🔴 *(en respuestas.md: iii. Functional)*
    **Esta es la principal diferencia.** examcollection, brainscape y marks4sure coinciden en **Unit tests (Whitebox)**. La lógica que espera el examen: las pruebas se hacen **antes de desplegar a staging**, sin conexión a backends y con datos mockeados *suficientes para probar la implementación por completo*. Eso describe **MUnit**, que corre en un Mule runtime embebido con *mocks* de los conectores. Las pruebas funcionales (blackbox) en el modelo MuleSoft se hacen contra la app desplegada, normalmente con dependencias reales. Tu guía (7.6) lo marca como "exam trap", pero los bancos de preguntas dicen lo contrario en **esta** pregunta concreta. Recomendación: en el examen, ve con **Unit tests**.

28. **i. Customer-hosted runtime plane (manual) + customer-hosted control plane** 🟢
    Si **todos** los datos y **metadatos** deben quedarse dentro del firewall, el control plane también tiene que ser on-prem → **Anypoint Platform PCE**.

29. **ii. 4.0.0** 🟢
    Cambiar la zona horaria cambia el **significado** del dato aunque el formato sea igual → breaking change → versión MAJOR.

30. **i. Drive consumption as much as production of assets** 🟢
    Confirmado en examcollection.

31. **i. The credentials provided by the IdP for identity management** 🟢
    Confirmado en brainscape. Anypoint CLI se autentica como **usuario** (identity management), no como cliente OAuth de client management.

32. **i. Una sola System API `customerManagement` con todas las operaciones como recursos** 🟢
    Una API por **capacidad o entidad de negocio**, no una por operación. Además, poner "CRMZ" en el nombre acopla la API al backend.

33. **i. Anypoint Runtime Fabric** 🟢
    RTF corre sobre Azure (AKS) o VMs y da balanceo, zero-downtime y escalado horizontal/vertical, parecido a CloudHub. CloudHub (1.0) solo corre en AWS.

34. **iii. When development is already organized into several independent initiatives or groups** 🟢
    Un C4E federado encaja cuando ya existen equipos o LOBs independientes.

35. **iv. Horizontal autoscaling por CPU > 70 %** 🟢
    Confirmado en examcollection. El cuello de botella es CPU (el backend responde bien) y los picos son ocasionales. Agregar workers solo durante el pico es lo más eficiente, mejor que subir el tamaño de forma permanente.

36. **ii. OpenAPI Specification (OAS)** 🟢
    Confirmado en examcollection. WSDL es para SOAP, YAML es un formato (no un IDL) y AsyncAPI es para APIs asíncronas o de eventos.

37. **i. Database, JMS, VM** 🟢
    Son los conectores transaccionales (single resource y XA). HTTP, File y SFTP no soportan transacciones.

38. **i. HTTP/1.x** 🟢
    Las políticas de API Manager funcionan sobre HTTP/HTTPS estándar, no sobre TCP, WebSocket ni gRPC.

39. **i. Cuando cambia la estructura de request o response** 🟢
    El RAML es el contrato. Cambios internos (backend, versión del runtime, rendimiento) no lo modifican.

40. **ii. The test runs immediately after the Mule application has been compiled and packaged** 🟢
    Eso describe un unit test. El integration test necesita la app **desplegada** y los sistemas accesibles.

41. **iii. Los workers se distribuyen aleatoriamente entre las AZs de la región** 🟢
    CloudHub reparte los workers entre AZs para dar alta disponibilidad; no se elige la AZ.

42. **iii. When a pragmatic approach with only limited isolation from the backend system is deemed appropriate** 🟢
    Imitar el modelo del backend es una decisión pragmática que acepta menos aislamiento.

43. **i. Un API proxy por API desplegado en los runtimes de Partner-subnet** 🟢
    Confirmado en examcollection. No toca las implementaciones existentes (impacto mínimo) y expone las APIs desde la subred permitida.

44. **iv. The API client code ONLY needs to be changed if it needs to take advantage of new features** 🟢
    Igual que la 15 (cambio MINOR).

45. **iii. Control plane y runtime plane en la misma jurisdicción** 🟢
    El control plane también maneja datos y metadatos; para cumplir con la residencia de datos (GDPR, etc.) ambos planos deben estar en la región (por ejemplo, control plane EU + runtime EU).

46. **ii. Cuando debe ser accesible dentro de una subred restringida de la red del cliente sin acceso público** 🟢
    Ese es el caso de uso de la VPC (conectividad privada con VPN o peering). Las demás no lo requieren.

47. **iv. Combinación de CloudHub y runtimes on-prem manuales, gestionados por el control plane hospedado por MuleSoft** 🟢
    Modelo híbrido: CloudHub para SaaS y runtimes on-prem para los sistemas de la intranet. PCE no es necesario porque no hay requisito de control plane on-prem.

48. **iii. El consumer crea un client que envía invocaciones a una API, procesadas por una implementación** 🟢
    Es la definición del curso.

49. **i. Buscar en Exchange una fallback API existente e invocarla además de la Order API** 🟢
    Es la que dan los bancos: reutilizar activos (Exchange) y que el fallback sea **otra** API independiente. Una segunda entrada en API Manager (ii) sigue apuntando a la misma Order API caída.

50. **iii. Anti-corruption layer en la Order API** 🟢
    Confirmado en examcollection y brainscape. La Order API tiene mucha lógica de integración: conviene proteger su modelo interno traduciendo el de Product API con un ACL.

51. **i. Un worker falla con out-of-memory** 🟢
    Confirmado en marks4sure. Hay **varios** workers: el load balancer redirige el tráfico a los sanos. Las otras opciones (sin API Manager en el despliegue inicial, caída de región, backend inaccesible) sí causan una caída del servicio.

52. **iv. MUnit en un Mule runtime embebido sin conectividad externa** 🟢
    Es la definición de unit test en Mule.

53. **ii. A higher number of discoverable API-related assets** 🟢
    Granularidad fina = más APIs = más activos descubribles. A cambio hay más conexiones y más latencia.

54. **i. Approve the client application request for the chosen SLA tier** 🟢
    Los SLA tiers pueden configurarse con **aprobación automática**. Lo demás lo hace el desarrollador.

55. **i. Proveer resiliencia adicional que aísla a los clientes de fallas prolongadas del backend** 🟢
    Si el backend cae por mucho tiempo, las APIs de encima también caen; API-led no da esa resiliencia por sí mismo.

56. **iii. Cuando la regulación exige procesar on-prem TODO dato, incluidos los metadatos** 🟢
    Solo PCE o PCF tienen el control plane en la infraestructura del cliente.

57. **iii. Por defecto, Anypoint CLI y el Mule Maven plugin NO están incluidos en el Mule runtime** 🟢
    Las demás son falsas: las APIs automatizan mucho más que CloudHub, no se aplican políticas a las APIs de la plataforma y no hay permisos separados para la CLI.

58. **iii. No hay timeout posible que cumpla; hay que negociar otro SLA o usar una API alternativa** 🟢
    El p95 del primer downstream (1000 ms) ya supera el p99 del upstream (800 ms). Con un timeout de 100 ms (la mediana) falla la mitad de las llamadas. No hay forma de cumplir.

59. **iv. IP whitelist** 🟢
    Las apps móviles de consumidores tienen IPs dinámicas y desconocidas.

60. **ii. Cada API moderna se trata como producto, diseñada para una audiencia concreta** 🟢
    Principio "API as a product".

61. **i. Guarding against Denial of Service attacks** 🟡
    Para el curso, una política se ejecuta **dentro** del Mule runtime: cuando un ataque DoS llega ahí, ya consumió recursos. La defensa efectiva contra DoS está en el borde (Anypoint Security Edge, WAF o CDN). Las credenciales a prueba de manipulación (JWT/OAuth), el logging (Message Logging) y la protección del backend (Spike control) sí pueden hacerse con políticas. *Algunos marcan la ii, pero la i es la más repetida.*

62. **i. Documentar la API con un activo fácil de consumir, como RAML** 🟢
    Imitar el backend o exponer detalles técnicos no son buenas prácticas, y un EDM por cada backend no tiene sentido.

63. **i. Basic Authentication – LDAP contra Active Directory** 🟢
    Sin presupuesto para más componentes (no hay servidor OAuth). AD ya existe como fuente LDAP y se puede restringir por grupo. Client ID no identifica usuarios y la lista blanca de IPs no restringe por grupo.

64. **iii. API Notebooks en Exchange** 🟢
    Eran el entorno "code-centric" ejecutable de Exchange. *(Hoy están deprecados, pero el examen todavía los usa.)*

65. **i. SLA-based rate limiting con un tier por tipo de cliente** 🟢
    Los límites por tipo de cliente equivalen a SLA tiers asignados a cada client app.

66. **iv. JSON threat protection** 🟢
    Protege contra payloads JSON maliciosos (profundidad, tamaño de strings o arrays) sin necesidad de autenticación.

67. **iv. Agregar los headers `X-RateLimit-*` en las respuestas del RAML** 🟢
    Así se refleja la política en el contrato (ver también la 14).

68. **iii. Persistent Object Store** 🟢
    Es la solución nativa compartida entre workers. Redis no viene incluido, y WeakHashMap y los archivos son locales a cada worker.

69. **iv. GET, OPTIONS, HEAD** 🟢
    Métodos seguros y cacheables en la lógica del examen. POST, PUT y DELETE modifican estado.

70. **iii. Los clientes deben enviar tokens emitidos por ese mismo IdP** 🟢
    Con client management externo, la política OAuth valida contra ese IdP.

71. **iv. 8082** 🟡
    En CloudHub, la app escucha en `${https.port}` = **8082**. Llamando directo al worker (`mule-worker-<app>.<region>.cloudhub.io:8082`) se evita el shared LB público (443) y el tráfico se queda en la red de AWS. 8091/8092 son puertos internos de **VPC**, y 8091 además es HTTP, no HTTPS. *Hay debate porque algunos razonan con 8092, pero no está entre las opciones.*

72. **iii. Cuando el tiempo de respuesta supera un umbral** 🟢
    Es la única condición que depende del procesamiento **end-to-end** de la implementación (alerta de response time en API Manager o Monitoring).

73. **ii. Se define en API Manager para una instancia concreta y solo se aplica a esa instancia** 🟢
    Confirmado en pass4success.

74. **ii. Permitir que las System APIs devuelvan datos que hoy no requieren las Process o Experience APIs** 🟢
    Las System APIs se diseñan para reutilizarse más allá del caso actual. Las demás opciones son anti-patrones (personalizar en Process, exactamente 1 API por capa, prohibir Process → Process).

75. **iii. Los certificados SSL que usa la app para exponer HTTPS** 🟢
    Con el shared LB, MuleSoft gestiona su propio certificado `*.cloudhub.io`, pero el keystore del listener HTTPS de la app lo gestiona la app.

76. **ii. Los FQDNs se determinan por el nombre de la app, SIN IMPORTAR la región** 🟡
    Es la respuesta sugerida en pass4success y examcatalog. *La comunidad está dividida* (algunos votan la iv: "app name + organization"). Técnicamente el FQDN regional incluye la región, pero el examen marca la ii porque el nombre de la app es globalmente único y es lo que determina el DNS.

77. **i. Varios bounded context data models** 🟢
    Confirmado en certifhub. Las LOBs están aisladas, tienen presupuestos separados y comparten pocas entidades: un EDM central no es viable.

78. **iv. XML over HTTP** 🟢
    Para el curso, una API "válida" en una red de aplicaciones es una API web basada en HTTP.

79. **ii. SLA-based rate limiting** 🟢
    De las opciones, es la única que limita volumen. (Spike control sería ideal, pero no aparece.)

80. **iii. Las implementaciones siguen corriendo aunque no puedan comunicarse con el control plane** 🟢
    El runtime funciona de forma autónoma. Es el runtime el que inicia la conexión con el control plane (no al revés), el shared LB solo existe en CloudHub y Runtime Manager no crea nodos.

81. **i. Que Marketing interactúe con el mocking service desde el API Console** 🟢
    Ese es el propósito del diseño temprano: feedback rápido sin implementar nada.

82. **i. La visibilidad de las instancias de la API debe ser pública** 🟢
    Es la que dan los bancos: para que una instancia aparezca en el portal público, su visibilidad debe ser pública.

83. **i. Hace que API Manager conozca la implementación y pueda aplicar políticas** 🟢

84. **i. No se puede ofrecer un SLA para la API upstream** 🟢
    Sin timeout y con un downstream sin SLA, el upstream no puede garantizar tiempos.

85. **iv. Del Mule runtime, sin importar el modelo de despliegue** 🟢
    Es la respuesta en examcatalog. Los datos de monitoreo y alertas los genera el runtime (agentes de monitoring o API gateway) en cualquier modelo.

86. **iii. El client ID y secret obtenidos en Exchange para la instancia de la API en STAGING** 🟢
    Se obtienen al registrar la client app y solicitar acceso a esa instancia.

87. **iii. Experience APIs separadas para móvil y web, una Process API común y System APIs separadas para BD y CRM** 🟢
    Es la estructura API-led de libro.

88. **iii. Cambiar la implementación manteniendo el RAML sin cambios siempre que se pueda** 🟢
    Confirmado en examcollection.

89. **ii. Alerta "Worker not responding" en Runtime Manager** 🟡
    Es la respuesta en certifhub: es la alerta nativa que detecta de inmediato que el worker dejó de responder. *Debate:* muchos defienden el heartbeat externo (i) porque detecta también fallos que no son del worker. Para el examen, ve con la ii.

90. **ii. El tráfico entre la VPC y los sistemas on-prem puede quedarse en una red privada** 🟢
    Con VPN o Direct Connect. El rango de IPs lo elige el cliente, una VPC puede servir a varios entornos y el peering solo funciona entre VPCs de AWS.

91. **iii. Datos de invocaciones pasadas para identificar anomalías y patrones de uso** 🟢
    Son métricas históricas, no ROI ni predicciones.

92. **iv. Cuando se requiere TLS mutuo con balanceo del lado del servidor** 🟢
    El shared LB no soporta mTLS ni certificados propios; el DLB sí.

93. **iv. Un despliegue en CloudHub con 3 workers que comparten el estado** 🟢
    El Object Store de CloudHub es por aplicación (y por región): se comparte entre los workers de la **misma** app, no entre regiones, business groups ni runtimes on-prem.

94. **iv. El número de especificaciones RAML/OAS publicadas en Exchange** 🟢
    Es un KPI del C4E que se obtiene directamente de las APIs de la plataforma (Exchange).

95. **iv. JSON threat protection** 🟢
    Confirmado en brainscape y collegesidekick. La Process API la llaman Experience APIs internas, que ya validan el payload de los clientes externos. Client ID, rate limiting y circuit breaker sí son comunes en Process.

---

### Fuentes consultadas

- [pass4success – FQDNs en CloudHub (Q47)](https://www.pass4success.com/salesforce/discussions/exam-mulesoft-platform-architect-i-topic-5-question-47-discussion)
- [pass4success – Dónde se define una política (Q48)](https://www.pass4success.com/salesforce/discussions/exam-mulesoft-platform-architect-i-topic-3-question-48-discussion)
- [certifhub – Alerta "worker not responding"](https://blog.certifhub.com/?p=901925)
- [certifhub – Bounded Context Data Models](https://blog.certifhub.com/?p=901928)
- [examcollection – MuleSoft Platform Architect I](https://www.examcollection.us/exam/MuleSoft-Platform-Architect-I-question-answer.html)
- [examcatalog – MCPA Level 1](https://www.examcatalog.com/exam/mulesoft/mcpa-level-1/)
- [brainscape – MCPA Level 1 flashcards](https://www.brainscape.com/flashcards/mulesoft-certified-platform-architect-le-13807618/packs/17277120)
- [marks4sure – MCPA Level 1](https://www.marks4sure.com/mcpa-level-1-mulesoft-certified-platform-architect-level-1-questions.html)
- [collegesidekick – Mule-Arch-201 Q&A](https://www.collegesidekick.com/study-docs/28199132)
- [MuleSoft Docs – Spike Control](https://docs.mulesoft.com/gateway/latest/policies-included-spike-control)
