---
title: iOS
position: 3
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
  ~~~ swift
  @import CarTrawlerSDK;

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
  user:nil
  style:nil
  customAttributes:customAttributes];
  }

  @end
  ~~~
  {: title="Swift" }
---


CarTrawler for iOS supports iOS 8, iOS 9, iOS 10 and iOS 11.

&nbsp;

&nbsp;