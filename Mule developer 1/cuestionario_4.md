# Cuestionario de prueba 4

## [Respuestas y explicaciones](respuestas_4.md)

---

1. According to MuleSoft, what is the first step to create a API for use in an application network?
   1. Create a prototype of the API implementation
   2. Create an API specification and get feedback from stakeholders
   3. Gather a list of requirements to secure the API
   4. Performance tune and optimize the backend systems and network <br/><br/>
2. Refer to the exhibit. The input array of strings is passed to the batch job, which does NOT do any filtering or aggregating. <br/> What payload is logged by the Logger component? <br/> ![pic_1](img/yt/pic_1.png)
   1. ["Apple1", "Banana1", 2]
   2. ["Apple12", "Banana12"]
   3. Summary report of processed records
   4. ["Apple", "Banana"] <br/><br/>
3. Refer to the exhibits. The main flow contains an HTTP Request in the middle of the flow. The HTTP Request use default configurations. <br/> After a web client sumits a request to http://localhost:8081/order?color=red, what values are accesible to the Logger at the end of the main flow? <br/> ![pic_2](img/yt/pic_2.png)
   1. payload <br/> color query param
   2. payload
   3. payload <br/> quantity var
   4. payload <br/> color query param <br/> quantity var <br/><br/>
4. A web client sens a request to http://localhost:8081/books/0471767840. The value "0471767840" is captured by a Set Variable transformer to a variable named bookISBN. <br/> What is a valid DataWeave expression to access the bookISBN variable later in the flow?
   1. bookISBN
   2. attributes.bookISBN
   3. variables.bookISBN
   4. vars.bookISBN <br/><br/>
5. Refer to the exhibit. The main flow contains a Flow Reference for the child flow. <br/> After a web client submits a request to http://localhost:8081/order?color=red, what values are accesible in the child flow? <br/> ![pic_3](img/yt/pic_3.png)
   1. payload <br/> color query param <br/> quantity var
   2. payload <br/> color query param
   3. payload <br/> quantity var
   4. payload <br/><br/>
6. When using MuleSoft's Anypoint API-led connectivity approach, what HTTP method is a RESTful web service is generally recommended to be used to completely replace an existing resource?
   1. POST
   2. GET
   3. PUT
   4. PATCH <br/><br/>
7. A Mule application uses the ${http.port} property placeholder for its HTTP Listener port when it is deployed to CloudHub. <br/> What benefit does this Mule application configuration enable?
   1. Clients to VPN directly to the Mule application at the Mule application's configured HTTP port
   2. MuleSoft Support to trobuleshoot the application by connecting directly to the HTTP Listener
   3. CloudHub to automatically register the application with API Manager
   4. CloudHub to automatically change HTTP port to allow external clients to connect to the HTTP Listener <br/><br/>
8. Refer to the exhibit. How Many private flows does APIkit generate from the RAML specification? <br/> ![pic_4](img/yt/pic_4.png)
   1. 1
   2. 2
   3. 3
   4. 4 <br/><br/>
9. ![pic_5_1](img/yt/pic_5_1.png) <br/> ![pic_5_2](img/yt/pic_5_2.png)
   1. "String"
   2. "XML"
   3. "Object"
   4. "Java" <br/><br/>
10. ![pic_6_1](img/yt/pic_6_1.png) <br/> ![pic_6_2](img/yt/pic_6_2.png)
    1. A file named productUpdates.txt.bak containing the text "FINISHED"
    2. A file named productUpdates.txt.bak containing the text "START"
    3. A file named productUpdates.txt containing the text "START" <br/> A file named productUpdates.txt.bak containing the text "FINISHED"
    4. A file named productUpdates.txt containing the text "START" <br/> A file named productUpdates.txt.bak containing the text "START" <br/><br/>
