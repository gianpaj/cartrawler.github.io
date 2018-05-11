---
title: Opening COD Views
position: 6
right_code: |-
  ~~~ java
  UIView *rootView = [manager codViewWithModuleName:@"<module name>" initialProperties:nil];

  self.window = [[UIWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
  UIViewController *rootViewController = [[UIViewController alloc] init];
  rootViewController.view = rootView;
  self.window.rootViewController = rootViewController;
  [self.window makeKeyAndVisible];
  ~~~
  {: title="Opening COD View" }
---

Alyternatively, if the hosting application wants more fina-grained control over the COD view contents, the CODSDK can be used to open CODSDK as a iOS UIKit `UIView`. In this case, the hosting application is responsible of maintaining the `CODView` object and presenting it to the user. Please note the following considerations:

1. `CODView` maintains its own navigation bar and the hosting app should hide its navigation bar to preven duplicate UI elements.
2. `CODView` has been designed to be used as full-screen UI element
3. Only one instance of `CODView`should be open at the time

An example of opening the COD View is on the right ->

The   `moduleName`   and   `initialProperties`   parameters are defined as above.