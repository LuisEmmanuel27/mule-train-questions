# Cuestionario de prueba 1

Cuestionario de prueba para el examen de certificación de Mulesoft con Explicaciones incluidas

## [Respuestas y explicaciones](respuestas_1.md)

---

1. This Mule application has an HTTP Request that is configured with hardcoded values. To change this, the Mule application is configured to use a properties file named config.yaml. <br/> What valid expression can the HTTP Request host value be set to so that it is no longer hardcoded? <br/> ![pic_1](img/cues_1/pic_1.webp)
   1. $[training:host]
   2. #[training.host]
   3. #{training.host}
   4. ${training.host} <br/><br/>
2. What is the correct syntax to define and and call a function in Dataweave script?

```dw
i.
fun addKV( object: Object, key: String, value: Any) =           
           object ++ {(key):(value)}
 
---
 
addKV ( {"hello': "world"}, "hola", "mundo" )
```

```dw
ii.
%function addKV( object: Object, key: String, value: Any) =           
                  object ++ {(key):(value)}
 
---
 
{ hello: "world"} addKV ( "hola","mundo" )
```

```dw
iii.
%function addKV( object: Object, key: String, value: Any) =           
                 object ++ {(key):(value)}
 
---
 
addKV ( {"hello': "world"}, "hola", "mundo" )
```

```dw
iv.
fun addKV( object: Object, key: String, value: Any) =           
           object ++ {(key):(value)}
 
---
 
{ hello: "world"} addKV ( "hola","mundo" )
```

3. What is correct syntax for a Logger component to output a message with the contents of a JSON Object payload?
   1. The payload is: $(payload)
   2. #["The payload is " ++ payload]
   3. The payload is: #[payload]
   4. #["The payload is " + payload] <br/><br/>
4. Refer to the exhibits. A web client submits the request to ***`http://localhost:8081/flights?destination=SFO`*** and the Web Service Consumer throws a WSC:BAD_REQUEST error. What is the next step to fix this error? <br/> ![pic_2](img/cues_1/pic_2.webp)
   1. Set a header in Consume operation equal to destination query parameter
   2. Set a JSON payload before the Consume operation that contains the destination query parameter
   3. Set a SOAP payload before the Consume operation that contains the destination query parameter
   4. Set a property in Consume operation equal to destination query parameter <br/><br/>
5. Refer to exhibits. What message should be added to Logger component so that logger prints "The city is Pune" (Double quote should not be part of logged message)? <br/> ![pic_3](img/cues_1/pic_3.webp)
   1. #["The city is" ++ payload.City]
   2. The city is #[payload.City]
   3. #[The city is ${payload.City}
   4. The city is + #[payload.City] <br/><br/>
6. Refer to the exhibit. What is the output of Logger activity named payload in the On Complete phase? <br/> ![pic_4](img/cues_1/pic_4.webp)
   1. Summary statistics with No record data
   2. The records are processed by all batch steps
   3. The records are processed by last batch step
   4. The original payload : [1,2,3] <br/><br/>
7. A Mule application configured with _Autodiscovery_ implements an API. <br/> Where is governance enforced for policies defined for this Mule application?
   1. In API Exchange
   2. In Runtime Manager
   3. In the Mule Application
   4. In API Manager <br/><br/>
8. Following Mulesoft's recommended API-led connectivity approach , an organization has created an application network. The organization now needs to create API's to transform , orchestrate & aggregate the data provided by the other API's in the application network.  This API should be flexible enough to handle the data from additional API's in future. <br/> According to Mulesoft's recommended API-led connectivity approach , what is the best layer for this new API?
   1. Experience Layer
   2. System Layer
   3. Data Layer
   4. Process Layer <br/><br/>
9. Refer to the exhibits. As a Mulesoft developer, what you would change in Database connector configuration to resolve this error? <br/> ![pic_5](img/cues_1/pic_5.webp) <br/> ![pic_6](img/cues_1/pic_6.jpg)
   1. Configure the correct JDBC Driver
   2. Configure the correct table name
   3. Configure the correct database name
   4. Configure the correct host URL <br/><br/>
10. Refer to the exhibits. The mule application is debugged in Anypoint Studio and stops at the breakpoint as shown in below exhibit. <br/> What is the value of the payload displayed in the debugger at this breakpoint? <br/> ![pic_7](img/cues_1/pic_7.webp)
    1. Finished
    2. Process
    3. Payload is always empty at the breakpoint
    4. Start <br/><br/>
