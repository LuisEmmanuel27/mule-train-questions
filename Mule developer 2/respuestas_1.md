# Respuestas y explicaciones

1. `ii.`

Cuando Mule expone una API HTTPS (actúa como servidor), el objetivo principal de TLS es identificarse frente al cliente y cifrar la comunicación.

Keystore (OBLIGATORIO)

El keystore contiene el certificado y la clave privada del servidor. Es lo que permite:
- Presentar la identidad del servidor al cliente.
- Establecer el canal seguro (HTTPS).
- Sin keystore, no hay HTTPS, por eso es mandatory.

Truststore (OPCIONAL)

El truststore se usa para validar certificados del cliente. Solo es necesario cuando:
- Se requiere mutual TLS (mTLS).
- El servidor debe autenticar al cliente.
- En un escenario HTTPS estándar (cliente → API):
- El cliente valida al servidor.
- El servidor no necesita validar al cliente.
- Por eso el truststore es optional.

2. `ii.`

En CloudHub, los logs de DEBUG se controlan mediante la configuración de registro de Runtime Manager, no mediante el archivo log4j2.xml de la aplicación. Para habilitar los logs de DEBUG, el nivel de registro del paquete org.mule debe estar configurado en DEBUG en Runtime Manager.

3. `i.`

Ante el error Remotely Closed, el HTTP Requester reintenta automáticamente solo métodos idempotent (indepotentes).
Por defecto, esos métodos son GET y DELETE; POST, PUT y PATCH no se reintentan porque pueden provocar efectos secundarios.

4. `i.`

En Anypoint Monitoring, los custom dashboards solo soportan los widgets Graphs, Singlestats y Text; no existen otros widgets adicionales que puedan agregarse de manera custom.

5. `iv.`

Anypoint MQ solo maneja mensajes en formato text-based, por lo que cualquier payload no textual (binary) es convertido a string automáticamente antes de ser enviado a la queue; no se almacena como binario ni se genera un error por formato.

6. `iii. & iv.`

Para reutilizar configuraciones Mule entre aplicaciones, el proyecto apps-commons debe empaquetarse como una librería reutilizable usando el classifier mule-plugin, ya que solo este tipo de empaquetado permite que flows, error handlers y configuraciones puedan ser consumidos por otras aplicaciones Mule. El uso de mule-application no es válido para este propósito, ya que está destinado únicamente a aplicaciones desplegables.

Además, la aplicación consumidora check-in-papi debe declarar apps-commons como dependency en su pom.xml e importar explícitamente los archivos Mule XML compartidos. Sin esta importación, las configuraciones definidas en la librería no quedan disponibles en tiempo de ejecución, aunque la dependencia exista.

7. `iii.`

**¿Qué es un keystore en TLS y por qué lo necesitas?**

Cuando construyes una aplicación HTTPS en MuleSoft, debes configurar un contexto TLS (tls:context) que:

- Contenga un keystore con tu clave privada y certificado público para el servidor o cliente.
- Opcionalmente contenga un truststore para validar certificados externos (por ejemplo, de un servidor al que te conectas).

El keystore es esencial porque TLS necesita presentar un certificado y probar posesión de la llave privada correspondiente para establecer conexiones cifradas.

**Keystores soportados por MuleSoft**

Según la documentación oficial de MuleSoft sobre configuración de TLS y keystores, Mule soporta varios tipos de almacenes de claves:

- JCEKS (Java Cryptography Extension KeyStore)
- PKCS12
- JKS (Java KeyStore)

Estos son los tipos explícitamente documentados como soportados para el elemento <tls:key-store> en Mule.

8. `i.`

In Mule, the entry TTL (time-to-live) determines how long a stored object should be considered valid, while the expirationInterval controls how often the Object Store runs a background task to actually purge expired entries.

Here, the entry TTL is set to 1 second, but the expiration interval is 30 seconds. Because the cleanup job only runs every 30 seconds, the entry is still present in the store when the os:retrieve executes after ~12 seconds. As a result, the stored value (`testPayload`) is returned — the object hasn’t been removed yet.

9. `iii.`

