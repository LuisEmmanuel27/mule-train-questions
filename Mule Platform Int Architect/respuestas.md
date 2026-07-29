# Respuestas cuestionario MCPA

1. ii. - **Tema de la guía:** 1.5 "APIs as Products" y 2.5 "Production and Consumption of Reusable Assets"
2. iii. - **Tema de la guía:** No está explícitamente cubierto con este desglose exacto de "4 capacidades" en la guía, pero se relaciona con varias secciones combinadas:

   * **4.1** (Designing & Sharing APIs) → API Design and Development
   * **2.7** (Control Plane and Runtime Plane) → API Runtime Execution and Hosting
   * **5.1** (API Manager Overview) → API Operations and Management
   * **1.5** (APIs as Products) → API Consumer Engagement (developer experience, discoverability)
3. i. & iii. - **Tema de la guía:**

   * **5.1** (API Manager Overview) → gestión de instancias, políticas, clientes → "API Operations and Management"
   * **5.9 / 5.10** (Client Management / API Client Applications and Contracts) → relación con consumidores → "API Consumer Engagement"
4. iii. - **Tema de la guía:** Se relaciona con  **3.1 (System APIs)** ,  **3.4 (Process APIs)** , **3.5 (Experience APIs)** y  **2.1 (Center for Enablement)** , aunque el mapeo específico de "ownership" por rol organizacional no está detallado textualmente en la guía.

   **Razonamiento (modelo típico de MuleSoft):**

   * **Central IT** → suele tener control y conocimiento profundo de los sistemas de registro (SAP, ERP, mainframes), por lo que es el dueño natural de las **System APIs** (estabilidad, gobernanza centralizada).
   * **LOB IT (Line of Business IT)** → conoce las reglas de negocio específicas de su unidad, por lo que orquesta y posee las  **Process APIs** , que combinan lógica de negocio reutilizable.
   * **App Developers** → están más cerca del canal/consumidor final (mobile, web), por lo que poseen las  **Experience APIs** , adaptadas a cada experiencia de usuario.
5. iii. - **Tema de la guía:** Sección **3.1 (System APIs)**
6. ii. - **Tema de la guía:** Secciones **8.5 (Shared Load Balancer vs Dedicated Load Balancer)** y **8.3 (Worker Sizing and Scaling)**
7. iii. -**Tema de la guía:** Sección **2.4 (Modern IT Operating Model)** y **2.5 (Production and Consumption of Reusable Assets)**
8. i. - **Tema de la guía:** Secciones  **1.2 (Application Networks)** , **2.4 (Modern IT Operating Model)** y **3.7 (Separation of Responsibilities Across API Layers)**
9. i. - **Tema de la guía:** Se relaciona con **9.2 (Resilience Patterns)** y  **9.4 (Performance Optimization Techniques - Parallel Processing)** , aunque este patrón específico (invocar en paralelo primary+DR y quedarse con la primera respuesta) no está explícitamente detallado en la guía.
10. i. - **Tema de la guía:** Sección **1.2 (Application Networks)** y **1.4 (Composability and Reuse)**

