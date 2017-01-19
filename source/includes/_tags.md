# Tags
## Get tags of a given scenario

```shell
curl "https://hiptest-net/api/projects/<project_id>/scenarios/<scenario_id>/tags"
  -H 'accept: application/vnd.api+json; version=1'
  -H 'token-type: Bearer'
  -H <all your authentication headers>
```

> The above command returns JSON structured like this:

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