When you try to publish a custom policy with a `-SNAPSHOT` **version using the Exchange Maven Facade API v3**, Exchange treats that version as a development asset and not a valid stable release. Custom policy assets need a proper release version (not a snapshot) in order to be recognized and stored by the Exchange publication engine used by API Manager. As a result, the deployment fails and the asset isn’t successfully published to Exchange — so it doesn’t become available in API Manager.

10. `ii.`

In Anypoint MQ, the `Redelivery Policy` and `Dead-Letter Queue` control how many times a message is retried and where it goes after exceeding that count, but they do not inherently protect your application from continuous repeated failures during processing. What does prevent a consumer from repeatedly attempting to process failing messages is the Circuit Breaker configuration on the MQ subscriber: once a defined number of consecutive errors occurs, it stops polling new messages for a configured timeout period, giving the downstream system time to recover. This is the pattern that provides protection against repeated delivery failures.

11. `iii.`

In Mule you use the secure property placeholder feature to store encrypted or sensitive configuration values. To read a secure property inside a DataWeave transformation, you must use the `p()` function and include the `secure::` prefix before the property key. This tells Mule to look in the secure properties file and decrypt the value at runtime. The `${...}` syntax is for XML configs, and the other options (`![...]` and unprefixed `p('database.property')`) don’t correctly access a secure property.

12. `ii.`

The Spike Control policy in MuleSoft API management is specifically designed to **regulate overall API traffic** by limiting how many requests the API processes within a defined time window, regardless of which client is sending them. It ensures that the number of messages handled in a period doesn’t exceed the configured limit, protecting the backend from sudden spikes and excessive load. This behavior is exactly what the question describes — controlling total API throughput — whereas the other policies either enforce client-specific quotas (Rate-Limiting SLA) or address different concerns like IP filtering or caching.

13. `iv.`

To satisfy high-availability and high-reliability non-functional requirements — especially no message loss — messages must be stored durably and protected through retries and error handling:

- `Persistent VM queues` ensure that messages are not lost if the Mule app or runtime restarts, because they are stored to disk or backing storage instead of only in memory. Transient queues, by contrast, lose messages on crashes.
- `A redelivery policy on the VM Listener` makes Mule retry processing a message multiple times before failing. If processing repeatedly fails, Mule will raise a `MULE:REDELIVERY_EXHAUSTED` error.
- **Catching the** `REDELIVERY_EXHAUSTED` error and redirecting to a dead-letter queue ensures that messages which cannot be processed after retries aren’t dropped, but are instead captured for later analysis or manual intervention.

Together these steps build a pattern where messages persist through failures, are retried logically, and are safely caught rather than lost — which meets the high availability/reliability and no message loss goals.

14. `i.`

According to the official MuleSoft documentation for the HTTP Connector, it supports certain authentication schemes on outbound HTTP requests — specifically Basic Authentication, Digest Authentication, NTLM Authentication, and OAuth 2.0 Authorization Code and Client Credentials grant types. The implicit OAuth2 flow is not supported by the HTTP Connector because the connector expects server-to-server style flows (like client credentials or authorization code) rather than browser-centric implicit flows. Therefore, if an API specification includes an OAuth 2.0 implicit flow, the HTTP Connector cannot handle it directly.

15. `i.`

In Mule 4, every incoming event gets a Correlation ID that’s part of the Mule event’s context. When a client calls a Mule API via HTTP, Mule first checks if the request includes an X-Correlation-Id header. If the client does not provide one, Mule will automatically generate a random Correlation ID at the start of the flow execution. This ID is used for tracking and logging throughout the flow. Mule does not throw an error or look for a different header like X-Mule-Transaction-Id in this process.

16. `iii.`

In Mule 4 the Correlation ID is part of the event context and is determined at the time the message enters the application. If the incoming HTTP request contains an X-Correlation-Id header, Mule uses that value as the correlation ID throughout the flow; otherwise Mule generates its own random ID. To meet a requirement that a scheduled batch must send a custom correlation ID (like "application-name-UUID"), the client must explicitly set the X-Correlation-Id HTTP header on each outbound request with that custom value. This ensures Mule uses the defined correlation ID rather than generating its own.

