---
title: Integration
position: 2
type: Android
description:
right_code: >
  ~~~ java

  compile "com.rakuten.android:dc-storm:1.0.0@aar"

  compile "com.cartrawler.android:payment-card:0.2.5"

  compile "com.cartrawler.android:car-rental:1.4.9"


  maven {
      url "http://artifactory.cartrawler.com/artifactory/libs-release-local"
      credentials { username = "" password = "" }
  }

  ~~~

  {: title="Gradle" }


  ~~~ java

  -dontwarn sun.misc.**


  -keepclassmembers class rx.internal.util.unsafe.*ArrayQueue*Field* {
      long producerIndex;
      long consumerIndex;
  }


  -keepclassmembers class rx.internal.util.unsafe.BaseLinkedQueueProducerNodeRef
  {
      rx.internal.util.atomic.LinkedQueueNode producerNode;
  }


  -keepclassmembers class rx.internal.util.unsafe.BaseLinkedQueueConsumerNodeRef
  {
      rx.internal.util.atomic.LinkedQueueNode consumerNode;
  }


  -dontnote rx.internal.util.PlatformDependent

  ~~~

  {: title="Proguard" }


  ~~~ xml

  <activity android:name="cartrawler.core.engines.RentalActivity"
  android:theme="@style/CartrawlerAppTheme" />

  ~~~

  {: title="Manifest" }
---


Our engine supports all Android versions starting from 4.4 KitKat (sdk version 19). For the partners we are providing following libraries:

car-rental – Android library containing our engine

payment-card - separate Android library, which provides logic and interface for native card payments to CarTrawler API. It’s hosted and included separately for PCI compliance reasons.

In order to integrate and start using our libraries, first make sure the Android SDK versions are matching. Currently we support following versions:

<dl><dt>minSdkVersion</dt><dd>19</dd><dt>targetSdkVersion</dt><dd>25</dd></dl>

Then check out list of dependencies we provide, and don’t forget to add our repository and its credentials to your gradle config.

Finally include our activity into you app's manifest and update the proguard config accordinly.