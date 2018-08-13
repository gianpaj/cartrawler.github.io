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

  // Call this to navigate to the in path flow
  func didTapGroundTransportationCard() {  
  }

  // Called when best daily rate received
  func didReceiveGroundTransportationBestDailyRate(_ price: NSNumber, currency: String) {
  }

  // Called when best daily rate fails
  func didFailToReceiveGroundTransportationBestDailyRate() {
      print("Error on Ground Transportation request")
  }

  // Create Ground Transportation payment payload
  func didProduceGT(inPathPaymentRequest request: [AnyHashable : Any], vehicle: GTInPathVehicle) {
    print("\(request)")
    print("\(vehicle)")
  }

  // Refreshes the Ground Transportation in path search.
  // This will trigger a new best daily rate fetch, and the subsequent delegate callbacks
  // The SDK must be initialised, and the In Path card added before calling this method
  func refreshGroundTransportation(){
  }

  // Removes an added Ground Transportation if selected
  func removeGroundTransportation(){
  }


  ```
  {: title="InPath Delegate (GROUND TRANSPORTATION)" }
  ``` swift

  // Called when the in path card is tapped. We suggest to present the in path flow at this time.
  func didTapCrossSellCard() {
    CarTrawlerSDK.sharedInstance().presentInPath(from: self)
  }

  // Called when best daily rate received
  func didReceiveBestDailyRate(_ price: NSNumber, currency: String) {
  }

  // Called when best daily rate fails
  func didFailToReceiveBestDailyRate() {
  }

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

  // Refreshes the in path search.
  // This will trigger a new best daily rate fetch, and the subsequent delegate callbacks
  // The SDK must be initialised, and the In Path card added before calling this method
  func refreshInPath(){
  }

  // Removes an added vehicle if selected
  func removeVehicle(){
  }

  ```

  {: title="InPath Delegate (RENTAL)"}
  ``` swift

  carTrawlerSDK?.initializeGroundTransportationInPath(withClientId: "105614",
                                                      pickupAirportIATACode: "DUB",
                                                      dropoffAirportIATACode: "ALC",
                                                      pickupDateTime: 2018-08-10 10:24:17 +0000,
                                                      currencyCode: "EUR",
                                                      languageCode: "EN",
                                                      countryCode: "IE",
                                                      passengerQuantity: 1,
                                                      delegate: self)

  // Called when received best daily rates
  func didReceiveGroundTransportationBestDailyRate(_ price: NSNumber, currency: String) {
  }

  // Called when fails to receive best daily rates
  func didFailToReceiveGroundTransportationBestDailyRate() {
        print("Error on Ground Transportation request")
  }

  // Called when payment payload is received
  func didProduceGT(inPathPaymentRequest request: [AnyHashable : Any], vehicle: GTInPathVehicle) {
  }


  // Returns Rental Card to the client
  func getRentalCard()-> UIView {
  }

  // Returns Ground Transportation card to the client
  func getGroundTransportationCard() -> UIView{
  }

  ```

  {: title="Delegate" }
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

Present Stand Alone:

<dl>

  <dt>presentingViewController</dt><dd>Your view controller from which the SDK will be presented.</dd>
  <dt>clientID</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
  <dt>countryCode</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>currencyCode</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>

</dl>

Add In Path Card - See code to right for available methods and callbacks for in path

<dl>

  <dt>containerView</dt><dd>Your view from which your application will display the in path widget.</dd>
  <dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>customerCountry</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>airportCode</dt><dd>An optional IATA code.</dd>
  <dt>pickupDate</dt><dd>An required Pickup Date.</dd>
  <dt>pickupDate</dt><dd>An optional Return Date, default will be PickupDate + 3 days.</dd>
  <dt>flightNumber</dt><dd>An optional Flight Number, suck as "Flight 123".</dd>
  <dt>passengers</dt><dd>An optional Array of Passengers , the first one will be the main passenger.</dd>
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

InPath Delegate (RENTAL):

<dl>
<dt>clientID</dt>
<dd>Your client ID, required to use the CarTrawler InPath Delegate (RENTAL).</dd>
<dt>pickupAirportIATACode</dt>
<dd>An required IATA code for pickup airport.</dd>
<dt>dropoffAirportIATACode</dt>
<dd>An required IATA code for dropoff airport.</dd>
<dt>pickupDateTime</dt>
<dd>Date and time for required service.</dd>
<dt>currencyCode</dt>
<dd>An required currency code, such as "USD". Default is "EUR" if not provided.</dd>
<dt>languageCode</dt>
<dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
<dt>countryCode</dt>
<dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
<dt>passengerQuantity</dt>
<dd>Quantity of passengers</dd>
<dt>delegate</dt>
<dd>Your class that will handle callback methods</dd>
</dl>
