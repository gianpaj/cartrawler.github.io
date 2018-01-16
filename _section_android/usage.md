---
title: Usage
position: 3
type: Android
description:
right_code: |
    ~~~ java
    Context context = getApplicationContext();
        
    Boolean production = false;
    String requestor = "787697";
    String language = "EN";
    String country = "IE";
    String currency = "EUR";

    User user = new User("Title", “Name”, “Surname”, “Email”, “Phone”, “Address”, “City”, “Postcode”, “Country”, “Flight code“, “Age”);
    
    HashMap<String, String> customAttributes = Interface.getCustomAttributes();

    Intent rentalIntent = Interface.getRentalIntent(getApplicationContext(), user, requestor, production, language, country, currency, customAttributes);
    startActivity(rentalIntent);
    ~~~
    {: title="Usage" }
---

Now we are ready to start using the SDK.

The simplest form of usage is initializing the standalone booking sequence. You do it in 2 steps: first use the function that we provide to create the intent, then simply launch the activity with it. Here is the list of parameters that our function accepts:

production
: switch between test and production endpoints

requestor
: client id, required to use CarTrawler API

language
: language code

country
: country code, can be null

currency
: currency code, can be null

user
: user data object (we provide class for it), can be null

customAttributes
: any additional attributes, custom to particular partner