11. An API specification is defined using RAML. <br/> What is the next step to create a REST Connect connector from this API specification?
    1. Download the API specification and build the interface using APIkit
    2. Add the specification to a Mule project's src/main/resources/api folder
    3. Publish the API specification to Anypoint Exchange
    4. Implement the API specification using Flow Designer <br/><br/>
12. A client submits a GET request to a Mule 4 application to the endpoint /customers?id=48493. <br/> Where is the ID stored in the Mule event by the HTTP Listener?
    1. Attributes
    2. Variables
    3. Payload
    4. Inbound Properties <br/><br/>
13. A Mule application contains a global error handler configured to catch any errors. <br/> Where must the global error handler be specified so that it catches all errors from flows that do not have their own error handlers?
    1. In a configuration properties file
    2. In a pom.xml file
    3. In the mule-artifact.json file
    4. In the global element <br/><br/>
14. ![pic_7_1](img/yt/pic_7_1.png)
    1. ![pic_7_2](img/yt/pic_7_2.png) <br/><br/>
15. ![pic_8_1](img/yt/pic_8_1.png) <br/> ![pic_8_2](img/yt/pic_8_2.png)
    1. "Success - main flow"
    2. "Error - private flow"
    3. "Error - main flow"
    4. "Validation Error" <br/><br/>
16. ![pic_9](img/yt/pic_9.png) <br/><br/>
17. A development team was developing a mobile banking app. It took the team two months to create their own APIs to access transaction information from a central database. <br/> The development team later found out that anoter team had already build an API tha accessed this transaction information. <br/> According to MuleSoft, what organization structure could have saved the development team two months of development time?
    1. Center for Enablement
    2. MuleSoft Support Center
    3. Central API Review Board
    4. Center of Excellence <br/><br/>
18. What is the correct way to format the decimal 20.3844 as a string to two decimal places?
    1. 20.3844 format { String: ".0#" }
    2. 20.3844 as String ( {format: ".0#"} )
    3. 20.3844 {format: ".0·" as String}
    4. 20.3844 as String {format: ".0#"} <br/><br/>
19. An SLA-based policy has been enabled in API Manager. <br/> What should now be changed in the RAML specification and/or the API Proxy to enforce the SLA-based policy?
    1. Restart the API Proxy to clear the API policy cache
    2. Add new property placeholders and redeploy the API Proxy
    3. Add requeride headers to the RAML specification and redeploy the API Proxy
    4. Add new enviroment variables and restart the API Proxy <br/><br/>
20. A flow contains a Database Select operation followed by an HTTP Request operation. The flow must combine and return data recived from these two connector operations. <br/> What is a valid and idiomatic (use for its intended purpose) way to capture both payloads so the payload output from the second HTTP Request operation does not overwrite the payload output from the first Database Select operation?
    1. Save the payload from the Database Select operation to a variable
    2. Set the combined Payloads attribute to true in the Database Select operation configuration
    3. Put the Database Select operation in a Try scope configured with a transaction
    4. Put the Database Select operation inside a Cache scope <br/><br/>
21. ![pic_10](img/yt/pic_10.png)
    1. Deploy the dependency to a MuleSoft Maven repository
    2. Edit the dependency in the Mule project's pom.xml file
    3. Add the dependency to the MULE_HOME/lib/bin folder
    4. Install the dependency to the computer's local Maven repository <br/><br/>
