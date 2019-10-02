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
  
  
  ~~~java
     //CartrawlerSDKPassenger
      data class CartrawlerSDKPassenger(val firstName: String?, // First Name
                                        val lastName: String?, // Surname
                                        val email: String?,
                                        val phoneCountryCode: String?, // 3 digit phone country code
                                        val phoneNumber: String?, //  Phone number in national format
                                        val address: String?, // Address line
                                        val city: String?, // City
                                        val postcode: String?, // Post Code
                                        val country: String?, // Country ISO code, e.g. IE, FR, DE
                                        val flightNumber: String?, // Flight number
                                        var age: String?) : Parcelable { // Driver Age , "30"
           
    ~~~
    
    
    {: title="CartrawlerSDKPassenger" }

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


<h5>Reservation Retrieval from Standalone Process</h5>

If a user booked a car during the standalone process, the onActivityForResult will be fired.
The reservation object is accessed via the return intent by onActivityForResult:
returnIntent.getStringExtra(CartrawlerSDK.RESERVATION)
    
    override fun onActivityForResult(requestCode: Int, resultCode: Int, data: Intent?) {
       if (resultCode == Activity.RESULT_OK) {
           if (requestCode == 123) {
                yourMethod(data!!.getStringExtra(CartrawlerSDK.RESERVATION))
            }      
    }
    
    // The Reservation Object is defined as the following
    
    data class ReservationDetails (
       val status: String,// In this scernario it will be confirmed
       val givenName: String, // first name
       val surname: String, // Surname
       val resId: String, // Reservation ID
       val resuid: String, // resuid, use this along with the resId to retrieve the booking later
       val pickUpDateTime: GregorianCalendar, //The date & time of pickup
       val returnDateTime: GregorianCalendar,  //The date & time of pickup 
       val pickupLocation: LocationDetails, //Location details of pickup
       val returnLocation: LocationDetails, //Location details of pickup
       val insurance: Insurance, // Insurance, null if none attached
       val rentalInfo: RentalInfo, // Information on reservation costs
       val vehicle: VehicleDetails) // Information on the selected vehicle
      
        data class LocationDetails (
           val atAirport: Boolean, // Location at Airport? (boolean)
           val iataCode: String,  // IATA Code (if airport)
           val code: Int,  // Unique Location Code (code type is internal to Cartrawler)
           val name: String, // Text description of location
           val address: Address, // Postal address of location
           val phoneNumber: String // Vendor contact number
       )
    
       data class Insurance (
           val company: String, // Insurance company name
           val id: String, // Code of offered insurance product
           val cost: Double, // base cost
           val currency: String, // base currency
           val createDate: String, // date insurance was purchased
           val costCharge: Double, // Cost converted into charged currency (presented currency)
           val currencyCharge: String, // the presented currency to the customer
           val companyLogo: String, // a link to the company logo
           val companyPolicyURL: String, // a link to the policy terms and conditions
           val text: String, // A marketing description of the insurance (markup)
       )
    
       data class RentalInfo (
           val cost: Double, // base cost
           val currency: String, // base currency
           val customerCost: Double, // /cost in the currency of the customer
           val customerCurrency: String // the presented currency to the customer
       )
    
       data class Address (
           val addressLine: String, // Post adddress of location
           val countryNameCode: String // 2 letter country code.
       )
       
       @Parcelize
       data class VehicleDetails(
           //OTA
            val referenceId: String,
            val name: String,
            val orSimilar: String,
            val code: String,
            val vehicleAssetNumber: String,
            val pictureURL: String,
            val passengerQuantity: Int,
            val doorCount: Int?,
            val baggageQuantity: Int
            val fuelType: String,
            val driveType: Stringl,
            val airConditionInd: Boolean,
            val transmissionType: String,
            val size: String,
       
            //Supplier
            val supplier: String,
            val supplierRating: Double,
            val supplierImageURL: String,
       
            //Widget localization values
            val passengersText: String,
            val baggageText: String?,
            val doorsCountText: String,
            val transmissionText: String,
            val categoryText: String,
            val sizeText: String
       
            //Price
            val price: Double,
            val pricePerDay: Double,
            val currencyCode: String
       ) : Parcelable
    }
    
    
<h5>Present Standalone with Deeplinking</h5>

This is a variant on the standalone flow whereby the vehicle list is shown based on the pickup and dropoff parameters, rather than the regular initial search screen.
Optionally, if a vehicle refId is provided, this will be become the pinned item in the list.
If a user backs out of the list, it will return the user to the Cartrawler search.

- If the pickup and drop off dates are invalid, out of date, or not present the SDK will fallback to regular standalone search.
- If the vehicle refId is invalid (or out of date), the list will be shown without the vehicle being pinned.
- If the parameters are valid but no search results are returned by the CarTrawler system, the SDK will fallback to the regular standalone search.

setPinnedVehicle call is optional, as ths is on dependent on whether the vehicle is known (by Partner App), if know this becomes the pinned item in the list.

setDropOffTime, setPickupLocation (or setDropOffLocationID/setPickupLocationId), setPickupTime, are required so that the list is displayed (rather then the search).