11. iii. - **Tema de la guía:** Sección **4.4 (Bounded Contexts - Enterprise Data Models vs Bounded Context Data Models)**
12. iv. - **Tema de la guía:** Sección **5.6 (API Policies - Traffic Management Policies)**
13. iii. - **Tema de la guía:** Secciones **8.3 (Worker Sizing and Scaling)** y **8.7 (Identifying and Avoiding Single Points of Failure)**
14. iv. - **Tema de la guía:** Se relaciona con **5.6 (API Policies - Traffic Management Policies: Rate Limiting)** y **5.7 (API Specification Changes to Reflect Applied Policies)**
15. iii. - **Tema de la guía:** Sección **4.3 (Semantic Versioning)**
16. iv. - **Tema de la guía:** Secciones  **8.2 (CloudHub Deployment Models - VPC)** , **8.4 (CloudHub Networking)** y **7.1 (Environment Separation)**
17. iv. - **Tema de la guía:** Secciones **5.3 (Auto-Discovery vs API Proxy)** y **5.4 (Choosing Between Auto-Discovery and API Proxy)**
18. i. - **Tema de la guía:** Secciones **7.2 (Externalized Configuration)** y **7.3 (CI/CD Pipelines)**
19. i. - **Tema de la guía:** Relacionado con **9.2 (Resilience Patterns: Retry, Timeout, Fallback)** y  **8.7/8.8 (Single Points of Failure, Reliability by Region)** , aunque este escenario específico de failover primary→DR con rate limiting no está explícitamente cubierto en la guía.
20. iii. - **Tema de la guía:** Relacionado con **3.4 (Process APIs)**
21. iv. - **Tema de la guía:** Sección **5.11 (API Client Applications and Contracts)**
22. i. - **Tema de la guía:** Sección **5.3 (Auto-Discovery vs API Proxy)**
23. iii. - **Tema de la guía:** Sección **4.3 (Semantic Versioning)** y **1.6 (Breaking Changes and Versioning)**
24. iii. - **Tema de la guía:** Sección **4.4 (Bounded Contexts)** — específicamente "Mapping Between Bounded Contexts" y sección **3.3 (Relating the System API Data Model to the Backend System)**
25. ii. - **Tema de la guía:** Sección **4.1 (API, API Specification, Implementation, and Clients: Key Dependencies)** y **5.10 (API Client Applications and Contracts)**.

    La guía cubre los conceptos de API, Implementation y Client, pero no describe explícitamente esta secuencia ordenada de 4 pasos. Se reforzó con documentación/material oficial de preparación de MuleSoft (Anypoint Platform - diagrama de conceptos fundamentales), que confirma el flujo: **API Consumer solicita acceso a la API** (a través de Anypoint Exchange, obteniendo credenciales) → **API Client implementa la lógica para llamar a la API** (usando esas credenciales) → **la API enruta la solicitud a** → **API Implementation** (donde realmente se ejecuta la lógica de negocio).

    Se recomienda reforzar este flujo revisando la sección **5.10** de la guía junto con la documentación oficial "Requesting Access to an API Instance" (docs.mulesoft.com/api-experience-hub/requesting-access-to-an-api-instance), ya que este es un patrón conceptual que suele aparecer en el examen distinguiendo Consumer vs. Client.
26. ii. - **Tema de la guía:** Relacionado con secciones **2.4 (Modern IT Operating Model)** y **2.5 (Production and Consumption of Reusable Assets)**, aunque el modelo completo de "producción-consumo-feedback" no está descrito explícitamente en la guía con ese nombre.

    Se buscó en documentación/material oficial de MuleSoft (Salesforce Trailhead — "Discover the MuleSoft IT Operating Model" y el artículo oficial "The secret to managing IT projects" de mulesoft.com), donde se confirma que el modelo operativo efectivo de IT se basa en un **ciclo virtuoso de tres partes**: los activos deben ser descubribles y los desarrolladores deben poder auto-servirse de ellos en los proyectos, y la parte virtuosa del ciclo es obtener retroalimentación activa del modelo de consumo junto con métricas de uso para informar al modelo de producción.

    Esto corresponde exactamente a la opción **2**: crear activos reusables → hacerlos descubribles para autoservicio → obtener feedback activo y métricas de uso. La opción 3 se queda corta porque omite el paso de feedback/métricas de uso, que es precisamente lo que "cierra el ciclo" (production → consumption → feedback) y hace que el modelo sea efectivo y de mejora continua, no solo un ciclo lineal de creación y descubrimiento.

    Se recomienda reforzar este concepto revisando **Salesforce Trailhead: "MuleSoft Catalyst Playbooks – Discover the MuleSoft IT Operating Model"**, ya que este ciclo de producción-consumo-feedback es un tema recurrente en el examen y no está desarrollado a fondo en la guía actual (podría valer la pena añadirlo como un apartado nuevo dentro de la sección 2.4/2.5).
27. iii. - **Tema de la guía:** Secciones **7.5 (Types of Tests)** y **7.6 (Choosing the Appropriate Test Strategy)**

    La guía es explícita y directa sobre este escenario exacto. En la sección 7.5 se indica que los **Functional Tests** pueden ejecutarse contra sistemas backend reales o contra servicios simulados (mocked) cuando el acceso al backend no está disponible, siempre que el comportamiento funcional de la aplicación pueda validarse por completo,  y que el objetivo es verificar que la aplicación produce los resultados esperados para los escenarios de negocio, independientemente de su implementación interna.

    Además, la sección 7.6 advierte textualmente que este es un **exam trap**: escenarios como "backend access is unavailable", "mocked data is sufficient" o "no active connection to backend systems" **no necesariamente indican un Unit Test**. Si el objetivo es validar el comportamiento observable externamente de la aplicación (es decir, desde la perspectiva del consumidor de la API), la respuesta correcta es **Functional Testing**, no Unit Testing ni Integration Testing.

    La razón clave para descartar Unit Test (opción 4): un Unit Test valida un flow/subflow aislado (una pieza pequeña de lógica), no el comportamiento **end-to-end** de la API completa desde la perspectiva del consumidor. Aquí se dice explícitamente que los datos mockeados son suficientes para probar **la implementación completa de la API** ("entirely test the API implementations"), lo cual apunta a una prueba de caja negra (blackbox) a nivel funcional, no a pruebas unitarias de caja blanca (whitebox) de componentes individuales.
