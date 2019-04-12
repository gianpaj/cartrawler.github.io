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
  ~~~

  {: title="Rental (Standalone deeplink)" }
  
  ~~~java      

     //Standalone with deeplinking to Vehicle list
         try {
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
                     .setPickupLocation(iataAirportCode = "YXJ")
                     .setPickupLocationId(locationId = 1234)
                     .setDroppOffLocationId(locationId = 1234)
                     .setDropOffTime(dropOffDateTime = GregorianCalendar())
                     .setPickupTime(pickupDateTime = GregorianCalendar())
                     .setPinnedVehicle(refId = "123")
                     .startRentalStandalone(activity = this, requestCode = 123)
            } catch (cartrawlerSDKIncorrectArgument: CartrawlerSDK.IncorrectArgument) {
              cartrawlerSDKIncorrectArgument.printStackTrace()
            }
  ~~~

  {: title="Rental (InPath)" }

  ~~~xml
        
     //SDK versions below 8.0 & 8.1: Ceate a theme that extends the CTAppTheme and implement the colorPrimaryDark,         colorPrimary and colorAccent attributes.  See example below:
  <style name="YourThemeExtendingCTAppTheme" parent="CTAppTheme">
    <item name="colorPrimary">#039be5</item>
    <item name="CTPrimaryColor">#039be5</item>
    <item name="colorPrimaryDark">#FF01579B</item>
    <item name="CTSecondaryColor">#FF01579B</item>
    <item name="colorAccent">#FF2E7D32</item>
    <item name="CTAccentColor">#FF2E7D32</item>
    <item name="CTPrimaryLightColor">#4BA4B5</item>
  </style>

//Theming Changes: SDK version 8.0
//CTSecondaryColor and CTAAccentColor have changed names, to CTPrimaryDarkColor and CTCTAColor and we strongly recommend partners to move to new color naming convenions (defaults color will be applied otherwise). We have introduced additional theming attributes.
  
  <style name="YourThemeExtendingCTAppTheme" parent="CTAppTheme">
    <item name="colorPrimary">@color/MainBlue</item>
    <item name="colorPrimaryDark">@color/DarkBlue</item>
    <item name="colorAccent">@color/MainYellow</item>
    <item name="CTPrimaryColor">@color/MainBlue</item>
    <item name="CTPrimaryDarkColor">@color/DarkBlue</item>// Was CTSecondaryColor
    <item name="CTPrimaryLightColor">@color/BrightBlue</item>
    <item name="CTCTAColor">@color/MainYellow</item> // Was CTAccentColor (default: colorAccent)
    <item name="CTCTATextColor">@color/DarkBlue</item> // New color (default: white)
    <item name="CTSecondaryActionColor">@color/MainYellow</item> //Optional Colours
    <item name="CTSecondaryActionTextColor">@color/DarkBlue</item> //Optional Colours
  </style>

//If the old color names are used the following overrides will apply and CTSeconary/CTAccentColor will be ignored:
    <item name="CTPrimaryDarkColor">@color/secondaryColor</item>
    <item name="CTCTAColor">@color/accentColor</item>
    <item name="CTToolbarTintColor">@android:color/white</item>
    <item name="CTCTATextColor">@color/General_White</item>
  
//Theming Changes: SDK version 8.3
//We have now introduced a new parent Theme, CTLightTheme, the attriburtes are the same, but the text color gets inverted accordingly, due to the light theme being used.

  <style name="YourThemeExtendingCTLightTheme" parent="CTLightTheme">
    <item name="colorPrimary">@color/General_White</item>
    <item name="colorPrimaryDark">@color/General_White</item>
    <item name="colorAccent">#EC028E</item>
    <item name="CTPrimaryColor">@color/General_White</item>
    <item name="CTPrimaryDarkColor">@color/General_White</item>
    <item name="CTPrimaryLightColor">#1B90EA</item>
    <item name="CTCTAColor">#EC028E</item>
    <item name="CTCTATextColor">@color/General_White</item>
    <item name="CTSecondaryActionColor">#EC028E</item>
    <item name="CTSecondaryActionTextColor">@color/General_White</item>
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
    <dt>setPassenger</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
    <dt>setVisitorId</dt><dd>A String value that represents the Visitor ID.</dd>
    <dt>startRentalStandalone</dt><dd>Start Rental standalone activity.</dd>
    </dl>
    
