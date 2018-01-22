# Projects

## Get projects
```http
GET https://hiptest.net/api/projects/ HTTP/1.1
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
curl "https://hiptest.net/api/projects/" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "projects",
      "id": "1",
      "attributes": {
        "created-at": "2017-10-02T12:01:27.125Z",
        "updated-at": "2018-01-10T14:55:49.848Z",
        "last-author": "harry@example.org",
        "name": "And the Philosopher's Stone",
        "description": "This is where all starts",
        "bdd-mode": true
      },
      "links": {
        "self": "/projects/1"
      },
      "relationships": {
        "scenarios-folder": {
          "links": {
            "self": "/projects/1/relationships/scenarios-folder",
            "related": "/projects/1/scenarios-folder"
          }
        }
      }
    },
    {
      "type": "projects",
      "id": "2",
      "attributes": {
        "created-at": "2017-10-02T12:01:27.125Z",
        "updated-at": "2018-01-10T14:55:49.848Z",
        "last-author": "harry@example.org",
        "name": "And the Chamber of Secrets",
        "description": "With douchebag Draco Malfoy...",
        "bdd-mode": false
      },
      "links": {
        "self": "/projects/2"
      },
      "relationships": {
        "scenarios-folder": {
          "links": {
            "self": "/projects/2/relationships/scenarios-folder",
            "related": "/projects/2/scenarios-folder"
          }
        }
      }
    }
  ]
}
```

This endpoint retrieves all projects of the logged-in user

## Get a particular project
```http
GET https://hiptest.net/api/projects/<project_id> HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "projects",
      "id": "1",
      "attributes": {
        "created-at": "2017-10-02T12:01:27.125Z",
        "updated-at": "2018-01-10T14:55:49.848Z",
        "last-author": "harry@example.org",
        "name": "And the Philosopher's Stone",
        "description": "This is where all starts",
        "bdd-mode": true
      },
      "links": {
        "self": "/projects/1"
      },
      "relationships": {
        "scenarios-folder": {
          "links": {
            "self": "/projects/1/relationships/scenarios-folder",
            "related": "/projects/1/scenarios-folder"
          }
        }
      }
    }
  ]
}
```

This endpoint retrieves a specific project of the logged-in user

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve

## Getting root scenarios folder of a project

```http
GET https://hiptest.net/api/projects?include=scenarios-folder HTTP/1.1
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
curl "https://hiptest.net/api/project?include=scenarios-folder" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```
> Also works when retrieving a single project

You can use the JSONAPI [include syntax](http://jsonapi.org/format/#fetching-includes) to fetch the scenarios root folder of your project
