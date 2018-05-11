---
title: Additional Properties
position: 7
---

Additional properties may be specified when opening CODSDK views. The properties may be related to communicating user profile details from the embedding application to the CODSDK, or they may be related to providing contextual information for the taxi booking flow, e.g. destination address/airport if known.

The following properties are supported. All properties are optional:

|Property name               |Type           |Mandatory|Description                                       |
|:---------------------------|:--------------|:-------:|:-------------------------------------------------|
|user                        |NSDictionary   |No (1)   |User details                                      |
|user.firstName              |NSString       |Yes      |First name                                        |
|user.lastName               |NSString       |Yes      |Last name                                         |
|user.email                  |NSString       |No       |email                                             |
|user.phone                  |NSString       |Yes      |phone                                             |
|user.phoneVerified          |BOOL           |No       |true if phone number has been verified            |
|membership                  |NSDictionary   |No (2)   |User loyalty program membership details           |
|membership.userId           |NSString       |Yes (3)  |Loyalty program user id                           |
|membership.password         |NSString       |Yes (3)  |Loyalty program password                          |
|membership.authToken        |NSString       |Yes (3)  |Loyalty program auth token                        |
|payment                     |NSDictionary   |No       |Payment details                                   |
|paymentToken                |NSString       |No       |Payment token to be used in CC payments           |
|booking                     |NSDictionary   |No       |Booking details                                   |
|booking.destinationAddress  |NSString       |No       |Destination address                               |
|booking.destinationIATA     |NSString       |No       |IATA of the destination airport                   |

(1) If specified, user on-boarding screens/process will be omitted and a user profile is automatically created for the user.

(2) If specified, no loyalty program authentiation screen is displayed.

(3) Either userId and password or authToken is required.
