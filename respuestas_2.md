# Respuestas del segundo cuestionario

1. `i.` - `Install the dependency to the computer's local Maven repository`
   1. **Explicación:** As dependency is not present in Mulesoft Maven repository, we need to install the dependency on computer's local Maven repository. <br/><br/>
2. `ii.` - `Creates and manages discoverable assets to be consumed by line of business developers`
   1. **Explicación:** C4E does not get directly involved in projects. <br/> ![pic_1](img/resp_2/pic_1.webp) <br/><br/>
3. `i.` - `{ port : p('db.port')}`
   1. **Explicación:** <h3>p(String): String</h3> This function returns a string that identifies the value of one of these input properties: Mule property placeholders, System properties, or Environment variables. <br/> The `p` function returns a `null` value if the property is not set or if the function does not find the property. <h3>Parameters</h3> `propertyName` --> A string that identifies property. <br/> **Example** <br/> This example logs the value of the property `http.port` in a Logger component.
      ```xml
      <flow name="simple"> 
          <logger level="INFO" doc:name="Logger"   
          message="#[Mule::p('http.port')]"/>
      </flow>
      ```
    <br/>
4. `iii.` - `3`
   1. **Explicación:** The flow can be described as below. <br/> 1) First HTTP POST requets is made in which paylaod is set to 1 and it gets returned to our mail flow. <br/> 2) Second call is initiated for JMS Publish Consume JMS: num1 which add 1 to the payload which makes it as 2. Note that pubih consume is a synchronous operation. Hence paylaod is returned to main flow. <br/> 3) Third call is initiated for JMS Publish JMS: num2 which add 1 to the payload . Note that pubih is asynchronous operation. Hence paylaod is never returned to main flow. So payload in main flow is still 2. <br/> 4) Finally Set Payload increments payload by 1 making payload as 3 which is returned by the flow. Hence option 3 is the correct answer. <br/><br/>
5. `iii.` - `String`
   1. **Explicación:** It will not be object. Because then you would need to set MIME Type as application/xml in Set Payload properties. But doing so will add that information in configuration xml which would be something like below. <br/> `doc:name="Set Payload" doc:id="e06e16d8-0b6e-41cd-af4e-08439bc9f8be" mimeType="application/xml"/>` <br/> In question , configuration xml snap does not mention about using any such mimeType so we can assume that it has default value which plaintext. Hence String is the correct answer as it is type associated with plain text. <br/><br/>
6. `i.` - `Merges elements of two lists (arrays) into a single list`
   1. **Explicación:** [Reference Doc](https://docs.mulesoft.com/dataweave/latest/dw-core-functions-zip). <br/><br/>
7. `iv.` - `Validation error`
   1. **Explicación:** Flow: <br/> 1) Payload is  set to “Before” <br/> 2) Is null validation is used which will pass the message only if payload is null. In this case as payload is not null, it creates an Error Object. Flow execution stops <br/> #[error.description] = “Validation error” <br/> 3) Because no error handler is defined, the Mule default error handler handles the error <br/> 4) “Validation error” is the error message returned to the requestor in the body of the HTTP request with HTTP Status Code: 500 <br/> ![pic_2](img/resp_2/pic_2.webp) <br/><br/>
8. `iv.` - `Entire event would be sent to each route in parallel`
   1. **Explicación:** Entire event would be sent to each route in parallel. <br/> Scatter-Gather works as follows : <br/> - The Scatter-Gather component receives a Mule event and sends a reference of this Mule event to each processing route. <br/> - Each of the processing routes starts executing in parallel. After all processors inside a route finish processing, the route returns a Mule event, which can be either the same Mule event without modifications or a new Mule event created by the processors in the route as a result of the modifications applied. <br/> - After all processing routes have finished execution, the Scatter-Gather component creates a new Mule event that combines all resulting Mule events from each route, and then passes the new Mule event to the next component in the flow. <br/><br/>
9. `i.`
   1. **Explicación:** DataWeave 2.0 functions are packaged in modules. Before you begin, note that DataWeave 2.0 is for Mule 4 apps. For Mule 3 apps, refer to DataWeave Operators in the Mule 3.9 documentation. For other Mule versions, you can use the version selector for the Mule Runtime table of contents. <br/> Functions in the Core (`dw::Core`) module are imported automatically into your DataWeave scripts. To use other modules, you need to import the module or functions you want to use by adding the import directive to the head of your DataWeave script, for example: <br/> `import dw::core::Strings` <br/> `import camelize, capitalize from dw::core::Strings` <br/> `import * from dw::core::Strings` <br/> The way you import a module impacts the way you need to call its functions from a DataWeave script. If the directive does not list specific functions to import or use `* from` to import all functions from a function module, you need to specify the module when you call the function from your script. For example, this import directive does not identify any functions to import from the String module, so it calls the `pluralize` function like this: `Strings::pluralize("box")`.

      ```js
      %dw 2.0
      import dw::core::Strings
      output application/json
      ---
      { 
          'plural': Strings::pluralize("box") 
      }
      ```
    <br/>
10. `iii.` - `Set the watermark column to the login_date_time column`
    1. **Explicación:** * Watermark allows the poll scope to poll for new resources instead of getting the same resource over and over again. <br/> * The database table must be ordered so that the "watermark functionality" can move effectively in the ordered list. Watermark stores the current/last picked up "record id." <br/> * If the Mule application is shut down, it will store the last picked up "record id" in the Java Object Store and the data will continue to exist in the file. This watermark functionality is valuable and enables developers to have increased transparency. <br/> * Developers do not need to create code to handle caching; it is all configurable! * There are two columns and both are unique but user_id can't guaranty sequence whereas date_time will always be in increasing order and table content can easily be ordered on the basis of last processed date_time. <br/><br/>
11. `iii.`
    1. **Explicación:** Attributes in the incoming xml payload are always accessed using `@`. Similarly `*item` is required as we have multiple items in the request. <br/><br/>
12. 