17. `ii.`

By default, the Scatter-Gather router executes all of its configured routes in parallel using separate threads for each route. However, the component provides a maxConcurrency attribute that controls how many routes can run concurrently. If you set maxConcurrency="1" on the Scatter-Gather itself, Mule will process the routes one at a time in sequence rather than in parallel. Changes to the flow’s own concurrency don’t affect the router’s internal route execution — only the router’s own maxConcurrency can enforce sequential execution.

18. `ii.`

According to the official Mule documentation on secure configuration properties, a secure properties file (whether YAML or .properties) can include both encrypted and non-encrypted values together. In such a file, you put encrypted values using the special syntax like `![encryptedValue]`, and normal clear-text values are just written as regular property values without requiring any prefix. You do not need to split clear text and encrypted properties into separate files, and clear text entries don’t use a secure:: prefix — the prefix is only for referring to secure values at runtime once configured.

19. `iii.`

In MUnit 2.x, the `<munit-tools:assert-that>` processor is used to compare an expression against an expected value using a matcher from the `MunitTools` library. To check that a boolean expression is true, you must use a matcher function like `MunitTools::equalTo(value)`, where the expected value is a boolean (`true` in this case). Simply putting `true` without a matcher (like in option 2) isn’t valid matcher syntax. The matcher must come from `MunitTools`, and `MunitTools::equalTo(true)` is the correct way to assert the value is true.

20. `iv.`

API Autodiscovery in Mule is the mechanism that pairs a deployed Mule application with the API instance defined in API Manager. By configuring Autodiscovery with the API’s ID, the Mule runtime registers itself with API Manager so that policies defined in API Manager (like rate-limiting, security, SLA, etc.) are retrieved and enforced by the running application. This makes API Manager aware of the implementation and allows real-time governance and analytics for that API.

21. `ii.`

When you deploy a Mule application to CloudHub using the Mule Maven plugin, you must authenticate the deployment against the Anypoint Platform. The plugin supports several authentication methods, including:

- Username and password (standard credentials)
- Server credentials stored in your Maven settings.xml
- Authorization token (authToken) — a bearer token that the plugin uses instead of username/password
- Connected App credentials for programmatic authentication

Among the answer choices listed, Authorization Token is the supported method for the Mule Maven plugin to authenticate with CloudHub during deployment.

22. `iv.`

The Scatter-Gather router executes its routes in parallel by default. That means both routes read the initial vars.counter value (which starts at 1) at the same time and each route independently sets it to vars.counter + 1, which is 2.

Since both routes write 2 back to the same variable concurrently, the final value after the scatter-gather completes is 2, and that is what the Logger prints. Even though there are two increments, they happen in parallel without coordination, so the counter isn’t incremented twice cumulatively.

23. `iii.`

For mutual TLS (mTLS) the client must present its own identity to the server during the TLS handshake. To do that, the client keystore must contain a private key and a corresponding certificate — this certificate can be self-signed or CA-signed, but it must match the private key. Without both the private key and its associated certificate in the keystore, the client cannot authenticate itself to the server in an mTLS exchange.

**Bonus data**

Mutual TLS (mTLS) is an extension of the standard Transport Layer Security (TLS) protocol in which both the client and the server authenticate each other using digital certificates before establishing a secure connection. In traditional TLS (such as HTTPS), only the server presents its certificate to the client so the client can verify the server’s identity. With mTLS, the server also requires the client to present a certificate, and verifies it — creating a two-way (mutual) authentication.

Difference between TLS and mTLS:

- `TLS (standard)`: Only the server proves its identity to the client using a certificate, which ensures the client is communicating with the correct server.
- `mTLS`: Adds an extra step where the client also presents and proves its own certificate to the server, so both ends verify each other’s identities. This provides stronger authentication and security, especially in service-to-service communications or zero-trust environments.

24. `iii.`

