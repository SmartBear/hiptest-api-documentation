# Test execution

## Getting started with test executions
Test execution results in HipTest are organized in the following way:

* Test execution results are grouped into builds
* Each build belongs to an execution environment
* A test run can contain multiple execution environments, each containing their own builds of test execution results.

**The notion of execution environments is entirely optional.**
You can use them if you have several environments on which you want to execute your tests.
If you do not wish to have specific environments, you can ignore them and work directly with builds at test run level.

<aside class="notice">
If no environment is specified, test runs will always have a default environment in which all builds are created.
At any moment it is possible to start working with multiple environments
by <a href="#create-a-new-execution-environment">creating new ones</a>.
All existing builds will still exist in the first, default execution environment.
</aside>

The [Builds section](#builds) specifies all operations that can be performed without execution environments.

The [Execution environments section](#execution-environments) specifies how to work with multiple environments.

It also updates the documentation for the following endpoints from the Builds section, for which specifying an environment becomes mandatory:

* [Listing builds](#list-builds-of-an-execution-environment)
* [Creating a new builds](#create-a-new-build-in-a-specific-execution-environment)
* [Getting the current build](#get-the-current-build-of-an-execution-environment)
* [Getting the execution results of the current build](#get-test-execution-results-of-the-current-build-of-an-execution-environment)

Each entry in the Builds section has a warning if an execution environment ID is mandatory
when working with multiple environments.

All other build operations can still be perfomed with multiple environments.

## Add a test execution result

```http
POST https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>


{
  "data": {
    "type": "test-results",
    "attributes": {
      "status": "passed",
      "status-author": "Harry",
      "description": "All was well"
    }
  }
}
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
execution_environment | (JSONAPI Relationship) The execution environment containing your test execution result

<aside class="notice">
If the optional execution environment field is provided, the test result will be created in the current build of that execution environment
</aside>
<aside class="warning">
If both build and execution environment are provided, the build must belong to the execution environment.
Specifying an execution environment is not needed if a build is already specified
</aside>

```http
POST https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>


{
  "data": {
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
            "type: "build",
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

```http
POST https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots/<test_snapshot_id>/test_results HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>


{
  "data": {
    "type": "test-results",
    "attributes": {"status": "passed", "status-author": "Harry", "description": "All was well"},
    "relationships": {
      "execution-environment": {
        "data": {
          "type": "execution-environment",
          "id": 1
        }
      }
    }
  }
}
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
        "execution-environment": {
          "data": {
            "type: "execution-environment",
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
    -H 'client: <your client id>' \
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
