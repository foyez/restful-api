# RESTful API

- RESTful api is a way to communicate between the client (frontend) and the server (backend).
- REST (**Representational State Transfer**) is a software architectural style created by _Roy Fielding_ in 2000.
- Any API (**Application Programming Interface**) that follows the REST design principal is called RESTful API.

## RESTful API Design

#### Simple endpoints

| Method | endpoint                         | Details       |
| ------ | -------------------------------- | ------------- |
| GET    | https://example.com/posts        | fetch posts   |
| POST   | https://example.com/posts        | create a post |
| GET    | https://example.com/posts/postId | fetch a post  |
| PUT    | https://example.com/posts/postId | update a post |
| PATCH  | https://example.com/posts/postId | update a post |
| DELETE | https://example.com/posts/postId | delete a post |

#### Nested endpoints

| Method | endpoint                         | Details                    |
| ------ | -------------------------------- | -------------------------- |
| GET    | /posts/postId/comments           | fetch comments of a post   |
| POST   | /posts/postId/comments           | create a comment in a post |
| GET    | /posts/postId/comments/commentId | fetch a comment of a post  |
| GET    | /posts/author                    | fetch posts by author      |

- Nesting endpoint shouldn't be deep more than 3 levels.

#### Filtering, Sorting, Pagination, etc

| Method | endpoint                               | Details                                                              |
| ------ | -------------------------------------- | -------------------------------------------------------------------- |
| GET    | /posts?tags=go,rust                    | filtering post by go & rust tag using query string                   |
| GET    | /posts?limit=20&offset=50              | offset pagination, get 20 items starting with 50th item              |
| GET    | /posts?limit=20&created:lte:2020-04-08 | keyset pagination, get 20 items & minimum created date of 2020-04-08 |
| GET    | /posts?limit=20&after_id=30            | seek pagination, get 20 items after id 30                            |
| GET    | /posts?sort_by=+email,-created         | get posts sort by email ascending & created descending               |

#### API versioning

| Method | endpoint                            | Details       |
| ------ | ----------------------------------- | ------------- |
| GET    | https://example.com/api/v1/products | api version 1 |

#### HTTP status code for restful api

- **1xx: Informational** – Communicates transfer protocol-level information.
- **2xx: Success** – Indicates that the client’s request was accepted successfully.
- **3xx: Redirection** – Indicates that the client must take some additional action in order to complete their request.
- **4xx: Client Error** – This category of error status codes points the finger at clients.
- **5xx: Server Error** – The server takes responsibility for these error status codes.

| Status code                  | Description                                                                                                                                                                             |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200 (OK)                     | successful client request with a response body                                                                                                                                          |
| 201 (Created)                | return a response body after creating a new resource                                                                                                                                    |
| 202 (Accepted)               | request has been accepted for processing, but the processing has not been completed                                                                                                     |
| 204 (No Content)             | usually sent out in response to a PUT, POST, or DELETE request when the REST API declines to send the response message’s body                                                           |
| 304 (Not Modified)           | the resource has not been modified (return an empty body like 204)                                                                                                                      |
| 400 (Bad Request)            | used when no other 4xx error code is appropriate (generic client-side error), e.g. malformed request syntax, invalid request message parameters, or deceptive request routing etc       |
| 401 (Unauthorized)           | the client's identity is known to the server                                                                                                                                            |
| 403 (Forbidden)              | The client does not have access rights to the content                                                                                                                                   |
| 404 (Not Found)              | The server can not find the requested resource. commonly used when the server does not wish to reveal exactly why the request has been refused, or when no other response is applicable |
| 405 (Method Not Allowed)     | response must include the Allow header, which lists the HTTP methods that the resource supports. For example: Allow: GET, POST                                                          |
| 406 (Not Acceptable)         | when client request for incorrect format data in response, e.g. request for application/xml instead of application/json                                                                 |
| 415 (Unsupported Media Type) | when client request including data format is not correct, e.g. request data format is applications/xml instead of application/json                                                      |
| 500 (Internal Server Error)  | generic server error                                                                                                                                                                    |
| 501 (Not Implemented)        | The server either does not recognize the request method, or it cannot fulfill the request. Usually, this implies future availability (e.g., a new feature of a web-service API)         |

[resource - http status codes](https://restfulapi.net/http-status-codes/)