A webhook is a user-defined HTTP callback that enables one system (the provider) to push an HTTP request to another system’s endpoint when a specific event occurs — without the consumer having to repeatedly ask (“poll”) the provider for updates. This push-based, event-driven pattern means the provider initiates the request as soon as the event happens, delivering the data to the consumer’s registered URL

25. `iii.`

Two-way (mutual) TLS requires the client to present its own certificate, which is stored in a keystore. A truststore is also normally needed to verify the server's certificate, but since the server's CA is already in the JDK truststore, Mule uses it automatically — no explicit truststore configuration is needed. Therefore, only a keystore is required.

26. `ii. & iii.`

To monitor the health of APIs in a MuleSoft digital transformation program, you need tools or mechanisms that actively check whether the APIs are running correctly and meeting expectations — not just deploy them. Two valid methods are:

- Dedicated health check endpoints: By exposing a specific /health (or similar) endpoint in an API, you allow monitoring tools to call that endpoint regularly to determine if the API is healthy (e.g., returns a 200 status). This is a common pattern used in API monitoring and observability.
- API Functional Monitoring: Anypoint Platform’s API Functional Monitoring lets you define scheduled tests that call your API endpoints at regular intervals and verify their behavior (status codes, response contents, etc.). It’s designed to check the runtime health and functionality of APIs from inside or outside the network.

The other options aren’t directly used for health monitoring: policies in API Manager control policy execution but don’t act as health checks; an API mocking service simulates APIs for development/testing, not ongoing health monitoring; and existing resource endpoints aren’t standardized health indicators unless explicitly built and monitored.

27. `i.`

In Log4j, log levels are ordered by verbosity — that is, how much detail they produce:

- DEBUG is more verbose than INFO
- INFO is more verbose than WARN
- WARN is more verbose than ERROR
- ERROR is more verbose than FATAL
- OFF turns off all logging (least verbose)

This means from most verbose to least verbose the order is DEBUG → INFO → WARN → ERROR → FATAL → OFF. When you set a logging level, Log4j outputs messages at that level and all levels above it in severity.

28. `iv.`

For Object Store v2 in Mule 4, entries don’t expire immediately if you don’t set a custom entryTtl; instead, Mule uses a rolling TTL mechanism by default for newer Mule versions (4.2.1+). With rolling TTL, each entry has a 30-day window, and accessing the data during the last 7 days of that window extends it another 30 days. This means if you keep accessing the entry at least once a week, the TTL keeps rolling forward indefinitely — effectively giving you “unlimited” time to live for those entries.

Setting a maximum or static TTL won’t guarantee true unlimited TTL, and there’s no configuration like partitions that makes TTL infinite by itself — the only way to prevent eviction forever is to continually access the data within the rolling TTL window.

29. `iv.`

In CloudHub 2.0 shared spaces, the platform hosts your applications behind a managed shared ingress load balancer that does not support custom mutual TLS (mTLS) configuration at the HTTP ingress level because you cannot upload custom TLS contexts or truststores in a shared space. Only private spaces let you configure TLS contexts that enable client certificate (mTLS) validation and custom certificates. Since in a shared space you can’t configure mTLS authentication at the ingress (and there’s no built-in mTLS by default), no action on the API itself will enable mTLS in that scenario — you’d need to deploy the app in a private space to use mTLS.

30. `iii.`

When an HTTP API routinely fails with responses like HTTP 502 (Bad Gateway), it usually indicates a temporary or downstream problem. A common way to make your Mule application more fault-tolerant in that situation is to provide an alternate path — a fallback API or endpoint — that the application can invoke when the primary API fails. The First Successful router in Mule allows you to configure multiple routes and stops execution as soon as one route succeeds. If the first (primary) route fails with an error such as a 502, the router automatically tries the next route (the fallback). This enables graceful handling of repeated upstream errors by trying an alternate service instead of letting the failure propagate further.

The other options refer to timeouts, circuit breakers, or transactional retries, which address aspects of fault handling but do not by themselves provide an automatic alternate invocation when an upstream service repeatedly fails — whereas the First Successful router explicitly implements that pattern.

31. `iv.`

When following API-led best practices and RESTful design principles (as recommended by MuleSoft), you want your endpoints to be:

