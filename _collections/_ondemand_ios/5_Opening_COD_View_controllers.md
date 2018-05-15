---
title: COD View Controllers
position: 5
permalink: /ondemand/
right_code: |-
  ~~~ java
    CODManager *manager = [CODManager sharedManager];
    [manager initWithOptions:launchOptions];

    // Instantiate COD view controller
    CODViewController* viewController = [manager codViewControllerWithModuleName:@"<module name>" initialProperties:nil];

    // Hide the current navigation bar
    self.navigationController.navigationBar.hidden = YES;

    // Display the COD view controller
    [self.navigationController pushViewController:viewController animated:YES];
  ~~~
  {: title="Opeing CODView Controllers" }
---

`CODVIewController` is a iOS UIKIt `UIViewController` subclass that can be used to create a complete view controller to manage the lifecycle of the booking UI. The view controllers can be embedded into a navigation view controller, but if done so, the embedding view should hide its navigation bar as CODSDK booking view maintains its own navigation bar.

The first parameter `moduleName` shall be used to indicate the main entry point for CODSDK. This value is assigned to you by CarTrawler.

The second parameter `initialProperties` is a `NSDictionary` containing any additional properties to be passed to the CODSDK. See "Additional Properties" below.
