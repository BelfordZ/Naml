Naml
====

Node API Modeling Language

Config.naml
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
  
```

api.naml
```
/Movies:
  Get:
    params:
      genre:
        description: Find movies for rent
    responseHandler: controller.find
    
  Post:
    /{MovieId}:
      permissions: ["Customer", "Admin"]
      
      Get:
        description: Returning the specified movie
        responseHandler: controller.returnMovie
      
      Post:
        params:
          creditcard:
            description: credit card number to charge for a rental.
            validate: CreditCard
        responseHandler controller.rentMovie
          
      Delete:
        description: Remove video from stock
        permission: ["Admin"]
        responseHandler: controller.remove
          
```
