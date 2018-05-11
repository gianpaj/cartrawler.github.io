---
title: Introduction
position: 1
---
## CarTrawler Confidential

This document is confidential and shared under a non-disclosure agreement. If you need to share the document or parts of it with external parties (such as outsourced software development companies), it is your responsibility to ensure that these parties are covered with a non-disclosure agreement and understand the confidential nature of this document.

# CODSDK Client Integration

CarTrawler On-Demand SDK ("CODSDK") is a client framework and a set of tools that enables quick and easy integration of CarTrawler on-demand taxi services ("COD") into CarTrawler Partner mobile apps.

The framework provides a native mobile app plugin with easy and intuitive functionality for the entire on-demand taxi booking user flow with the following main functions:

- Searching available taxis at user's location with ASAP pickup time
- Displaying available cars, their estimated time of arrival, and pricing
- Making bookings with credit card and Partner loyalty program membership points
- Tracking the on-going order and car arrival
- Viewing driver and car details
- Reviewing ride and payment details
- Rating the service

The client framework is distributed as a dynamic iOS Framework and Android library that Partner mobile application development teams can embed into their into their native iOS and Android apps. The framework provides complete functionality and UIs that can be invoked by the Partner embedding apps (hereinafter referred as "Partner App") as appropriate.




## Implementation Technology

The CarTrawler On-Demand client and CODSDK has been implemented as native mobile application component using Facebook's React Native technology. For more details, see [https://facebook.github.io/react-native/](https://facebook.github.io/react-native/)).

## CODSDK System Requirements

### iOS

|Area                   |Description                          |
|:----------------------|:------------------------------------|
|iOS version            |iOS 8.0 or later on iPhone           |
|Memory footprint       |~9 MB (iOS, armv64) (1)              |

1) Please note that the SDK is distributed as iOS Universal framework, containing binary code for both iOS Simulator (i386, x86_64) and iOS devices (armv7, armv7s, arm64). The unnecessary architectures are stripped out automatically when building for production, keeping the on-device memory footprint of CODSDK below 10 MB.
