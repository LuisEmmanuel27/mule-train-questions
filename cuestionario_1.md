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
11. 