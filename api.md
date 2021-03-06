# kanban

# Kanban Api
 
​
List of available endpoints:
​
- `POST /register`
- `POST /login`
 
And routes below need authentication
- `POST /tasks`
- `GET /tasks`
- `GET /tasks/:id`
- `PUT /tasks/:id`
- `DELETE /tasks/:id`
 
 
### POST /register
 
Request:
 
- data:
 
```json
{
  "email": "string",
  "fullname": "string",
  "password": "string"
}
```
 
Response:
 
- status: 201
- body:
  ​
 
```json
{
  "id": "integer",
  "email": "string"
}
```

Response: 
- status 400
``` 
{
  msg: bad request
}
``` 

### POST /login
 
Request:
 
- data:
 
```json
{
  "email": "string",
  "password": "string"
}
```
 
Response:
 
- status: 200
- body:
  ​
 
```json
{
  "access_token": "string"
}
```

Response: 
- status 400
``` 
{
  msg: bad request
}
``` 
 
### POST /tasks
Request:
 
- headers: access_token
 
- data:
 
```json
{
  "title": "Create REST API",
  "category": "todo"
 
}
```
 
​Response:
 
- status: 201
- body:
  ​
 
```json
{
  "id": "integer",
  "UserId": "integer",
  "title": "Creat REST API",
  "category": "todo",
  "createdAt": "2020-11-15T05:45:10.669Z",
  "updatedAt": "2020-11-15T05:45:10.669Z"
```

Response: 
- status 400
``` 
{
  msg: bad request
}
``` 
### GET /tasks
Description: Get all current tasks in loggedin user organization 
Request:
- headers:
- access_token: string
Response:
- status: 200
- body:
  ​
```json
[
  {
      "id": 1,
      "name": "Create REST API",
      "category": "todo",
      "UserId": 1,
      "createdAt": "2020-11-15T05:45:10.669Z",
      "updatedAt": "2020-11-15T05:45:10.669Z",
      "User": {
          "id": 1,
          "fullname": "Delvia Putri",
          "email": "d@mail.com"
      }
  },{
    ...
  }
]
```

Response: 
- status 400
``` 
{
  msg: bad request
}
``` 
### GET /tasks/:id
description: 
  Get one of the current logged in user task. (cannot get another user task)
Request:
- headers: access_token
- params: 
  - id: integer (required)
Response:
- status: 200
- body:
```json
{
    "id": 1,
    "title": "Create REST API",
    "category": "todo",
    "UserId": 1,
    "createdAt": "2020-06-19T13:09:06.917Z",
    "updatedAt": "2020-06-19T20:48:41.811Z"
}
```

Response: 
- status 400
``` 
{
  msg: bad request
}
``` 
### PUT /tasks/:id
description: 
  Update one of the current logged in user task. (cannot update another user task)
Request:
- headers: access_token
- params: 
  - id: integer (required)
- data:
```json
{
    "title": "Create REST API using express",
    "category": "done"
}
```
Response:
- status: 200
- body:
  ​
```json
{
    "id": 1,
    "title": "Create REST API using express",
    "category": "done",
    "UserId": 1,
    "createdAt": "2020-11-19T13:09:06.917Z",
    "updatedAt": "2020-11-19T20:48:41.811Z"
}
```

Response: 
- status 400
``` 
{
  msg: bad request
}
``` 
### DELETE /tasks/:id
description: 
  Delete one of the current logged in user task. (cannot delete another user task)
Request:
- headers: access_token
- params: 
  - id: integer (required)
Response:
- status: 200
- body:
```json
{
    "message": "todo has been deleted"
}
```

Response: 
- status 400
``` 
{
  msg: bad request
}
``` 