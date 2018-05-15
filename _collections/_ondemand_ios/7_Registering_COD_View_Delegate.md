---
title: COD View Delegate
position: 7
permalink: /ondemand/
---

In order to receive events (callbacks) from the COD view, the hosting application may register itself as a delegate for the `CODManager`. The currently supported callbacks are:

1. `didLoadCODView` called after the COD view or view controller has been loaded sucesfully.
2. `didFailToLoadCODView` called if there was an unrecoverable error during the COD view or view controller loading
3. `shouldCloseCODViewWithReason:(CODViewCloseReason)reason` called when the COD view or view controller needs to be closed (typically as a response to an user interaction)

See `CODSDK/CODManagerDelegate.h` for more details.

