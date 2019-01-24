---
title: Prerequisites
position: 2
---


Please ensure that you have received the following from a CarTrawler representative.
{: .present-before-paste}

* A Client ID
* CarTrawler Repository Credentials
* Artifactory Crendentials (Android)
* Dedicated Slack channel for support while integrating SDK into native application

**Definitions:**
* A car rental product, comprises of the physical car rental itself, and optional add on product line items, to include insurance and car extras.
* A Flow is a set of Cartrawler UI Screens, with a specific business objective.
* Currently there are two business flows (implemented in SDK):  Standalone, Inpath Rental.
* It should be noted that the Inpath Rental solution requires **additional backend development effort** and orginazation between CarTrawler and Partners.

**Workflows**
* Standalone - Allows the customer to reserve a car rental product independently from the flight.
* Standalone deeplink - Variant on the standalone flow whereby customer is presented with the vehicle list based on the pickup and dropoff parameters passed to the SDK, rather than the regular initial search screen.
* Inpath Rental - Allows a customer to reserve a car rental product to accompany their flight, this product forms part of the customer’s  flight itenary. 
