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
                         clientID:@"787697"
                       production:YES
                         language:@"EN"
                          country:@"IE"
                         currency:@"EUR"
                            style:nil
                 customAttributes:nil];
  }
  
  @end
  
  ~~~
  {: title="Objective-C" }
  ~~~ java
  import CarTrawlerSDK

      let carTrawlerSDK = CarTrawlerSDK()

      @IBAction func carRentalButtonTapped(_ sender: Any) {

          carTrawlerSDK.presentCarTrawler(self,
                                          clientID: "123456",
                                          production: true,
                                          language: "EN",
                                          country: "IE",
                                          currency: "EUR",
                                          style: nil,
                                          customAttributes: nil)
      }
  ~~~
  {: title="Swift" }
---


The steps to use the SDK are:

1. Import the header files.
2. Initialise the SDK.
3. Present the SDK with the required parameters.

Usage of the SDK is demonstrated to the right, the parameters are as follows:

<dl>

  <dt>presentingVC</dt><dd>Your view controller from which the SDK will be presented.</dd><dt>clientID</dt><dd>Your client ID, required to use the CarTrawler API.</dd><dt>production</dt><dd>A boolean to switch between test and production endpoints.</dd><dt>language</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd><dt>country</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd><dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd><dt>style</dt><dd>An optional custom style object, used to set the fonts and primary, secondary and accent colors in the SDK. Please ensure any custom fonts used are included in your main bundle.</dd>
  <dt>customAttributes</dt>
  <dd>A dictionary of attributes, custom to a particular partner.</dd>

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
</dl>
