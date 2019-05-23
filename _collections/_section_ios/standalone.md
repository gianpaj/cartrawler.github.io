---
title: Standalone
position: 2
type: iOS
description:
right_code: |-
  ``` swift

  import CarTrawlerSDK

  // In application(_:didFinishLaunchingWithOptions:)
  CarTrawlerSDK.sharedInstance().initialiseSDK(
    with: nil,
    customParameters: nil,
    production: false)

  ```
  {: title="App Delegate" }
  ``` swift

  import CarTrawlerSDK

  CarTrawlerSDK.sharedInstance().presentStandAlone(
    from: self,
    clientID: "105614",
    countryCode: "IE",
    currencyCode: "EUR",
    languageCode: "EN",
    passengers: nil)

  ```
  {: title="Standalone" }

  ``` swift

  import CarTrawlerSDK

  CarTrawlerSDK.sharedInstance().presentStandAlone(
    from: self,
    clientID: "105614",
    countryCode: "IE",
    currencyCode: "EUR",
    languageCode: "EN",
    pickupDate: Date(timeIntervalSinceNow: 2629746), // next month
    dropOffDate: Date(timeIntervalSinceNow: 2888946), // next month + 3 days
    iataCode: "DUB",
    pickupLocationID: "11", // Dublin airport code
    dropOffLocationID: "1316", // Cork airport code
    pinnedVehicleID: "1892038", // Vehicle RefID
    passengers: nil)

   ```
   {: title="Deeplink" }

  ``` swift

   ```


---


The steps to use the SDK are:

1. Initialise the SDK in App Delegate
2. Present the SDK in either stand alone or in path mode

Initialisation of the SDK

<dl>
<dt>style</dt><dd>An optional style object, used to set the fonts and primary, secondary and accent colors in the SDK. Please ensure any custom fonts used are included in your main bundle.</dd>
<dt>customParameters</dt><dd>A dictionary of parameters, custom to a particular partner, see below for options.</dd>
<dt>production</dt><dd>A boolean to switch between endpoints, true is production, false is test.</dd>
</dl>

<h5>Present Stand Alone</h5>

<dl>

  <dt>presentStandAlone</dt><dd>Your view controller from which the SDK will be presented.</dd>
  <dt>clientID</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
  <dt>countryCode</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>currencyCode</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>passengers</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>

</dl>

Present Stand Alone with Deeplinking :

This is a variant on the standalone flow whereby the vehicle list is shown based on the pickup and dropoff parameters, rather than the regular initial search screen.
Optionally, if a vehicle refId is provided, this will be become the pinned item in the list.
If a user backs out of the list, it will return the user to the Cartrawler search.

- If the pickup and drop off dates are invalid, out of date, or not present the SDK will fallback to regular standalone search.
- If the vehicle refId is invalid (or out of date), the list will be shown without the vehicle being pinned.
- If the parameters are valid but no search results are returned by the CarTrawler system, the SDK will fallback to the regular standalone search.

<dl>

  <dt>presentStandAlone</dt><dd>Your view controller from which the SDK will be presented.</dd>
  <dt>clientID</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
  <dt>countryCode</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>currencyCode</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>pickupDate</dt><dd>A required Pickup Date.</dd>
  <dt>dropOffDate</dt><dd>A required Drop-off Date.</dd>
  <dt>IATACode</dt><dd>An optional IATA code for pickup location</dd>
  <dt>pickupLocationID</dt><dd>A required OTA Location ID for pickup location.</dd>
  <dt>dropOffLocationID</dt><dd>An optional OTA Location ID for drop off location.</dd>
  <dt>pinnedVehicleID</dt><dd>An optional refId to highlight and pin a vehicle to the top of the list. Returned by the abandonment deeplink.</dd>
  <dt>passengers</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
</dl>
