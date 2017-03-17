# Tests

## Get tests of a test run

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json

{
  "data": [
    {
      "type": "test-snapshots",
      "id": "1",
      "attributes": {
        "name": "Find horcruxes",
        "definition-json": {
          "scenario_name": "Find horcruxes",
          "dataset_name": null,
          "dataset_id": null,
          "steps": [
            {
              "action": "Given Harry has one horcrux"
            },
            {
              "result": "Then he should destroy it"
            },
          ],
          "index": 0
        },
        "status": "failed"
      },
      "links": {
        "self": "/test-snapshots/1"
      },
      "relationships": {
        "scenario": {},
        "dataset": {}
      }
    },
    {
      "type": "test-snapshots",
      "id": "2",
      "attributes": {
        "name": "Defeat Voldemort",
        "definition-json": {
          "scenario_name": "Defeat Voldemort",
          "dataset_name": null,
          "dataset_id": null,
          "steps": [
            {
              "action": "Given Harry cast the Expelliarmus spell"
            },
            {
              "result": "Then Voldemort should be defeated"
            }
          ],
          "index": 0
        },
        "status": "success"
      },
      "links": {
        "self": "/test-snapshots/2"
      },
      "relationships": {
        "scenario": {},
        "dataset": {}
      }
    }
  ]
}
```

This endpoint retrieves all test snapshots of a test run

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the tests from
test_run_id | The ID of the test run that contains the tests you want

## Get a test

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id> HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
  {
    "data": {
      "type": "test-snapshots",
      "id": "1",
      "attributes": {
        "name": "Find horcruxes",
        "definition-json": {
          "scenario_name": "Find horcruxes",
          "dataset_name": null,
          "dataset_id": null,
          "steps": [
            {
              "action": "Given Harry has one horcrux"
            },
            {
              "result": "Then he should destroy it"
            },
          ],
          "index": 0
        },
        "status": "failed"
      },
      "links": {
        "self": "/test-snapshots/1"
      },
      "relationships": {
        "scenario": {},
        "dataset": {}
      }
    }
  }
```

This endpoint retrieves a particular test of a test run

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the tests from
test_run_id | The ID of the test run that contains the test you want
test_snapshot_id | The ID of the test you want to get

## Get a test additional data

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=<fields> HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=<fields>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

> The data you want to include in the response must be coma-separated

You can use the JSONAPI [include syntax](http://jsonapi.org/format/#fetching-includes) to fetch additional data
about your tests.

The available additional data are the following:

Field name | Description
-----------| -----------
scenario | The original scenario that produced the test
dataset | The dataset that produced the test (if it comes from a scenario using a datatable)

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=scenario HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=scenario" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

> Get a test scenario

```http
GET https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=dataset HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=dataset" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

> Get a test dataset


### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the tests from
test_run_id | The ID of the test run that contains the test you want
test_snapshot_id | The ID of the test you want to get

### Request parameters

Parameter | Description
----------|------------
include | The data to include in the test JSON response. Fields must be coma-separated


## Add a test execution result

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the tests from
test_run_id | The ID of the test run that contains the test you want
test_snapshot_id | The ID of the test whose you want add a test result to

### Mandatory fields

Field | Description
--------- | -----------
result | (String) The result of the test execution. Possible values are 'passed', 'failed', 'wip', 'retest', 'blocked', 'skipped', 'undefined'.
result_author | (String) The name of the author of the test execution
description | (String) A comment about the test execution

<aside class="notice">
If the provided 'result' value does not match any of the listed possible values, the result will be set as 'undefined'
</aside>

### Optional fields
Field | Description
--------- | -----------
build | (JSONAPI Relationship) The build containing your test execution result
