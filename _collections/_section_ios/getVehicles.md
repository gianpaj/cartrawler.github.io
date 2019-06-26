---
title: Vehicles API
position: 8
type: iOS
description:
right_code: |-
  ```swift
    import CarTrawlerSDK
  
    // This will trigger a new vehicles fetch, and the subsequent delegate callbacks
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
    params.numberOfVehicles = 20 // Default 0, it will return all vehicles
    params.sortType = .recommended // .recommended (Default) or .bestPrice

    CarTrawlerSDK.sharedInstance().requestVehicles(params)
  ```
    {: title="Vehicles API" }
  
  ``` swift
  // Called when best daily rate received
  func didReceiveVehicles(_ vehicles: [CTVehicleDetails]) {
  }

  // Called when best daily rate fails
  func didFailToReceiveVehicles(error: Error) {
  }
  ```
  {: title="Delegate" }


---
<h5>Request Vehicles</h5>

We expose a method to retrieve the vehicle list based on a sort type and limit you specify. 

Calling the requestVehicles function will trigger a vehicles request based on the provided IATA or PickupLocationCode, pickup and dropoff date, also we limit the list returned to a set number of vehicles you specify. 

For the sort type can be either:
- .bestPrice, which returns the cheapest cars in the list 
- .recommended, which returns the cartrawler recommended cars.

A list of vehicle objects (CTVehicleDetails) will be returned in the CarTrawlerSDKDelegate function didReceiveVehicles.
