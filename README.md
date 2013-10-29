Naml
====

Node API Modeling Language
```
title: BlockBusted Video Rental
useVersionedUrl = true
version = "v1"

validator: "lib/utils/validator"
permissions: "lib/permissions"

controllers: "lib/controllers"

models:
  Movies:
    
  Customers:
  

/Movies:
  get:
    queryParameters:
      genre:
        description: filter the songs by genre
    post:
      /{songId}:
        get:
          body:
            application/json:
              schema: |
                { "$schema": "http://json-schema.org/schema",
                  "type": "object",
                  "description": "The canonical song representation",
                  "properties": {
                    "title":  { "type": "string" },
                    "artist": { "type": "string" }
                  }
                  "required": [ "title", "artist" ]
                }
            application/xml:
    delete:
      description: |
        This method will *delete* an **individual song**
```
