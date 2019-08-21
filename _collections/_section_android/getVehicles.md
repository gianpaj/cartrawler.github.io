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
                       //Deprecated please use onReceiveVehicleDetails instead
                       }
                       
                       override fun onReceiveVehicleDetails(vehicleDetails: List<VehicleDetails>) {
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


A VehiclesListener is past into the getVehicleDetails method and the SDK will call the relevant methods once the relevant events have happen.

The vehicle object takes the following form:

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

