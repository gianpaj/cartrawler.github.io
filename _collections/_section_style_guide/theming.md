---
title: Usage
position: 2
type: 
description: 'Customising the CarTrawler SDK'
right_code: |-
  ```swift

  let style = CTStyle(theme: .dark,  // .dark or .light
             primaryColor: UIColor.gray)
   style.primaryLightColor = UIColor.lightGray // Optional, default light generated based on primary color
   style.primaryDarkColor = UIColor.darkGray // Optional, default dark generated based on primary color
   style.ctaColor = UIColor.blue // Optional, default iOS blue RGB(0,122,255)
   style.ctaFontColor = UIColor.white  // Optional, default white or dark based on theme
   style.secondaryCtaColor = UIColor.black // Optional, default primary color
   style.secondaryCtaFontColor = UIColor.white // Optional, default white or dark based on theme

  ```  
  {: title="iOS" }
  
  ~~~java
  
  //SDK versions below 8.0 & 8.1: Ceate a theme that extends the CTAppTheme and implement the colorPrimaryDark,              colorPrimary and colorAccent attributes.  See example below:
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
  {: title="Android" }
   
---  
Theming is achieved by creating the CTStyle (iOS) and CTAppTheme (Android) objects and initialising the SDK with it.

The style objects have the following properties:

theme
<br>primaryColor
<br>primaryLightColor (optional)
<br>primaryDarkColor (optional)<br>ctaColor (optional)
<br>ctaFontColor (optional)
<br>secondaryCtaColor (optional)
<br>secondaryCtaFontColor (optional)

By Default, the colour for text and icons on colour backgrounds are white for native SDK. If your brand colours are a bright colour (high luminosity), it's recommended you change to a dark text theme for legibility of text and colours.
<picture>
  <source media="(max-width: 799px)" srcset="/uploads/theming-example.png">
  <source media="(min-width: 800px)" srcset="/uploads/theming-example.png">
  <img src="/uploads/theming-example.png">
</picture>

If you do not wish to set the four optional properties manually, the CarTrawler SDK will create the colours for you (Note: this is currently only an iOS feature within the SDK)
