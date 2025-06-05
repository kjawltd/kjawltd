Introduction

This document provides a guide to the Application Programme Interface (API) used in the implementation of the KJAW™ platform. It is intended primarily for developers to use in their own implementations of the KJAW™ platform, but can also be used as a reference by product and technical project managers to build understanding of API operations and functionality.
Note: This document relates to version 1.0 of the API only. Further versions will be documented separately.
KJAW API documentation is written and shared with developers in partner organisations who are working to roll out customer instances based on the KJAW software platform.
KJAW have designed their API with two main advantages in mind:
•	Automatically generated - the developer works with the most up-to-date version of the base code.
•	Interactive - developers learn about KJAW functionality by using the site to enter user data, execute requests and return results. 

Gaining an understanding of the platform by exercising different areas of functionality can help to clarify requirements and support the delivery of the partner instance.
The API has been designed to follow REST principles and the API documentation below is generated directly from the codebase using a REST visualisation framework called Swagger. Using this approach, the API site is updated when the server is updated, minimising any discrepancies between codebase and documentation. Each HTTP operation maps to the base CRUD (Create, Read, Update, Delete) functions.

Create - PUT with a new URI, POST to a base URI returning a newly created URI
Read – GET 
Update - PUT with an existing URI only
Delete – DELETE

Swagger presents the API in a clear and logical structure, meaning that a user can explore the code functionality without having direct access to or knowledge of the codebase, and build up knowledge of the API functionality by using the data returned in each response to make further requests.
For further information, URLs for Swagger and REST are listed in the References section.

 
1.	API Website

The API website home page lists the class names on the left, and functions on the right. The API base URL and a link to the API release notes at the bottom of the site page. 

<Screenshot>

Clicking once on each link will display the next level of API code. 
Class name, Show/Hide, and List Operations display the operations used by the class in question.
Expand Operations displays the contents of each operation within a class, including descriptions of the class functionality, details of any response parameters, text fields to enter test values and the HTTP code for any errors returned during a request.
Raw displays the code used to generate the API class view in JSON compliant format.
The API is also versioned, which gives the development team clarity in establishing functionality and allows them to factor in changes to code.
Two main areas of code are subject to versioning:
●	New mandatory parameters in requests. Optional parameters are not affected.
●	Changes to returned values in responses, when the value type of or name changes, or a value is removed. New values are not affected.

Versioning is implemented by using the Accept header in a request to specify a version of the API. This approach complies with principles of RESTful API development. To avoid having to send the version information with each request, a baseline value for the request version is set when a user logs in and retained during the session. 
A feature in a previous version of the API will be available in all updated versions.
At a server level, API versions are managed by a request matcher that matches the Accept header to a required controller.
@ApiVersion(introduced="1.0", withdrawn="0.9")
public SomeController {...}
@ApiVersion(introduced="1.0")
public SomeControllerV7 {...}

At a client level, the API version is specified on request via the Accept header.

GET /api/users/test/Accept: application/vnd.KJAW.v1.0+json

 
2.	Getting Started 

Before you use the API, you’ll need 
-	a user account
-	a device

A basic customer account allows you to login and gather information about your own device or account, but a developer may need higher permissions to be able to return and gather information about any device or account in the environment. Contact the System Administrator to check the level of access you require and have an account set up. You’ll also need to check you can access the API website via your web browser. 
Note: URLs for the API documentation page in each environment are available in the References section.

3.	Login

If you are looking to start using the API interactively, you need to log in to the website using the login class. 
●	Click on the login class to display the class operation information, and then click on Expand Operations to open the POST operation.
●	Enter values into each text field (all fields are mandatory)

-	Username
-	Password
-	API caller

●	Click on the Try it out! button to execute the request.

<Screenshot>

If the request is successful you should receive 

-	a request URL
-	response data
-	the HTTP response code
-	a set of response headers.

<Screenshot>

If the request is unsuccessful you should receive the HTTP status code defined in the Error Status Codes section listed in the method documentation.
A successful login request returns parameters you can use to try out other classes, such as the device ID.

