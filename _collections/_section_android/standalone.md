---
title: Standalone
position: 2
type: Android
description:
right_code: >
  ~~~java
    //Standalone (Rental)
      CartrawlerSDK.Builder()
          .setRentalStandAloneClientId(clientId = "1234")
          .setAccountId(accountId = "123")
          .setCountry(twoLetterISOCountry = "IE")
           .setCurrency(currency = "EUR")
           .setEnvironment(environment = CartrawlerSDK.Environment.STAGING)
           .setFlightNumberRequired(required = true)
           .setLogging(logging = true)
           .setLoyalty(loyaltyProgramId = "LoyaltyId",membershipNumber =  "123")
           .setOrderId(orderId = "123")
           .setPassenger(ctPassenger = cartrawlerSDKPassenger)
           .setVisitorId(visitorId = "123")
           .startRentalStandalone(activity = this, requestCode = 123)
  ~~~

  {: title="Standalone" }
  
  ~~~java
   //Standalone with deeplinking (Rental) 
    CartrawlerSDK.Builder()
         .setRentalStandAloneClientId(clientId = "1234")
         .setAccountId(accountId = "123")
         .setCountry(twoLetterISOCountry = "IE")
         .setCurrency(currency = "EUR")
         .setDropOffTime(dropOffDateTime = GregorianCalendar())
         .setEnvironment(environment = CartrawlerSDK.Environment.STAGING)
         .setFlightNumberRequired(required = true)
         .setLogging(logging = true)
         .setLoyalty(loyaltyProgramId = "LoyaltyId",membershipNumber =  "123")
         .setOrderId(orderId = "123")
         .setPassenger(ctPassenger = cartrawlerSDKPassenger)
         .setPickupLocation(iataAirportCode = "YXJ")
         .setPickupLocationId(locationCode = 123)
         .setDropOffLocationId(locationCode = 123)
         .setPickupTime(pickupDateTime = GregorianCalendar())
         .setDropOffTime(dropOffDateTime = GregorianCalendar()
         .setPickupTime(pickupDateTime = GregorianCalendar())
         .setVisitorId(visitorId = "123")
         .setPinnedVehicle(refId = "123")
         .startRentalStandalone(activity = this, requestCode = 123)
         
  ~~~
  
  {: title="Deeplink" }

---

Usage of the SDK is demonstrated to the right, the parameters are as follows:

<h5>Standalone</h5>

<dl>
<dt>setClientId</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
<dt>setAccountId</dt><dd>A String value that represents the Account ID.</dd>
<dt>setCountry</dt><dd>An optional country code to used switch between languages</dd>
<dt>setCurrency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
<dt>setEnvironment</dt><dd>Switch between CarTrawlers endpoints for STAGING and PRODUCTION environments.</dd>
<dt>setFlightNumberRe...</dt><dd>A boolean key to enable Flight Number as a required field in the Payment Form.</dd>
<dt>setLogging</dt><dd>Boolean value for additional logging while debugging.</dd>
<dt>setLoyalty</dt><dd>loyaltyProgramId: A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES". membershipNumber: A String value that is used to pre-populate the loyalty field.</dd>
<dt>setOrderId</dt><dd>A String value that represents the Order ID</dd>
<dt>setPassenger</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
<dt>setVisitorId</dt><dd>A String value that represents the Visitor ID.</dd>
<dt>startRentalStandalone</dt><dd>Start Rental standalone activity.</dd></dl>

<h5>Present Standalone with Deeplinking</h5>

This is a variant on the standalone flow whereby the vehicle list is shown based on the pickup and dropoff parameters, rather than the regular initial search screen.
Optionally, if a vehicle refId is provided, this will be become the pinned item in the list.
If a user backs out of the list, it will return the user to the Cartrawler search.

- If the pickup and drop off dates are invalid, out of date, or not present the SDK will fallback to regular standalone search.
- If the vehicle refId is invalid (or out of date), the list will be shown without the vehicle being pinned.
- If the parameters are valid but no search results are returned by the CarTrawler system, the SDK will fallback to the regular standalone search.

setPinnedVehicle call is optional, as ths is on dependent on whether the vehicle is known (by Partner App), if know this becomes the pinned item in the list.

setDropOffTime, setPickupLocation (or setDropOffLocationID/setPickupLocationId), setPickupTime, are required so that the list is displayed (rather then the search).