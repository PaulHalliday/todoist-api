# Projects

> An example project object

```shell
{
    "comment_count": 10,
    "id": 1234,
    "indent": 1,
    "name": "My project",
    "order": 1
}
```

```python
{
    "comment_count": 10,
    "id": 1234,
    "indent": 1,
    "name": "My project",
    "order": 1
}
```

### Properties

Property | Description
----------|------------
id *Integer* | Project id.
name *String* | Project name.
order *Integer* | Project position in the list of projects/Project order (read-only).
indent *Integer* | Value from 1 to 4 for the Project indentation level (read-only).
comment_count *Integer* | Number of project comments.


## Get all projects

> Get all projects

```shell
$ curl -X GET \
  https://beta.todoist.com/API/v8/projects \
  -H "Authorization: Bearer $token"

[
    {
        "id": 1234,
        "name": "Inbox",
        "comment_count": 10,
        "order": 1,
        "indent": 1
    }
]
```

```python
import requests
requests.get("https://beta.todoist.com/API/v8/projects", headers={"Authorization": "Bearer %s" % your_token}).json()

[
    {
        "id": 1234,
        "name": "Inbox",
        "comment_count": 10,
        "order": 1,
        "indent": 1
    }
]
```

Returns JSON-encoded array containing all user projects.

## Create a new project

> Create a new project

```shell
$ curl "https://beta.todoist.com/API/v8/projects" \
    -X POST \
    --data '{"name": "Movies to watch"}' \
    -H "Content-Type: application/json" \
    -H "X-Request-Id: $(uuidgen)" \
    -H "Authorization: Bearer $token"

{
    "id": 1234,
    "name": "Movies to watch",
    "comment_count": 0,
    "order": 1,
    "indent": 1
}
```

```python
import uuid, requests, json
requests.post(
    "https://beta.todoist.com/API/v8/projects",
    data=json.dumps({
        "name": "Movies to watch"
    }),
    headers={
        "Content-Type": "application/json",
        "X-Request-Id": str(uuid.uuid4()),
        "Authorization": "Bearer %s" % your_token
    }).json()


{
    "id": 1234,
    "name": "Movies to watch",
    "comment_count": 0,
    "order": 1,
    "indent": 1
}
```

Creates a new project and return its value in a JSON format.

### Parameters

Parameter | Required | Description
--------- | -------- | -----------
name *String* | Yes | Name of the project.


## Get a project

> Get a project

```shell
$ curl "https://beta.todoist.com/API/v8/projects/1234” \
  -H "Authorization: Bearer $token”

{
    "id": 1234,
    "name": "Movies to watch",
    "comment_count": 0,
    "order": 1,
    "indent": 1
}
```

```python
import uuid, requests, json
requests.get("https://beta.todoist.com/API/v8/projects/1234", headers={"Authorization": "Bearer %s" % your_token})

{
    "id": 1234,
    "name": "Movies to watch",
    "comment_count": 0,
    "order": 1,
    "indent": 1
}
```

Returns a JSON object containing a project object related to the given id.

## Update a project

> Update a project

```shell
$ curl "https://beta.todoist.com/API/v8/projects/1234" \
    -X POST \
    --data '{"name": "Movies to review"}' \
    -H "Content-Type: application/json" \
    -H "X-Request-Id: $(uuidgen)" \
    -H "Authorization: Bearer $token"
```

```python
import uuid, requests, json
requests.post(
    "https://beta.todoist.com/API/v8/projects/1234",
    data=json.dumps({
        "name": "Movies to review"
    }),
    headers={
        "Content-Type": "application/json",
        "X-Request-Id": str(uuid.uuid4()),
        "Authorization": "Bearer %s" % your_token
    })

```

Updates the project for the given id and returns HTTP status code 204
with an empty body.

### Parameters

Parameter | Required | Description
--------- | -------- | -----------
name *String* | Yes | Name of the project.


## Delete a project

> Delete a project

```shell
$ curl -X DELETE "https://beta.todoist.com/API/v8/projects/1234" \
    -H "Authorization: Bearer $token"
```

```python
import requests, json
requests.delete("https://beta.todoist.com/API/v8/projects/2176857441", headers={"Authorization": "Bearer %s" % your_token})
```

Deletes a project and returns an empty response.
