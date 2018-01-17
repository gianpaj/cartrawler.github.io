---
title: Usage
position: 3
type: iOS
description:
right_code: |
    ~~~ java
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
    ~~~
    {: title="Usage" }
---

This is the example of setup and configuration.