●	Make a note of the data returned in the successful login request to use in the session (example below.)
{
  "device ids": [
    "Example device ID"
  ],
  "userId": Example User ID,
  "partnerId": Example Partner ID,
  "username": "Example Username",
  "tandcConfirmed": True or False,
  "permissions": [],
  "ApiSession": "API Session Token, used in each call"
}
 
4.	Returning Data

The information in the Login response can be used to return data about the device. The most basic class returns a list of the devices associated with your username.

●	Click on List Operations in the device class to display the class operation information and click on the URL for the GET operation in the list with the description
●	Enter your username and click on the Try it out! button.

<Screenshot>

If the request is successful you should receive 

-	the request URL
-	response data
-	the HTTP response code
-	a set of response headers.

<Screenshot>

If the request is unsuccessful you should receive the HTTP status code defined in the Error Status Codes section listed in the method documentation.

●	Make a note of the data returned in the request to use in the session (example below.)
 
  {
    "id": "Device ID",
    "name": "Device name",
    "status": Device Status,
    "short_id": "Device Short ID",
    "install_complete": True or False
  }
 
If the request is successful you should receive 

-	the request URL
-	response data (for the device)
-	the HTTP response code
-	a set of response headers.

If the request is unsuccessful you should receive the HTTP status code defined in the Error Status Codes section listed in the method documentation.

The data in the response contains identifiers for that particular device, as can be seen in the example below.

  {
    "id": "Device ID",
    "name": "Device Name 1",
    "type": "Device Type 1",
    "channels": {
      "channel1": true,
      "channel2": false,
      "channel3": 2.8,
      "channel4": 100,
      "channel5": 5,
      "channel6": 100
    }

id - the unique device ID.
name - the device name
type - the device type, which can be shared with other devices
channels - these parameters relate to particular readings from the device

The id value can be used to retrieve further information about the device.
 
5.	Example Functions

Some example operations are listed below, with a URL for each request. Mandatory parameters are marked with *.

login – manages the user login function
URL – POST /login
Parameters - username*, password*, caller
Response - returns a summary of the login data for the user.
{
  "deviceIds": [
    null
  ],
  "userId": 123303,
  "partnerId": 1,
  "username": "kwhyte",
  "tandcConfirmed": true,
  "extCustomerLevel": 1,
  "permissions": [
    "ROLE_ADMIN"
  ],
  "ApiSession": "35221f5b6be02379290bd709c39c9c24"
}

users - manages functions relating to user data.
URL - GET /users/{username}
Parameters - details, username*
Response - returns information about a particular user.
{
"email": "test@KJAW.com",
  "firstName": "Test",
  "lastName": "Test",
  "mobile": "",
  "phone": "",
  "address": "test",
  "addressAdditional": "",
  "city": "Test",
  "state": "test",
  "dob": null,
  "postcode": "xxxxxx",
  "country": "test",
  "username": "test",
  "installStep": "x",
  "pin": "xxxx",
  "memorable": null,
  "memorable_question": null,
  "answer": null,
  "partnerId": "x",
  "partnerSpecificId": "",
  "userConfigSource": "DEFAULT",
  "tandcConfirmed": 0,
}

contacts - manages functions relating to user contact information.
URL – GET /users/{username}/contacts/{id}
Parameters – id*, username*
Response - returns contact information for a particular user.
{
  "135": {
    "id": 135,
    "name": "User name 1",
    "email": null,
    "mobile": "+447000000000",
    "phone": null
  },
  "136": {
    "id": 136,
    "name": "User name 2 ",
    "email": null,
    "mobile": "+447000000000",
    "phone": null
  },
  "137": {
    "id": 137,
    "name": "User name 3 ",
    "email": null,
    "mobile": "+447000000000",
    "phone": null
  }
}
 
References

Swagger site	https://helloreverb.com/developers/swagger
API base site staging	http://KJAW.com:8080/api/docs
API base site internal prod	http://KJAW.com:8080/api/docs

Glossary

Throughout this document, the following acronyms have their given meaning:

Term	Description
API	Application Programme Interface
REST	A set of architecture principles used for internet communications. HTTP and CRUD are based on REST principles.
HTTP	Hyper Text Transfer Protocol.
CRUD	Create, Read, Update, Delete.



