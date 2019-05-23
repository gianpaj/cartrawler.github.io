---
title: Inpath
position: 3
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
  CarTrawlerSDK.sharedInstance().initialiseInPath(withClientID: "105614",
                                                        currency: "EUR",
                                                        customerCountry: "IE",
                                                        languageCode: "EN",
                                                        iataCode: "DUB",
                                                        pickupDate: Date(timeIntervalSinceNow: 86400),
                                                        return: nil,
                                                        pinnedVehicleID: nil, // New parameter for abandonment flow
                                                        flightNumber: "111",
                                                        passengers: nil,
                                                        delegate: self)

  ```

  {: title="Initialisation"}
  ``` swift

  import CarTrawlerSDK

  // Required. Called when user wants to add in path booking to their flight booking.
  func didProduce(inPathPaymentRequest request: [AnyHashable : Any], vehicle: CTInPathVehicle) {
    print("\(request)")

    print("Total \(vehicle.totalCost)")
    print("Insurance \(vehicle.insuranceCost)")

    print("Vehicle Name \(vehicle.vehicleName)")
    print("Vehicle First Name \(vehicle.firstName)")
    print("Vehicle LastName \(vehicle.lastName)")

    print("*** PAYNOW: \(vehicle.payNowPrice)\n" ,
    "*** PAYLATER: \(vehicle.payLaterPrice)\n" ,
    "*** PAYDESK: \(vehicle.payAtDeskPrice)\n" ,
    "*** BOOKINGFEE: \(vehicle.bookingFeePrice)\n")
  }

  // Called when the in path card is tapped. We suggest to present the in path flow at this time.
  func didTapCrossSellCard() {
    CarTrawlerSDK.sharedInstance().presentInPath(from: self)
  }

  // Called when best daily rate received
  func didReceiveBestDailyRate(_ price: NSNumber, currency: String) {
  }

  // Called when best daily rate fails
  func didFailToReceiveBestDailyRate(error: Error) {
  }

  ```

  {: title="Delegate" }
  
  ``` swift

   ```


---


The steps to use the SDK are:

1. Initialise the SDK in App Delegate
2. Present the SDK in either standalone or inpath mode

Initialisation of the SDK

<dl>
<dt>style</dt><dd>An optional style object, used to set the fonts and primary, secondary and accent colors in the SDK. Please ensure any custom fonts used are included in your main bundle.</dd>
<dt>customParameters</dt><dd>A dictionary of parameters, custom to a particular partner, see below for options.</dd>
<dt>production</dt><dd>A boolean to switch between endpoints, true is production, false is test.</dd>
</dl>

<h5>Add Inpath Card</h5>
See code to right for available methods and callbacks for in path

<dl>

  <dt>containerView</dt><dd>Your view from which your application will display the in path widget.</dd>
  <dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>customerCountry</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>IATACode</dt><dd>An optional IATA code.</dd>
  <dt>pickupDate</dt><dd>A required Pickup Date.</dd>
  <dt>returnDate</dt><dd>An optional Return Date, default will be PickupDate + 3 days.</dd>
  <dt>pinnedVehicleID</dt><dd>An optional refId to highlight and pin a vehicle to the top of the list. Returned by the abandonment deeplink.</dd>
  <dt>flightNumber</dt><dd>An optional Flight Number, such as "Flight 123".</dd>
  <dt>passengers</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
  <dt>delegate</dt><dd>A delegate for in path callbacks</dd>

</dl>

Custom Attributes:

<dl>
  <dt>loyaltyEnabled</dt>
  <dd>A boolean key to enable loyalty field in the payment form</dd>
  <dt>customProgramID</dt>
  <dd>A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES"</dd>
  <dt>membershipID</dt>
  <dd>A String value that represents the membershipID, it will be pre populated in the Payment Form. Example: "123"</dd>
  <dt>flightNumberRequired</dt>
  <dd>A boolean key to enable Flight Number as a required field in the Payment Form. Default : 1 </dd>
  <dt>ORDERID</dt>
  <dd>A String value that represents the Order ID</dd>
  <dt>MyAccountId</dt>
  <dd>A String value that represents the Account ID</dd>
  <dt>VisitorId</dt>
  <dd>A String value that represents the Visitor ID </dd>
</dl>

InPath Delegate:

<dl>
<dt>clientID</dt>
<dd>Your client ID, required to use the CarTrawler InPath Delegate.</dd>
<dt>pickupAirportIATA...</dt>
<dd>A required IATA code for pickup airport.</dd>
<dt>dropoffAirportIATA...</dt>
<dd>A required IATA code for dropoff airport.</dd>
<dt>pickupDateTime</dt>
<dd>Date and time for required service.</dd>
<dt>currencyCode</dt>
<dd>A required currency code, such as "USD". Default is "EUR" if not provided.</dd>
<dt>languageCode</dt>
<dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
<dt>countryCode</dt>
<dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
<dt>passengerQuantity</dt>
<dd>Quantity of passengers</dd>
<dt>delegate</dt>
<dd>Your class that will handle callback methods</dd>
</dl>