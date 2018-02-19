# Folders

## Get folders of a given project

```http
GET https://hiptest.net/api/projects/<project_id>/folders HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/folders" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "folders",
      "id": "1",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "HP Saga",
        "description": "This project is designed to keep track of the evolution of the HP saga,
        in the most expressive way possible, thanks to BDD!",
        "parent-id": null
      },
      "links": {
        "self": "/folders/1"
      }
    },
    {
      "type": "folders",
      "id": "2",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "The Philosopher's Stone",
        "description": "",
        "parent-id": 1
      },
      "links": {
        "self": "/folders/2"
      }
    }
  ]
}
```

This endpoint retrieves all folders of a given project.
<aside class="warning"> Note that this endpoint will only return the attributes of folders
and not their elements (scenarios and subfolders)</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from

## Get a single folder

```http
GET https://hiptest.net/api/projects/<project_id>/folders/<folder_id> HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/folders/<folder_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data":
    {
      "type": "folders",
      "id": "2",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "The Philosopher's Stone",
        "description": "",
        "parent-id": 1
      },
      "links": {
        "self": "/folders/2"
      }
    }
}
```

This endpoint retrieves a specific folder of a given project.
<aside class="warning"> Note that this endpoint will only return the attributes of the folder
and not its elements (scenarios and subfolders)</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id | The ID of the folder you want to get

## Get children of a folder

```http
GET https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/children HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/children" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "folders",
      "id": "2",
      "attributes": {
        "name": "The Philosopher's stone",
        "description": "",
        "parent-id": 1
      },
      "links": {
        "self": "/folders/2"
      }
    },
    {
      "type": "folders",
      "id": "3",
      "attributes": {
        "name": "The Chamber of Secrets",
        "description": "",
        "parent-id": 1
      },
      "links": {
        "self": "/folders/3"
      }
    }
  ]
}
```
This endpoint retrieves the subfolders of a specific folder

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id | The ID of the folder you want to get the children

## Get scenarios of a folder

```http
GET https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/scenarios HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/scenarios" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "scenarios",
      "id": "1",
      "attributes": {
        "name": "Read a Hogwarts letter"
      },
      "links": {
        "self": "/scenarios/1"
      }
    },
    {
      "type": "scenarios",
      "id": "2",
      "attributes": {
        "name": "Shopping on Diagon Alley"
      },
      "links": {
        "self": "/scenarios/2"
      }
    }
  ]
}
```

This endpoint retrieves the scenarios of a specific folder

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id | The ID of the folder you want to get the scenarios

## Create a folder

```http
POST https://hiptest.net/api/projects/<project_id>/folders HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>

{
  "data": {
    "attributes": {
      "name": "A new folder",
      "parent-id": 1234
    }
  }
}
```
```http
HTTP/1.1 201 Created
Content-Type: application/vnd.api+json
```

```shell
curl -XPOST "https://hiptest.net/api/projects/<project_id>/folders" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>' \
    --data '{"data": {"attributes": {"name": "A new folder", "parent-id": "1234" } } }'
```

```json
{
  "data": {
    "type": "folders",
    "id": "1235",
    "attributes": {
      "created-at": "2017-10-17T08:00:33.978Z",
      "updated-at": "2017-10-18T08:28:07.791Z",
      "last-author": "harry@example.org",
      "name": "A new folder",
      "description": "",
      "definition": "folder do\nend\n",
      "parent-id": 1234
    },
    "links": {
      "self": "/folders/1235"
    }
  }
}
```

This endpoint create a new folder

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from

### Mandatory fields

Field | Description
--------- | -----------
name | (String) The name of the folder.

### Other fields

Field | Description
--------- | -----------
parent-id | (Integer) The id of the folder that will contain the created folder.

<aside class="notice"> If no parent folder is specified, the folder will be created inside the root folder of the project</aside>

## Update a folder

```http
PATCH https://hiptest.net/api/projects/<project_id>/folders/<folder_id> HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>

{
  "data": {
    "type": "folders",
    "id": "<folder_id>"
    "attributes": {
      "name": "A new folder name",
      "description: "A new description",
      "definition": "folder do end"
      "parent-id": 1233
    }
  }
}
```
```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl -XPATCH "https://hiptest.net/api/projects/<project_id>/folders/<folder_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>' \
    --data '{"data": {"attributes": {"name": "A new folder name", "parent-id": "1233", "description: "A new description", "definition": "folder do end" } } }'
```

```json
{
  "data": {
    "type": "folders",
    "id": "1234",
    "attributes": {
      "created-at": "2017-10-17T08:00:33.978Z",
      "updated-at": "2017-10-18T08:28:07.791Z",
      "last-author": "harry@example.org",
      "name": "A new folder name",
      "description": "A new descriptio",
      "definition": "folder do\nend\n",
      "parent-id": 1233
    },
    "links": {
      "self": "/folders/1234"
    }
  }
}
```

This endpoint updates a folder

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from

### Fields

Field      | Description
---------  | -----------
name       | (String) The name of the folder.
description| (String) The description of the folder.
definition | (String) The definition of the folder.
parent-id  | (Integer) The id of the parent folder.

<aside class="notice">Attributes to update are all optional. Specify only the ones you want to update.</aside>

## Delete a folder

```http
DELETE https://hiptest.net/api/projects/<project_id>/folders/<folder_id> HTTP/1.1
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
curl -XDELETE "https://hiptest.net/api/projects/<project_id>/folders/<folder_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": {}
}
```

This endpoint destroy a folder

### URL Parameters

Parameter  | Description
---------  | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id  | The ID of the target folder

<aside class="warning"><b>Warning:</b> this action will destroy all the children and scenarios within the given folder</aside>

## Delete a folder children

```http
DELETE https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/children HTTP/1.1
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
curl -XDELETE "https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/children" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": {}
}
```

This endpoint destroys all sub-folders of the target folder

### URL Parameters

Parameter  | Description
---------  | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id  | The ID of the target folder

<aside class="warning"><b>Warning:</b> this action will destroy all the children and their scenarios</aside>

## Delete a folder scenarios

```http
DELETE https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/scenarios HTTP/1.1
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
curl -XDELETE "https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/scenarios" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": {}
}
```

This endpoint destroy a folder scenarios

### URL Parameters

Parameter  | Description
---------  | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id  | The ID of the target folder

<aside class="warning"><b>Warning:</b> this action will destroy all the scenarios of the given folder</aside>

