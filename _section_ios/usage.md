---
title: Usage
position: 2
type: iOS
description:
right_code: |-
  ~~~ java
  @import CarTrawlerSDK;

  @interface ClientViewController ()
  @property (nonatomic, strong) CarTrawlerSDK *sdk;
  @end

  @implementation ClientViewController

  - (void)viewDidLoad {
      [super viewDidLoad];
      self.carTrawlerSDK = [CarTrawlerSDK new];
  }

  - (void)carRentalButtonTapped {
      [self.sdk presentCarTrawler:self
                         clientID:@"123456"
                       production:YES
                         language:@"EN"
                          country:@"IE"
                         currency:@"EUR"
                            style:nil
                 customAttributes:nil];
  }
  ~~~
  {: title="Objective-C" }
  ~~~ java
  import CarTrawlerSDK 

      let carTrawlerSDK = CarTrawlerSDK()

      @IBAction func carRentalButtonTapped(_ sender: Any) {
          let customAttributes = ["offlineMode": false,
                                  "loggingEnabled": true]
          
          let style = customStyle()
          
          carTrawlerSDK.presentCarTrawler(self,
                                          clientID: "123456",
                                          production: true,
                                          language: "EN",
                                          country: "IE",
                                          currency: "EUR",
                                          style: style,
                                          customAttributes: customAttributes)
      }
  ~~~
  {: title="Swift" }
---


CarTrawler for iOS supports iOS 9, iOS 10 and iOS 11.

Code snippets for Objective-C and Swift are provided to the right, and a sample app for both languages is provided with the SDK.

The steps to use the SDK are:

1. Import the header files
2. Initialise the SDK
3. Present the SDK view controller with the relevant parameters

Parameters:

<dl><dt>presentingViewController</dt><dd>The view controller, from which the SDK will be presented</dd><dt>clientID</dt><dd>Your client ID, required to use the CarTrawler API.</dd><dt>production</dt><dd>A boolean to switch between test and production endpoints.</dd><dt>language</dt><dd>An optional language code to switch between languages. Default is "EN" if not provided.</dd><dt>country</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd><dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd><dt>style</dt><dd>An optional custom style object, used to set the color scheme and fonts of the SDK. Please ensure any custom fonts used are included in your main bundle</dd><dt>customAttributes</dt><dd>A dictionary of attributes, custom to a particular partner.</dd></dl>



