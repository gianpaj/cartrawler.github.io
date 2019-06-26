---
title: Best Rate API
position: 5
type: iOS
description:
right_code: |-
  ``` swift
  
    import CarTrawlerSDK
  
    // This will trigger a new best daily rate fetch, and the subsequent delegate callbacks
    // The SDK must be initialised, and a CTAPIQueryParams object with the necessary parameters must be set before calling this method
  
    let params = CTAPIQueryParams()  
    params.delegate = self
    params.clientID = "12345"
    params.countryCode = "IE"
    params.currencyCode = "EUR"
    params.languageCode = "EN"
    params.iataCode = "DUB"
    params.pickupDate = Date(timeIntervalSinceNow: 86400) // next day
    params.dropOffDate = Date(timeIntervalSinceNow: 86400 * 3) // next day + 3 days
  
    CarTrawlerSDK.sharedInstance().requestBestDailyRate(params)
  ```
  {: title="Best Daily Rates" }

  ``` swift
  // Called when best daily rate received
  func didReceiveBestDailyRate(_ price: NSNumber, currency: String) {
  }

  // Called when best daily rate fails
  func didFailToReceiveBestDailyRate(error: Error) {
  }
  ```
  {: title="Delegate" }


---

<h5>Request Best Daily Rates</h5>

Calling the requestBestDailyRate function will trigger a best daily rate request based on the provided IATA or PickupLocationCode and pickup and dropoff dates.

The best daily rate (price and currency) will be returned in the CarTrawlerSDKDelegate function didReceiveBestDailyRate.
