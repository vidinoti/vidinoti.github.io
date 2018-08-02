---
layout: documentation
title: Tour
category: API
order: 2
---

This pages lists the available APIs for the tours.

# `GET /v1/tour` - Get the list of tours

## Parameters

* **maxResults** - optional, the maximum number of results to return (i.e. the size of a page) (default 100)
* **pageOffset** - optional, the page offset (default is 0)
* **sort** - optional, sort order. Allowed values are `name` and `-name`
* **tag** - optional, the tag requirements. By setting this value, you can filter the returned tours using the tags. It expects a JSON representation of 2 nested string array representing a logic combination of tags. For instance: `[["tag1", "tag2"],["tag3"]]` means *(tag1 AND tag2) OR tag3*.

## Response

HTTP 200 OK

Example:

`curl <Authentication Headers> 'https://sdk.vidinoti.com/v1/tour?tags=%5B%5B%22V-Discover%22%5D%5D&sort=name'`

    {
        "content": [
            {
            "id": 107,
            "name": "New 7 Wonders of the World",
            "shortDescription": "An amazing trip around the world !",
            "description": "Start your journey in Italia and travel the world to see all the 7 Wonders of the new World.\n\nNew7Wonders of the World was a campaign to choose Wonders of the World from a selection of 200 existing monuments. The New7Wonders Foundation claimed that more than 100 million votes were cast through the Internet or by telephone.\n\nWinners are :\n- The Colosseum\n- Petra\t\n- Taj Mahal\n- Great Wall of China\n- Chichen Itza\n- Machu Picchu\n- Christ the Redeemer",
            "length": "All around the globe",
            "duration": "Very long",
            "difficulty": null,
            "start": "Roma",
            "end": "Rio de Janeiro",
            "altitude": null,
            "latitude": 41.890308141,
            "longitude": 12.4922276392,
            "sequential": true,
            "imageUrl": "https://vidinoti.com/e7577c73-2be0-485d-a2cc-7551a8c1c570.jpg",
            "imageThumbnailUrl": "https://vidinoti.com/e7577c73-2be0-485d-a2cc-7551a8c1c570_thumbnail.jpg"
            }
        ],
        "totalPages": 1,
        "totalElements": 1,
        "last": true,
        "sort": [
            {
            "direction": "ASC",
            "property": "name",
            "ignoreCase": false,
            "nullHandling": "NATIVE",
            "ascending": true,
            "descending": false
            }
        ],
        "first": true,
        "numberOfElements": 1,
        "size": 100,
        "number": 0
    }

# `GET /v1/tour/:tourID` - Get the tour details

## Response

HTTP 200 OK

Example:

`curl <Authentication Headers> 'https://sdk.vidinoti.com/v1/tour/107'`

    {
        "id": 107,
        "name": "New 7 Wonders of the World",
        "shortDescription": "An amazing trip around the world !",
        "description": "Start your journey in Italia and travel the world to see all the 7 Wonders of the new World.\n\nNew7Wonders of the World was a campaign to choose Wonders of the World from a selection of 200 existing monuments. The New7Wonders Foundation claimed that more than 100 million votes were cast through the Internet or by telephone.\n\nWinners are :\n- The Colosseum\n- Petra\t\n- Taj Mahal\n- Great Wall of China\n- Chichen Itza\n- Machu Picchu\n- Christ the Redeemer",
        "length": "All around the globe",
        "duration": "Very long",
        "difficulty": null,
        "start": "Roma",
        "end": "Rio de Janeiro",
        "altitude": null,
        "latitude": 41.890308141,
        "longitude": 12.4922276392,
        "sequential": true,
        "imageUrl": "https://vidinoti.com/e7577c73-2be0-485d-a2cc-7551a8c1c570.jpg",
        "imageThumbnailUrl": "https://vidinoti.com/e7577c73-2be0-485d-a2cc-7551a8c1c570_thumbnail.jpg",
        "points": [
            {
            "name": "The Colosseum",
            "description": "The Colosseum or Coliseum, also known as the Flavian Amphitheatre, is an oval amphitheatre in the centre of the city of Rome, Italy.",
            "publicID": "gan2e97caw1ol5d",
            "type": "gps",
            "latitude": 41.890169,
            "longitude": 12.492269,
            "category": "The Seven New Wonders",
            "imageUrl": "https://ar.vidinoti.com/api/api.php?getImage=gan2e97caw1ol5d",
            "imageThumbnailUrl": "https://ar.vidinoti.com/api/api.php?getImageThumbnail=gan2e97caw1ol5d"
            },
            {
            "name": "Petra",
            "description": "Petra is a historical and archaeological city in southern Jordan.",
            "publicID": "ri0jpifmrvw9j9p",
            "type": "gps",
            "latitude": 30.328611,
            "longitude": 35.441944,
            "imageUrl": "https://ar.vidinoti.com/api/api.php?getImage=ri0jpifmrvw9j9p",
            "imageThumbnailUrl": "https://ar.vidinoti.com/api/api.php?getImageThumbnail=ri0jpifmrvw9j9p"
            }
        ]
    }