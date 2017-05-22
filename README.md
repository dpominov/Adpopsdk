# Adpopsdk
Library for add banner in android application

# Prerequisites
Developing for Android API level 14 or higher

# Implementation path


1 Connect your app in personal cabinet / create account

2 Add line in project dependencies:
```
compile 'com.adpop.adpopsdk:adpopborder:1.0'
```

3 Add lines in Manifest:
```
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
<uses-permission android:name="android.permission.READ_PHONE_STATE"/>
```

4 Add Banner to layout:

```
<com.adpop.adpopsdk.adborder.AdpopBorder

   android:id="@+id/border"

   android:layout_width="wrap_content"

   android:layout_height="wrap_content">

</com.adpop.adpopsdk.adborder.AdpopBorder>
```
5 Load Banner in Activity class:
```
AdpopBorder border = (AdpopBorder) findViewById(R.id.border);
border.setConfigBanner("uniqId","spotId",  true);
border.loadBanner();
```

uniqId - unique id publisher

spotId - uniq id spot

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

or you can close Banner:

```
border.closeAdpop();
```



# Implementation path for game engines(e.g. Cocos2d-x, libGdx):

1. Repeat steps 1-3
2. Create container View
3. Create new Banner, add it to the view and load banner:

```
AdpopBorder border = new AdpopBorder(this);
border.setConfigBaner("uniqId","spotId",false);
border.loadBaner();


RelativeLayout.LayoutParams adParams = new RelativeLayout.LayoutParams(RelativeLayout.LayoutParams.WRAP_CONTENT, RelativeLayout.LayoutParams.WRAP_CONTENT);
adParams.addRule(RelativeLayout.ALIGN_PARENT_BOTTOM);
adParams.addRule(RelativeLayout.CENTER_IN_PARENT);
layout.addView(border, adParams);
```

# Testing

For testing you can use:

uniqId = adsn-pub-273000048

spotId = 1075

Size of the test banner = 320*50

Good practice is to place the key value in strings.xml, e.g.

```
<string name="uniqId">adsn-pub-273000048</string>
<string name="spotId ">1075</string>
```
```
border = (AdpopBorder) findViewById(R.id.border);
border.setConfigBanner(R.string.uniqId,R.string.spotId, true);
border.loadBanner();
```
Do not forget to destroy the instance
```
@Override
    protected void onDestroy() {
        super.onDestroy();
        border.closeAdpop();
    }
```
