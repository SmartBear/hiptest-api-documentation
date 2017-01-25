# Test runs
## Get test runs of a project

```shell
curl "https://hiptest-net/api/projects/<project_id>/test_runs"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "test-runs",
      "id": "1",
      "attributes": {
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

```shell
curl "https://hiptest-net/api/projects/<project_id>/test_runs/<test_run_id>"
```

> The above command returns JSON structured like this:

```json
{
  "data":
    {
      "type": "test-runs",
      "id": "1",
      "attributes": {
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
