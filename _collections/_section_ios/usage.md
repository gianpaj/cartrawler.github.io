---
title: Usage
position: 2
type: iOS
description:
right_code: |-
  ``` ruby

  #import "ViewController.h"
  #import "CarTrawlerSDK.h"

  @implementation ViewController

  - (void)viewDidLoad {
      [super viewDidLoad];
      [[CarTrawlerSDK sharedInstance] setupSDKWithClientID:@"105614"
                                          customParameters:nil
                                                     style:nil
                                                   sandBox:NO];
  }

#pragma mark - Stand Alone

  - (IBAction)presentStandAlone:(id)sender {
    [[CarTrawlerSDK sharedInstance] presentStandAloneFromViewController:self
                                                              country:@"IE"
                                                             currency:@"EUR"
                                                             language:@"EN"];
  }

#pragma mark - In Path

  @end

  ```
  {: title="Objective-C" }
  ``` swift

  import CarTrawlerSDK

    let carTrawlerSDK = CarTrawlerSDK.sharedInstance()

    override func viewDidLoad() {
      super.viewDidLoad()
      carTrawlerSDK.setupSDK(withClientID: "105614",
                             customParameters: nil,
                             style: nil,
                             sandBox:false)

    }

    //MARK: Stand Alone

    @IBAction func presentStandAlone(_ sender: Any) {
      carTrawlerSDK.presentStandAlone(from : self,
                                             country: "IE",
                                             currency: "EUR",
                                             language: "EN")
    }

    //MARK: In Path

  ```
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
