---
title: Integration
position: 2
type: iOS
description: 
right_code: |
    ~~~ ruby
    source 'https://github.com/CocoaPods/Specs.git'
    source 'https://github.com/cartrawler/cartrawler-ios-pods'

    platform :ios, '8.0'

    target ‘MyTarget’ do
      pod 'CarTrawlerSDK', '~> 4.1'
      pod 'CTPayment', '~> 1.0'
    end
    ~~~
    {: title="Podfile" }
    ~~~ ruby
    github "cartrawler/cartrawler-ios-sdk"
    ~~~
    {: title="Cartfile" }
    ~~~ ruby
    bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/CarTrawlerSDK.framework/strip-frameworks.sh"
    bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/CTPayment.framework/strip-frameworks.sh"
    ~~~
    {: title="Manual" }
---

**CocoaPods**

1. Include the CarTrawler [private spec repository](http://guides.cocoapods.org/making/private-cocoapods.html) in your podfile:
```
source 'https://github.com/cartrawler/cartrawler-ios-pods'
```
2. Include the pod in your podfile:
```
pod 'CarTrawlerSDK'
```
3. From the terminal, run:
```
pod install
```

**Manual Installation**

1. [Download Car Trawler for iOS](https://github.com/cartrawler/cartrawler-ios-sdk/archive/master.zip) and extract the zip.

2. Go to your Xcode project's "General" settings. Drag `CarTrawlerSDK.framework` to the "Embedded Binaries" section. Make sure "Copy items if needed" is selected and click Finish.

3. Create a new "Run Script Phase" in your app’s target’s "Build Phases" and paste the following snippet in the script text field:

```
bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/CarTrawlerSDK.framework/strip-frameworks.sh"
bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/CTPayment.framework/strip-frameworks.sh"
```

This step is required to work around an [App Store submission bug](http://www.openradar.me/radar?id=6409498411401216) when archiving universal binaries.
