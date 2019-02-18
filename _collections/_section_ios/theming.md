---
title: Theming
position: 3
type: iOS
description: 'Customising the CarTrawler iOS SDK'
right_code: |-
  ``` swift
  
  let style = CTStyle(
    primaryColor: UIColor.black,
    primaryLightColor: UIColor.grey,
    primaryDarkColor: UIColor.white,
    ctaColor: UIColor.red,
    ctaFontColor: UIColor.white
  )

  ```  
  {: title="CTStyle" }
---

Color principles for the CarTrawler SDK are based on the iOS Human Interface Design Guidelines. 
Theming is achieved by creating a CTStyle object and initializing the SDK with it. 

The CTStyle class has the following properties: 

primaryColor<br />
primaryLightColor (optional)<br />
primaryDarkColor (optional)<br />
ctaColor (optional)<br />
ctaFontColor (optional)

We recommend using a light and dark variant of your primary colour for the product, which is useful for creating contrast between UI elements, such as a navigation bar and secondary panel bar.

If you do not wish to set the four optional properties manually, the CarTrawler SDK will create the colours for you. 

For more information please see our <a href="https://invis.io/6ZQILRF3TW2">style guide</a>.

