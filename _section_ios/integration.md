---
title: Integration
position: 2
type: iOS
description: 
right_code: |
    ~~~ swift
    source 'https://github.com/CocoaPods/Specs.git'
    source 'https://github.com/cartrawler/cartrawler-ios-pods'

    platform :ios, '8.0'

    target ‘MyTarget’ do
        pod 'CarTrawlerSDK', '~> 4.1'
        pod 'CTPayment', '~> 1.0'
    end
    {: title="CocoaPods" }
---

Car Trawler uses a private spec repository to publish libraries.

Include the CarTrawler spec repository and pods in your Podfile and run pod install