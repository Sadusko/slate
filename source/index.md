---
title: API Reference

language_tabs:
  - c#

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Rocket API! You can use our API to access Rocket API endpoints, which can get information on various information about players and objects in Unturned.

The API is written in C# and only supports C#! You can view code examples for using the parts of the API in the dark area to the right.

This is bound to change as Rocket is a constant work in progress and this documentation may be outdated.

# Components
## RocketPlayerComponent
> To use, your class should inherit from this component

```csharp
public class PluginPlayer : RocketPlayerComponent {

	public bool HasKitten;
	
	public void Load() {
		this.HasKitten = true;
	}
	
	public void FixedUpdate() {
		if (this.Loaded && this.HasKitten) {
			RocketChatManager.Say(this.PlayerInstance, "You have a kitten!");
		}
	}
}
```

Applied to all players when they connect and removed when they disconnect (or plugin unloaded).

### Fields
Name | Type | Default
---------- | ---------- | ----------
PlayerInstance | RocketPlayer | Current RocketPlayer instance


Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```C#
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```


> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```C#
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

