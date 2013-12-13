Naml
====

Node API Modeling Language

Inspiration from projects like 
 - http://raml.org/
 - https://github.com/intridea/grape

Config.naml
```
title: "BlockBusted Video Rental"
useVersionedUrl: true
version: "v1"

validator: "lib/utils/validator/"
permissions: "lib/permissions/"

controllers: "lib/controllers/"

Validators: "lib/utils/validators/"
```

api.naml
```
/Movie:
  GET:
    params:
      title: # defines some properties and actions that will act on this param.
        description: "a title being searched"  # For api documentation generation.
        validate: Validators.Movie.title   # Will look for a property 'catagoryName 
                                           #  in your defined validators module'
      catagory_name:
        description: "a catagory to look for"
        normalize: Normalizers.String.toLower, Normalizers.String.escape
        validate: Validators.String.length [3..14]
    Controller: controller.find
    View: Views.Movie.find # render the callback result with the specified template/engine
  
  /{MovieId}: # for example, /Movies/23142...
    GET:
      description: "Returning the specified movie"
      controller: Controllers.Movie.return
    
    POST:
      params:
        creditcard:
          description: "credit card number to charge for a rental."
          validate: Validators.String.CreditCard
      controller: Controllers.Movie.rent
        
    DELETE:
      description: "Remove video from stock"
      controller: Controller.Movie.remove
            
