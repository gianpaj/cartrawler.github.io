---
title: Best Daily Rate
position: 4
type: iOS
description:
right_code: |-
  ``` swift
  
    import CarTrawlerSDK
  
    // This will trigger a new best daily rate fetch, and the subsequent delegate callbacks
    // The SDK must be initialised, and a CTBestDailyRateParams object with the necessary parameters must be set before calling this method
  
    let params = CTBestDailyRateParams()
  
    params.delegate = self
    params.clientID = "12345"
    params.countryCode = "IE"
    params.currencyCode = "EUR"
    params.languageCode = "EN"
    params.iataCode = "DUB"
    params.pickupDate = Date(timeIntervalSinceNow: 2629746) // next month
    params.dropOffDate = Date(timeIntervalSinceNow: 2888946) // next month + 3 days
  
    CarTrawlerSDK.sharedInstance().requestBestDailyRate(params)
  
    ```
  
    {: title="Best Daily Rates" }
    ``` swift
  
     ```


---


<h5>Request Best Daily Rates</h5>

The best daily rates API has been exposed independently of the CarTrawler SDK workflows (Inpath & Standalone). This will return the best recommended rate for an individual vehicle at a specific location.

After initializing the SDK, please create a CTBestDailyRateParams object and initialize it with the following parameters:
<dl>
<dt>delegate</dt>
<dd>a delegate for receiving the best daily rate response</dd>
<dt>ClientID</dt>
<dd>Your client ID, required to use the CarTrawler API.</dd>
<dt>countryCode</dt>
<dd>A country code, such as "US". Default is the device location if not provided.</dd>
<dt>currencyCode</dt>
<dd>A currency code, such as "USD". Default is "EUR" if not provided</dd>
<dt>languageCode</dt>
<dd>A language code. Default is "EN" if not provided.</dd>
<dt>pickupDate</dt>
<dd>A required Pickup Date.</dd>
<dt>dropOffDate</dt>
<dd>A required Drop-off Date.</dd>
<dt>IATACode </dt>
<dd>An optional IATA code for pickup location.</dd>
<dt>pickupLocationID</dt>
<dd>An optional OTA Location ID for pickup location.</dd>
<dt>dropOffLocationID</dt>
<dd>An optional OTA Location ID for drop off location.</dd>
<dt>passengers</dt>
<dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
</dl>

Calling the requestBestDailyRate function will trigger a best daily rate request based on the provided IATA or PickupLocationCode and pickup and dropoff dates.

The best daily rate (price and currency) will be returned in the CarTrawlerSDKDelegate function didReceiveBestDailyRate.
