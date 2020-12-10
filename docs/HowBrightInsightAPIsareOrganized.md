# HowBrightInsightAPIsAreOrganized

This section explains how our APIs are organized so you can navigate them and apply them to your implementation.

An API is an application programming interface, which is a set of rules that lets programs talk to each other, exposing data and functionality across the internet in a consistent format.

REST, [Representational State Transfer](http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm), is an architectural pattern that describes how distributed systems can expose a consistent interface. The term “REST API” means an API accessed via HTTP protocol at a predefined set of URLs. These URLs represent various resources. Resources are information or content accessed at that location, which can be returned as date in the form of JSON, HTML, audio files, or images. These resources often have one or more methods that can be performed on them over HTTP, like GET, POST, PUT, PATCH, and DELETE. 

## How Is Information Organized in BrightInsight APIs?

In Swagger, APIs are listed by method, URL, and then title. Each method is color-coded, and when you click on it, the details expand below. Often BrightInsight APIs are grouped in sections to help you find what you need. These display in the code as “tags.”

### Parameters, Responses, and Extensions

Each API lists Parameters, if any, and Responses. As you develop your application, you should review and edit these to your preferences. Error messages are generic and provided as templates. You may also work with any available Extensions in a section at the bottom of the API description. 

### Operation IDs

Every BrightInsight API has an operation ID, listed within the API as a tag. These IDs use the naming convention “API-CS##”, such as “API-CS01”. You can easily locate an API using these IDs, or by using the API name.

### Examples and Schemas

To see examples and schemas for an object, expand the API, then under the object, locate the **Example Value** and **Schema** toggles. 

![Examples Schemas Toggles](../assets/images/ExampleSchemaToggle.png)

Clicking either changes the display to show examples or schemas.

### Components

Compliant with the OAS 3.0 specification, BrightInsight APIs organize the following reusable objects in a #/components section in the code:
- [ ] responses 
- [ ] parameters 
- [ ] examples
- [ ] requestBodies
- [ ] headers
- [ ] links
- [ ] callbacks
- [ ] schemas

When viewed in Swagger, the components section displays at the bottom of the document in grey. 
