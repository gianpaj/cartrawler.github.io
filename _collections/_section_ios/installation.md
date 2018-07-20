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
    pod 'CarTrawlerSDK', '~> 5.4.0'
  end

  ~~~

  {: title="Podfile" }

  ~~~ ruby

  bash
  "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/CarTrawlerSDK.framework/strip-frameworks.sh"

  bash
  "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/CTPayment.framework/strip-frameworks.sh"

  ~~~

  {: title="Manual" }
---


**CocoaPods**

1. Include the CarTrawler private spec repository in your podfile: source 'https://github.com/cartrawler/cartrawler-ios-pods'
2. Include the pod in your podfile: pod 'CarTrawlerSDK'
3. From the terminal, run: pod install. Note you will have to enter your Github credentials when you run this for the first time.

**Manual Installation**

1. Download the&nbsp;[CarTrawlerSDK](https://github.com/cartrawler/cartrawler-ios-sdk/archive/master.zip)&nbsp;and [CTPayment](https://github.com/cartrawler/cartrawler-ios-payment/archive/master.zip) libraries and extract the zip files.
2. Go to your Xcode project's "General" settings. Drag CarTrawlerSDK.framework and CTPayment.framework to the "Embedded Binaries" section. Make sure "Copy items if needed" is selected and click Finish.
3. Create a new "Run Script Phase" in your app’s target’s "Build Phases" and paste the snippet found in the Manual tab on the right in the script text field. This step is required to work around an [App Store submission bug](http://www.openradar.me/radar?id=6409498411401216) when archiving universal binaries.