28. i. - **Tema de la guía:** Sección **2.7 (Control Plane and Runtime Plane)** y **2.7 - Runtime Plane Hosting Options**

    La guía cubre los conceptos de Control Plane (metadatos, gestión) vs. Runtime Plane (ejecución/datos de payload), y las opciones de hosting (CloudHub, Runtime Fabric, customer-hosted), pero no menciona explícitamente que el **Control Plane también pueda ser customer-hosted** (esto corresponde a **Anypoint Platform Private Cloud Edition**, no cubierto en la guía actual).

    Se confirmó con fuentes de material de preparación oficial/documentación de MuleSoft (docs de Anypoint Platform Private Cloud Edition y bancos de preguntas de práctica ampliamente citados del examen MCPA), donde la explicación estándar es: si se usara un Control Plane alojado por MuleSoft (cloud-based), este requeriría que al menos cierto nivel de metadatos salga fuera del firewall corporativo. Como el requerimiento es explícito en que **tanto los datos como los metadatos** deben permanecer dentro del firewall corporativo, la única combinación que satisface esto es **Runtime Plane customer-hosted (aprovisionado manualmente) + Control Plane customer-hosted**, aunque esto sacrifique la meta de velocidad ("as quickly as possible"), ya que la restricción de seguridad tiene prioridad sobre la conveniencia de despliegue rápido.

    Se recomienda reforzar este tema agregando a la sección **2.7** de la guía una nota sobre **Anypoint Platform Private Cloud Edition (PCE)**, ya que es la única opción que permite un Control Plane 100% customer-hosted, y es un distractor común en el examen frente a Runtime Fabric (que sigue usando el Control Plane alojado por MuleSoft).
29. ii. - **Tema de la guía:** Sección **1.6 (Breaking Changes and Versioning)** y **4.3 (Semantic Versioning)**

    La guía cubre que un cambio disruptivo (breaking change) siempre requiere una nueva versión mayor, y que ejemplos incluyen "modificar la estructura del payload de respuesta, cambiar un tipo de dato". El caso de cambio de zona horaria no está explícitamente mencionado como ejemplo en la guía, así que se reforzó con fuentes de material de preparación oficial de MuleSoft ampliamente reconocidas (bancos de preguntas de práctica del examen MCPA-Level-1).

    La explicación clave es: aunque el **formato** del campo (`hh:mm:ss`, ISO 8601) permanece idéntico, el **significado/valor** de los datos cambia por completo, ya que un mismo timestamp representará un momento distinto en el tiempo real (PST vs. CEST). Cualquier consumidor que ya esté parseando y utilizando esos valores asumiendo la zona horaria PST obtendrá resultados incorrectos sin haber cambiado su propio código — esto es la definición misma de un **breaking change** según semver.org ("changes that are not backward compatible"), sin importar que el esquema/formato de la respuesta no haya cambiado.

    Por lo tanto, corresponde una nueva **versión mayor: 4.0.0**, no un patch (que implicaría una corrección compatible hacia atrás) ni un minor (que implicaría una adición de funcionalidad compatible).

    Se recomienda reforzar la sección **4.3** de la guía agregando este ejemplo específico (cambio de zona horaria sin cambio de formato = breaking change), ya que ilustra que "breaking change" no se limita a cambios de estructura/esquema, sino también a cambios de **semántica** de los datos.
