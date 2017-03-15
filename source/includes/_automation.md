# Test execution

## What's a build?
A build is a way to group the execution results of the tests contained in a Hiptest test run.
Even if the notion of build does not appear (for now!) in the Hiptest interface, they are used in our
database when you push the results of a test execution using the Hiptest publisher.

## List builds of a test run
```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/builds HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/builds" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "builds",
      "id": "1",
      "attributes": {
        "created-at": "1980-07-01T12:00:00.350Z",
        "test-run-id": 1
      },
      "links": {
        "self": "/builds/1"
      }
    },
    {
      "type": "builds",
      "id": "2",
      "attributes": {
        "created-at": "1980-07-01T12:00:00.350Z",
        "test-run-id": 1
      },
      "links": {
        "self": "/builds/2"
      }
    }
  ]
}
```

This endpoint retrieves all builds of a given test run.
<aside class="warning"> Note that this endpoint will only return the attributes of builds
and not their test results</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the requested test run
test_run_id | The ID of the test run you want to retrieve the builds from

## Get a specific build of a test run

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/builds/<build_id>" HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/builds/<build_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": {
    "type": "builds",
    "id": "1",
    "attributes": {
      "created-at": "1980-07-01T12:00:00.350Z",
      "test-run-id": 1
    },
    "links": {
      "self": "/builds/1"
    },
    "relationships": {
      "test-results": {
        "data": []
      }
    }
  },
  "included": []
}
```

This endpoint retrieves a specific build of a given test run.
<aside class="warning"> Note that this endpoint will only return the attributes of the build
and not their test results</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
test_run_id | The ID of the test run you want to retrieve the build from

## Get test execution results of a build

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/builds/<build_id>?include=test-results HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/builds/<build_id>?include=test-results" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": {
    "type": "builds",
    "id": "1",
    "attributes": {
      "created-at": "1980-07-01T12:00:00.350Z",
      "test-run-id": 1
    },
    "links": {
      "self": "/builds/1"
    },
    "relationships": {
      "test-results": {
        "data": [
          {
            "type": "test-results",
            "id": "1"
          },
          {
            "type": "test-results",
            "id": "2"
          }
        ]
      }
    }
  },
  "included": [
    {
      "type": "test-results",
      "id": "1",
      "attributes": {
        "status": "passed",
        "created-at": "1980-07-01T12:00:00.350Z",
        "description": "",
        "status-author": "Jenkins",
        "test-snapshot-id": 1
      },
      "links": {
        "self": "/test-results/1"
      }
    },
    {
      "type": "test-results",
      "id": "2",
      "attributes": {
        "status": "failed",
        "created-at": "1980-07-01T12:00:00.350Z",
        "description": "Error on line 42",
        "status-author": "Jenkins",
        "test-snapshot-id": 2
      },
      "links": {
        "self": "/test-results/2"
      }
    }
  ]
}
```
Use the JSONAPI [include syntax](http://jsonapi.org/format/#fetching-includes) to fetch the test execution results
of your build.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
test_run_id | The ID of the test run you want to retrieve the build from

## Create a new build

```http
POST https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/builds" HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/builds" \
    -XPOST
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
  {
    "data": {
      "type": "builds",
      "id": "3",
      "attributes": {
        "created-at": "now!",
        "test-run-id": 1
      },
      "links": {
        "self": "/builds/3"
      },
      "relationships": {
        "test-results": {}
      }
    }
  }
```

<aside class="notice">You MUST create a new build when you need to push the execution results of a new run of your tests</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
test_run_id | The ID of the test run you are executing


## Assign test execution results to a build
