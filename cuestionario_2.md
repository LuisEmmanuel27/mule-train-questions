# Cuestionario de prueba 2

Segundo cuestionario de prueba para el examen de certificación de Mulesoft con Explicaciones incluidas

## [Respuestas y explicaciones](respuestas_2.md)

---

1. Refer to the exhibit. The error occurs when a project is run in Anypoint Studio. The project, which has a dependency that is not in the MuleSoft Maven repository, was created and successfully run on a different computer. What is the next step to fix the error to get the project to run successfully? <br/> ![pic_1](img/cues_2/pic_1.webp)
   1. Install the dependency to the computer's local Maven repository
   2. Add the dependency to the MULE_HOME/bin folder
   3. Edit the dependency in the Mule project's pom.xml file
   4. Deploy the dependency to MuleSoft's Maven repository <br/><br/>
2. According to MuleSoft, what is the Center for Enablement’s role in the new IT operating model?
   1. Implements line of business projects to enforce common security requirements
   2. Creates and manages discoverable assets to be consumed by line of business developers
   3. Implements line of business projects to enforce common security requirements
   4. Centrally manages partners and consultants to implement line of business projects <br/><br/>
3. As a part of requirement , application property defined below needs to be accessed as Dataweave expression. What is the correct expression to map it to port value?
   1. `{ port : p('db.port')}`
   2. `{ port : p['db.port']}`
   3. Application property cannot be accessed in Dataweave
   4. `{ port : {db:port}}` <br/><br/>
4. Refer to the exhibit. What payload is returned when client sends request to `http://localhost:8081/`? <br/> ![pic_2](img/cues_2/pic_2.webp)
   1. 1
   2. 2
   3. 3
   4. 4 <br/><br/>
5. Refer to the exhibits. A web client submits a request to below flow. What is the output at the end of the flow? <br/> ![pic_3](img/cues_2/pic_3.webp) <br/> ![pic_4](img/cues_2/pic_4.webp) <br/> ![pic_5](img/cues_2/pic_5.webp)
   1. Java
   2. XML
   3. String
   4. Object <br/><br/>
6. Which of the below functionality is provided by zip operator in DataWeave?
   1. Merges elements of two lists (arrays) into a single list
   2. All of the above
   3. Minimize the size of long text using encoding.
   4. Used for sending attachments <br/><br/>
7. Refer to the exhibits. What is the response received when a client submits a GET request to `http://localhost:8081`? <br/> ![pic_6](img/cues_2/pic_6.webp)
   1. Before
   2. After
   3. null
   4. Validation error <br/><br/>
8. There are three routes configured for Scatter-Gather and incoming event has a payload is an Array of three objects. How routing will take place in this scenario?
   1. Incoming array objects would be split into three and each part would be sent to one route each in parallel
   2. Incoming array objects would be split into three and each part would be sent to one route each in sequential manner
   3. Entire event would be sent to each route sequentially
   4. Entire event would be sent to each route in parallel <br/><br/>
9. A Utlility.dwl is located in a Mule project at src/main/resources/modules. <br/> The Utility.dwl file defines a function named encryptString that encrypts a String What is the correct DataWeave to call the encryptString function in a Transform Message component?

```js
// i.
%dw 2.0
output application/json
import modules::Utility
---
Utility::encryptString( "John Smith" )
```

```js
// ii.
%dw 2.0
output application/json
import modules.Utility
---
Utility.encryptString( "John Smith" )
```

```js
// iii.
%dw 2.0
output application/json
import modules::Utility
---
encryptString( "John Smith" )
```

```js
// iv.
%dw 2.0
output application/json
import modules.Utility
---
encryptString( "John Smith" )
```

10. A Database On Table Row listener retrieves data from a CUSTOMER table that contains a primary key user_id column and an increasing login_date_time column. Neither column allows duplicate values. How should the listener be configured so it retrieves each row at most one time?
    1. Set the watermark column to the user_id column
    2. Set the target value to the last retrieved user_id value
    3. Set the watermark column to the login_date_time column
    4. Set the target value to the last retrieved login_date_time value <br/><br/>
11. Refer to the exhibit. What DataWeave expression transforms the example XML input to the CSV output? <br/> ![pic_7](img/cues_2/pic_7.webp)

```js
// i.
%dw 2.0
output application/csv
---
payload.sale.item map ((value, index) -> {
index: index,
sale: value.saleId,
itemName: value.desc,
itemPrice: (value.quantity) * (value.price),
item: value.itemId
} )
```

```js
// ii.
%dw 2.0
output application/csv
---
payload.sale.item map ((value, index) -> {
index: index,
sale: value.@saleId,
itemName: value.desc,
itemPrice: (value.quantity) * (value.price),
item: value.@itemId
} )
```

```js
// iii.
%dw 2.0
output application/csv
---
payload.sale.*item map ((value, index) -> {
index: index,
sale: value.@saleId,
itemName: value.desc,
itemPrice: (value.quantity) * (value.price),
item: value.@itemId
} )
```

```js
// iv.
%dw 2.0
output application/csv
---
payload.sale.*item map ((value, index) -> {
index: index,
sale: value.saleId,
itemName: value.desc,
itemPrice: (value.quantity) * (value.price),
item: value.itemId
} ) a
```

12. 