30. i. - **Tema de la guía:** Secciones **2.4 (Modern IT Operating Model)** y **2.5 (Production and Consumption of Reusable Assets)**

    La guía indica explícitamente en la sección 2.5 que "MuleSoft no recomienda enfocarse solo en producir activos" y que "una red de aplicaciones madura promueve tanto la producción como el consumo de activos reusables", y en 2.4 que las organizaciones deben cambiar hacia un modelo federado que aumente el **clock speed** mediante la reutilización y el consumo activo de assets existentes (no solo su creación).

    Esto descarta las demás opciones:
    - La opción 2 (MDM) es un distractor técnico; MDM no es el cambio central recomendado por MuleSoft para el modelo operativo de IT.
    - La opción 3 (SOA con foco solo en producción) es explícitamente el **anti-patrón** que la guía contrasta (sección 2.5: "MuleSoft does NOT recommend focusing only on producing assets"), además de que SOA/WSDL no es el enfoque promovido por API-led connectivity.
    - La opción 4 ("lean and agile organization... many small decisions") suena parecida a conceptos de la sección 2.4, pero es una **media verdad**: describe una consecuencia/característica del modelo federado, pero no es "el cambio principal" que MuleSoft recomienda — el cambio central y explícitamente nombrado es **impulsar tanto la producción como el consumo de assets reusables** (ciclo de producción-consumo-feedback, como vimos en la pregunta 26), del cual la agilidad organizacional y la toma de decisiones descentralizada son un resultado, no la causa raíz del aumento de clock speed.

    La opción 1 es la que MuleSoft identifica de forma más directa y consistente en su documentación oficial (Trailhead: "Discover the MuleSoft IT Operating Model") como el cambio fundamental: pasar de un modelo centrado solo en producción a uno que impulsa **igualmente el consumo**, habilitando el autoservicio, la reutilización y la estandarización.
