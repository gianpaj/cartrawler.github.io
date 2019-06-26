---
title: Inpath Process
position: 3
type:
description:
right_code:
---

Following the inpath process a payload is returned in JSON Format, this json can later be used to make a reservation with our backend system, when its appropriate in the partner app. 
However their are placeholder fields that need to be populated prior to doing the reservation:


Payload Structure 
This is the payload structure that is passed back via call backs in our native SDK. A placeholder tag will only be present in the case that input data is not supplied for that tag. For example if the users country name code is empty/null on input, this will be replaced with the placeholder tag

Placeholder Fields
[FIRSTNAME], [SURNAME], [TELEPHONE], [EMAIL], [ADDRESSLINE1], [CITY], [POSTCODE], [COUNTRYNAMECODE]

Notes on field formats:
COUNTRYNAMECODE - address line country code

Example JSON Payload:

    {
      "@xmlns": "http://www.opentravel.org/OTA/2003/05",
      "@Version": "1.002",
      "@Target": "Production",
      "@PrimaryLangID": "EN",
      "POS": {
        "Source": {
          "@ISOCurrency": "EUR",
          "RequestorID": {
            "@Type": "16",
            "@ID": "787697",
            "@ID_Context": "CARTRAWLER"
          
        
      },
      "VehResRQCore": {
        "@Status": "All",
        "VehRentalCore": {
          "@PickUpDateTime": "2017-09-20T10:00:00",
          "@ReturnDateTime": "2017-09-25T21:00:00",
          "PickUpLocation": {
            "@CodeContext": "CARTRAWLER",
            "@LocationCode": "470"
          },
          "ReturnLocation": {
            "@CodeContext": "CARTRAWLER",
            "@LocationCode": "470"
          
        },
        "Customer": {
          "Primary": {
            "PersonName": {
              "GivenName": "[FIRSTNAME]",
              "Surname": "[SURNAME]"
            },
            "Telephone": {
              "@PhoneTechType": "1",
              "@PhoneNumber": "[TELEPHONE]"
            },
            "Email": {
              "@EmailType": "2",
              "#text": "[EMAIL]"
            },
            "Address": {
              "@Type": "2",
              "[ADDRESSLINE1]",
               "CityName": "[CITY]",
               "PostalCode": "[POSTCODE]”,
               "CountryName": {
                "@Code": "[COUNTRYNAMECODE]"
              
            },
            "CitizenCountryName": {
              "@Code": "IE"
            
          
        },
        "DriverType": {
          "@Age": "30"
        
      },
      "VehResRQInfo": {
        "@PassengerQty": "1",
        "ArrivalDetails": {
          "@TransportationCode": "14",
          "@Number": "FR",
          "OperatingCompany": "123"
        },
        "RentalPaymentPref": {
          "PaymentCard": {
            "@CardType": "1",
            "@CardCode": "[CARDCODE]",
            "@CardNumber": "[CARDNUMBER]",
            "@ExpireDate": "[EXPIREDATE]",
            "@SeriesCode": "[SERIESCODE]",
            "CardHolderName": "[CARDHOLDERNAME]"
          
        },
        "Reference": {
          "@Type": "16",
          "@ID": "419488971",
          "@ID_Context": "CARTRAWLER",
          "@DateTime": "2017-07-18T15:46:42.148+01:00",
          "@URL": "7ef64533-7ca7-4c45-ad27-c3066fd817d4.36"
        },
        "TPA_Extensions": {
          "Reference": {
            "@Type": "16",
            "@ID": "AXA.0F09I30F09I4",
            "@ID_Context": "INSURANCE",
            "@Amount": "12.12",
            "@CurrencyCode": "EUR",
            "@URL": "http://www.cartrawler.com/res/conditions/insurance/CT_AXA_TC_GB.pdf"
          },
          "Window": {
            "@engine": "Android Engine",
            "@name": "ANDROID-V1",
            "@region": "en-us",
            "@svn": "1.4.9-14"
    }