11. What statement is a part of MuleSoft's description of an application network?
    1. Leverages Central IT to deliver complete point-to-point solutions with master data management
    2. Creates and manages a collection of JMS messaging services and infrastructure
    3. Creates and manages high availability and fault tolerant services and infrastructure
    4. Creates reusable APIs and assets designed to be consumed by other business units <br/><br/>
12. Refer to the exhibits. Each route in the Scatter-Gather sets the payload to the number shown in the label. <br/> What response is returned to a web client request to the HTTP Listener? <br/> ![pic_8](img/cues_1/pic_8.webp) <br/> ![pic_9](img/cues_1/pic_9.webp)

```ts
// i.
["100","200]
```

```json
// ii.
{	
  "0" : "100",	
  "1" : "200"
}
```

```json
// iii.
[	{		
    "attributes": ...,		
    "payload": "100"	
  },	
  {		
    "attributes": ...,		
    "payload": "200"	
  }
]
```

```json
// iv.
{	
  "0": {		
    "attributes": ...,		
    "payload": "100"	
  },	
  "1": {		
    "attributes": ...,		
    "payload": "200"	
  }
}
```

13. Refer to the exhibits. What payload and variable are logged at the end of the main flow? <br/> ![pic_10](img/cues_1/pic_10.webp) <br/> ![pic_11](img/cues_1/pic_11.webp)
    1. [[5,10,15,20], 1]
    2. [[5,10,15,20], 5]
    3. [[Req5, Req10, Req15, Req20], 5]
    4. [[Req5, Req10, Req15, Req20], 1] <br/><br/>
14. A flow has a JMS Publish consume operation followed by a JMS Publish operation. Both of these operations have the default configurations. Which operation is asynchronous and which one is synchronous?
    1. Publish consume: Asynchronous. <br/> Publish: Synchronous
    2. Publish consume: Synchronous. <br/> Publish: Synchronous
    3. Publish consume: Asynchronous. <br/> Publish: Asynchronous
    4. Publish consume: Synchronous. <br/> Publish: Asynchronous <br/><br/>
15. How can you call a flow from Dataweave?
    1. tag function
    2. include function
    3. lookup function
    4. Not Allowed <br/><br/>
16. What is the correct Syntax to add a customerID as a URI parameter in the HTTP listener's path attribute? <br/> ![pic_12](img/cues_1/pic_12.webp)
    1. {customerID}
    2. $[customerID]
    3. #[customerID]
    4. (customerID) <br/><br/>
17. Refer to the exhibits. What expression correctly specifies input parameters to pass the city and state values to SQL query? <br/> ![pic_13](img/cues_1/pic_13.webp)
    1. #[inputParams: { city: "San Fransisco", state: "CA"}]
    2. #[inputParams: [ "San Fransisco", "CA"]]
    3. #[{ city: "San Fransisco", state: "CA"}]
    4. #[[ "San Fransisco", "CA"]] <br/><br/>
18. An API instance of type API endpoint with API proxy is created in API manager using an API specification from Anypoint Exchange. The API instance is also configured with an API proxy that is deployed and running in CloudHub. <br/> An SLA- based policy is enabled in API manager for this API instance. <br/> Where can an external API consumer obtain a valid client ID and client secret to successfully send requests to the API proxy?
    1. In the organization's public API portal in Anypoint Exchange, from an approved client application for the API proxy
    2. In Anypoint Studio, from components generated by APIkit for the API specification
    3. In Runtime Manager, from the properties tab of the deployed approved API proxy
    4. In Anypoint Studio, from components generated by Rest Connect for API specification <br/><br/>
19. Refer to the exhibits. The validation component in the private flow throws an error. What response message is returned to a client request to the main flow's HTTP Listener? <br/> ![pic_14](img/cues_1/pic_14.webp) <br/> ![pic_15](img/cues_1/pic_15.webp)
    1. Validation Error
    2. Error - private flow
    3. Success - main flow
    4. Error - main flow <br/><br/>
20. What the correct RAML syntax which retrieves details on a specific order by its orderId as a URI parameter?

```yaml
# i.
/orders:  
      get:     
        /{orderId}:
```