- Resource-oriented (using plural nouns like /customers)
- Versioned explicitly in the path (/v1/...)
- Filtered via query parameters when returning subsets of a resource (e.g., ?type=gold for Gold customers)

Query parameters are the recommended way to filter or search a collection instead of burying filter values deeper into the path (like /customers/gold). They keep the API intuitive and consistent with RESTful design patterns and the MuleSoft best practices for API URLs.

So the best-practice URL for the development environment is:

```
https://customers-papi-dev.us-e2.cloudhub.io/api/v1/customers?type=gold
```

This clearly shows the environment (-dev), service (customers-papi), API version (v1), resource (customers), and uses a query parameter to return only Gold customers.

32. `iv.`

In the OAuth 2.0 Authorization Code grant type, after the client receives an authorization code, it must exchange that code for an access token by calling the authorization server’s **token endpoint**. To do this securely, the client needs to include several fields in that access token request:

- `grant_type=authorization_code` and the code itself
- The redirect URI — it must match the redirect URI originally registered and used in the authorization request
- The client ID and client secret so that the server can authenticate the client who is making the token exchange request

This ensures the request is coming from the same registered client that initiated the flow and that the redirect URI is valid.

33. `iv.`

The Cache scope stores the response result from the first execution (a cache miss) and on subsequent identical requests (cache hit) returns the cached response without re-executing the processors inside the scope. In this flow, the first execution calls the HTTP Request and returns `200`, which is then captured in `vars.responseStatus`. On the second execution of the same request:

- The cache produces a cache hit, so the HTTP Request is not executed again.
- Because the HTTP Request isn’t executed on a cache hit, `attributes.statusCode` isn’t updated a second time — meaning the logger sees no new status code from an HTTP call and the `responseStatus` variable ends up being null on the second run.

So the logger prints `200` for the first run, and `null` for the second identical request because only the cached data is returned on the second invocation, not a new HTTP response.

34. `i.`

To intercept all downstream HTTP requests and inject the client IP address as a header for auditing/tracing, you must use a custom outbound API policy that runs **before the** `execute-next` **statement** and modifies the request attributes. MuleSoft’s out-of-the-box Header Injection policy can add headers, but it doesn’t dynamically capture client IP information and cannot be configured to run outbound before execution of the backend call for this purpose out of the box. Instead, a custom policy built with the **mule-http-policy-transform-extension** lets you write DataWeave logic or expressions to extract the client IP and **add it to the HTTP request header before sending the request downstream**. The transform extension is used inside custom policies to modify request headers in the correct phase.

35. `iv.`

When you develop a custom **XML SDK module** and want your operation to automatically accept the **message payload** as input without the caller needing to explicitly bind a parameter, you define a content parameter with the special `role="PRIMARY"`. In the Mule XML SDK, a primary content parameter maps directly to the payload and defaults to `#[payload]`, making the module easier to use.

36. `ii.`

By default the HTTP Request connector in Mule treats any HTTP status code ≥ 400 as a failure and throws an error. That means a 404 (Not Found) will stop flow processing unless you explicitly tell Mule to accept it.

To accomplish the requirement — accept only standard successful status codes and 404 as success — you must configure the response validator so that Mule does not treat 404 as a failure. In Mule’s HTTP Request configuration you can do this by specifying the failure-status-code-validator with the values that should be considered failures, or better yet by using a success-status-code-validator with the values that should be accepted as non-errors.

The correct configuration to accept standard success codes (200..299) and 404 as non-errors looks like this:

```xml
<http:response-validator>
  <http:success-status-code-validator values="200..299, 404" />
</http:response-validator>
```

This tells Mule to treat 404 as a success alongside the normal 2xx range, so the flow continues normally when the external API returns 404 — but will still fail for other 4xx or 5xx error codes.

37. `i.`

In the Mule Maven plugin’s `cloudhubDeployment` configuration, the `<server>` element refers to a Maven `<server>` entry in your local settings.xml file. That entry contains your Anypoint Platform credentials (username and password) or their encrypted form. By setting `<server>` in the deployment config, the Maven plugin will look up those credentials and use them to authenticate against Anypoint Platform — so you don’t have to hard-code your username and password directly in the `pom.xml`. This is exactly what the `<server>` configuration element is intended for.

