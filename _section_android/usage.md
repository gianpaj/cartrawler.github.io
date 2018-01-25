---
title: Usage
position: 3
type: Android
description:
right_code: >
  ~~~ java

  String clientId = "787697";

  Boolean production = false;

  String language = "EN";

  String country = "IE";

  String currency = "EUR";


  HashMap<String, String> customAttributes = new HashMap<String, String>();


  CartrawlerSDK.presentCarTrawler(this, clientId, production, language, country,
  currency, customAttributes));

  ~~~

  {: title="Usage" }


  ~~~ xml

  <color name="CT_ColorPrimary">#2AA9E0</color>

  <color name="CT_ColorSecondary">#21456D</color>

  <color name="CT_ColorAccent">#21456D</color>

  ~~~

  {: title="Colors" }
---


Usage of the SDK is demonstrated to the right, the parameters are as follows:

<dl><dt>clientId (String)</dt><dd>client id, required to use CarTrawler API</dd><dt>production (Boolean)</dt><dd>switch between test and production endpoints</dd><dt>language (String)</dt><dd>language code</dd><dt>country (String)</dt><dd>country code, can be null</dd><dt>currency (String)</dt><dd>currency code, can be null</dd><dt>customAttributes (Hashmap)</dt><dd>any additional attributes, custom to particular partner</dd></dl>

You can also customise the color scheme of our engine by setting **CT\_ColorPrimary**, **CT\_ColorSecondary** and **CT\_ColorAccent** values in your app's colors.xml file.