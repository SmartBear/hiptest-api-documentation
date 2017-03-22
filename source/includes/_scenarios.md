# Scenarios

## Get scenarios of a given project

```http
GET https://hiptest.net/api/projects/<project_id>/scenarios HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/scenarios" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "scenarios",
      "id": "1",
      "attributes": {
        "name": "Find horcruxes",
        "description": "That will help to kill Voldemort"
      },
      "links": {
        "self": "/scenarios/1"
      }
    },
    {
      "type": "scenarios",
      "id": "2",
      "attributes": {
        "name": "Defeat Voldemort",
        "descrption": "And save the world, hurray !"
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



## Get a single scenario

```http
GET https://hiptest.net/api/projects/<project_id>/scenarios/<scenario_id> HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/scenarios/<scenario_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data":
    {
      "type": "scenarios",
      "id": "1",
      "attributes": {
        "name": "Find horcruxes",
        "description": "That will help to kill Voldemort"
      },
      "links": {
        "self": "/scenarios/1"
      }
    }
}
```
This endpoint retrieves a single scenario of a given project.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the scenario from
scenario_id | The ID of the scenario you want to get

## Update a scenario

```http
PATCH https://hiptest.net/api/projects/<project_id>/scenarios/<scenario_id> HTTP/1.1
Accept: application/vnd.api+json; version=1
access-token: <your access token>
client: <your client id>
uid: <your uid>


{
  "data": {
    "type": "scenarios",
    "id": <scenario_id>,
    "attributes": {
      "name": "The new name of the scenario",
      "description": "The new description of the scenario"
    }
  }
}
```
```http
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
```

```shell
curl -XPUT "https://hiptest.net/api/projects/<project_id>/scenarios/<scenario_id>" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
    --data '{"data": {"type": "scenarios", "id": <scenario_id>, "attributes": {"name": "The new name of the scenario", "description": "The new description of the scenario" }}}'
```

```json
{
  "data":
    {
      "type": "scenarios",
      "id": "1",
      "attributes": {
        "name": "The new name of the scenario",
        "description": "The new description of the scenario"
      },
      "links": {
        "self": "/scenarios/1"
      }
    }
}
```
This endpoint updates the name and descrpition of a single scenario of a given project.
Note that both name and description parameters are optional, you can update only one of them if wanted, just don't set the key in the "attributes" hash.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the scenario from
scenario_id | The ID of the scenario you want to update