```yaml
# ii.
/orders:  
      /orderId:    
         get:
```

```yaml
# iii.
/orders:  
   /{orderId}:    
      get:
```

```yaml
# iv.
/orders:  
     /get:       
        /orderId
```

21. Refer to the exhibits. The Batch job processes an array of strings. <br/> What information is logged by the logger component after the batch job scope completes processing of the input payload? <br/> ![pic_16](img/cues_1/pic_16.webp) <br/> ![pic_17](img/cues_1/pic_17.webp)
    1. Total Records Processed: 3 <br/> Successful Records: 3 <br/> Failed Records: 0 <br/> payload: ["A","B","C"]
    2. Total Records Processed: 3 <br/> Successful Records: 3 <br/> Failed Records: 0
    3. Total Records Processed: 3 <br/> Successful Records: 3 <br/> Failed Records: 0 <br/> payload: ["a","b","c"]
    4. ["A","B","C"] <br/><br/>
22. Refer to the exhibit. What is the correct DataWeave expression for the Set Payload transformer to call the createCustomerObject flow with values for the first and last names of a new customer? <br/> ![pic_18](img/cues_1/pic_18.webp)
    1. `lookup("createCustomerObject", {first: "Alice, last: "Green"})`
    2. `lookup( "createCustomerObject", ("Alice", "Green"))`
    3. `createCustomerObject({first: "Alice", last' "Green"})`
    4. `createCustomerObject("Alice", "Green")` <br/><br/>
23. Refer to the exhibits. A web client submits the request to the HTTP Listener. What response message would be returned to web client? <br/> ![pic_19](img/cues_1/pic_19.webp)
    1. String is not blank
    2. No response would be sent back to client and request will get errored out in Mule
    3. End
    4. Start <br/><br/>
24. What HTTP method in a RESTful web service is typically used to completely replace an existing resource?
    1. PUT
    2. GET
    3. POST
    4. PATCH <br/><br/>
25. What is the main purpose of flow designer in Design Center?
    1. To design and mock Mule application templates that must be implemented using Anypoint Studio
    2. To design API RAML files in a graphical way
    3. To define API lifecycle management in a graphical way
    4. To design and develop fully functional Mule applications in a hosted development environment <br/><br/>
26. In the execution of scatter gather, the "sleep 2 sec" Flow Reference takes about 2 sec to complete, and the "sleep 8 sec" Flow Reference takes about 8 sec to complete. <br/> About how many sec does it take from the Scatter-Gather is called until the Set Payload transformer is called? <br/> ![pic_20](img/cues_1/pic_20.webp)
    1. 10
    2. 2
    3. 0
    4. 8 <br/><br/>
27. Refer to the exhibits. A web client sends a POST request to the HTTP Listener with the payload “Hello-“. <br/> What response is returned to the web client? <br/> ![pic_21](img/cues_1/pic_21.webp) <br/> ![pic_22](img/cues_1/pic_22.webp) <br/> ![pic_23](img/cues_1/pic_23.webp)
    1. Hello-HTTP-Three
    2. Hello-JMS1-HTTP-JMS2-Three
    3. Hello-HTTP-JMS2-Three
    4. HTTP-JMS2-Three <br/><br/>
28. What is output of Dataweave flatten function?
    1. Array
    2. LinkedHashMap
    3. Map
    4. Object <br/><br/>
29. Refer to the exhibits. Client sends the request to _ClientRequestFlow_ which calls _ShippingFlow_ using HTTP Request activity. <br/> During E2E testing it is found that that _HTTP:METHOD_NOT_ALLOWED_ error is thrown whenever client sends request to this flow. <br/> What attribute you would change in _ClientRequestFlow_ to make this implementation work successfully? <br/> ![pic_24](img/cues_1/pic_24.webp) <br/> ![pic_25](img/cues_1/pic_25.jpg) <br/> ![pic_26](img/cues_1/pic_26.webp)
    1. Change the allowed method attributes value to "POST"
    2. Change the protocol attribute value to "HTTPS"
    3. Change the path attribute value to "/api/ship"
    4. Change the method attribute value to "*" <br/><br/>
