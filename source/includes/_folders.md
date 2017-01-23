# Folders

## Get folders of a given project
```shell
curl "https://hiptest-net/api/projects/<project_id>/folders"
```
> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "folders",
      "id": "1",
      "attributes": {
        "name": "HP Saga",
        "description": "This project is designed to keep track of the evolution of the HP saga,
        in the most expressive way possible, thanks to BDD!",
        "parent-id": null
      },
      "links": {
        "self": "/folders/1"
      },
      "relationships": {
        "children": {},
        "scenarios": {}
      }
    },
    {
      "type": "folders",
      "id": "2",
      "attributes": {
        "name": "The Philosopher's Stone",
        "description": "",
        "parent-id": 1
      },
      "links": {
        "self": "/folders/2"
      },
      "relationships": {
        "children": {},
        "scenarios": {}
      }
    }
  ]
}
```

This endpoint retrieves all folders of a given project.
<aside class="warning"> Note that this endpoint will only return the attributes of the folders
and not their elements (scenarios and subfolders)</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from

## Get a single folder

```shell
curl "https://hiptest-net/api/projects/<project_id>/folders/<folder_id>"
```
> The above command returns JSON structured like this:

```json
{
  "data":
    {
      "type": "folders",
      "id": "2",
      "attributes": {
        "name": "The Philosopher's Stone",
        "description": "",
        "parent-id": 1
      },
      "links": {
        "self": "/folders/2"
      },
      "relationships": {
        "children": {},
        "scenarios": {}
      }
    }
}
```

This endpoint retrieves a specific folder of a given project.
<aside class="warning"> Note that this endpoint will only return the attributes of the folder
and not its elements (scenarios and subfolders)</aside>

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id | The ID of the folder you want to get

## Get children of a folder

```shell
curl "https://hiptest-net/api/projects/<project_id>/folders/<folder_id>/children"
```
> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "folders",
      "id": "2",
      "attributes": {
        "name": "The Philosopher's stone",
        "description": "",
        "parent-id": 1
      },
      "links": {
        "self": "/folders/2"
      },
      "relationships": {
        "children": {},
        "scenarios": {}
      }
    },
    {
      "type": "folders",
      "id": "3",
      "attributes": {
        "name": "The Chamber of Secrets",
        "description": "",
        "parent-id": 1
      },
      "links": {
        "self": "/folders/3"
      },
      "relationships": {
        "children": {},
        "scenarios": {}
      }
    }
  ]
}
```
This endpoint retrieves the subfolders of a specific folder

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id | The ID of the folder you want to get the children

## Get scenarios of a folder

```shell
curl "https://hiptest-net/api/projects/<project_id>/folders/<folder_id>/scenarios"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "scenarios",
      "id": "1",
      "attributes": {
        "name": "Read a Hogwarts letter"
      },
      "links": {
        "self": "/scenarios/1"
      }
    },
    {
      "type": "scenarios",
      "id": "2",
      "attributes": {
        "name": "Shopping on Diagon Alley"
      },
      "links": {
        "self": "/scenarios/2"
      }
    }
  ]
}
```

This endpoint retrieves the scenarios of a specific folder

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the folders from
folder_id | The ID of the folder you want to get the scenarios
