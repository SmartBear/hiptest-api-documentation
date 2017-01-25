# Tests

## Get tests of a test run

```shell
curl "https://hiptest.net/api/projects/<project_id>/test_runs/<test_run_id>/test_snapshots"
```

> The above command returns JSON structured like this:

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

```shell
curl "https://hiptest.net/api/projects/<project_id>/test_runs\
                                      /<test_run_id>/test_snapshots\
                                      /<test_snapshot_id>"
```

> The above command returns JSON structured like this:

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

```shell
curl "https://hiptest.net/api/projects/<project_id>/test_runs\
                                      /<test_run_id>/test_snapshots\
                                      /<test_snapshot_id>?include=<fields>"
```
> The data you want to include in the response must be coma-separated

You can use the JSONAPI [include syntax](http://jsonapi.org/format/#fetching-includes) to fetch additional data
about your tests.

The available additional data are the following:

Field name | Description
-----------| -----------
scenario | The original scenario that produced the test
dataset | The dataset that produced the test (if it comes from a scenario using a datatable)


```shell
curl "https://hiptest.net/api/projects/<project_id>/test_runs\
                                      /<test_run_id>/test_snapshots\
                                      /<test_snapshot_id>?include=scenario"
```

> Get a test scenario

```shell
curl "https://hiptest.net/api/projects/<project_id>/test_runs\
                                      /<test_run_id>/test_snapshots\
                                      /<test_snapshot_id>?include=dataset"
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
fields | The data to include in the test JSON response. Fields must be coma-separated