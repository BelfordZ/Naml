Naml
====

Node API Modeling Language

Config.naml
```
title: "BlockBusted Video Rental"
useVersionedUrl: true
version: "v1"

validator: "lib/utils/validator"
permissions: "lib/permissions"

controllers: "lib/controllers"

models:
  Movies:
    
  Customers:
  
```

api.naml
```
/Movies:
  GET:
    params:
      genre:
        description: "Find movies for rent"
    responseHandler: controller.find
    
  POST:
    /{MovieId}:
      permissions: ["Customer", "Admin"]
      
      GET:
        description: "Returning the specified movie"
        responseHandler: controller.returnMovie
      
      POST:
        params:
          creditcard:
            description: "credit card number to charge for a rental."
            validate: CreditCard
        responseHandler controller.rentMovie
          
      DELETE:
        description: "Remove video from stock"
        permission: ["Admin"]
        responseHandler: controller.remove
          
```

permissions.naml
```
Movie:
  GET: ["Customer", "Admin", "Guest"]
  POST:
    "/{id}":
      GET:
```
