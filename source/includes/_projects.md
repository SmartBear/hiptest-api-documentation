# Projects

## Get projects
```http
GET https://app.hiptest.com/api/projects/ HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/" \
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
GET https://app.hiptest.com/api/projects/<project_id> HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>" \
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

## Create a project backup

### Watch the backup creation state

```http
GET https://app.hiptest.com/api/projects/<project_id>/backups/last HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/backups/last" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": {
    "type": "backups",
    "id": "126",
    "attributes": {
      "backup-information": {
        "backup_in_progress": false,
        "last_generated_backup_url": "https://attachments-hiptest-production.s3.amazonaws.com/backups/backup_files/000/003/331/original/coffee_machine__hiptest_publisher_sample_20180419.zip?AWSAccessKeyId=AKIAJYH3PESN3X5KLXJA&Expires=1528298175&Signature=38MrqnJ9Zw0lw2cK06aVmEJArwU%3D"
        }
    },
    "links": {
      "self": "/backups/126"
    }
  }
}
```
This endpoint is useful to track the state of a project backup creation and get the last created backup URL.

### Create the project backup

```http
POST https://app.hiptest.com/api/projects/<project_id>/backups HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/backups" \
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
        "bdd-mode": true,
        "backup-information": {
          "backup_in_progress": true,
        }
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

This endpoint will start the backup creation of a given project.

<aside class="notice">
Since this is an asynchronous operation, the backup creation might not be done when the server responds back. Use the previous endpoint to watch the state of the
backup creation before doing anything else with your project data.
</aside>

<aside class="notice">
Only one backup of a project and between projects of the same organization can be created at the same time. Calling this endpoint when a backup creation is in progress won't do anything.
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to create the backup for

## Getting root scenarios folder of a project

```http
GET https://app.hiptest.com/api/projects?include=scenarios-folder HTTP/1.1
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
curl "https://app.hiptest.com/api/project?include=scenarios-folder" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```
> Also works when retrieving a single project

You can use the JSONAPI [include syntax](http://jsonapi.org/format/#fetching-includes) to fetch the scenarios root folder of your project
