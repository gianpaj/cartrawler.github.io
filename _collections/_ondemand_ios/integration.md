---
title: Integration
permalink: /ondemand/
position: 2
right_code: >-
  ~~~ shell
    bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/CODSDK.framework/strip-frameworks.sh"

  ~~~

  {: title="Xcode bash script" }
---

CODSDK has been implemented as iOS dynamic Framework that needs to be included with the embedding application.

1. Drag `CODSDK.framework` from Finder to the `Embedded Binaries` section of your project target settings.

![Image 1](./images/1.png)

2. Add a new `Run Script Phase` to your target build phases, after the `Embed/Copy Frameworks` build phase. The script to be run should be configured as below. The CODSDK framework has been built as a Universal Framework that contains binary slices for multiple architectures, including i386/x86_64 for iOS Simulator on OS X. In order to submit the application to Apple AppStore review process, the unnecessary binary targets need to be stripped from the framework. See 
[http://www.openradar.me/radar?id=6409498411401216](http://www.openradar.me/radar?id=6409498411401216)
for more details.

![Image 2](./images/2.png)

3. Import CODSDK header files using `#import <CODSDK/CODSDK.h>` to your source files using CODSDK.