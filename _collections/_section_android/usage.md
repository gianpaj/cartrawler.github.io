---
title: Usage
position: 3
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

  {: title="Usage" }

  ~~~java      

     //Passenger
            new CartrawlerSDKPassenger(
              "firstname",
                             "lastName",
                             "email",
                             "phoneCountryCode",
                             "phoneNumber",
                             "Address",
                             "City",
                             "Postcode",
                             "Country",
                             "Flight Number",
                             "Age");

     //InPath
         try {
           CartrawlerSDK.Builder()
                     .setRentalInPathClientId(clientId = "1234")
                     .setAccountId(accountId = "123")
                     .setCountry(twoLetterISOCountry = "IE")
                     .setCurrency(currency = "EUR")
                     .setDropOffTime(dropOffDateTime = GregorianCalendar())
                     .setEnvironment(environment = CartrawlerSDK.Environment.STAGING)
                     .setFlightNumberRequired(required = true)
                     .setLogging(logging = true)
                     .setLoyalty(loyaltyProgramId = "LoyaltyId", membershipNumber = "123")
                     .setOrderId(orderId = "123")
                     .setPassenger(ctPassenger = cartrawlerSDKPassenger)
                     .setPickupLocation(iataAirportCode = "YXJ")
                     .setPickupTime(pickupDateTime = GregorianCalendar())
                     .setVisitorId(visitorId = "123")
                     .startRentalInPath(activity = this, requestCode = 123)
            } catch (cartrawlerSDKIncorrectArgument: CartrawlerSDK.IncorrectArgument) {
              cartrawlerSDKIncorrectArgument.printStackTrace()
            }
  ~~~

  {: title="Rental (InPath)" }

  ~~~java
              
         //InPath
             CartrawlerSDK.Builder()
                    .setGroundTransferInPathClientId(clientId = "1234")
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
                    .setPickupTime(pickupDateTime = GregorianCalendar())
                    .setVisitorId(visitorId = "123")
                    .startGroundTransferInPath(activity = this, requestCode = 123)
  ~~~    

  {: title="Ground Transfer (InPath)" }

  ~~~xml
        
    //Create a theme that extends the CTAppTheme and implement the colorPrimaryDark, colorPrimary and colorAccent attributes.  See example below:
        
      <style name="YourThemeExtendingCTAppTheme" parent="CTAppTheme">
            <item name="colorPrimary">#039be5</item>
            <item name="CTPrimaryColor">#039be5</item>
            <item name="colorPrimaryDark">#FF01579B</item>
            <item name="CTSecondaryColor">#FF01579B</item>
            <item name="colorAccent">#FF2E7D32</item>
            <item name="CTAccentColor">#FF2E7D32</item>
      </style>
  ~~~

  {: title="Theme" }
---

Usage of the SDK is&nbsp;demonstrated to the right, the parameters are as follows:

<dl>
Rental (Standalone)
</dl>

<dl>
    <dt>setRentalStandAloneClientId	</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
    <dt>setAccountId</dt><dd>A String value that represents the Account ID.</dd>
    <dt>setCountry</dt><dd>An optional country code to used switch between languages </dd>
    <dt>setCurrency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
    <dt>setEnvironment</dt><dd>Switch between CarTrawlers endpoints for STAGING and PRODUCTION environments.</dd>
    <dt>setFlightNumberRequired</dt><dd>A boolean key to enable Flight Number as a required field in the Payment Form.</dd>
    <dt>setLogging</dt><dd>Boolean value for additional logging while debugging.</dd>
    <dt>setLoyalty</dt><dd>loyaltyProgramId: A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES". membershipNumber: A String value that is used to pre-populate the loyalty field.</dd>
    <dt>setOrderId</dt><dd>A String value that represents the Order ID</dd>
    <dt>setPassenger</dt><dd>An optional Array of Passengers , the first one will be the main passenger.</dd>
    <dt>setVisitorId</dt><dd>A String value that represents the Visitor ID.</dd>
    <dt>startRentalStandalone</dt><dd>Start Rental standalone activity.</dd>
    </dl>

Rental (InPath):

<dl>
    <dt>CartrawlerSDKPassenger	</dt><dd>An optional Array of Passengers , the first one will be the main passenger.</dd>
    <dt>setRentalInPathClientId	</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
    <dt>setAccountId</dt><dd>A String value that represents the Account ID.</dd>
    <dt>setCountry</dt><dd>An optional country code to used switch between languages </dd>
    <dt>setCurrency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
    <dt>setEnvironment</dt><dd>Switch between CarTrawlers endpoints for STAGING and PRODUCTION environments.</dd>
    <dt>setFlightNumberRequired</dt><dd>A boolean key to enable Flight Number as a required field in the Payment Form.</dd>
    <dt>setLogging</dt><dd>Boolean value for additional logging while debugging.</dd>
    <dt>setLoyalty</dt><dd>loyaltyProgramId: A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES". membershipNumber: A String value that is used to pre-populate the loyalty field.</dd>
    <dt>setOrderId</dt><dd>A String value that represents the Order ID</dd>
    <dt>setPassenger</dt><dd>An optional Array of Passengers , the first one will be the main passenger.</dd>
    <dt>setPickupLocation</dt><dd>An optional IATA code.</dd>
    <dt>setPickupTime</dt><dd>Pick up date time for required service.</dd>
    <dt>setVisitorId</dt><dd>A String value that represents the Visitor ID.</dd>
    <dt>startRentalInPath</dt><dd>Start Rental InPath activity.</dd>
    </dl>
    
Ground Transfer (InPath):

<dl>
    <dt>setGroundTransferInPathClientId</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
    <dt>setAccountId</dt><dd>A String value that represents the Account ID.</dd>
    <dt>setCountry</dt><dd>An optional country code to used switch between languages </dd>
    <dt>setCurrency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
    <dt>setDropOffTime</dt><dd>Drop off date time for required service.</dd>
    <dt>setEnvironment</dt><dd>Switch between CarTrawlers endpoints for STAGING and PRODUCTION environments.</dd>
    <dt>setFlightNumberRequired</dt><dd>A boolean key to enable Flight Number as a required field in the Payment Form.</dd>
    <dt>setLogging</dt><dd>Boolean value for additional logging while debugging.</dd>
    <dt>setLoyalty</dt><dd>loyaltyProgramId: A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES". membershipNumber: A String value that is used to pre-populate the loyalty field.</dd>
    <dt>setOrderId</dt><dd>A String value that represents the Order ID</dd>
    <dt>setPassenger</dt><dd>An optional Array of Passengers , the first one will be the main passenger.</dd>
    <dt>setPickupLocation</dt><dd>An optional IATA code.</dd>
    <dt>setPickupTime</dt><dd>Pick up date time for required service.</dd>
    <dt>setVisitorId</dt><dd>A String value that represents the Visitor ID.</dd>
    <dt>startGroundTransferInPath</dt><dd>Start Ground Transfer InPath activity.</dd>
    </dl>

You will need to create a theme that extends the **CTAppTheme** and set the values for the **colorPrimaryDark**, **colorPrimary** and **colorAccent** attributes. **android:statusBarColor** can also be set to update the status bar color. (see Theme tab on the right)
