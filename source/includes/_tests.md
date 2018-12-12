# Tests

## Get tests of a test run

```http
GET https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots" \
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
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
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
        "status": "failed",
        "scenario-snapshot-id": 1,
        "folder-snapshot-id": 2
      },
      "links": {
        "self": "/test-snapshots/1"
      },
      "relationships": {
        "scenario": {},
        "dataset": {},
        "last-result": {}
      }
    },
    {
      "type": "test-snapshots",
      "id": "2",
      "attributes": {
        "created-at" : "2017-02-28T11:39:08.281Z",
        "updated-at" : "2017-02-28T11:39:08.281Z",
        "last-author" : "harry@example.org",
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
        "status": "success",
        "scenario-snapshot-id": 1,
        "folder-snapshot-id": 5
      },
      "links": {
        "self": "/test-snapshots/2"
      },
      "relationships": {
        "scenario": {},
        "dataset": {},
        "last-result": {}
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

<aside class="notice">
  The list of available statuses for a test are:
  <ul>
    <li>undefined</li>
    <li>passed</li>
    <li>failed</li>
    <li>retest</li>
    <li>blocked</li>
    <li>wip</li>
    <li>skipped</li>
  </ul>
</aside>

### Optional parameter
Parameter | Description
--------- | -----------
show_step_statuses (value: 'true') | Embed detailed test results including statuses per step with every tests


## Get a test

```http
GET https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id> HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>" \
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
      "created-at" : "2017-02-28T11:39:08.281Z",
      "updated-at" : "2017-02-28T11:39:08.281Z",
      "last-author" : "harry@example.org",
      "name": "Find horcruxes",
      "definition-json": {
        "scenario-name": "Find horcruxes",
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
      "status": "failed",
      "scenario-snapshot-id": 1,
      "folder-snapshot-id": 5
    },
    "links": {
      "self": "/test-snapshots/1"
    },
    "relationships": {
      "scenario": {},
      "dataset": {},
      "last-result": {}
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
GET https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=<fields> HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=<fields>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

You can use the JSONAPI [include syntax](http://jsonapi.org/format/#fetching-includes) to fetch additional data
about your tests.

> Following example returns a test with scenario, last result and the pass rate.

```http
GET https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=dataset,scenario&show_passrate HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>?include=dataset,scenario&show_passrate" \
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
      "created-at" : "2017-02-28T11:39:08.281Z",
      "updated-at" : "2017-02-28T11:39:08.281Z",
      "last-author" : "harry@example.org",
      "name": "Find horcruxes",
      "definition-json": {
        "scenario-name": "Find horcruxes",
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
      "status": "passed",
      "scenario-snapshot-id": 1,
      "folder-snapshot-id": 5,
      "pass-rate": "75"
    },
    "links": {
      "self": "/test-snapshots/1"
    },
    "relationships": {
      "scenario": {
        "data": {
          "type": "scenarios",
          "id": "10"
        }
      },
      "dataset": {},
      "last-result": {
        "links": {
          "self": "/test-snapshots/1/relationships/last-result",
          "related": "/test-snapshots/1/last-result"
        },
        "data": {
          "type": "test-results",
          "id": "7"
        }
      }
    }
  },
  "included": [
    {
      "type": "scenarios",
      "id": "10",
      "attributes": {
        "created-at": "2017-02-26T07:10:42.651Z",
        "updated-at": "2017-02-26T10:22:23.206Z",
        "last-author": "harry@example.org",
        "name": "Find horcruxes",
        "description": "That will help to kill Voldemort",
        "folder-id": 162629,
        "definition": "scenario 'Find horcruxes' do\n  call given 'Harry has one horcrux'\n  call then 'he should destroy it\nend\n"
      },
      "links": {
        "self": "/scenarios/10"
      },
      "relationships": {
        "folder": {}
      }
    },
    {
      "type": "test-results",
      "id": "7",
      "attributes": {
        "created-at": "2017-03-01T14:38:16.612Z",
        "updated-at": "2018-03-01T14:38:16.612Z",
        "last-author": "harry@example.org",
        "status": "passed",
        "description": null,
        "status-author": "Harry",
        "step-statuses": [
          "passed",
          "passed"
        ]
      },
      "links": {
        "self": "/test-results/7"
      },
      "relationships": {
        "test-snapshot": {},
        "build": {},
        "execution-environment": {}
      }
    }
  ]
}
```

The available additional data are the following:

Field name | Description
-----------| -----------
scenario | The original scenario that produced the test
dataset | The dataset that produced the test (if it comes from a scenario using a datatable)
last-result | The details of the last test result of the test

`show_passrate` parameter can be added to include test pass rate in the response.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the tests from
test_run_id | The ID of the test run that contains the test you want
test_snapshot_id | The ID of the test you want to get

### Request parameters

Parameter | Description
----------|------------
include | The data to include in the test JSON response. Fields must be comma-separated
show_passrate | Add this parameter to get the test pass rate in the data

<aside class="notice">
The pass rate is only based on three types of results: passed, failed and blocked. The pass rate is computed on the last 10 results of the test.
Note: the pass rate is expressed as a percentage (25 meaning 25% for example). If there are no usable results to compute the data, an empty string will be returned.
</aside>


## Add a test execution result

```http
POST https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results HTTP/1.1

{"data": {"type": "test-results", "attributes": {"status": "passed", "status-author": "Harry", "description": "All was well"}}}

Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>
```

```http
HTTP/1.1 201 Created
Content-Type: application/vnd.api+json
```

```shell
curl -XPOST "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>' \
    --data '{"data": {"type": "test-results", "attributes": {"status": "passed", "status-author": "Harry", "description": "All was well"}}}'
```

> Newly created test result

``` json
{
  "data": {
    "type": "test-results",
    "id": "1",
    "attributes": {
      "created-at" : "2017-02-28T11:39:08.281Z",
      "updated-at" : "2017-02-28T11:39:08.281Z",
      "last-author" : "harry@example.org",
      "status": "passed",
      "created-at": "Couple of miliseconds ago",
      "description": "",
      "status-author": "Harry"
    },
    "links": {
      "self": "/test-results/1"
    },
    "relationships": {
      "test-snapshot": {
        "data": {
          "type": "test-snapshots",
          "id": "1"
        }
      },
      "build": {
        "data": null
      }
    }
  },
  "included": [
    {
      "test-snapshot": "test data"
    }
  ]
}
```

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the tests from
test_run_id | The ID of the test run that contains the test you want
test_snapshot_id | The ID of the test whose you want add a test result to

### Mandatory fields

Field | Description
--------- | -----------
status | (String) The result of the test execution. Possible values are 'passed', 'failed', 'wip', 'retest', 'blocked', 'skipped', 'undefined'.
status-author | (String) The name of the author of the test execution
description | (String) A comment about the test execution

<aside class="notice">
If the provided 'status' value does not match any of the listed possible values, the result will be set as 'undefined'
</aside>

### Optional fields
Field | Description
--------- | -----------
build | (JSONAPI Relationship) The build containing your test execution result

```http
POST https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results HTTP/1.1

{ "data": {
    "type": "test-results",
    "attributes": {"status": "passed", "status-author": "Harry", "description": "All was well"},
    "relationships": {
      "build": {
        "data": {
          "type": "build",
          "id": 1
        }
      }
    }
  }
}

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
curl -XPOST "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>' \
    --data '{
      "type": "test-results", "attributes": {"status": "passed", "status-author": "Harry", "description": "All was well"},
      "relationships": {
        "build": {
          "data": {
            "type: "build,
            "id": 1
          }
        }
      }
    }'
```

> Newly created test result

``` json
{
  "data": {
    "type": "test-results",
    "id": "1",
    "attributes": {
      "status": "passed",
      "created-at": "Couple of miliseconds ago",
      "description": "",
      "status-author": "Harry"
    },
    "links": {
      "self": "/test-results/1"
    },
    "relationships": {
      "test-snapshot": {
        "data": {
          "type": "test-snapshots",
          "id": "1"
        }
      },
      "build": {
        "data": {
          "type": "builds",
          "id": "1"
        }
      }
    }
  },
  "included": [
    {
      "type": "test-snapshots",
      "attributes": "test data"
    },

    {
      "type": "builds",
      "attributes": "build data"
    }
  ]
}
```

## Update a test execution result

```http
PATCH https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results/<test_result_id> HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>

{
  "data": {
    "type": "test-results",
    "id": <test_result_id>,
    "attributes": {
      "status": "passed",
      "status-author": "Jenkins",
      "description": "Automated jenkins job"
    }
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl -XPUT "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results/<test_result_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
    --data '{"data": {"type": "test-results", "id": <test_result_id>, "attributes": {"status": "passed", "status-author": "Jenkins", "description": "Automated jenkins job"}}}'
```

> Updated test result

``` json
{
  "data": {
    "type": "test-results",
    "id": "<test_result_id>",
    "attributes": {
      "created-at" : "2017-02-28T11:39:08.281Z",
      "updated-at" : "2017-02-28T11:39:08.281Z",
      "last-author" : "harry@example.org",
      "status": "passed",
      "created-at": "Couple of miliseconds ago",
      "description": "Automated jenkins job",
      "status-author": "Jenkins"
    },
    "links": {
      "self": "/test-results/<test_result_id>"
    },
    "relationships": {
      "test-snapshot": {},
      "build": {}
    }
  }
}
```

The API allows you to update a test result following the
[{json:api} way to patch resources](http://jsonapi.org/format/#crud-updating).

Status, author and/or description may be updated specifying the
`status`, `status-author` and/or `description` attributes of the resource.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the tests from
test_run_id | The ID of the test run that contains the test you want
test_snapshot_id | The ID of the test whose you want to update a test result to
test_result_id | The ID of the test result you want to update

### Attributes that may be updated

Field | Description
--------- | -----------
status | (String) The status of the test execution. Possible values are 'passed', 'failed', 'wip', 'retest', 'blocked', 'skipped', 'undefined'.
status-author | (String) The name of the author of the test execution
description | (String) A comment about the test execution

<aside class="notice">
If the provided 'status' value does not match any of the listed possible values, the result will be set as 'undefined'
</aside>