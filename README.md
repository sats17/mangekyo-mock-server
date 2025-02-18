# Mock Verse 
Mock Verse is a server that provides mock behavior for APIs based on the data you provide. This document will guide you through the process of running the server and using it.

## Prerequisites
Ensure that you have Java and Maven installed on your machine.

## How to start the server
* Clone the Mock Verse repository.
* Open a terminal or command prompt and navigate to the project's root directory.
* Run the provided shell script by executing the command: sh run_me.sh.

## Using the server
Once the server is running, you can interact with it through its API endpoints. You can insert data into the server, which will then provide mock behavior for the specified API paths and methods.

For detailed information about the API endpoints, their parameters, and usage, refer to the API documentation provided below

With the server running, you can use tools like curl or Postman to send requests to the Mock Verse server and receive the expected mock responses based on the data you've provided.

## API Usage Documentation

This Spring Boot application provides a MockServer with various API endpoints to store and retrieve mock API responses. The following is a list of available API endpoints with their descriptions and usage:

### 1. Insert Mock data to in-memory storage

#### Endpoint: /api/mem/insert
#### Method: POST
#### Description: 
Inserts data into an in-memory map for a given API path and method.

#### Query Parameters:

* **apiPath (Required):** The API path that you want to mock. It should start with a /.
* **apiMethod (Required):** The HTTP method that you want to mock (e.g., GET, POST, PUT, DELETE).
* **apiQueryParams (Optional):** Any query parameters that should be considered for the mocked API.
* **apiHeaders (Optional):** The API accepts apiHeaders query parameter to specify the Content-Type (e.g., 'application/json', 'text/plain'). The mock server returns a response with the same content type. If not provided, the default is 'application/json'.

#### Request Body: 
The mock request and response body in any supported format.
```
{
    "request": {
        "key": "value",
        "value": "valeu1"
    },
    "response": {
        "resp_key": "value",
        "value": "valeu1"
    }
}
```

```curl
Example usage:
- curl -X POST "http://localhost:8080/api/map/insert?apiPath=/test&apiMethod=GET&apiQueryParams=param1=value1;param2=value2&apiHeaders=content-type=application/json" -d '{"key": "value"}'
```

### 2. Insert Data to Database

#### Endpoint: /api/disk/insert
#### Method: POST
#### Description: 
Inserts data into a JSON file for a given API path and method. You can see your mock JSON in folder /{path-to-project}/mock-responses

#### Query Parameters:

* **apiPath (Required):** The API path that you want to mock. It should start with a /.
* **apiMethod (Required):** The HTTP method that you want to mock (e.g., GET, POST, PUT, DELETE).
* **apiQueryParams (Optional):** Any query parameters that should be considered for the mocked API.
* **apiHeaders (Optional):** The API accepts apiHeaders query parameter to specify the Content-Type (e.g., 'application/json', 'text/plain'). The mock server returns a response with the same content type. If not provided, the default is 'application/json'.

#### Request Body: 
The mock request and response body in any supported format.
```
{
    "request": {
        "key": "value",
        "value": "valeu1"
    },
    "response": {
        "resp_key": "value",
        "value": "valeu1"
    }
}
```
```curl
Example usage:
- curl -X POST "http://localhost:8080/api/map/insert?apiPath=/test&apiMethod=GET&apiQueryParams=param1=value1;param2=value2&apiHeaders=content-type=application/json" -d '{"key": "value"}'
```

### Retrieve Mocked Data

#### Endpoint: /**
#### Method: 
Any valid HTTP method (GET, POST, PUT, DELETE, etc.)
#### Description: 
Retrieves the mocked data for the given API path and method from the in-memory map or JSON file.

```curl
Example usage -
curl -X GET "http://localhost:8080/test?param1=value1&param2=value2"

```
