# AWS Services Needed

App
-Server Static App (Angular App)
Service: S3 (Simple Storage Service)

REST API
-to store and fetch data
-REST API
Service: DynamoDB (NoSQL Database)

Logic
-Execute Code on Demand
Service: AWS Lambda

Database
-Store and Retrieve Data
Service: DynamoDB (NoSQL Database)

Authentication
-Authenticate Users
Service: Cognito

DNS
-Route Traffic to the correct service
Service: Route 53

Cache
-Improve Performance
Service: CloudFront

## Application Architecture

1. Web App (S3)
2. Auth
3. API (API Gateway)
   -POST
   -GET
   -DELETE
4. Logic (Lambda)
5. Database (DynamoDB)

## How it works

Application
-Web App
-Mobile App
-Other Source (Postman)

Application calls REST API
REST API calls Lambda

## API Gateway: Useful Resources & Links

- API Gateway Overview: https://aws.amazon.com/api-gateway/

- API Gateway Developer Documentation: https://aws.amazon.com/documentation/apigateway/

Understanding the costs of API Gateway is also crucial. What you see in this course will be within the free tier but once you start playing around with it on your own or you're using it for production, you may encounter costs.

## AWS Permissions (IAM)

Brief overview: https://youtu.be/9CKsX6MOPDQ

Besides that, have a look at the following article to get an introduction: http://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html

By default, AWS doesn't give any permissions to any of your services. That means, that no service may interact with other services.

## Lifecycle

1. Method Request
   -Gatekeeper for the request, may reject the request

2. Integration Request
   -Transforms the request into a format the backend can process

3. Endpoint

4. Integration Response
   -Transforms the response into a format the client can process

5. Method Response
   -Defines boundaries of the response

## Swagger

File type and service that can define a REST API

## Configure as Proxy Resource

This will be a catch all resource, catching all our pop and methods and forwarding them to the lambda function
-if you don't want to catch all then don't use this, using different HTTP methods

## CORS

Cross Origin Resource Sharing
-Security model built into browsers
-Protects users from malicious scripts
-Prevents AJAX calls to domains other than the one that served the page

-It needs to pass the right headers to the browser will block the request
-provide an options method to handle the preflight request

## Lambda proxy integration

It will take the incoming request and metadata off this request and pass it to the lambda function, will pass unfiltered as a JSON object to the lambda function

-in the lambda function you will have to parse the event object to get the data you need

Clear seperation of Logic and Gateway

## AWS Lambda: Useful Resources & Links

How it works

Event source
-a file upload could trigger a lambda function

CloudWatch
-schedule events to trigger a lambda function
-useful for cleanup jobs

API Gateway
-Run the code anytime a request hits the API Gateway

Event Source Triggers our Code
-Stored in Lambda and written in NodeJS, Python, Java, or C#

In this code you can do any logic you want, you can call other services, you can do anything you want

Return response to the event source

- AWS Lambda Overview: https://aws.amazon.com/lambda/

- AWS Lambda Developer Documentation: http://docs.aws.amazon.com/lambda/latest/dg/welcome.html

More details about Lambda pricing: https://aws.amazon.com/lambda/pricing/

## AWS Lambda Function Page

1. Test: to run the function

2. Triggers

Look for handler on Lambda page

Want to play around with Lambda? It has a very generous free tier - learn more here: https://aws.amazon.com/lambda/pricing/

## Here's how it works

Here's how it works (for JavaScript, adjust the syntax if you're using another language!):

1. Create a root entry file + handler method. For example an index.js file with the exports.handler = (event, ...) => { ... } method.

If you use a different file name AND/OR different starting handler function, you'll need to adjust your Lambda config! Set Handler to [FILENAME].[HANDLER-FUNCTION-NAME] (default: index.handler).

2. You may split your code over multiple files and import them into the root file via require('file-path') . This is also how you could include other third-party JavaScript (or other languages) packages.

3. Select all files and then zip them into an archive. Important: DON'T put them into a folder and zip the folder. This will not work!

4. Upload the created zip file to Lambda ("Code" => "Code entry type" => "Upload a .ZIP file")
