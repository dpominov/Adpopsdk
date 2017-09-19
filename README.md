# Adpopsdk
Library for add advertising in android application

Atention! All information to belongs to AdpopBorder module, which is a bottom banner

# Prerequisites
Developing for Android API level 14 or higher

# Implementation path

1 Connect your app in personal cabinet / create account

2 download [Jar](https://github.com/ColiseumChaoS/Adpopsdk/raw/master/adpopsdk.jar)

Adpopsdk uses OKHttp3 in work, please check dependencies in your project, it must to include: 
```
compile 'com.squareup.okhttp3:okhttp:3.+'
```
3 Add lines in Manifest:
```
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.READ_PHONE_STATE"/>
```

4 Add Banner to layout:

```
<com.adpop.sdkadpop.adborder.AdpopBorder
   android:id="@+id/border"
   android:layout_width="wrap_content"
   android:layout_height="wrap_content">
</com.adpop.sdkadpop.adborder.AdpopBorder>
```
5 Load Banner in Activity class:
```
AdpopBorder border = (AdpopBorder) findViewById(R.id.border);
border.setConfigBaner("uniqId","spotId","idDomain",true);
border.loadBaner();
```

uniqId - unique id publisher

spotId - uniq id spot

idDomain - id domain network

true/false - Show/not close button

6 Size Banner - AdpopBorder will automatically determines and chooses the banner size most suitable for the device screen.

# Callbacks
```
border.setAdListener(new AdBorderListener() {

   @Override
   public void onBorderLoad() {
       Log.i("TAG","baner is load");
   }


   @Override
   public void onBorderErrorLoad() {
       Log.i("TAG","baner load error");
   }


   @Override
   public void onBorderClose() {
       Log.i("TAG","baner is close");
   }

});

```
closeAdpop() method will destroy instance^

```
border.closeAdpop();
```



# Implementation path for game engines(e.g. Cocos2d-x, libGdx):

1. Repeat steps 1-3
2. Create container View
3. Create new Banner, add it to the view and load banner:

```
AdpopBorder border = new AdpopBorder(this);
border.setConfigBaner("uniqId","spotId","idDomain",true);
border.loadBaner();


RelativeLayout.LayoutParams adParams = new RelativeLayout.LayoutParams(RelativeLayout.LayoutParams.WRAP_CONTENT, RelativeLayout.LayoutParams.WRAP_CONTENT);
adParams.addRule(RelativeLayout.ALIGN_PARENT_BOTTOM);
adParams.addRule(RelativeLayout.CENTER_IN_PARENT);
layout.addView(border, adParams);
```