Rental (Standalone with Deeplinking) 

This is a variant on the standalone flow whereby the vehicle list is shown based on the pickup and dropoff parameters, rather then the regular initial search screen. 
Optionally, if a vehicle refId is provided, this will be become the pinned item in the list. 
If a user backs out of the list, it will return the user to the Cartrawler search.

- If the pickup and drop off dates are invalid, out of date, or not present the SDK will fallback to regular standalone search.
- If the vehicle refId is invalid (or out of date), the list will be shown without the vehicle being pinned.
- If the parameters are valid but no search results are returned by the CarTrawler system, the SDK will fallback to the regular standalone search.

  <dl>
      <dt>setRentalStandAloneClientId</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
      <dt>setAccountId</dt><dd>A String value that represents the Account ID.</dd>
      <dt>setCountry</dt><dd>An optional country code to used switch between languages </dd>
      <dt>setCurrency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
      <dt>setEnvironment</dt><dd>Switch between CarTrawlers endpoints for STAGING and PRODUCTION environments.</dd>
      <dt>setFlightNumberRequired</dt><dd>A boolean key to enable Flight Number as a required field in the Payment Form.</dd>
      <dt>setLogging</dt><dd>Boolean value for additional logging while debugging.</dd>
      <dt>setLoyalty</dt><dd>loyaltyProgramId: A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES". membershipNumber: A String value that is used to pre-populate the loyalty field.</dd>
      <dt>setOrderId</dt><dd>A String value that represents the Order ID</dd>
      <dt>setPassenger</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
      <dt>setVisitorId</dt><dd>A String value that represents the Visitor ID.</dd>
      <dt>setPickupLocation</dt><dd>An optional IATA code.</dd>
      <dt>setPickupLocationId</dt><dd>A required OTA Location ID for pickup location.</dd>
      <dt>setDropOffLocationId</dt><dd>A required OTA Location ID for dropoff location.</dd>
      <dt>setPickupTime</dt><dd>Pick up date time for required service.</dd>
      <dt>setPinnedVehicle</dt><dd>An optional refId to highlight pinned vehicle to top of list. Returned by the abandonment deeplink.</dd>
      <dt>startRentalStandalone</dt><dd>Start Rental standalone activity.</dd>
      </dl>

Rental (InPath):

<dl>
    <dt>CartrawlerSDKPassenger	</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
    <dt>setRentalInPathClientId	</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
    <dt>setAccountId</dt><dd>A String value that represents the Account ID.</dd>
    <dt>setCountry</dt><dd>An optional country code to used switch between languages </dd>
    <dt>setCurrency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
    <dt>setEnvironment</dt><dd>Switch between CarTrawlers endpoints for STAGING and PRODUCTION environments.</dd>
    <dt>setFlightNumberRequired</dt><dd>A boolean key to enable Flight Number as a required field in the Payment Form.</dd>
    <dt>setLogging</dt><dd>Boolean value for additional logging while debugging.</dd>
    <dt>setLoyalty</dt><dd>loyaltyProgramId: A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES". membershipNumber: A String value that is used to pre-populate the loyalty field.</dd>
    <dt>setOrderId</dt><dd>A String value that represents the Order ID</dd>
    <dt>setPassenger</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
    <dt>setPickupLocation</dt><dd>An optional IATA code.</dd>
    <dt>setPickupTime</dt><dd>Pick up date time for required service.</dd>
    <dt>setVisitorId</dt><dd>A String value that represents the Visitor ID.</dd>
    <dt>startRentalInPath</dt><dd>Start Rental InPath activity.</dd>
    </dl>

You will need to create a theme that extends the **CTAppTheme** and set the values for the **colorPrimaryDark**, **colorPrimary** and **colorAccent** attributes. **android:statusBarColor** can also be set to update the status bar color. (see Theme tab on the right)