30. An organization is beginning to follow Mulesoft's recommended API led connectivity approach to use modern API to support the development and lifecycle of the integration solutions and to close the IT delivery gap. <br/> What distinguishes between how modern API's are organized in a MuleSoft recommended API-led connectivity approach as compared to other common enterprise integration solutions?
    1. The APIO implementations are monitored with common tools, centralized monitoring and security systems
    2. The API interfaces are specified as macroservices with one API representing all the business logic of an existing and proven end to end solution
    3. The API interfaces are specified at a granularity intended for developers to consume specific aspect of integration processes
    4. The API implementation are built with standards using common lifecycle and centralized configuration management tools <br/><br/>
31. An organization's Center for enablement (C4E) has built foundational assets (API specifications and implementation templates, common frameworks, and best practices guides) and published them to _Anypoint Exchange_. <br/> What is a metric related to these foundational assets that helps the organization measure the success of it's C4E efforts?
    1. Correlation of each foundational asset with the counts of developers that download such asset
    2. Count how many Lines of Business (LoBs) onsumed each foundational asset
    3. Correlation of key performance indicators (KPI) of production applications with foundational assets
    4. Utilization counts of foundational assets in production applications <br/><br/>
32. Refer to the exhibits. The Mule application configures and uses two HTTP Listener global configuration elements. <br/> Mule application is run in Anypoint Studio. <br/> If the mule application starts correctly, what URI and port numbers can receive web client requests? <br/> If the mule applications fails to start , what is the reason for the failure? <br/> ![pic_27](img/cues_1/pic_27.webp) <br/> ![pic_28](img/cues_1/pic_28.webp) <br/> ![pic_29](img/cues_1/pic_29.webp)
    1. The mule application start successfully <br/> Web client requests can be only received at URI on port 2222 but not on port 3333
    2. The mule application fails to start because of the port binding conflict as HTTP request also use same port i.e. 3333
    3. The mule application start successfully <br/> Web client requests can be received at URI on port 2222 and on port 3333
    4. The mule application fails to start <br/> There is URL path conflict because both HTTP Listeners are configured with same path <br/><br/>
33. Refer to the exhibits. All three of the conditions for the Choice router are true. What messages are written in the application log? <br/> ![pic_30](img/cues_1/pic_30.webp)
    1. Route 1, Route 2, Default
    2. Route 2
    3. Route 1, Route 2
    4. Route 1 <br/><br/>
34. The main flow contains an HTTP Request in the middle of the flow. The HTTP Listeners and HTTP Request use default configurations. <br/> A web client sends a GET request to the main flow’s HTTP Listener. The GET request includes query for the pedigree of a piano. <br/> What values are accessible to the Logger component at the end of the main flow? <br/> ![pic_31](img/cues_1/pic_31.webp) <br/> ![pic_32](img/cues_1/pic_32.webp)
    1. All Mule Events
    2. payload and all attributes
    3. payload and all variable
    4. payload <br/><br/>
35. Refer to the exhibit. The default scope in choice router recursively calls the color flow. <br/> A web client sends a PUT request to the HTTP listener with payload Blue. <br/> What response is returned to the web client? <br/> ![pic_33](img/cues_1/pic_33.webp)
    1. "Blk"
    2. Timeout Error
    3. ["Blue", "Red", "Blk"]
    4. "Green" <br/><br/>
36. What of the below is not a feature of API Notebooks?
    1. Creates a client for an API
    2. Creates a mock service for an API
    3. Perform authenticated live calls on a real server
    4. API documentation <br/><br/>
37. How would you debug Mule applications?
    1. By Deploying apps on production
    2. Checking RAML specifications
    3. Using Debugger Component
    4. Use third party debugger application <br/><br/>
38. Refer to the exhibits. The main flow is configured with three error handlers. A web client submits the request to the HTTP Listener and the HTTP Request throws an HTTP:NOT_FOUND error. What response message is returned? <br/> ![pic_34](img/cues_1/pic_34.webp)
    1. HTTP:NOT_FOUND
    2. Other Error
    3. Success - main flow
    4. APP: API RESOURCE NOT FOUND <br/><br/>
39. What should this endpoint return considering the API is build using standard practices? <br/> `http://dev.acme.com/api/patients?year=2022`
    1. All patients
    2. Patient with id 2022
    3. Patients from year 2022
    4. No patients <br/><br/>
40. Which of the module is imported automatically in Dataweave scripts?
    1. dw::Runetime
    2. dw::System
    3. dw::core
    4. dw::Systemcore <br/><br/>
