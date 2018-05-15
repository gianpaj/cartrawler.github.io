---
title: Usage
position: 3
type: Android
description:
right_code: >
  ~~~ java

  String clientId = "787697";

  Boolean production = false;

  String language = null; //Language is to be deprecated in the library interface

  String country = "IE";

  String currency = "EUR";


  HashMap<String, String> customAttributes = new HashMap<String, String>();


  CartrawlerSDK.presentCarTrawler(this, clientId, production, language, country,
  currency, customAttributes));

  ~~~

  {: title="Usage" }


  ~~~ xml

  <style name="YourThemeExtendingCTAppTheme" parent="CTAppTheme">
        <item name="colorPrimaryDark">#2AA9E0</item>
        <item name="colorPrimary">#21456D</item>
        <item name="colorAccent">#21456D</item>
  </style>

  ~~~

  {: title="Theme" }
---


Usage of the SDK is&nbsp;demonstrated to the right, the parameters are as follows:

<dl><dt>clientId</dt><dd>Your client ID, required to use the CarTrawler API.</dd><dt>production</dt><dd>A boolean to switch between test and production endpoints. Default is test.</dd><dt>language</dt><dd>An optional language code to switch between languages, NOTE: this field will be removed from the interface in the future and needs to be passed in as null</dd><dt>country</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd><dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd><dt>customAttributes</dt><dd>A hash map of attributes, custom to a particular partner.</dd></dl>

Custom Attributes:

<dl>
  <dt>loyaltyEnabled</dt><dd>A boolean key to enable loyalty field in the payment form</dd>
  <dt>customProgramID</dt><dd>A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES"</dd>
  <dt>flightNumberRequired</dt><dd>A String boolean value that enables or disables the flight number being required (default value is true), Example: "true"</dd>
  <dt>membershipID</dt><dd>A String value that is used to pre-populate the loyalty field</dd>
</dl>

You will need to create a theme that extends the **CTAppTheme** and set the values for the **colorPrimaryDark**, **colorPrimary** and **colorAccent** attributes.  **android:statusBarColor** can also be set to update the status bar color.
