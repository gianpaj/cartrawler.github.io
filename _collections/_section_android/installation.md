---
title: Installation
position: 1
type: Android
description: Supports Android 4.4 KitKat (SDK version 19) and above
right_code: >-
  ~~~ java
  
     //Java 8 Support
       android {
          compileOptions {
              sourceCompatibility 1.8
              targetCompatibility 1.8
          }
       }
    
       //Car trawler dependencies
    
       implementation "com.cartrawler.android:payment-card:0.2.5"
    
       implementation "com.cartrawler.android:car-rental:+" //please use the version number sent to you by the CT team
    
    
       //Google support
       implementation 'com.android.support:design:27.1.1'
       implementation 'com.android.support:cardview-v7:27.1.1'
    
       //RX Android
       implementation 'io.reactivex:rxandroid:1.2.1'
    
       //Gson
       implementation 'com.google.code.gson:gson:2.8.1'
    
       //Retrofit & OkHttp
       implementation 'com.squareup.retrofit2:retrofit:2.3.0'
       implementation 'com.squareup.okhttp3:logging-interceptor:3.8.1'
       implementation 'com.squareup.retrofit2:converter-gson:2.3.0'
       implementation 'com.squareup.retrofit2:adapter-rxjava:2.6.0'
    
       //Glide   
       implementation 'com.github.bumptech.glide:glide:4.8.0'
    
       //Constraint layout
       implementation 'com.android.support.constraint:constraint-layout:1.1.2'
    
       //Dagger
       implementation 'com.google.dagger:dagger:2.11'
    
       //Android Jetpack
       implementation "android.arch.lifecycle:livedata:1.1.1"
       implementation 'android.arch.persistence.room:runtime:1.1.1'
    
       repositories {
          maven {
              url "http://artifactory.cartrawler.com/artifactory/libs-release-local"
              credentials { username = "your_username_here" password = "your_password_here" }
          }
       }
  ~~~

  {: title="Gradle" }

  ~~~ java 
  
   # rxjava
   -keep class rx.schedulers.Schedulers {
     public static <methods>;
   }
   -keep class rx.schedulers.ImmediateScheduler {
      public <methods>;
   }
   -keep class rx.schedulers.TestScheduler {
      public <methods>;
   }
   -keep class rx.schedulers.Schedulers {
      public static ** test();
   }
   -keepclassmembers class rx.internal.util.unsafe.*ArrayQueue*Field* {
      long producerIndex;
      long consumerIndex;
   }
   -keepclassmembers class rx.internal.util.unsafe.BaseLinkedQueueProducerNodeRef {
      long producerNode;
      long consumerNode;
   }
   
  ~~~

  {: title="Proguard" }


  ~~~ xml
  
   //Add the CartrawlerActivity to the Android manifest and set the theme as the theme created in the previous step.  See example below:
   
   <activity
      android:name="cartrawler.core.base.CartrawlerActivity"
      android:windowSoftInputMode="adjustResize"
      android:screenOrientation="portrait"
      android:theme="@style/YourThemeExtendingCTAppTheme" />
   
   //Note: we do not support landscape and it is required that the orientation is fixed to portrait

  ~~~

  {: title="Manifest" }
---


1. Add the necessary gradle configuration for dependencies and repository to the app modules build.gradle file (see Gradle tab on the right).
2. Add our maven repository and enter the artifactory credentials (see Gradle tab on the right).
3. Create a theme that extends the **CTAppTheme**.
4. Include activity cartrawler.core.base.CartrawlerActivity (see Manifest tab on the right).
5. If you are using proguard, update the proguard config as shown on the right.
