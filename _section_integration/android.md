---
title: Android
position: 2
type: Android
description:
right_code: >-
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


Our engine supports all Android versions starting from 4.4 KitKat (SDK version 19).

The SDK consists of the following libraries:

* car-rental: Car rental flow
* payment-card: Secure payment form

1. Check out list of dependencies we provide (Daniel to clarify list location)
2. Add our repository (Daniel to clarify URL)
3. Add repository credentials to gradle config (Daniel to clarify which credentials)
4. Include activity (Daniel to clarify name)
5. Update the proguard config (Daniel to clarify what is updated