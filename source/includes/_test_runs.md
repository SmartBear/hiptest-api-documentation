# Test runs
## Get test runs of a project

```http
GET https://app.hiptest.com/api/projects/<project_id>/test_runs HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs" \
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
        },
        "archived": false
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
        },
        "archived": true
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

<aside class="notice">
<p>Note: you can add use the parameter "filter[status]" to only fetch achived or active test runs
as a query string of the request:</p>
<code>
https://app.hiptest.com/api/projects/&lt;project_id&gt;/test_runs?filter[status]=active
</code><br /><code>
https://app.hiptest.com/api/projects/&lt;project_id&gt;/test_runs?filter[status]=archived
</code>
</aside>

### URL Parameters

Parameter          | Description
------------------ | -----------
project_id         | The ID of the project you want to retrieve the test runs from
filter[status]     | "active" or "archived"

## Get a single test run

```http
GET https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id> HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>" \
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
        },
        "archived": false
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
GET https://app.hiptest.com/api/projects/<project_id>/test_runs?include=tags HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs?include=tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```
> Also works when retrieving a single test run

You can use the JSONAPI [include syntax](http://jsonapi.org/format/#fetching-includes) to fetch the tags of your test runs

## Create a test run

```http
POST https://app.hiptest.com/api/projects/<project_id>/test_runs HTTP/1.1
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
curl -XPOST "https://app.hiptest.com/api/projects/<project_id>/test_runs" \
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
        },
        "archived": false
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
project_id | The ID of the project in which you want to create the test run

<aside class="notice">
You can create tags alongside the test run by specifying them in the "relationship" section, as explained in the <a href="#create-tags-alongside-elements">tags creation section</a>.
</aside>

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


## Synchronize a test run
Synchronization give you the ability to update the tests of your test run with their last version, based on the current scenarios definitions

### Watch synchronization state
```http
GET https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>?show_synchronization_information=true HTTP/1.1
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
curl "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>?show_synchronization_information=true" \
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
        },
        "archived": false,
        "synchronization-information": {
          "synchronizable": true,
          "synchronizing": false,
          "details": {
            "deleted_folders_snapshots": [],
            "deleted_scenarios_snapshots": [],
            "deleted_tests_snapshots": []
          }
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
This endpoint is useful to track the state of a test run synchronization.

The synchronization operation can be dangerous. If some of your test run tests and folders are based on scenarios and folders that no longer exist, they will be destroyed.
It is strongly advised to use this endpoint to get the potential impacts of a synchronization before running one.

### Synchronize the test run
```http
POST https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/synchronize HTTP/1.1
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
curl -XPOST "https://app.hiptest.com/api/projects/<project_id>/test_runs/<test_run_id>/synchronize" \
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
        },
        "archived": false,
        "synchronization-information": {
          "synchronizable": true,
          "synchronizing": true,
          "details": {
            "deleted_folders_snapshots": [],
            "deleted_scenarios_snapshots": [],
            "deleted_tests_snapshots": []
          }
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

This endpoint will start the synchronization of a given test run.

<aside class="notice">
Since this is an asynchronous operation, the synchronization might not be done when the server responds back. Use the previous endpoint to watch the state of the
synchronization before doing anything else with your test run data.
</aside>

<aside class="notice">
Only one synchronization of a test run can be run at the same time. Calling this endpoint when the test run is synchronizing won't do anything.
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project containing the test run
test_run_id | The ID of the test run you want to synchronize
