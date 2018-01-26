---
title: Integration
position: 1
type: Android
description: Supports Android 4.4 KitKat (SDK version 19) and above
right_code: >-
  ~~~ java

  //Car trawler dependencies

  implementation "com.cartrawler.android:payment-card:0.2.5"

  implementation "com.cartrawler.android:car-rental:5.0.0"


  //RX Android

  implementation 'io.reactivex:rxandroid:1.2.1'


  //Android Support

  implementation 'com.android.support:cardview-v7:26.1.0'

  implementation 'com.android.support:design:26.1.0'


  //Retrofit

  implementation 'com.squareup.retrofit2:converter-gson:2.3.0'


  //Glide

  implementation 'com.github.bumptech.glide:glide:3.8.0'


  //Room

  implementation "android.arch.persistence.room:runtime:1.0.0"

  annotationProcessor "android.arch.persistence.room:compiler:1.0.0"


  //Validator

  implementation 'commons-validator:commons-validator:1.5.1'


  maven {
      url "http://artifactory.cartrawler.com/artifactory/libs-release-local"
      credentials { username = "your_username_here" password = "your_password_here" }
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


1. Add the necessary gradle configuration to the app modules build.gradle (see Gradle tab on the right).
2. Add our maven repository and enter the artifactory credentials (see Gradle tab on the right).
3. Include activity cartrawler.core.engines.RentalActivity (see Manifest tab on the right).
4. If you are using proguard, update the proguard config as shown on the right.