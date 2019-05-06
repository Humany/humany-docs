> This documentation is valid for widget V1-V4

# Contact Method WebHook

This described how to use the Customized Web Service contact method to pass information from a form to a system external to Humany and display information from this service to users using Humany widgets. Developers are the intended audience of this documentation.

## Background

When creating a new contact method, you have the option of choosing a type called Customized Web service. This is a special kind of contact method that transfers the end user's request to an external HTTP REST web service of your choosing. The receiving web service is then responsible to take any action appropriate, based on that request. It can also choose to optionally respond back to Humany with a dynamic answer that describes the outcome of the action. This dynamic answer will then be injected into a special placeholder and displayed to the end user.

The intent of this type of contact method is to provide a way to immediately solve more complex, dynamic end user issues than would have been possible using just simple static text.

## Web service requirements

When executing a contact method of type Customized Web service, Humany will act as a middle-man between the end-user and the external service. The web service is expected to follow a certain contract. More exactly,

- Humany will send a HTTP request with verb POST to the URL specified by the editor under URL.
- The request body will be one of the Content-Types specified by the editor under MIME FORMAT (see section Receiving Content-Type).
- The web service now has a maximum of 15 seconds to complete whatever task it undertakes before responding, or there will be a timeout error on Humany's side.
- Humany expects that the external web service honor the Accept header of the request, making text/html or text/plain the 2 only valid response formats of your service.
- Humany receives a properly formatted response from the web service and injects any possible response text into the special placeholder specified by the editor under the section Text displayed after sending.
- The dynamic answer is displayed to the user.

## Receiving Content-Type

Humany will transfer the current state and context of the end user request to the external web service in the formats listed below. The context includes any possible form fields filled-out by the end user prior to sending the contact method form, aswell as Humanys current list of parameters associated with the current user request.

## Example application/json

```javascript
{
	Context:
	{
		Parameters: [
			{ Name = "FirstName", Value = "Mikael" },
			{ Name = "LastName", Value = "Robinson" },
			{ Name = "ProblemDescription", Value = "Lorem ipsum dolor sit amet" },
			{ Name = "UserId", Value = "1992883-37746GX-F00" },
			{ Name = "Site", Value = "http://demobolaget.humany.net/test-interface#humany-test-interface=/contact/1362" },
			{ Name = "Perspective", Value = "Default" }
		]
	}
}
```

## Example application/xml

```xml
<context>
	<parameters>
	<parameter name="FirstName">Mikael</parameter>
	<parameter name="LastName">Robinson</parameter>
	<parameter name="ProblemDescription">Lorem ipsum dolor sit amet</parameter>
	<parameter name="UserId">1992883-37746GX-F00</parameter>
	<parameter name="Site">http://demobolaget.humany.net/test-interface#humany-test-interface=/contact/1362</parameter>
	<parameter name="Perspective">Default</parameter>
	</parameters>
</context>
```

## Example x-www-form-urlencoded

```
FirstName=Mikael&LastName=Robinson&ProblemDescription=Lorem+ipsum+dolor+sit+amet&UserId=1992883-37746GX-F00&
Site=http%3a%2f%2fdemobolaget.humany.net%2ftest-interface%23humany-test-interface%3d%2fcontact%2f1362&Perspective=Default
```

## Troubleshooting

Any error that occurs in the communication between Humany and the external web service will be reported as a 500 Internal Server Error on the original request to Humany, along with an error message for debugging purposes.