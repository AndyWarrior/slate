---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Mamazon API. You can use our API to access Mamazon API endpoints, which can get information on the different products and breeds in our database.

We have a language binding in Shell, which gives an example of how to access the various endpoints.


# Authentication

## Create session

```shell
# With shell, you need to access the sign in endpoint sending the email and password as parameters to receive a json strcture user with the auth_token attribute
curl "localhost:3000/api/sign_in"
```
> The above command returns JSON structured like this:

```json
{
    "id":2,
    "email":"andres@andres.com",
    "budget":null,
    "created_at":"2015-05-14T22:00:03.507Z",
    "updated_at":"2015-05-15T03:52:08.729Z",
    "auth_token":"-zMbsrU8BcFxzC8zcpUb"
}
```
This endpoint creates a new session that returns an authentication token that you can use to access the different endpoints of the API.

### HTTP Request

`POST http://localhost:3000/api/sign_in`

### Parameters

Parameter | Description
--------- | -----------
email | The email of an existing user
password | The password of an existing user

Mamazon uses API tokens to allow access to the API. To use the Mamazon API you first need to create a session and then use the token received to access the endpoints.

Mamazon expects for the API token and the Accept header to be included in all API requests to the server in headers that look like the following:

`Accept: application/vnd.list.com+json; version=1`

`Authorization: Token token=auth_token`

<aside class="notice">
You must replace <code>auth_token</code> with the token you receive after creating a session.
</aside>

## Destroy session

```shell
# With shell, you need to access the sign out endpoint passing the auth_token as a header
curl "localhost:3000/api/sign_in"
  -H "Accept: application/vnd.list.com+json; version=1"
  -H "Authorization: Token token=auth_token"
```

> The above command returns a 204 status which means the session ended.

This endpoint destroys the current session, and requiring the user to sign in again to receive a new token.

### HTTP Request

`DELETE http://localhost:3000/api/sign_out`

### Parameters

This request requires no parameters.


# Products

## Get All Products


```shell
curl "http://localhost:3000/api/products"
  -H "Accept: application/vnd.list.com+json; version=1"
  -H "Authorization: Token token=auth_token"
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


```shell
curl "http://localhost:3000/api/products/1"
  -H "Accept: application/vnd.list.com+json; version=1"
  -H "Authorization: Token token=auth_token"
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


## Update a product


```shell
curl "http://localhost:3000/api/products/1"
  -H "Accept: application/vnd.list.com+json; version=1"
  -H "Authorization: Token token=auth_token"
```

> The above command returns JSON like this:

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

This endpoint updates the attributes of a certain product.


### HTTP Request

`PATCH http://localhost:3000/api/products/<ID>`

### Parameters

Parameter | Description
--------- | -----------
name | The name of the product
description | The description of a product
price | The price of a product
image_url | The link to an image
available | The number of available productss