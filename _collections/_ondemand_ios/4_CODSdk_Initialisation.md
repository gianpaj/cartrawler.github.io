---
title: CODSDK Initialization
position: 4
permalink: /ondemand/
right_code: |-
  ~~~ java
    - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
        [[CODManager sharedManager] initWithOptions:launchOptions];
        ...
    }
  ~~~
  {: title="CODSDK launch example" }
---

CODSDK must be initialised before any of the views can be opened. Call `[CODManager sharedManager]` to obtain a reference to a CODManager instance. This object is responsible of mediating actions between the views and controllers within COD application.

A typical place to initialise `CODManager` is in your application delegates init method. Parameter `launchOptions` is required to pass possible launch parameters (e.g. deep-linkin URL params) to the `CODManager`.

After the COD manager has been succesfully initialised, the `CODManager` interface can be used to open the COD as normal view object, or as a view controller.