41. What object type is returned by the File List operation?
    1. Array of Mule Event Objects
    2. Array of String File Names
    3. Object of Mule Event Objects
    4. Object of String of File of Names <br/><br/>
42. Refer to the exhibits. What payload is logged at the end of the main flow? <br/> ![pic_35](img/cues_1/pic_35.webp)
    1. order4
    2. `[1,2,3,4]`
    3. order1order2order3order4
    4. `[order1, order2, order3, order4]` <br/><br/>
43. Which out of below is not an asset?
    1. Exchange
    2. Connector
    3. Example
    4. Template <br/><br/>
44. A company has defined two RAML fragments, Book Data Type and Book Example to be used in APIs. <br/> What would be valid RAML to use these fragments? <br/> ![pic_36](img/cues_1/pic_36.webp) <br/> ![pic_37](img/cues_1/pic_37.webp)

```yaml
# i.

#%RAML 1.0title: 
Bookstypes: 
Book: bookDataType.raml
/books: 
 post:  
   body:   
     application/json:    
        type: Book     
          examples:        
            input: !include bookDataType.raml
   responses:      
     201:           
       body:          
         application/json:           
            example:              
               message: Book added
```

```yaml
# ii.

#%RAML 1.0title: 
Bookstypes: 
Book: ABC/Examples/bookDataType.raml
/books: 
 post:  
   body:   
     application/json:    
        type: Book     
          examples:        
            input: ABC/Examples/bookExample.raml  
   responses:      
     201:           
       body:          
         application/json:           
            example:              
               message: Book added
```

```yaml
# iii.

#%RAML 1.0title: 
Bookstypes: 
Book: !include bookDataType.raml
/books: 
 post:  
   body:   
     application/json:    
        type: Book     
          examples:        
            input: !include bookDataType.raml
   responses:      
     201:           
       body:          
         application/json:           
            example:              
               message: Book added
```

```yaml
# iv.

#%RAML 1.0
title: Books
types:  
    Book: !include bookDataType.raml
/books:   
    post:    
      body:      
         application/json:      
         type: Book      
         examples:        
               input: !include bookExample.raml    
      responses:      
         201:        
           body:           
             application/json:           
                example:             
                    message: Book added
```

45. Refer to the exhibits. In the choice router, the When expression for the domestic shipping route is set to <br/> `"#[payload= "FR"]"` <br/> What is the output of logger after the execution of choice router is completed? <br/> ![pic_38](img/cues_1/pic_38.webp)
    1. "International"
    2. "US"
    3. A dataweave syntax error
    4. "Domestic" <br/><br/>
46. Refer to the exhibits. The Database Select operation returns five rows from a database. <br/> What is logged by the Logger component? <br/> ![pic_39](img/cues_1/pic_39.webp) <br/> ![pic_40](img/cues_1/pic_40.webp)
    1. Array
    2. Object
    3. LinkedHashMap
    4. CaseInsensitiveHashMap <br/><br/>
47. How to import Core (dw::Core) module into your DataWeave scripts?
    1. import core
    2. import dw::core
    3. #include dw::core
    4. Not Needed <br/><br/>
48. Refer to the exhibits. The Batch Job scope contains two Batch Steps scopes with different accept expression. <br/> The input payload is passed to the Batch Job scope. <br/> After the entire payload is processed by the batch job scope , what messages have been logged by the Logger component? <br/> ![pic_41](img/cues_1/pic_41.webp) <br/> ![pic_42](img/cues_1/pic_42.webp) <br/> ![pic_43](img/cues_1/pic_43.webp)

```js
// i.
{amount=140}
{amount=102}
{step2amount=100}
```

```js
// ii.
{amount=140}
{amount=102}
{step2amount=100}
{step2amount=140}
{step2amount=102}
```

```js
// iii.
{amount=140}
{amount=102}
{step2amount=100}
{step2amount=140}
```

```js
// iv.
{amount=140}
{amount=102}
{step2amount=100}
{step2amount=40}
```

49. Mule application contains ActiveMQ JMS dependency. Mule application was compiled and run successfully in Anypoint Studio. <br/> The mule application must now be exported from Anypoint Studio and shared with other developer. <br/> What export options should be selected to create the smallest JAR file that can be imported into other developer's Anypoint Studio and run successfully?
    1. Select both Attach Project Sources and Include project modules and dependencies option
    2. Select only Attach Project Sources only
    3. Select the Include project modules and dependencies option only
    4. De-select both Attach Project Sources and Include project modules and dependencies option <br/><br/>
