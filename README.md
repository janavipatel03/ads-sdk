# ads-sdk
To get a Git project into your build: Step 1. Add the JitPack repository to your build file

========= Features ==========

      ==> For Banner, Interstitial, and Native ads, you can use multiple ad IDs; 
      ==> You can set interstitial ads to appear periodically.
========= Gradle ==========

1). Add it in your root build.gradle at the end of repositories:

      allprojects {
          repositories {
                 maven { url 'https://jitpack.io' }
        }
      }
2). Add the dependency

==> FOR PRELOADED ADS

   implementation 'com.github.newtech:ads-sdk:1.0.0'

==> FOR SIMPLE ADS

   implementation 'com.github.newtech:ads-sdk:1.0.0'  
   
===== color guide ======

        <------------   set color in theme --------------->

                 Progressbar color ------> colorPrimary
                 Button and Space -------> buttonColor
3). use below code in activity

          Button showAds;
          RelativeLayout rlBanner,rl_native;
          View tv_space;

         showAds = findViewById(R.id.btn_next);
              rlBanner = findViewById(com.infyom.adssdk.R.id.rl_banner);
              rl_native = findViewById(com.infyom.adssdk.R.id.rl_native);
              tv_space = findViewById(com.infyom.adssdk.R.id.tv_space);


              NewTech.initializeAds(this);  // Once Application
              NewTech.enableTestMode(this); // Once

              NewTech.initDefaultValue(); // Once Splash
              
              NewTech.showBanner(this,rlBanner,1);
              NewTech.showNative(this,rl_native,tv_space,1, InfyOmAds.AdTemplate.NATIVE_300);

              showAds.setOnClickListener(v -> {
                  NewTech.showInterstitial(1, this, new Interstitial() {
                      @Override
                      public void onAdClose(boolean isFail) {
                          startActivity(new Intent(MainActivity.this,Main2Activity.class));
                      }
                  });
              });
======= Native Templates ===============

      NewTech.AdTemplate.NATIVE_300,
      NewTech.AdTemplate.NATIVE_100,
      NewTech.AdTemplate.NATIVE_50,
      NewTech.AdTemplate.NATIVE_40
