---
title: Vehicles API
position: 7
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
           .setPassenger(ctPassenger = ctPassenger)
           .setPickupLocation(iataAirportCode = "YXJ")
           .setPickupTime(pickupDateTime = GregorianCalendar())
   
   
           .getVehicles(
                   context = this,
                   numberOfVehicles = 1..X,
                   sortType = CartrawlerSDK.Builder.FLAG_BEST_PRICE or CartrawlerSDK.Builder.FLAG_RECOMMENDED,
                   vehiclesListener = object : CartrawlerSDK.VehiclesListener{
                       override fun onReceiveVehicles(vehicles: List<Vehicle>) {
                       }
   
                       override fun onError(type: Int, connectionError: CartrawlerSDK.ConnectionError) {
                       }
   
                       override fun onNoResults(type: Int) {
                       }


  ~~~

  {: title="Vehicles APIs" }

---

We expose a method on the builder to retrieve the vehicle list based on a sort type you specify. We limit the list returned to a set number of vehicles you specify. For the sort type can be either 
- FLAG_BEST_PRICE, which returns the cheapest cars in the list or FLAG_RECOMMENDED, which returns the cartrawler recommended cars.


A VehiclesListener is past into the getVehicles method and the SDK will call the relevant methods once the relevant events have happen.

The vehicle object takes the following form:

    package cartrawler.core.ui.views.partner

    @Parcelize
    data class Vehicle @JvmOverloads constructor(
            val logo: String, // Logo name of supplier
            val model: String, // Model of car
            val image: String, // URL to image of car
            val seats: String, // Number of Seats localized format
            val bags: String, // Number of Bags localized format
            val doors: String, // Number of Doors localized format
            val transmission: String, // Type of transmission
            val isAircon: Boolean, // Has it got aircon
            val price: Double, // price
            val pricePerDay: Double = price, // price per Day
            val currencyCode: String, // currencyCode of price
            val category: String? = null, // category of car
            val supplier: String? = null, // supplier of car
            val supplierRating: String? =null,  // supplier rating
            val supplierImageURL:String? = null // Image of the supplier URL
        ): Parcelable

