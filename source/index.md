---
title: API Reference

language_tabs:
  - shell
  - javascript

toc_footers:
  - <a href='http://trygaas.com'>Sign Up for an API Token</a>
  - <a href='http://trygaas.com'>GAAS</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to GAAS API Doc, GAAS is the service help you gorwth your user's retention rate with achievement system.

It's all design for developers to easily use it, you can use our API to access GAAS API endpoints, which can auto help you manage your user's achevement in our service.

We have language bindings in Shell and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


This example API documentation page was created with [GAAS](http://trygaas.com). 

# Authentication



To authorize, use this code:

GAAS uses API Token to allow access to the API. You can register a new GAAS API Token at our [Dashboard](http://trygaas.com).

Kittn expects for the API Token to be included in all API requests to the server in params that looks like the following:

`{ "api_token": "your-api-token" }`

<aside class="notice">
You must replace <code>your-api-token</code> with your projetc's API Token.
</aside>


# Events

## Send Event

```shell
curl -X POST 'http://trygaas/api/v1/events?name=my_event&user_id=tw_no_1&api_token=your_api_token'
```

```javascript
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```


> Return: If your user didn't get achievement through this event, return empty array.


```json
{
  "achievements": []
}
```


> Return: If your user got achievement through this event, return array of achievement objects.

```json
{
  "achievements": [
    {
      "id": 1,
      "icon_url": "http://trygaas.com/images/your_iconurl.jpg",
      "name": "Achievement 1",
      "description": "Achievement 1 description",
      "is_completed": true,
      "percentage": 100.0
    }
  ]
}

```


This endpoint send an event to GAAS, we return `Achievement` object back only if your user achieve it through this event.

### HTTP Request

`POST http://trygaas/api/v1/events`

### Query Parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | String | true | Event name, set it from your project
user_id | String | true | Your user's uniq ID.
api_token | String | true | Your project's API Token.

<aside class="success">
Notice — there are no "Event" object returned, only "Achievement" will be returned.
</aside>


# Achievement

## Describe Achievement object

All achievement objects will be base on a user (your user, identify by your user_id params)

> All Achievements object looks like this

```json
{
  "id": 1,
  "icon_url": "http://trygaas.com/images/your_iconurl.jpg",
  "name": "Achievement 1",
  "description": "Achievement 1 description",
  "is_completed": true,
  "percentage": 100.0
}
```

Attribute | Type | Meaning |
--------- | ---- | -------- |
id | String | Achievement ID
icon_url | String | Achievement badge icon's url
name | String | Achievement name
description | String | Achievement description
is_completed | String | To see if your user achieved this Achievement or not
percentage | String | To see how many percentage of condition your user got to achieved this Achievement




## Retrieve All Achievements


```shell
curl -X GET 'http://trygaas/api/v1/achievements?user_id=tw_no_1&api_token=your_api_token'
```

```javascript
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Return


```json
[
  {
    "id": 1,
    "icon_url": "http://trygaas.com/images/your_iconurl.jpg",
    "name": "Achievement 1",
    "description": "Achievement 1 description",
    "is_completed": true,
    "percentage": 100.0
  },
  {
    "id": 2,
    "icon_url": "http://trygaas.com/images/your_iconurl.jpg",
    "name": "Achievement 2",
    "description": "Achievement 2 description",
    "is_completed": false,
    "percentage": 50.0
  }
]
```


Retrieve all achievements for a specific user


### HTTP Request

`GET http://trygaas/api/v1/achievements`

### Query Parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
user_id | String | true | Your user's uniq ID.
api_token | String | true | Your project's API Token.


