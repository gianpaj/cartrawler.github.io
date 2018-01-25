---
title: Usage
position: 3
type: Android
description:
right_code: |
    ~~~ java
    String clientId = "787697";
    Boolean production = false;
    String language = "EN";
    String country = "IE";
    String currency = "EUR";

    HashMap<String, String> customAttributes = new HashMap<String, String>();

    CartrawlerSDK.presentCarTrawler(this, clientId, production, language, country, currency, customAttributes));
    ~~~
    {: title="Usage" }

    ~~~ xml
    <color name="CT_ColorPrimary">#2AA9E0</color>
    <color name="CT_ColorSecondary">#21456D</color>
    <color name="CT_ColorAccent">#21456D</color>
    ~~~
    {: title="Colors" }
---

Now we are ready to start using the SDK.

The simplest form of usage is initializing the standalone booking sequence. You do it by simply calling the function we provide and passing the required parameters. Here is the list of parameters that our function accepts:

clientId
: client id, required to use CarTrawler API

production
: switch between test and production endpoints

language
: language code

country
: country code, can be null

currency
: currency code, can be null

customAttributes
: any additional attributes, custom to particular partner

You can also customise the color scheme of our engine by setting **CT_ColorPrimary**, **CT_ColorSecondary** and **CT_ColorAccent** values in your app's colors.xml.