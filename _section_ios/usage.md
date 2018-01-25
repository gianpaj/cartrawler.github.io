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
{: .present-before-paste}

Code snippets for Objective-C and Swift are provided to the right, and a sample app for both languages is provided with the SDK.
{: .present-before-paste}

1. Import the SDK header files{: .present-before-paste}
2. Initialise the SDK{: .present-before-paste}
3. Present the SDK view controller{: .present-before-paste}