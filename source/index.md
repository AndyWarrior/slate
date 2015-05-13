---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Mamazon API. You can use our API to access Mamazon API endpoints, which can get information on the different products and breeds in our database.

We have a language binding in Shell, which gives an example of how to access the various endpoints.


# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Products

## Get All Products

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://localhost:3000/api/products"
  -H "Accept: application/vnd.list.com+json; version=1"
```

> The above command returns JSON structured like this:

```json
{

    "products": 

    [

        {

            "id": 1,
            "name": "Xbox one",
            "description": "Microsoft's successor to the Xbox 360",
            "price": 499.99,
            "image_url": "http://compass.xbox.com/assets/94/60/946002c9-dfc7-44fe-b20a-abf175c49d42.jpg?n=og-share-meet-xbox-one-955x955.jpg",
            "available": 5

        },
        {

            "id": 2,
            "name": "PlayStation 4",
            "description": "Sony's gaming console",
            "price": 599.99,
            "image_url": "http://cdn.latam.playstation.com/latamucm/groups/public/documents/webasset/ps4-hrdware-large6_mx.jpg",
            "available": 3

        },

        {
            "id": 3,
            "name": "Wii U",
            "description": "Nintendo's new home console following the success of the Wii",
            "price": 299.99,
            "image_url": "http://cdn02.nintendo-europe.com/media/images/03_teaser_module_1_square/systems_2/wiiu_3/TM_GenericWiiU.png",
            "available": 8
        }
    ]

}
```

This endpoint retrieves all products.

### HTTP Request

`GET http://localhost:3000/api/products`

### URL Parameters

There are no parameters for this request.


## Get a Specific Product

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://localhost:3000/api/products/1"
  -H "Accept: application/vnd.list.com+json; version=1"
```

> The above command returns JSON structured like this:

```json
{

    "product": 

    {
        "id": 1,
        "name": "Xbox one",
        "description": "Microsoft's successor to the Xbox 360",
        "price": 499.99,
        "image_url": "http://compass.xbox.com/assets/94/60/946002c9-dfc7-44fe-b20a-abf175c49d42.jpg?n=og-share-meet-xbox-one-955x955.jpg",
        "available": 5
    }

}
```

This endpoint retrieves a specific product.


### HTTP Request

`GET http://localhost:3000/api/products/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the product to retrieve

