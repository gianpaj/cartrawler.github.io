---
title: Usage
position: 2
type: iOS
description:
right_code: |-
  ~~~ java
  #import "ViewController.h"
  @import CarTrawlerSDK;

  @interface ViewController ()
  @property (nonatomic, strong) CarTrawlerSDK *sdk;
  @end

  @implementation ViewController

  - (void)viewDidLoad {
      [super viewDidLoad];
      self.sdk = [CarTrawlerSDK new];
  }

  - (IBAction)carRentalButtonTapped {
      [self.sdk presentCarTrawler:self
                         clientID:@"105614"
                       production:YES
                         language:@"EN"
                          country:@"IE"
                         currency:@"EUR"
                            style:nil
                 customAttributes:nil];
  }

  - (void)initializeGroundTransportationInPathWithClientId:(nonnull NSString *)clientId
									   pickupAirportIATACode:(nonnull NSString *)pickupAirportIATACode
									  dropoffAirportIATACode:(nonnull NSString *)dropoffAirportIATACode
										  pickupDateTime:(nonnull NSDate *)pickupDateTime
											currencyCode:(nonnull NSString *)currencyCode
											languageCode:(nonnull NSString *)languageCode
											 countryCode:(nullable NSString *)countryCode
									   passengerQuantity:(nullable NSNumber *)passengerQuantity
												delegate:(nullable id <CarTrawlerSDKDelegate>)delegate;

  @end

  ~~~
  {: title="Objective-C" }
  ~~~ java
  import CarTrawlerSDK

      let carTrawlerSDK = CarTrawlerSDK()

      @IBAction func carRentalButtonTapped(_ sender: Any) {

          carTrawlerSDK.presentCarTrawler(self,
                                          clientID: "105614",
                                          production: true,
                                          language: "EN",
                                          country: "IE",
                                          currency: "EUR",
                                          style: nil,
                                          customAttributes: nil)
      }

      carTrawlerSDK?.initializeGroundTransportationInPath(withClientId: (Constants.Parameters.gtPartnerId), pickupAirportIATACode: Constants.Parameters.iataPickupLocation, dropoffAirportIATACode: Constants.Parameters.iataDropoffLocationCode, pickupDateTime: pickUpDate, currencyCode: (settingsService?.currencyItem.parm)!, languageCode: (settingsService?.languageItem.parm)!, countryCode: (settingsService?.countryItem.parm)!, passengerQuantity: 1, delegate: self)
  ~~~
  {: title="Swift" }
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

Ground Transportation InPath:

<dl>
  <dt>clientID</dt>
  <dd>Your client ID, required to use the CarTrawler Ground Transportation InPath.</dd>
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
