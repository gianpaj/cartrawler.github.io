---
title: Project configuration
position: 3
---

Make sure the following application settings have been applied in your project:

1. Info.plist includes the following configuration items:

|Item                             |Value                              |Description                              |
|:--------------------------------|:----------------------------------|:----------------------------------------|
|Supported interface orientations |Portrait                           |CODSDK supports portait only             |
|NSLocationWhenInUseUsageDescription|Determine user location          |Use of location service                  |
|NSAllowsArbitraryLoads           |YES                                |Allow use of HTTP requests (test only)   |
|LSApplicationQueriesSchemes      |comgooglemaps, careem              |For "view destination" feature, for careem deep link support|
|CODBuildEnvironment              |Demo                               |Use COD demo/test environment            |

2. In your application seetings "Capabilities", turn on support for "Maps"

![Image 3](./images/3.png)