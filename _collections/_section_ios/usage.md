---
title: Usage
position: 2
type: iOS
description:
right_code: |-
  ``` swift

  CarTrawlerSDK.sharedInstance().initialiseSDK(with: nil, customParameters: nil, production: false)

  ```
  {: title="App Delegate" }
  ``` swift

  CarTrawlerSDK.sharedInstance().presentStandAlone(from: self, clientID: "105614", countryCode: "IE", currencyCode: "EUR", languageCode: "EN", passengers: nil)

  ```
  {: title="Stand Alone" }
  ``` swift
  
  // Call this to add the in path card, and trigger a best daily rate fetch
  CarTrawlerSDK.sharedInstance().addInPathCard(to: containerView, clientID: "105614", currency: "EUR", customerCountry: "IE", languageCode: "EN", iataCode: "ALC", pickupDate: pickUpDate, return: nil, flightNumber: "FL123", passengers: nil, delegate: self)
  
  // Call this to navigate to the in path flow
  CarTrawlerSDK.sharedInstance().presentInPath(from: self)
  
  // Call this to remove an added vehicle, and trigger a best daily rate fetch
  CarTrawlerSDK.sharedInstance().removeVehicle()
  
  // Call this to refresh the best daily rate
  CarTrawlerSDK.sharedInstance().refreshInPath()
  
  ```
  {: title="In Path" }
  ``` swift
  
  func didTapCrossSellCard() {
  CarTrawlerSDK.sharedInstance().presentInPath(from: self)
  }
  
  func didReceiveBestDailyRate(_ price: NSNumber, currency: String) {
  // Update best daily rate label
  }
  
  func didFailToReceiveBestDailyRate() {
  // Handle best daily rate error
  }
  
  // Required
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
  
  ```
  {: title="Delegate" }
---


The steps to use the SDK are:

1. Import the header files.
2. Initialise the SDK.
3. Present the SDK with the required parameters.

Initialisation of the SDK

<dl>
<dt>clientID</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
<dt>customParameters</dt><dd>A dictionary of parameters, custom to a particular partner.</dd>
<dt>style</dt><dd>An optional custom style object, used to set the fonts and primary, secondary and accent colors in the SDK. Please ensure any custom fonts used are included in your main bundle.</dd>
<dt>isSandboxMode</dt><dd>A boolean to switch between test and production endpoints.</dd>
</dl>

Usage of the SDK (StandAlone Mode) is demonstrated to the right, the parameters are as follows:

<dl>

  <dt>presentingViewController</dt><dd>Your view controller from which the SDK will be presented.</dd>  
  <dt>country</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>language</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>

</dl>

Usage of the SDK (InPath Mode) is demonstrated to the right, the parameters are as follows:

<dl>

  <dt>containerView</dt><dd>Your view from which your application will display the widget.</dd>  
  <dt>parentViewController</dt><dd>Your view controller from which the SDK will be presented (Delegate).</dd>  
  <dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>customerCountry</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>airportCode</dt><dd>An optional IATA code.</dd>
  <dt>pickupDate</dt><dd>An required Pickup Date.</dd>
  <dt>pickupDate</dt><dd>An optional Return Date, default will be PickupDate + 3 days.</dd>
  <dt>flightNumber</dt><dd>An optional Flight Number, suck as "Flight 123".</dd>
  <dt>passengers</dt><dd>An optional Array of Passengers , the first one will be the main passenger.</dd>


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
