---
title: Usage
position: 2
type: iOS
description:
right_code: |-
  ``` swift

  CarTrawlerSDK.sharedInstance().initialiseSDK(
    with: nil,
    customParameters: nil,
    production: false)

  ```
  {: title="App Delegate" }
  ``` swift

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

  CarTrawlerSDK.sharedInstance().presentStandAlone(
    from: self,
    clientID: "105614",
    countryCode: "IE",
    currencyCode: "EUR",
    languageCode: "EN",
    pickupDate: Date(),
    dropOffDate: Date(),
    pickupLocationID: "11", // Dublin airport code
    dropOffLocationID: "1316", // Cork airport code
    pinnedVehicleID: "1892038", // Vehicle RefID
    passengers: nil)

   ```
   {: title="Standalone (deeplink)" }

  ``` swift

  // Returns Rental Card to the client
  func getRentalCard()-> UIView {
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
  func didFailToReceiveBestDailyRate() {
  }

  // Create Ground Transportation payment payload
  func didProduceGT(inPathPaymentRequest request: [AnyHashable : Any], vehicle: GTInPathVehicle) {
    print("\(vehicle.totalCost!) EUR"))
  }

  // Call this to navigate to the in path flow
  func didTapGroundTransportationCard() {  
  }


  // Called when received best daily rates
  func didReceiveGroundTransportationBestDailyRate(_ price: NSNumber, currency: String) {
  }

  // Called when fails to receive best daily rates
  func didFailToReceiveGroundTransportationBestDailyRate() {
        print("Error on Ground Transportation request")
  }

  ```

  {: title="Delegate" }
  ``` swift

  // This will trigger a new best daily rate fetch, and the subsequent delegate callbacks
  // The SDK must be initialised, and a CTBestDailyRateParams object with the necessary parameters must be set before calling this method
  let params = CTBestDailyRateParams()
  params.delegate = self
  params.clientID = “12345”
  params.countryCode = “IE”
  params.currencyCode = “EUR”
  params.languageCode = “EN”
  params.iataCode = “DUB”
  params.pickupDate = Date()
  params.dropOffDate = Date()
        
  CarTrawlerSDK.sharedInstance().requestBestDailyRate(params)

  ```

  {: title="Best Daily Rates" }
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

Present Stand Alone with Deeplinking :

This is a variant on the standalone flow whereby the vehicle list is shown based on the pickup and dropoff parameters, rather than the regular initial search screen.
Optionally, if a vehicle refId is provided, this will be become the pinned item in the list.
If a user backs out of the list, it will return the user to the Cartrawler search.

- If the pickup and drop off dates are invalid, out of date, or not present the SDK will fallback to regular standalone search.
- If the vehicle refId is invalid (or out of date), the list will be shown without the vehicle being pinned.
- If the parameters are valid but no search results are returned by the CarTrawler system, the SDK will fallback to the regular standalone search.

<dl>

  <dt>presentingViewController</dt><dd>Your view controller from which the SDK will be presented.</dd>
  <dt>clientID</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
  <dt>countryCode</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>currencyCode</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>pickupLocationID</dt><dd>A required OTA Location ID for pickup location.</dd>
  <dt>dropOffLocationID</dt><dd>An optional OTA Location ID for drop off location.</dd>
  <dt>pickupDate</dt><dd>A required Pickup Date.</dd>
  <dt>dropOffDate</dt><dd>A required Drop-off Date.</dd>
  <dt>pinnedVehicleID</dt><dd>An optional refId to highlight and pin a vehicle to the top of the list. Returned by the abandonment deeplink.</dd>

</dl>

Add In Path Card - See code to right for available methods and callbacks for in path

<dl>

  <dt>containerView</dt><dd>Your view from which your application will display the in path widget.</dd>
  <dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
  <dt>customerCountry</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
  <dt>languageCode</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd>
  <dt>airportCode</dt><dd>An optional IATA code.</dd>
  <dt>pickupDate</dt><dd>A required Pickup Date.</dd>
  <dt>dropOffDate</dt><dd>An optional Return Date, default will be PickupDate + 3 days.</dd>
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

InPath Delegate (RENTAL):

<dl>
<dt>clientID</dt>
<dd>Your client ID, required to use the CarTrawler InPath Delegate (RENTAL).</dd>
<dt>pickupAirportIATACode</dt>
<dd>A required IATA code for pickup airport.</dd>
<dt>dropoffAirportIATACode</dt>
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

Request Best Daily Rates: 

The best daily rates API has been exposed independently of the CarTrawler SDK workflows (inPath & Standalone). This will return the best recommended rate for an individual vehicle at a specific location. 

After initializing the SDK, please create a CTBestDailyRateParams object and initialize it with the following parameters: 
<dl>
<dt>delegate</dt>
<dd>a delegate for receiving the best daily rate response</dd>
<dt>ClientID</dt>
<dd>Your client ID, required to use the CarTrawler API.</dd>
<dt>countryCode</dt>
<dd>A country code, such as "US". Default is the device location if not provided.</dd>
<dt>currencyCode</dt>
<dd>A currency code, such as "USD". Default is "EUR" if not provided</dd>
<dt>languageCode</dt>
<dd>A language code. Default is "EN" if not provided.</dd>
<dt>pickupDate</dt>
<dd>A required Pickup Date.</dd>
<dt>dropOffDate</dt>
<dd>A required Drop-off Date.</dd>
<dt>IATACode </dt>
<dd>An optional IATA code for pickup location.</dd>
<dt>pickupLocationID</dt>
<dd>An optional OTA Location ID for pickup location.</dd>
<dt>dropOffLocationID</dt>
<dd>An optional OTA Location ID for drop off location.</dd>
<dt>passengers</dt>
<dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
</dl>

Calling the requestBestDailyRate function will trigger a best daily rate request based on the provided IATA or PickupLocationCode and pickup and dropoff dates. 

The best daily rate (price and currency) will be returned in the CarTrawlerSDKDelegate function didReceiveBestDailyRate. 
