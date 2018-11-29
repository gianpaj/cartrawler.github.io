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

     //Passanger
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
    <dt>clientId</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
    <dt>production</dt><dd>A boolean to switch between test and production endpoints. Default is test.</dd>
    <dt>language</dt><dd>An optional language code to switch between languages, NOTE: this field will be removed from the interface in the future and needs to be passed in as null</dd>
    <dt>country</dt><dd>An optional country code, such as "US". Default is the device location if not provided.</dd>
    <dt>currency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
    <dt>customAttributes</dt><dd>A hash map of attributes, custom to a particular partner.</dd>
    </dl>

Custom Attributes:

<dl>
  <dt>loyaltyEnabled</dt><dd>A boolean key to enable loyalty field in the payment form</dd>
  <dt>customProgramID</dt><dd>A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES"</dd>
  <dt>flightNumberRequired</dt><dd>A String boolean value that enables or disables the flight number being required (default value is true), Example: "true"</dd>
  <dt>membershipID</dt><dd>A String value that is used to pre-populate the loyalty field</dd>
</dl>

You will need to create a theme that extends the **CTAppTheme** and set the values for the **colorPrimaryDark**, **colorPrimary** and **colorAccent** attributes. **android:statusBarColor** can also be set to update the status bar color. (see Theme tab on the right)