22. ![pic_11](img/yt/pic_11.png) <br/><br/>
23. A Mule application contains two HTTP Listeners, each configured for different API endpoints: http://acme.com/apis/orders and http://acme.com/apis/customers. <br/> What base path value should be set in an HTTP Listener config element so that it can be used to configure both HTTP Listeners?
    1. /apis/
    2. /apis/?
    3. /apis/*
    4. /apis/orders|customers <br/><br/>
24. ![pic_12](img/yt/pic_12.png)
25. ![pic_13_1](img/yt/pic_13_1.png) <br/> ![pic_13_2](img/yt/pic_13_2.png)
    1. "US"
    2. "REGION"
    3. ["US", "EU"]
    4. "EU" <br/><br/>
26. ![pic_14](img/yt/pic_14.png)
    1. #[ 'MuleSoft' == payload.'company' ]
    2. #[ if( 'MuleSoft' == payload.company ) ]
    3. #[ if( company == "MuleSoft" ) ]
    4. #[ company = "MuleSoft" ] <br/><br/>
27. ![pic_15](img/yt/pic_15.png)
    1. '#['The year is ++ payload.year']'
    2. '#['The year is' ++ payload.year]'
    3. '#[The year is $(payload.year)]'
    4. 'The year is #[payload.year]' <br/><br/>
28. ![pic_16_1](img/yt/pic_16_1.png) <br/> ![pic_16_2](img/yt/pic_16_2.png)
    1. "Error - main flow"
    2. "Success - Begin main flow"
    3. "Success - End main flow"
    4. "Validate - Payload is an integer" <br/><br/>
29. Each HTTP Listener is configured with the same host and with the port number, path, and operation shown in its display name. <br/> What is the minimum number of global elemnts that must be defined to support these HTTP Listeners? <br/> ![pic_17](img/yt/pic_17.png)
    1. 1
    2. 2
    3. 3
    4. 4 <br/><br/>
30. A RAML example fragment named BankAccountsExample.raml is placed in the examples folder in an API specification project. <br/> What is the correct syntax to reference the fragment?
    1. examples: !include BankAccountsExample.raml
    2. examples: #import BankAccountsExample.raml
    3. examples: !include examples/BankAccountsExample.raml
    4. examples: #include examples/BankAccountsExample.raml <br/><br/>
31. What payload is returned by an Anypoint Connector for Database's Select operation that does not match any rows in the database?
    1. null
    2. An empty array
    3. An exception
    4. false <br/><br/>
32. ![pic_18](img/yt/pic_18.png)
    1. For Each scope: 2000, 200, 1000, 100 <br/> Batch Job scope: 4000, 40, 3000, 300
    2. For Each scope: 100, 200, 1000, 2000 <br/> Batch Job scope: 4000, 40, 3000, 300
    3. For Each scope: 2000, 200, 1000, 100 <br/> Batch Job scope: 40, 300, 3000, 4000
    4. For Each scope: 100, 200, 1000, 2000 <br/> Batch Job scope: 40, 300, 3000, 4000 <br/><br/>
33. What is the output type of the DataWeave map function?
    1. Array
    2. String
    3. Object
    4. Map <br/><br/>
34. ![pic_19](img/yt/pic_19.png)
    1. application/xml
    2. application/dw
    3. application/java
    4. application/json <br/><br/>
35. ![pic_20](img/yt/pic_20.png)
    1. Session variables
    2. Key-value pairs in the ObjectStore
    3. Properties of the Mule runtime app object
    4. Properties of the Mule runtime flow object <br/><br/>
36. ![pic_21_1](img/yt/pic_21_1.png) <br/> ![pic_21_2](img/yt/pic_21_2.png)
    1. ![pic_21_3](img/yt/pic_21_3.png) <br/><br/>
37. ![pic_22](img/yt/pic_22.png) <br/><br/>
38. To avoid hard-coding values, a flow uses some property placeholders and the corresponding values are stored in a configuration file. <br/> Where does the configuration file's location need to be specified in the Mule application?
    1. The pom.xml file
    2. A global element
    3. A flow attribute
    4. The mule-artifact.json file <br/><br/>
39. ![pic_23](img/yt/pic_23.png)
    1. /accounts/#[ID]
    2. /accounts/{ID}
    3. /accounts/ID
    4. #[/accounts/ID] <br/><br/>
40. ![pic_24_1](img/yt/pic_24_1.png)
    1. ![pic_24_2](img/yt/pic_24_2.png) <br/><br/>
41. ![pic_25_1](img/yt/pic_25_1.png)
    1. ![pic_25_2](img/yt/pic_25_2.png)
    2. ![pic_25_3](img/yt/pic_25_3.png) <br/><br/>
42. ![pic_26_1](img/yt/pic_26_1.png) <br/> ![pic_26_2](img/yt/pic_26_2.png)
    1. "ERROR2"
    2. "END"
    3. "ERROR1"
    4. "Validation Error" <br/><br/>
43. ![pic_27](img/yt/pic_27.png) <br/><br/>
44. ![pic_28](img/yt/pic_28.png)
    1. A property in the Consume operation equal to the destination query parameter
    2. A JSON payload before the Consume operation that contains the destination query parameter
    3. A SOAP payload before the Consume operation that contains the destination query parameter
    4. A header in the Consume operation equal to the destination query parameter <br/><br/>
45. A Scatter-Gather processes three separate HTTP requests. Each request returns a Mule Event with a JSON payload. <br/> What is the final output of the Scatter-Gather?
    1. An array of three Mule Event objects
    2. An object containing three JSON payload objects
    3. An object containing three Mule Event objects
    4. An array of three JSON payload objects <br/><br/>
46. ![pic_29_1](img/yt/pic_29_1.png)
    1. ![pic_29_2](img/yt/pic_29_2.png) <br/><br/>
47. ![pic_30_1](img/yt/pic_30_1.png)
    1. ![pic_30_2](img/yt/pic_30_2.png) <br/><br/>
48. ![pic_31_1](img/yt/pic_31_1.png) <br/> ![pic_31_2](img/yt/pic_31_2.png)
    1. "Success - main flow"
    2. "HTTP: NOT FOUND"
    3. "APP: API RESOURCE NOT FOUND"
    4. "Other error" <br/><br/>
49. ![pic_32_1](img/yt/pic_32_1.png) <br/> ![pic_32_2](img/yt/pic_32_2.png)
    1. 1
    2. 2
    3. 3
    4. 4 <br/><br/>
50. In an application network, the implementation, not the interface, of a product API is being changed. <br/> Does anything need to change in the other APIs associated applications that consume the product API, and if so, what are these changes?
    1. The other APIs must be updated to consume the updated product API
    2. The applications associated with the other APIs must be recoded
    3. Nothing needs to be changed in the other APIs or their associated applications
    4. The application associated with the other APIs must be restarted <br/><br/>
51. ![pic_33](img/yt/pic_33.png) <br/><br/>
52. ![pic_34](img/yt/pic_34.png)
    1. The payload <br/> The modelName query param
    2. The payload <br/> The planeModel var
    3. The payload
    4. The payload <br/> The modelName query param <br/> The planeModel var <br/><br/>
53. ![pic_35](img/yt/pic_35.png)
    1. 100
    2. An empty array
    3. The database response
    4. The entire CSV file <br/><br/>
54. ![pic_36_1](img/yt/pic_36_1.png) <br/> ![pic_36_2](img/yt/pic_36_2.png)
    1. ![pic_36_3](img/yt/pic_36_3.png) <br/><br/>
55. ![pic_37](img/yt/pic_37.png)
    1. Validation Error
    2. "After"
    3. "Before"
    4. null <br/><br/>
56. ![pic_38](img/yt/pic_38.png) <br/><br/>
57. ![pic_39](img/yt/pic_39.png) <br/><br/>
58. ![pic_40](img/yt/pic_40.png) <br/><br/>
59. ![pic_41](img/yt/pic_41.png) <br/><br/>

### Fin del cuestionario de prueba 4 😙

---

### [Respuestas y explicaciones](respuestas_4.md)

### [Cuestionario de prueba 1](cuestionario_1.md)

### [Cuestionario de prueba 2](cuestionario_2.md)

### [Cuestionario de prueba 3](cuestionario_3.md)

---