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


Usage of the SDK is&nbsp;demonstrated to the right, the parameters are as follows:

<dt>clientId</dt><dd>Your client ID, required to use the CarTrawler API.</dd><dt>production</dt><dd>A boolean to switch between test and production endpoints. Default is test.</dd><dt>language</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd><dt>country</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd><dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd><dt>customAttributes</dt><dd>A hash map of attributes, custom to a particular partner.</dd>

You may also customise the color scheme by setting **CT\_ColorPrimary**, **CT\_ColorSecondary** and **CT\_ColorAccent** values in your app's colors.xml file.