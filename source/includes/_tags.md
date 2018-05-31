# Tags
## Get tags of a given action word

```http
GET https://app.hiptest.com/api/projects/<project_id>/actionwords/<actionword_id>/tags HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/actionwords/<actionword_id>/tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "1",
      "attributes": {
        "key": "platform",
        "value": "Android"
      },
      "links": {
        "self": "/tags/1"
      }
    },
    {
      "type": "tags",
      "id": "2",
      "attributes": {
        "key": "automated",
        "value": "yes"
      },
      "links": {
        "self": "/tags/2"
      }
    }
  ]
}
```

This endpoint retrieves all tags of a given action word.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted action word
actionword_id | The ID of the action word you want to retrieve the tags from


## Get tags of a given scenario

```http
GET https://app.hiptest.com/api/projects/<project_id>/scenarios/<scenario_id>/tags HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/scenarios/<scenario_id>/tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "1",
      "attributes": {
        "key": "Status",
        "value": "InProgress"
      },
      "links": {
        "self": "/tags/1"
      }
    },
    {
      "type": "tags",
      "id": "2",
      "attributes": {
        "key": "Priority",
        "value": "Over9000"
      },
      "links": {
        "self": "/tags/2"
      }
    }
  ]
}
```
This endpoint retrieves all tags of a given scenario.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted scenario
scenario_id | The ID of the scenario you want to retrieve the tags from

## Get tags of a given folder

```http
GET https://app.hiptest.com/api/projects/<project_id>/folders/<folder_id>/tags HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/folders/<folder_id>/tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "1",
      "attributes": {
        "key": "Javascript",
        "value": ""
      },
      "links": {
        "self": "/tags/1"
      }
    },
    {
      "type": "tags",
      "id": "2",
      "attributes": {
        "key": "Sprint",
        "value": "1"
      },
      "links": {
        "self": "/tags/2"
      }
    }
  ]
}
```
This endpoint retrieves all tags of a given folder.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted folder
folder_id | The ID of the folder you want to retrieve the tags from

## Get tags of a given test run

```http
GET https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/tags HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "1",
      "attributes": {
        "key": "priority",
        "value": "high"
      },
      "links": {
        "self": "/tags/1"
      }
    },
    {
      "type": "tags",
      "id": "2",
      "attributes": {
        "key": "jira",
        "value": "test"
      },
      "links": {
        "self": "/tags/2"
      }
    }
  ]
}
```
This endpoint retrieves all tags of a given test run.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted test run
test_run_id | The ID of the test run you want to retrieve the tags from

## Create tag in a scenario

```http
POST https://app.hiptest.com/api/projects/<project_id>/scenarios/<scenario_id>/tags HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>

{
  "data": {
    "attributes": {
      "key": "priority",
      "value": "high"
    }
  }
}
```

```http
HTTP/1.1 201 Created
Content-Type: application/vnd.api+json
```

```shell
curl -X POST "https://app.hiptest.com/api/projects/<project_id>/scenarios/<scenario_id>/tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "1",
      "attributes": {
        "key": "priority",
        "value": "high"
      },
      "links": {
        "self": "/tags/1"
      }
    }
  ]
}
```
This endpoint creates a new tag in a scenario.

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted scenario
scenario_id | The ID of the scenario where you want to create the tag

## Create tag in a test run

```http
POST https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/tags HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>

{
  "data": {
    "attributes": {
      "key": "priority",
      "value": "high"
    }
  }
}
```

```http
HTTP/1.1 201 Created
Content-Type: application/vnd.api+json
```

```shell
curl -X POST "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "1",
      "attributes": {
        "key": "priority",
        "value": "high"
      },
      "links": {
        "self": "/tags/1"
      }
    }
  ]
}
```
This endpoint creates a new tag in a test run.

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted test run
test_run_id | The ID of the test run where you want to create the tag

## Update a tag in a scenario

```http
PATCH https://app.hiptest.com/api/projects/<project_id>/scenarios/<scenario_id>/tags/<tag_id> HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>

{
  "data": {
    "type": "tags",
    "id": 5,
    "attributes": {
      "key": "priority",
      "value": "low"
    }
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl -XPATCH "https://app.hiptest.com/api/projects/<project_id>/scenarios/<scenario_id>/tags/<tag_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
    --data '{"data": {"type": "tags","id": 5,"attributes": {"key": "priority","value": "low"}}}'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "5",
      "attributes": {
        "key": "priority",
        "value": "low"
      },
      "links": {
        "self": "/tags/1"
      }
    }
  ]
}
```

This endpoint updates a tag in a scenario.


Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted scenario
scenario_id | The ID of the scenario where you want to update the tag
tag_id | The ID of the tag you want to update

## Update a tag in a test run

```http
PATCH https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/tags/<tag_id> HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>

{
  "data": {
    "type": "tags",
    "id": 5,
    "attributes": {
      "key": "priority",
      "value": "low"
    }
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl -XPATCH "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/tags/<tag_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
    --data '{"data": {"type": "tags","id": 5,"attributes": {"key": "priority","value": "low"}}}'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "5",
      "attributes": {
        "key": "priority",
        "value": "low"
      },
      "links": {
        "self": "/tags/1"
      }
    }
  ]
}
```

This endpoint updates a tag in a test run.


Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted test run
test_run_id | The ID of the test run where you want to update the tag
tag_id | The ID of the tag you want to update

## Delete a tag in a scenario

```http
DELETE https://app.hiptest.com/api/projects/<project_id>/scenarios/<scenario_id>/tags/<tag_id> HTTP/1.1
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
curl -XDELETE "https://app.hiptest.com/api/projects/<project_id>/scenarios/<scenario_id>/tags<tag_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{}
```

This endpoint deletes a tag in a scenario.


Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted scenario
scenario_id | The ID of the scenario where you want to delete the tag
tag_id | The ID of the tag you want to delete

## Delete a tag in a test run

```http
DELETE https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/tags/<tag_id> HTTP/1.1
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
curl -XDELETE "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/tags<tag_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{}
```

This endpoint deletes a tag in a test run.


Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted test run
test_run_id | The ID of the test run where you want to delete the tag
tag_id | The ID of the tag you want to delete
