# Tags
## Get tags of a given scenario

```http
GET https://hiptest.net/api/projects/<project_id>/scenarios/<scenario_id>/tags HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/scenarios/<scenario_id>/tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

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


## Get tags of a given folder

```http
GET https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/tags HTTP/1.1
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
curl "https://hiptest.net/api/projects/<project_id>/folders/<folder_id>/tags" \
    -H 'accept: application/vnd.api+json; version=1' \
    -H 'access-token: <your access token>' \
    -H 'uid: <your uid>' \
    -H 'client: <your client id>'
```

```json
{
  "data": [
    {
      "type": "tags",
      "id": "1",
      "attributes": {
        "key": "Javascript",
        "value": ""
      },
      "links": {
        "self": "/tags/1"
      }
    },
    {
      "type": "tags",
      "id": "2",
      "attributes": {
        "key": "Sprint",
        "value": "1"
      },
      "links": {
        "self": "/tags/2"
      }
    }
  ]
}
```
This endpoint retrieves all tags of a given folder.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted folder
folder_id | The ID of the folder you want to retrieve the tags from