31. i. - **Tema de la guía:** Sección **6.1 (Authentication and Authorization)**, **6.3 (Identity Providers - IdPs)** y **6.6 (Comparing Identity Management and Client Management)**

    La guía distingue en la sección 6.6 que **Identity Management** gobierna el acceso a **Anypoint Platform en sí** (Design Center, API Manager, Runtime Manager, y por extensión, herramientas administrativas como Anypoint CLI), respondiendo a la pregunta "¿quién es esta persona/sistema?", mientras que **Client Management** gobierna qué **aplicación registrada** puede consumir una API específica (a través de Client Applications en Exchange), respondiendo a "¿esta aplicación puede llamar a esta API?".

    Dado que Anypoint CLI ejecuta comandos contra las **APIs de gestión de Anypoint Platform** (el control plane en sí — Runtime Manager, Access Management, etc.), y no contra una API de negocio protegida por una política de Client ID Enforcement, las credenciales relevantes son las de **Identity Management** (el IdP configurado para autenticar usuarios/sistemas contra la plataforma), no las de Client Management (que aplican a Client Applications que consumen APIs específicas).

    Esto se confirma con la documentación oficial de MuleSoft referenciada en bancos de preguntas de práctica ampliamente citados (docs.mulesoft.com/runtime-manager/anypoint-platform-cli#authentication), la cual indica que para autenticar el CLI contra las APIs de Anypoint Platform se deben usar las **credenciales del IdP configurado para Identity Management**, ya que Client Management aplica específicamente al contexto de consumo de APIs vía Exchange/API Manager, no a la autenticación administrativa de herramientas como el CLI.

    Se recomienda reforzar la sección **6.6** de la guía añadiendo este caso de uso concreto (autenticación de Anypoint CLI) como ejemplo práctico de cuándo aplica Identity Management vs. Client Management, ya que ayuda a fijar la distinción de forma muy clara para el examen.
32. i. - **Tema de la guía:** Secciones **3.1 (System APIs)**, **3.3 (Relating the System API Data Model to the Backend System)** y **4.2 (Business Abstractions in API Design)**

    La guía indica en 3.1 que los System APIs proveen "una interfaz consistente y controlada a los sistemas de registro" y que su propósito es **abstraer la complejidad del sistema subyacente** completo (SAP, CRM, mainframe, etc.), no fragmentar cada función individual del backend en una API separada.

    La opción correcta es implementar **un único System API** (`customerManagement`) que exponga las 4 funcionalidades (create, amend, retrieve, suspend) como **operaciones/recursos dentro de esa misma API** (por ejemplo, `POST /customers`, `PATCH /customers/{id}`, `GET /customers/{id}`, `POST /customers/{id}/suspend`). Esto es consistente con el principio de **abstracciones de negocio** (sección 4.2): el System API debe representar el **concepto de negocio "Customer"** de forma unificada y reusable, no exponer cada operación técnica como una API independiente.

    Las opciones 2 y 3 representan un **anti-patrón de sobre-fragmentación** ("API sprawl"): crear una API separada por cada operación CRUD rompe la cohesión del recurso de negocio, multiplica innecesariamente el número de APIs a gobernar, versionar y documentar, y contradice el principio de que un System API debe encapsular el acceso a **un sistema/entidad de negocio como un todo**, no a una sola función técnica. Además, la opción 3 comete el error adicional de acoplar el nombre de la API al sistema backend específico ("...InCRMZ"), violando el principio de abstracción de backend (secciones 3.2/3.3): si CRM-Z fuera reemplazado en el futuro, el nombre de la API ya no tendría sentido y probablemente requeriría romper el contrato para los consumidores.

    Se recomienda reforzar este ejemplo específico en la sección **3.1** de la guía, ya que ilustra de forma muy clara y práctica el error común de diseñar "una API por operación" en lugar de "una API por capacidad/entidad de negocio".
33. i. - **Tema de la guía:** Sección **2.7 (Control Plane and Runtime Plane — Runtime Plane Hosting Options)** y **8.2 (CloudHub Deployment Models — Runtime Fabric)**

    La guía indica en la sección 2.7 que **Runtime Fabric** permite que Mule corra sobre infraestructura Kubernetes gestionada por el cliente ("customer-managed Kubernetes infrastructure"), y en 8.2 que RTF es "un modelo de despliegue basado en contenedores que permite a las organizaciones desplegar aplicaciones Mule en su propia infraestructura (on-premises o en la nube)".

    Se descartan las demás opciones:
    - **CloudHub (3)** solo se ejecuta sobre infraestructura AWS gestionada por MuleSoft; no puede desplegarse dentro del entorno Azure del cliente, por lo que no cumple el requisito.
    - **Anypoint Platform for Pivotal Cloud Foundry (2)** es una oferta legada/específica para clientes con infraestructura PCF, no aplica a Azure.
    - **Una combinación híbrida de runtimes customer-hosted y MuleSoft-hosted (4)** requeriría esfuerzo de integración y configuración manual significativo (balanceo de carga, HA, escalado), justo lo contrario de "minimizar el esfuerzo".

    Se confirmó con material de referencia oficial de MuleSoft (arquitectura de Runtime Fabric, incluyendo despliegues sobre Azure Kubernetes Service/AKS), donde se documenta explícitamente que Runtime Fabric on Self-Managed Kubernetes permite desplegar aplicaciones Mule y proxies de API en un clúster de Kubernetes que el cliente crea, configura y administra, ejecutándose como un servicio sobre un entorno existente de Amazon EKS, Azure Kubernetes Service (AKS), o Google Kubernetes Engine (GKE),  entregando así balanceo de carga HTTP, despliegues sin downtime ("rolling deployments") y escalado horizontal/vertical con el menor esfuerzo operativo posible al aprovechar componentes ya automatizados por MuleSoft dentro del clúster gestionado.

    Se recomienda reforzar la sección **2.7/8.2** de la guía agregando explícitamente que **Runtime Fabric puede desplegarse sobre AWS EKS, Azure AKS o Google GKE**, ya que el examen suele probar escenarios "quiero características tipo CloudHub pero en mi nube/infraestructura propia", cuya respuesta es consistentemente Runtime Fabric.
34. iii. - **Tema de la guía:** Secciones **2.1 (Center for Enablement - C4E)** y **2.4 (Modern IT Operating Model)**

    La guía indica que el C4E "balancea la consistencia a nivel empresarial con la autonomía de los equipos" y que en el **modelo federado**, "los equipos de entrega toman muchas decisiones arquitectónicas e implementación pequeñas de forma independiente", mientras el C4E provee gobernanza, estándares y guía arquitectónica en lugar de actuar como equipo de implementación.

    Un factor clave que decanta hacia un modelo **federado** (en contraposición al centralizado) es precisamente cuando la organización **ya tiene múltiples iniciativas o grupos de desarrollo independientes/descentralizados** operando (opción 3): en ese contexto, imponer un C4E centralizado que controle todo el desarrollo generaría fricción, iría en contra de la estructura organizacional existente y crearía el cuello de botella que la guía advierte explícitamente en la sección 2.4 ("as organizations grow, this centralized approach becomes a bottleneck"). Un modelo federado, en cambio, se adapta naturalmente a equipos ya distribuidos, dándoles autonomía dentro de guardrails comunes.

    Se descartan las demás opciones:
    - **Opción 1** (muchos activos comunes compartidos) no es un factor decisivo entre federado vs. centralizado; de hecho, activos compartidos son valiosos en ambos modelos.
    - **Opción 2** (equipos nuevos en integración, necesitan entrenamiento extensivo) apunta más bien hacia un modelo **centralizado** o al menos un rol más fuerte del C4E como entrenador/entregador directo al inicio (esto es más el enfoque de MuleSoft Catalyst en etapas tempranas, sección 2.2), no hacia federación inmediata.
    - **Opción 4** (aplicaciones basadas en la nube) es un dato de despliegue/infraestructura irrelevante para decidir el modelo organizacional de gobernanza del C4E.

    Este es un tema cubierto de forma sólida por la guía.
35. iv. - **Tema de la guía:** Secciones **8.3 (Worker Sizing and Scaling)** y **9.3 (Horizontal Scaling)**

    La guía indica en 8.3 que el **escalado horizontal** consiste en agregar más workers para manejar picos de tráfico, mientras que el **escalado vertical** implica aumentar el tamaño de los workers existentes; y en 9.3 que el escalado horizontal es la estrategia preferida para mejorar disponibilidad y throughput, especialmente cuando la aplicación está diseñada de forma stateless.

    El requisito clave de la pregunta es **"la forma más eficiente en recursos"** ("MOST resource-efficient"), lo cual apunta directamente a **escalado automático (autoscaling)** en lugar de un aumento **permanente** de capacidad:
    - Las opciones **1** y **3** proponen incrementos **permanentes** de tamaño/cantidad de workers (4x), lo cual desperdicia recursos (y costo) durante la mayor parte del año, ya que la carga normal se maneja bien con la configuración actual (CPU < 70% con 2 workers de 0.2 vCore). Esto es ineficiente porque el pico ocurre solo "varias veces al año".
    - La opción **2** (autoscaling **vertical**) no es una capacidad estándar/nativa de CloudHub de la misma manera; el autoscaling de CloudHub está diseñado en torno a agregar/quitar **workers** (horizontal), no cambiar dinámicamente el tamaño (vCores) de un worker en caliente.
    - La opción **4** (autoscaling **horizontal** disparado por utilización de CPU > 70%) es la respuesta correcta: agrega workers automáticamente solo durante los picos de tráfico (cuando el CPU supera el umbral) y los reduce cuando la carga vuelve a la normalidad, optimizando el uso de recursos. Esto es coherente con que el cuello de botella es de **CPU/capacidad de procesamiento** en el propio worker (no el backend, que responde a tiempo), por lo que agregar más instancias que compartan la carga (horizontal) resuelve directamente el problema sin sobreaprovisionar de forma permanente.

    Se recomienda reforzar la sección **8.3** de la guía agregando explícitamente el concepto de **CloudHub Autoscaling** (política nativa que agrega/remueve workers dinámicamente según CPU/memoria), ya que actualmente la guía solo menciona el escalado horizontal/vertical de forma manual/conceptual, sin cubrir la característica específica de autoscaling automático de CloudHub que este tipo de preguntas evalúa.
36. ii. - **Tema de la guía:** Sección **4.1 (API, API Specification, Implementation, and Clients: Key Dependencies)** y **1.1 (The Role and Characteristics of Web APIs)**

    La guía indica en 4.1 que la **API Specification** es "el documento formal y legible por máquina (escrito en **RAML u OAS**) que describe el contrato de la API", y en 1.1 que RAML y OAS/Swagger son los lenguajes estándar de definición de interfaz para APIs REST, mientras que WSDL se asocia a SOAP.

    Se descartan las demás opciones:
    - **WSDL (1)** es el lenguaje de definición de contrato para servicios **SOAP**, no para APIs REST.
    - **YAML (3)** es simplemente un **formato de serialización de datos** (como JSON), no un lenguaje de definición de interfaz de API en sí mismo; de hecho, tanto OAS como RAML *pueden escribirse* en formato YAML, pero YAML por sí solo no es un "lenguaje estándar de definición de interfaz para REST".
    - **AsyncAPI Specification (4)** es un estándar para describir APIs **basadas en eventos/mensajería asíncrona** (colas, topics, streams), no para APIs REST síncronas.

    La opción correcta y más directa entre las presentadas es **OpenAPI Specification (OAS)** (nótese que RAML, aunque es el otro estándar mencionado explícitamente en la guía y ampliamente usado en el ecosistema MuleSoft/Anypoint Exchange, no aparece como opción en esta pregunta).

    Este tema está bien cubierto por la guía.
37. i. - **Tema de la guía:** No cubierto explícitamente en la guía. Se reforzó con documentación oficial de MuleSoft.

    La guía no aborda en detalle qué conectores específicos soportan transacciones (este es un tema muy puntual de implementación en Mule Runtime, más cercano al dominio de un desarrollador que al de un arquitecto, aunque puede aparecer en el examen).

    Se confirmó con la documentación oficial de MuleSoft ("Transaction Management" y "XA Transactions", docs.mulesoft.com/mule-runtime/latest/transaction-management y .../xa-transactions), donde se indica explícitamente que los únicos componentes que pueden definir el tipo de transacción son las fuentes de eventos (por ejemplo, `jms:listener` y `vm:listener`) y el scope Try,  y en un ejemplo oficial de transacciones XA se muestra el uso conjunto de `vm:publish`, `jms:consume` y `db:insert` dentro de una misma transacción.

    Esto confirma que los conectores que soportan transacciones de forma nativa en Mule son: **Database (JDBC), JMS y VM** — coincidiendo exactamente con la opción **1**.

    Se descartan las demás opciones:
    - **HTTP (2)** no es un recurso transaccional (no implementa `TransactionalConnection`); las peticiones HTTP no pueden participar en un commit/rollback de transacción Mule.
    - **SFTP (3)** tampoco es un conector transaccional soportado en el mecanismo de transacciones de Mule.
    - **File (4)** tampoco soporta transacciones de la misma manera que Database/JMS/VM.

    Se recomienda agregar a la guía una nueva subsección (por ejemplo, dentro de la sección **9.2 Resilience Patterns** o como una nueva **9.x Transaction Management**) que cubra: tipos de transacción (Single Resource/Local vs. XA), qué conectores las soportan de forma nativa (Database, JMS, VM), y el uso del scope **Try** con `transactionalAction`, ya que este es un tema recurrente en el dominio "Meeting API Quality Goals" del temario oficial y actualmente no está documentado en la guía.
38. i. - **Tema de la guía:** Sección **5.6 (API Policies)** y **5.1 (API Manager Overview)**

    La guía no lo indica de forma tan explícita, pero se confirma con la documentación oficial de MuleSoft (docs.mulesoft.com — Mule Runtime overview), donde se establece de forma directa que las políticas sobre APIs basadas en HTTP pueden aplicar seguridad, regular el tráfico a través de las aplicaciones Mule, y adaptar las APIs a las necesidades de negocio, dejando claro que el mecanismo de políticas de API Manager está diseñado en torno al protocolo **HTTP** (request/response con headers y status codes estándar).

    Esto se corrobora además con bancos de preguntas de práctica ampliamente citados del examen oficial MCPA (Actual4test, ExamTopics), que confirman **Opción A (HTTP/1.x)** como la respuesta correcta a esta pregunta específica.

    Se descartan las demás opciones porque no son endpoints HTTP de request/response estándar sobre los cuales el motor de políticas de API Manager pueda aplicarse de forma nativa:
    - **JSON sobre TCP sin respuesta requerida (2):** no es HTTP; es un socket TCP crudo sin el modelo petición/respuesta que las políticas (rate limiting, autenticación, etc.) requieren.
    - **JSON sobre WebSocket (3):** WebSocket es un protocolo de comunicación full-duplex distinto de HTTP request/response; las políticas de API Manager no están diseñadas para interceptar mensajes WebSocket de la misma forma.
    - **gRPC sobre HTTP/2 (4):** aunque usa HTTP/2 como transporte, gRPC utiliza un formato binario (Protocol Buffers) y un modelo de streaming que no es compatible con el modelo estándar de políticas HTTP de API Manager.

    Se recomienda reforzar la sección **5.6** de la guía agregando una nota explícita indicando que **las políticas de API Manager están diseñadas para APIs HTTP/HTTP(S) estándar (request/response)**, y no aplican de forma nativa a protocolos como WebSocket, gRPC, o TCP crudo, ya que este es un matiz que el examen evalúa directamente.
39. i. - **Tema de la guía:** Sección **4.1 (API, API Specification, Implementation, and Clients: Key Dependencies)**

    La guía es muy clara en este punto: en 4.1 se establece que la **API Specification** (RAML/OAS) es "el contrato" del cual dependen los clientes, y que "cambiar la **implementación** sin cambiar la **especificación** no afecta a los clientes", mientras que "cambiar la **especificación** de forma disruptiva siempre afecta a los clientes, sin importar cuántos existan".

    El principio clave de **loose coupling** (sección 1.1 y 3.2) es que la especificación/contrato es independiente de los detalles internos de implementación. Por lo tanto, la especificación RAML **solo** necesita actualizarse cuando cambia algo que forma parte del **contrato observable por el consumidor** — es decir, la estructura de los mensajes de request/response, nuevos recursos, nuevos parámetros requeridos, nuevos códigos de estado, etc. (opción 1).

    Se descartan las demás opciones porque son cambios puramente internos de la **implementación**, que no afectan el contrato:
    - **Opción 2** (cambio de backend on-premises a SaaS): es exactamente el escenario que ilustra el propósito de un System API (secciones 3.1-3.3) — el System API existe precisamente para **abstraer/aislar** este tipo de cambios de backend, de modo que el contrato (RAML) permanezca estable aunque el sistema de origen cambie por completo.
    - **Opción 3** (migración de versión de Mule runtime): es un cambio puramente de infraestructura/tecnología de implementación, sin ningún impacto en el contrato expuesto a los consumidores.
    - **Opción 4** (optimización de tiempo de respuesta): es una mejora de rendimiento interna; mientras el contrato (estructura de request/response, códigos de estado) no cambie, no se requiere actualizar la especificación (esto es coherente además con la sección 5.7, donde se aclara que cambios puramente de comportamiento en tiempo de ejecución, sin afectar lo que el consumidor envía o recibe, no requieren actualizar la especificación).

    Este tema está bien cubierto por la guía; no fue necesario buscar información adicional fuera de ella.
40. ii. - **Tema de la guía:** Sección **7.5 (Types of Tests — Integration Tests)** y **7.4 (MUnit Testing)**

    La guía indica en 7.5 que los **Integration Tests** "verifican que múltiples componentes de la aplicación funcionen juntos correctamente... y **pueden comunicarse con sistemas externos reales o entornos de prueba dedicados**", lo cual respalda que las opciones 1 (necesita sistemas fuente/destino configurados y accesibles), 3 (activado por una solicitud HTTP externa) y 4 (prepara un payload conocido y valida la respuesta) son todas características plausibles y esperadas de un integration test contra una API REST real desplegada en un entorno de staging.

    Se confirma con fuente de banco de preguntas oficial de práctica del examen MCPA (vceguide.com, con explicación asociada): "los integration tests requieren desplegar la aplicación en un entorno de staging con todas las dependencias disponibles tal como en producción, por lo que no se permite el uso de mocks."  Bajo esta lógica, un integration test real necesita que la aplicación **ya esté desplegada y en ejecución** en un entorno con todas sus dependencias (backend, bases de datos, etc.) para poder recibir una solicitud HTTP externa y validar la respuesta contra sistemas reales.

    Por el contrario, la opción **2** ("el test se ejecuta inmediatamente después de que la aplicación Mule ha sido compilada y empaquetada") describe más bien la etapa de un **test unitario (MUnit)**, que se ejecuta como parte del proceso de build/compilación (ver sección 7.4: "MUnit tests pueden ejecutarse automáticamente como parte de los pipelines de CI/CD" inmediatamente tras compilar), sin necesidad de un despliegue completo a un entorno con sistemas reales. Un integration test, en cambio, requiere un paso adicional posterior: el **despliegue real de la aplicación** a un entorno con acceso a los sistemas de origen/destino, lo cual ocurre **después** (no "inmediatamente después") de la compilación/empaquetado.

    Se recomienda reforzar la sección **7.5** de la guía añadiendo esta distinción explícita: los integration tests requieren que la aplicación esté **desplegada y en ejecución** (no solo compilada) para poder invocarse mediante una solicitud HTTP real contra sistemas reales, a diferencia de los unit tests, que sí pueden ejecutarse inmediatamente tras el build/empaquetado sin despliegue.