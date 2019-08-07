---
title: Best Rates API
position: 6
type: Android
description:
right_code: >
  ~~~java      

   CartrawlerSDK.Builder()
     .setRentalInPathClientId(clientId = "1234")
     .setAccountId(accountId = "123")
     .setCountry(twoLetterISOCountry = "IE")
     .setCurrency(currency = "EUR")
     .setDropOffTime(dropOffDateTime = GregorianCalendar())
     .setEnvironment(environment = CartrawlerSDK.Environment.STAGING)
     .setFlightNumberRequired(required = true)
     .setLogging(logging = true)
     .setLoyalty(loyaltyProgramId = "LoyaltyId",membershipNumber =  "123")
     .setOrderId(orderId = "123")
        .setVisitorId(visitorId = "123")
           .setPassenger(ctPassenger = cartrawlerSDKPassenger)
           .setPickupLocation(iataAirportCode = "YXJ")
           .setPickupTime(pickupDateTime = GregorianCalendar())
           .getBestDailyRates(
              context = this,
              typeFlag = CartrawlerSDK.Builder.FLAG_RENTAL, // Set for now, future use
              bestDailyRatesListener = object : CartrawlerSDK.BestDailyRatesListener{
                 override fun onReceiveBestDailyRate(type: Int, price: Double, currency: String) {
                                              }
     
                        override fun onError(type: Int, connectionError: CartrawlerSDK.ConnectionError) {
                                               }
     
                        override fun onNoResults(type: Int) {
                                               }
     
                    })

  ~~~

  {: title="Best Rates API" }

---

We expose a method on the builder to retrieve the best rate for the products used.  

A BestDailyRatesListener is past into the getBestDailyRates method and will call the relevant methods once the relevant events have happen. 
 
A flag parameter is used to specify which products are required.
