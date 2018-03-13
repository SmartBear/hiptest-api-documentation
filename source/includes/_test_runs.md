# Test runs
## Get test runs of a project

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "test-runs",
      "id": "1",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "Sprint 1",
        "description": "Wandering in the countryside, doing boring stuff",
        "statuses": {
          "passed": 0,
          "failed": 0,
          "retest": 0,
          "undefined": 765,
          "blocked": 0,
          "skipped": 0,
          "wip": 0
        }
      },
      "links": {
        "self": "/test-runs/1"
      },
      "relationships": {
        "tags": {}
      }
    },
    {
      "type": "test-runs",
      "id": "2",
      "attributes": {
        "name": "Sprint 2",
        "description": "Bank robbery and blowing up things",
        "statuses": {
          "passed": 15,
          "failed": 42,
          "retest": 0,
          "undefined": 0,
          "blocked": 0,
          "skipped": 0,
          "wip": 0
        }
      },
      "links": {
        "self": "/test-runs/2"
      },
      "relationships": {
        "tags": {}
      }
    }
  ]
}
```

This endpoint retrieves all test runs of a given project.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the test runs from


## Get a single test run

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id> HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data":
    {
      "type": "test-runs",
      "id": "1",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "Sprint 1",
        "description": "Wandering in the countryside, doing boring stuff",
        "statuses": {
          "passed": 0,
          "failed": 0,
          "retest": 0,
          "undefined": 765,
          "blocked": 0,
          "skipped": 0,
          "wip": 0
        }
      },
      "links": {
        "self": "/test-runs/1"
      },
      "relationships": {
        "tags": {}
      }
    }
}
```

This endpoint retrieves a single test run of a given project.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the test run from
test_run_id | The ID of the test run you want to get

## Include tags when fetching your test run(s)

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs?include=tags HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs?include=tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```
> Also works when retrieving a single test run

You can use the JSONAPI [include syntax](http://jsonapi.org/format/#fetching-includes) to fetch the tags of your test runs

## Create a test run

```http
POST https://hiptest.net/api/projects/<project_id>/test_runs HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>


{
  "data": {
    "attributes": {
      "name": "Sprint 1",
      "scenario_ids": [1, 2, 3]
    }
  }
}
```

```http
HTTP/1.1 201 Created
Content-Type: application/vnd.api+json
```

```shell
curl -XPOST "https://hiptest.net/api/projects/<project_id>/test_runs" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>' \
    --data '{"data": {"attributes": {"name": "Sprint 1", "scenario_ids": [1, 2, 3]} } }'
```

```json
{
  "data":
    {
      "type": "test-runs",
      "id": "1",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
        "name": "Sprint 1",
        "description": "",
        "statuses": {
          "passed": 0,
          "failed": 0,
          "retest": 0,
          "undefined": 3,
          "blocked": 0,
          "skipped": 0,
          "wip": 0
        }
      },
      "links": {
        "self": "/test-runs/1"
      },
      "relationships": {
        "tags": {}
      }
    }
}
```

This endpoint create a new test run.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project in wich you want to create the test run

### Mandatory fields

Field | Description
--------- | -----------
name | (String) The name of the test run.

### Other fields

Field | Description
--------- | -----------
scenario_ids | (List of Integer) The ids of scenarios you want in the test run.

<aside class="notice">
You can create a test run from a subset of tests by specifying the list of scenario ids.
</aside>
