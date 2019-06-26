---
title: Inpath
position: 3
type: Androidimage = "https://ota-cars.imgix.net/otaimages/renault/clio_3dr_nologo.jpg?w=180&dpr=2",
description:
right_code: >
  
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

  {: title="Inpath" }
  

---

Usage of the SDK is demonstrated to the right, the parameters are as follows:

<h5>Inpath</h5>

<dl><dt>CartrawlerSDKPass...</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
<dt>setRentalInPathCl...</dt><dd>Your client ID, required to use the CarTrawler API.</dd>
<dt>setAccountId</dt><dd>A String value that represents the Account ID.</dd>
<dt>setCountry</dt><dd>An optional country code to used switch between languages</dd>
<dt>setCurrency</dt><dd>An optional currency code, such as "USD". Default is "EUR" if not provided.</dd>
<dt>setEnvironment</dt><dd>Switch between CarTrawlers endpoints for STAGING and PRODUCTION environments.</dd>
<dt>setFlightNumberRe...</dt><dd>A boolean key to enable Flight Number as a required field in the Payment Form.</dd>
<dt>setLogging</dt><dd>Boolean value for additional logging while debugging.</dd>
<dt>setLoyalty</dt><dd>loyaltyProgramId: A String value that represents the Loyalty Program ID , Example: "HAWAIIAN_MILES". membershipNumber: A String value that is used to pre-populate the loyalty field.</dd>
<dt>setOrderId</dt><dd>A String value that represents the Order ID</dd>
<dt>setPassenger</dt><dd>An optional Array of Passengers, the first one will be the main passenger.</dd>
<dt>setPickupLocation</dt><dd>An optional IATA code.</dd>
<dt>setPickupTime</dt><dd>Pick up date time for required service.</dd>
<dt>setVisitorId</dt><dd>A String value that represents the Visitor ID.</dd>
<dt>startRentalInPath</dt><dd>Start Rental InPath activity.</dd></dl>


<h5>Payload Retrieval from Inpath Process</h5>

If a user selected a car during the in path process, the onActivityForResult will be fired.
The Payload object is accessed via the return intent by onActivityForResult:
returnIntent.getStringExtra(CartrawlerSDK.PAYLOAD)
    
    override fun onActivityForResult(requestCode: Int, resultCode: Int, data: Intent?) {
       if (resultCode == Activity.RESULT_OK) {
           if (requestCode == 123) {
                openCreditCardProcessor(data!!.getStringExtra(CartrawlerSDK.PAYLOAD))
            }      
    }
