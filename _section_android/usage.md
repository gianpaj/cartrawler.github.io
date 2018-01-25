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

<dl><dt>clientId</dt><dd>Your client ID, required to use the CarTrawler API.</dd><dt>production</dt><dd>A boolean to switch between test and production endpoints. Default is test.</dd><dt>language</dt><dd>A language code to switch between languages. Default is "en".</dd><dt>country</dt><dd>A country code, such as "IE". Can be null. Default is the device location if not provided.</dd><dt>currency</dt><dd>A currency code, such as "USD". Can be null. Default is "EUR".</dd><dt>customAttributes</dt><dd>A hash map of attributes, custom to a particular partner.</dd></dl>

You can also customise the color scheme of our engine by setting **CT\_ColorPrimary**, **CT\_ColorSecondary** and **CT\_ColorAccent** values in your app's colors.xml file.