# Open Gateway APIs Postman collection and Sandbox environment

This repository contains, for your convenience when testing the Open Gateway APIs, the following resources:
- [x] A Postman collection containing:
	- A set of requests including
		- The endpoints for the OIDC standard authorization flows
		- The endpoints for the CAMARA standard service APIs
	- Documentation for each request
		- About the usage flows
		- Describing its parameters
		- With the proper purposes to use
	- A set of tests for each request to store the responses in Postman's environment variables for convenience
- [x] A Postman environment to target your tests to the Telefónica's Open Gateway Sandbox, with the following variables, used in the collection above:
	- From the Sandbox environment
		- `api-gateway-url` and `auth-gateway-url` to point to the Sandbox's API gateway, which acts as an aggregator routing your request to the proper operator (including a mock operator) according to the end-user phone number
	- From your apps registered in the Sandbox or your test cases (to be set by you)
		- `client-id` and `client-secret` to authenticate your app's requests
		- `api-product-purpose` to specify the purpose of your app's API usage according to the API product being tested (check API's documentation in the Postman collection)
		- `application-backend-callback-url` to point to your app's callback endpoint when authorized by using the OIDC's auth code flow
		- `identifier-type` and `enduser-identifier` to provide an application's end-user identifier on the network (e.g., `phone_number`, `ipport`)

## How to import these files into Postman

1. Download the files with .json extension from this repository to your computer
2. See https://learning.postman.com/docs/getting-started/importing-and-exporting/importing-data/

## How to use the Postman collection requests

In order to use any of the Open Gateway service APIs, you first need to authorize your app getting an access token as a result:

1. Use any of the flows in the `Authorization (OIDC)` folder to get an access token in two steps:
	- Backend flow (CIBA)
		- 1st - Get an `auth_req_id`
		- 2nd - Use it to get an access token
	- Frontend flow (Auth Code)
		- 1st - Trigger the authorization code flow by using an HTTP link in your browser (you won't be able to complete the flow in Postman)
		- 2nd - Use the authorization code received in your callback URL to get an access token
2. Use the access token to call any of the service APIs in the `Service APIs` folder
	- 1st - Check the purpose to be used in the authorization request previously to get the access token
	- 2nd - Use the access token in the `Authorization` tab of the request

## How to get onboard to the Telefónica's Open Gateway Sandbox

1. Join any of our programs at https://opengateway.telefonica.com/
	- Developer Hub: https://opengateway.telefonica.com/developer-hub
	- Partner Program: https://opengateway.telefonica.com/partner-program
2. From your Private Area, access the Open Gateway Sandbox console from the Technical Toolbox menu section
3. Register your app and get your `client-id` and `client-secret` to use in the Postman environment

