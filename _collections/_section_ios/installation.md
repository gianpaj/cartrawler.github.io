---
title: Installation
position: 0
type: iOS
description: 'Supports iOS 9, iOS 10 and iOS 11'
right_code: >-
  ~~~ ruby

  source 'https://github.com/CocoaPods/Specs.git'
  source 'https://github.com/cartrawler/cartrawler-ios-pods'
  platform :ios, '9.0'

  target 'CarTrawlerPartner' do
    pod 'CarTrawlerSDK', '~> 6.0.0'
  end

  ~~~

  {: title="Podfile" }

---


**CocoaPods**

1. Include the CarTrawler private spec repository in your podfile: source 'https://github.com/cartrawler/cartrawler-ios-pods'
2. Include the pod in your podfile: pod 'CarTrawlerSDK'
3. From the terminal, run: pod install.
