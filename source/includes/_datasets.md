# Datasets
## Get datasets of a given scenario

```shell
curl "https://hiptest-net/api/projects/<project_id>/scenarios/<scenario_id>/datasets"
  -H 'accept: application/vnd.api+json; version=1'
  -H 'token-type: Bearer'
  -H <all your authentication headers>
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "datasets",
      "id": "1",
      "attributes": {
        "name": "dataset-1",
        "data": {
          "parameter-1": "value 1-1",
          "parameter-2": "value 1-2"
        }
      },
      "links": {
        "self": "/datasets/1"
      }
    },
    {
      "type": "datasets",
      "id": "2",
      "attributes": {
        "name": "dataset-2",
        "data": {
          "parameter-1": "value 2-1",
          "parameter-2": "value 2-2"
        }
      },
      "links": {
        "self": "/datasets/2"
      }
    }
  ]
}
```
This endpoint retrieves all datasets of a given scenario.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted scenario
scenario_id | The ID of the scenario you want to retrieve the tags from

# Datatables

```shell
curl "https://hiptest-net/api/projects/<project_id>/scenarios/<scenario_id>/datatable"
  -H 'accept: application/vnd.api+json; version=1'
  -H 'token-type: Bearer'
  -H <all your authentication headers>
```

> The above command returns the same JSON as `https://hiptest-net/api/projects/<project_id>/scenarios/<scenario_id>/datasets`

```json
{
  "data": [
    {
      "type": "datasets",
      "id": "1",
      "attributes": {
        "name": "dataset-1",
        "data": {
          "parameter-1": "value 1-1",
          "parameter-2": "value 1-2"
        }
      },
      "links": {
        "self": "/datasets/1"
      }
    },
    {
      "type": "datasets",
      "id": "2",
      "attributes": {
        "name": "dataset-2",
        "data": {
          "parameter-1": "value 2-1",
          "parameter-2": "value 2-2"
        }
      },
      "links": {
        "self": "/datasets/2"
      }
    }
  ]
}
```

A `datatable` endpoint is available as an alias for the [`datasets`](#datasets)
resource.

