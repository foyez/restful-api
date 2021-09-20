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
