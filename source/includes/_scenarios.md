# Scenarios

## Get scenarios of a given project

```shell
curl "https://hiptest-net/api/projects/<project_id>/scenarios"
  -H 'accept: application/vnd.api+json; version=1'
  -H 'token-type: Bearer'
  -H <all your authentication headers>
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "scenarios",
      "id": "1",
      "attributes": {
        "name": "Find horcruxes"
      },
      "links": {
        "self": "/scenarios/1"
      }
    },
    {
      "type": "scenarios",
      "id": "2",
      "attributes": {
        "name": "Defeat Voldemort"
      },
      "links": {
        "self": "/scenarios/2"
      }
    }
  ]
}
```

This endpoint retrieves all scenarios of a given project.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the scenarios from
