# Action words

## Get action words of a given project

```http
GET https://hiptest.net/api/projects/<project_id>/actionwords HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>
```
```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl "https://hiptest.net/api/projects/<project_id>/actionwords" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "actionwords",
      "id": "1",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "Find horcruxes",
        "description": "That will help to kill Voldemort",
        "definition": "actionword 'Find horcruxes' do\n  step {action: \"Find the last one\"}\n  step {result: \"Found it!\"}\nend\n",
        "errors": []
      },
      "links": {
        "self": "/actionwords/1"
      }
    },
    {
      "type": "actionwords",
      "id": "2",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "Defeat Voldemort",
        "description": "And save the world, hurray!",
        "definition": "actionword 'Defeat Voldemort' do\nend\n",
        "errors": []
      },
      "links": {
        "self": "/actionwords/2"
      }
    }
  ]
}
```

This endpoint retrieves all action words of a given project.

You can retrieve tags of an action word from the [tags endpoint](#get-tags-of-a-given-action-word).

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the actionwords from



## Get a single action word

```http
GET https://hiptest.net/api/projects/<project_id>/actionwords/<actionword_id> HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>
```
```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl "https://hiptest.net/api/projects/<project_id>/actionwords/<actionword_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data":
    {
      "type": "actionwords",
      "id": "1",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "Find horcruxes",
        "description": "That will help to kill Voldemort",
        "definition": "actionword 'Find horcruxes' do\n  step {action: \"Find the last one\"}\n  step {result: \"Found it!\"}\nend\n",
        "errors": []
      },
      "links": {
        "self": "/actionwords/1"
      }
    }
}
```
This endpoint retrieves a single action word of a given project.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the actionword from
actionword_id | The ID of the action word you want to get

## Create an action word

```http
POST https://hiptest.net/api/projects/<project_id>/actionwords HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>

{
  "data": {
    "attributes": {
      "name": "Find horcruxes",
      "description": "That will help to kill Voldemort",
      "definition": "step {action: \"Find the last one\"}\n step {result: \"Found it!\"}"
    }
  }
}
```
```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl -XPOST "https://hiptest.net/api/projects/<project_id>/actionwords" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>' \
    --data '{"data": {"attributes": {"name": "Find horcruxes", "description": "That will help to kill Voldemort", "definition": "step {action: \"Find the last one\"}\n step {result: \"Found it!\"}" } } }'
```

```json
{
  "data":
    {
      "type": "actionwords",
      "id": "1",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "Find horcruxes",
        "description": "That will help to kill Voldemort",
        "definition": "actionword 'Find horcruxes' do\n  step {action: \"Find the last one\"}\n  step {result: \"Found it!\"}\nend\n",
        "errors": []
      },
      "links": {
        "self": "/actionwords/1"
      }
    }
}
```

This endpoint create new action word.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project in wich you want to create the actionword

### Mandatory fields

Field | Description
--------- | -----------
name | (String) The name of the action word.

### Other fields

Field | Description
--------- | -----------
description | (String) The description of the action word.
definition | (String) The body of the definition of the action word.

<aside class="notice">
The definition of the action word here must contains only the body of the definition. See
example aside.
</aside>
<aside class="notice">
If the definition cannot be properly parsed, the action word will be created and parsing
errors will be in the "errors" attribute of the returned data.
</aside>

## Update an action word

```http
PATCH https://hiptest.net/api/projects/<project_id>/actionwords/<actionword_id> HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>


{
  "data": {
    "type": "actionwords",
    "id": <actionword_id>,
    "attributes": {
      "name": "Find horcruxes",
      "description": "That will help to kill Voldemort",
      "definition": "actionword 'Find horcruxes' do\n  step {action: \"Find the last one\"}\n  step {result: \"Found it!\"}\nend\n"
    }
  }
}
```
```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl -XPATCH "https://hiptest.net/api/projects/<project_id>/actionwords/<actionword_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>' \
    --data $'{ "data": { "type": "actionwords", "id": <actionword_id>, "attributes": { "name": "Find horcruxes", "description": "That will help to kill Voldemort", "definition": "actionword \'Find horcruxes\' do\\n  step {action: \\"Find the last one\\"}\\n  step {result: \\"Found it!\\"}\\nend\\n" } } }'
```

```json
{
  "data":
    {
      "type": "actionwords",
      "id": "1",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "Find horcruxes",
        "description": "That will help to kill Voldemort",
        "definition": "actionword 'Find horcruxes' do\n  step {action: \"Find the last one\"}\n  step {result: \"Found it!\"}\nend\n",
        "errors": []
      },
      "links": {
        "self": "/actionwords/1"
      }
    }
}
```
This endpoint updates the name, descrpition and/or definition of a single action word of a given project.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the action word from
actionword_id | The ID of the action word you want to update

<aside class="notice">
Name, description and definition are optional. Specify only the attributes you want to update.
</aside>
<aside class="notice">
Unlike the creation of an action word the definition here must be fully specified.
</aside>
<aside class="warning">
Don't update name and definition attributes at the same time to avoid 409/conflict errors.
You can rename an action word and update its definition by specifying the new name in the definition.
</aside>

## Delete an action word

```http
DELETE https://hiptest.net/api/projects/<project_id>/actionwords/<actionword_id> HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>
```
```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl -XDELETE "https://hiptest.net/api/projects/<project_id>/actionwords/<actionword_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

This endpoint delete an action word.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the action word from
actionword_id | The ID of the action word you want to delete

<aside class="warning">
Caution: your action word will be totaly and permanently removed from your project.
</aside>
