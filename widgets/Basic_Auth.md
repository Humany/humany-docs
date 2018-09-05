## Basic Authentication Requirements
Humany supports authorizing users using Basic Authentication. This feature must first be enabled by Humany on an application, then it can be enabled for a specific user, and finally widgets can be configured to include Basic Authentication headers when communicating with Humany's backend API.

## Example of client code
```javascript
// This is an example of the widget configuration used to pass Basic Authentication headers:
Humany.configure(function (config) {
	const USERNAME = "user_name_in_humany@somedomain.com";
	const PASSWORD = "NotTheMostSecretPassword";
	config.registerPlugin({
		init: function (args, context) {
			context.container.get("serviceClient").proxy.interceptors.push({
				request: function (request) {
					request.options.headers = new Headers();
					request.options.headers.append('Authorization', 'Basic' + btoa(USERNAME + ":" + PASSWORD));
					return request;
				}
			});
		}
	});
});
```
