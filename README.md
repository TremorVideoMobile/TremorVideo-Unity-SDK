# TremorVideo-Unity-SDK
- Unity Plugin Version: 1.0.1.20
- SDK Version: iOS SDK and Android SDK 3.12
- Release Date: April 20th, 2016 

# To Download
Please contact the publisher team at Tremor Video to download the Unity Plugin which includes iOS and Android SDK 3.12
The Unity Plugin ships as a zip file, inside zip file includes:
- **TremorVideo.unitypackage** which includes Unity Plugin and iOS Android SDK
- **TremorVideoSample** which includes a sample app
 
# iOS and Android support and requirements
- Please visit [TremorVideo-iOS-SDK](https://github.com/TremorVideoMobile/TremorVideo-iOS-SDK) integration documentation to review iOS SDK requirements on minimum OS support, required frameworks, iOS 9 support, app orientation requirements
- Please visit [TremorVideo-Android-SDK](https://github.com/TremorVideoMobile/TremorVideo-Android-SDK) integration documentation to review Android SDK requirements on minimum OS support, Google Play Service requirement and required permission.

# Integrate Unity Package into your Unity Project
Follow the follow steps to Integrate Tremor SDK into your application. Inside the sample app, there is C# file **TVEntryPoint.cs**, which provides a sample on how the uses API. All of the code you will need to call is contained in **Plugins/TremorVideo.cs**.

### Step 1: Import the TermorVideo unity package
From the Assets menu, select Import Assets->Custom Package to import: **TremorVideo.unitypackage**

### Step 2: Create an empty gameObject. 
Add the TremorVideo.cs script as a component to your empty gameObject. (This will persist throughout your scenes.)

### Step 3: Initialize the SDK 
Initialize the sdk with your app id (This will be given to you by Tremor Video.). You can add a delegate if you want to track the changes of Ad state, for instance if an ad is ready.
```
    TremorVideo.InitWithID ("Your appID");
    TremorVideo.adReadyDelegate = AdReady;
```

### Step 4: Fetching the ad
Fetch a video ad by calling
```
    TremorVideo.LoadAd ();
```

### Step 5: Check if an Ad is ready to be shown
Wait for an adReady response (make sure you’ve set a delegate method).
```
    public void AdReady (string success) {
        Debug.Log ("TV entry point adReady");
    }

```

### Step 6: Show the ad
When your application is ready to show the ad, call showAd with the ad’s parent View Controller. 
```
    TremorVideo.ShowAd ();
```

### Optional Steps:
**Delegate Callbacks**

If your application would like to be notified of ad status, loading, start or completion, you can implement the TremorVideoAd delegate. For example:
```
    TremorVideo.adReadyDelegate = AdReady;
    TremorVideo.adStartDelegate = AdStart;
    TremorVideo.adCompleteDelegate = AdComplete;
```
Set the delegate:
```
    [TremorVideoAd setDelegate:self];
```
Then, implement the optional callbacks method.
```
    void AdReady (string success) {
		      Debug.Log ("Tremor Video ad ready callback");
	    }

    void AdStart {
		     Debug.Log ("Tremor Video ad start callback");
	    }

    void AdComplete (string responseCode) { 
        Debug.Log ("Tremor Video ad complete callback");
    }
```
**Check if an Ad is ready to be shown**

You can call `TremorVideoAd.IsAdReady()` to check if an ad is ready to be shown. 
