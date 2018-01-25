---
title: Introduction
type: iOS
position: 1
---


Now we are ready to start using the SDK.

The simplest form of usage is initializing the standalone booking sequence. You do it by simply calling the function we provide and passing the required parameters. Here is the list of parameters that our function accepts:

clientId

client id, required to use CarTrawler API

production

switch between test and production endpoints

language

language code

country

country code, can be null

currency

currency code, can be null

customAttributes

any additional attributes, custom to particular partner

You can also customise the color scheme of our engine by setting CT\_ColorPrimary, CT\_ColorSecondary and CT\_ColorAccent values in your app's colors.xml.

CarTrawler for iOS supports iOS 8, iOS 9, iOS 10 and iOS 11.