50. Refer to the exhibits. What is valid text to set the user field in the Database connector configuration to the username value specified in the config.yaml file? <br/> ![pic_44](img/cues_1/pic_44.webp)
    1. #[db:username]
    2. #[db.username]
    3. ${db.username}
    4. ${db:username} <br/><br/>
51. How are query parameters dynamically passed to an outbound REST request using an HTTP Request operation?
    1. As flow variable
    2. In the Mule event's Payload
    3. As query parameters in the HTTP Request Operation
    4. As URI parameters in the HTTP Request Operation <br/><br/>
52. Refer to the exhibits. What can be added to the flow to persist data across different flow executions? <br/> ![pic_45](img/cues_1/pic_45.webp)
    1. Key/value pair in Object store
    2. Session variables
    3. Properties of mule runtime app Object
    4. Properties of Mule runtime flow Object <br/><br/>
53. Refer to the exhibit. This RAML specification includes a resource and method to retrieve accounts by account_type and industry. <br/> What is the correct URI to get all retail finance accounts? <br/> ![pic_46](img/cues_1/pic_46.webp)
    1. `/accounts?account_type:retail?industry:finance`
    2. `/accounts/retail/finance`
    3. `/accounts?account_type:retail&industry:finance`
    4. `/accounts?account_type=retail&industry=finance` <br/><br/>
54. Mule application contains two HTTP Listeners, each configured for different API endpoints: <br/> `http://trainingdemo.com/apis/orders` and `http://trainingdemo.com/apis/customers`. <br/> What base path value should be set in an HTTP Listener config element so that it can be used to receive requests for both the API endpoints mentioned above?
    1. /apis/
    2. /apis/orders|customers
    3. /apis/?
    4. /apis/* <br/><br/>
55. Refer to the exhibits. What is written to the records.csv when the flow executes? <br/> ![pic_47](img/cues_1/pic_47.webp)
    1. An error message
    2. JSON payload
    3. payload converted to csv
    4. Nothing <br/><br/>
56. Refer to the exhibits. In the color flow , both the variable named color and payload are set to "red". <br/> An HTTP POST request is then sent to the decideColor flow's HTTP Listener. <br/> What is the payload value at the Logger component after the HTTP request completes? <br/> ![pic_48](img/cues_1/pic_48.webp) <br/> ![pic_49](img/cues_1/pic_49.webp)
    1. red
    2. error message
    3. white
    4. blue <br/><br/>
57. Refer to the exhibits. The web client sends a POST request to the ACME Order API with an XML payload. An error is returned. <br/> What should be changed in the request so that a success response code is returned to the web client? <br/> ![pic_50](img/cues_1/pic_50.webp)
    1. Set a request header with the name Content-Type to a value of application/octet-stream
    2. Set a request header with the name Content-Type to a value of application/xml
    3. Set a response header with the name Content-Type to a value of application/xml
    4. Set a response header with the name Content-Type to a value of application/octet-stream <br/><br/>
58. Refer to the exhibits. APIKit router is used to generate the flow components for RAML specification. <br/> The Mule application must be available to REST clients using the two URL's <br/> `http://localhost:8081/internal` and `http://localhost:8081/external` <br/> How many APIKit Router components are generated to handle requests to every endpoint defined in RAML specification?
    ```yaml
    Library.raml
    /books
            get:      
            post:
    /order:
            get:
            patch:
    /members
            get:
    ```
    1. 3
    2. 5
    3. 2
    4. 4
59. Refer to the exhibit. A Mule event is composed of a hierarchy of objects. Where in the hierarchy are variables stored? <br/> ![pic_51](img/cues_1/pic_51.webp)
    1. Mule message
    2. Mule message attributes
    3. Mule message payload
    4. Mule event <br/><br/>
60. What is the trait name you would use for specifying client credentials in RAML?
    1. cannot be specified in RAML
    2. client-id-required
    3. client-id
    4. headers <br/><br/>

### Fin del cuestionario de prueba 1 😀

---

### [Respuestas y explicaciones](respuestas_1.md)

### [Cuestionario de prueba 2](cuestionario_2.md)

---