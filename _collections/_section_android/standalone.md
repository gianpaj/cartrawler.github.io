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
