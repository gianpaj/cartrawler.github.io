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

  // Create a context for standAlone flow
  let context = CTContext(clientID: "105614", flow: .standAlone)
  context.countryCode = "IE"
  context.currencyCode = "EUR"
  context.languageCode = "EN"
  CarTrawlerSDK.sharedInstance().present(from: self.view, context: context)
  ```
  {: title="Standalone" }

  ``` swift
  import CarTrawlerSDK

  // Create a context for standAlone flow
  let context = CTContext(clientID: "105614", flow: .standAlone)
  context.countryCode = "IE"
  context.currencyCode = "EUR"
  context.languageCode = "EN"
  context.pickupLocationID = "11" // Dublin airport code
  context.dropOffLocationID = "1316" // Cork airport code
  context.pinnedVehicleID = "1892038" // Vehicle RefID
  context.pickupDate = Date(timeIntervalSinceNow: 2629746), // next month
  context.dropOffDate = Date(timeIntervalSinceNow: 2888946), // next month + 3 days
  CarTrawlerSDK.sharedInstance().present(from: self.view, context: context)
  ```
  {: title="Deeplink" }

  ``` swift
  import CarTrawlerSDK

  let passenger = CTPassenger(firstName: "Ryan",
                              lastName: "O'Connor",
                              addressLine1: "DunDrum",
                              addressLine2: "Dublin 14",
                              city: "Dublin",
                              postcode: "Dublin 14",
                              countryCode: "IE",
                              age: 25,
                              email: "ryan.oconnor@cartrawler.com",
                              phone: "0838880000",
                              phoneCountryPrefix: "353",
                              isPrimaryDriver: true)
  ```
  {: title="Passenger" }

  ``` swift

   ```


---


The steps to use the SDK are:

1. Initialise the SDK in App Delegate
2. Initialise the CTContext object with the parameters required
3. Present the SDK

<h5>Initialisation of the SDK</h5>

<dl>
<dt>style</dt><dd>An optional style object, used to set the fonts and primary, secondary and accent colors in the SDK. Please ensure any custom fonts used are included in your main bundle.</dd>
<dt>customParameters</dt><dd>A dictionary of parameters, custom to a particular partner, see below for options.</dd>
<dt>production</dt><dd>A boolean to switch between endpoints, true is production, false is test.</dd>
</dl>

<h5>Initialing CTContext for Standalone</h5>

To initialise standalone flow, it is necessary to instanciate a CTContext object and set the context in the SDK.

<dl>
  <dt>clientID</dt><dd>A <b>required</b> client ID, required to use the CarTrawler API.</dd>
  <dt>flow</dt><dd>A <b>required</b> Must be <b>.standAlone</b>.</dd>
  <dt>countryCode</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>currencyCode</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>passengers</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
</dl>

<h5>Initialising CTContext for Standalone with Deeplinking</h5>

This is a variant on the standalone flow whereby the vehicle list is shown based on the pickup and dropoff parameters, rather than the regular initial search screen.
Optionally, if a vehicle refId is provided, this will be become the pinned item in the list.
If a user backs out of the list, it will return the user to the Cartrawler search.

- If the pickup and drop off dates are invalid, out of date, or not present the SDK will fallback to regular standalone search.
- If the vehicle refId is invalid (or out of date), the list will be shown without the vehicle being pinned.
- If the parameters are valid but no search results are returned by the CarTrawler system, the SDK will fallback to the regular standalone search.

<dl>
  <dt>clientID</dt><dd>A <b>required</b> client ID, required to use the CarTrawler API.</dd>
  <dt>flow</dt><dd>A <b>required</b> Must be <b>.standAlone</b>.</dd>
  <dt>countryCode</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>currencyCode</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>pickupDate</dt><dd>A <b>required</b> Pickup Date.</dd>
  <dt>dropOffDate</dt><dd>A <b>required</b> Drop-off Date.</dd>
  <dt>pickupLocation</dt><dd>An IATA code for pickup location. <b>If is set, won't be used pickupLocationID and dropOffLocationID</b></dd>
  <dt>pickupLocationID</dt><dd>An <b>required (if pickupLocation is not set)</b> OTA Location ID for pickup location.</dd>
  <dt>dropOffLocationID</dt><dd>An optional OTA Location ID for drop off location.</dd>
  <dt>pinnedVehicleID</dt><dd>An optional refId to highlight and pin a vehicle to the top of the list. Returned by the abandonment deeplink.</dd>
  <dt>passengers</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
</dl>

<h5>Presenting standalone</h5>

After the initialisation of CTContext object filled with your parameters, is needed to use the presentation method:

```swift
let viewController = UIViewController() // Your view controller from which the SDK will be presented.
self.carTrawlerSDK.present(from: viewController, context: context)
```