38. `ii.`

In this scenario, many external clients written in different languages must be notified asynchronously when a long-running process completes — they shouldn’t have to constantly poll the API for status updates. The best architectural pattern for this situation is to use webhooks, where each client registers a callback URL with the Orders API. When the long-running order processing finishes, the API issues an HTTP callback (push) to the registered URLs, notifying each client of the completed event. This push-style notification model lets the server notify clients immediately without requiring polling — a common use of webhooks for asynchronous event notifications.

Other options like internal VM queues and JMS topics only work within the same runtime or messaging system (not ideal for external clients across languages/environments), and Mule’s automatic return address is not designed for cross-client notification.

39. `iii.`

When defining operations in an XML SDK component, the operation name becomes part of the XML tags used in the generated schema and in Mule configuration. Because of this, MuleSoft requires you to use a kebab-case naming convention (lowercase words separated by hyphens) for operation names so that the resulting XML elements are valid and unambiguous. Names like `example_operation` (underscore), `ExampleOperation` (camel case), or `Exampleoperation` (mixed case) can cause invalid XML tag names or unexpected schema generation errors. Therefore the correct convention to avoid XML tag generation problems is to use hyphenated kebab-case, e.g., `example-operation`.

40. `ii.`

When you need common data definitions reused now and across future APIs, the best practice in MuleSoft is to externalize those shared types into an API fragment and publish that fragment to Anypoint Exchange. API fragments can contain reusable components such as data types, traits, or libraries. Once published, other API specifications can import the fragment and reference the shared definitions using standard include or dependency mechanisms. This allows multiple APIs to reuse the same data structures without duplicating them, and you can manage versions of those fragments independently.

41. `iv.`

In this scenario, the process-api-flow is acting as the HTTPS client (using an HTTPS Request connector), and the system-api-flow is acting as the HTTPS server (using an HTTPS Listener).

For an HTTPS connection to be established, the server must present a certificate during the TLS handshake. That certificate is stored in a keystore, which contains the server’s private key and corresponding certificate.

Because self-signed certificates are being used, the minimum requirement to make the call work is:

- The server side (system-api-flow’s HTTPS Listener) must have a keystore configured.
- This keystore provides the certificate that will be presented to the client during the TLS handshake.

42. `ii. & v.`

To allow a Mule application’s log4j2.xml to accept the log package name and log level dynamically at startup, you must reference those values as Java system properties in the logging configuration and then actually provide them when Mule starts. This works because Log4j2 supports retrieving property values from the JVM’s system properties using the `sys:` prefix in the `${sys:...}` placeholder syntax.

- Option 2 ensures that in the log4j2.xml file, the `<AsyncLogger>` elements use `${sys:log.package}` and `${sys:log.level}`, telling Log4j2 to look up those values from system properties at runtime.
- Option 5 covers actually passing those system property values to Mule at startup with standard JVM `-D` arguments (`-Dlog.package=...` and `-Dlog.level=...`), so the variables referenced in the config are resolved.

Together these two steps let you externalize the logger name and level so they’re provided at launch time rather than hard-coded in the XML.

43. `iv.`

To move a Mule application using API Autodiscovery from a development environment to production, you must update both the API ID (so it points to the correct API instance in API Manager for production) and the environment-specific Anypoint Platform credentials (client ID and client secret) that the Mule runtime uses to authenticate to API Manager.

44. `i.`

The official MuleSoft MUnit documentation shows how to use a Spy processor to monitor an http:request and assert conditions on the payload both before and after the request is executed. In the behavior section of the test you configure:

- `<munit-tools:spy processor="http:request">` so that it spies every HTTP request in your flow.
- Inside it, a `<munit-tools:before-call>` with an assert that checks `#[payload]` is `#[MunitTools::nullValue()]` before the component executes.
- And a `<munit-tools:after-call>` with an assert that checks `#[payload]` is `#[MunitTools::notNullValue()]` after the component executes.

45. 