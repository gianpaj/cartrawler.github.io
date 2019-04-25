---
title: Theming
position: 3
type: iOS
description: 'Customising the CarTrawler iOS SDK'
right_code: |-
  ``` swift

  let style = CTStyle(theme: .dark,  // .dark or .light
             primaryColor: UIColor.gray)
  style.primaryLightColor = UIColor.lightGray // Optional, default light generated based on primary color
  style.primaryDarkColor = UIColor.darkGray // Optional, default dark generated based on primary color
  style.ctaColor = UIColor.blue // Optional, default iOS blue RGB(0,122,255)
  style.ctaFontColor = UIColor.white  // Optional, default white or dark based on theme
  style.secondaryCtaColor = UIColor.black // Optional, default primary color
  style.secondaryCtaFontColor = UIColor.white // Optional, default white or dark based on theme

  ```  
  {: title="CTStyle" }
---

Color principles for the CarTrawler SDK are based on the iOS Human Interface Design Guidelines.
Theming is achieved by creating a CTStyle object and initializing the SDK with it.

The CTStyle class has the following properties:

theme<br />
primaryColor<br />
primaryLightColor (optional)<br />
primaryDarkColor (optional)<br />
ctaColor (optional)<br />
ctaFontColor (optional)<br />
secondaryCtaColor (optional)<br />
secondaryCtaFontColor (optional)

We recommend using a light and dark variant of your primary colour for the product, which is useful for creating contrast between UI elements, such as a navigation bar and secondary panel bar.

If you do not wish to set the four optional properties manually, the CarTrawler SDK will create the colours for you.

For more information please see our <a href="pickupAirportIATACode">style guide</a>.
