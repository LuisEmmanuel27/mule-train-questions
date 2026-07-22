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
