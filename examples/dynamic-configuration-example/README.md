![Nevercode build status](https://app.nevercode.io/api/projects/a1c694b2-2e86-4a3b-9d0e-9671c5819b9f/workflows/d7a9ef3c-a383-4f1e-a4b1-2c6ed83ce9e7/status_badge.svg?branch=master&style=shields)

# Dynamic configuration example

This example app demonstrates how to dynamically configure the Thunderhead SDK.

## App flow summary 

1. On initial app start, [MainActivity.kt](https://github.com/thunderheadone/one-sdk-android/blob/master/examples/dynamic-configuration-example/app/src/main/java/com/thunderhead/dynamicconfigurationexample/MainActivity.kt) is presented with no region selected/configured.
2. The 'SELECT' button presents [ChangeRegionActivity.kt](https://github.com/thunderheadone/one-sdk-android/blob/master/examples/dynamic-configuration-example/app/src/main/java/com/thunderhead/dynamicconfigurationexample/ChangeRegionActivity.kt), which displays a list of regions to select from.
3. Upon selection of a new region, the SDK is *reconfigured* with new API credentials corresponding to the region selected, handled in the [`onActivityResult`](https://github.com/thunderheadone/one-sdk-android/blob/master/examples/dynamic-configuration-example/app/src/main/java/com/thunderhead/dynamicconfigurationexample/MainActivity.kt#L57) method.

## SDK initialization not required

The Thunderhead SDK is automatically initialized in an unconfigured state.
* While *unconfigured*, the SDK will continue to locally queue end-user data and will upload the data to server once the SDK is configured with valid parameters.
* This can be disabled at any time by setting the `oneOptOutConfiguration` to `true`. See more about opt out [here](https://github.com/thunderheadone/one-sdk-android#opt-an-end-user-out-of-tracking).

## Configure and reconfigure the SDK

You can configure and reconfigure the SDK as many times as necessary. 
* The SDK does not support partial, or piecemeal, configuration. All parameters must be provided, either all valid or invalid (`empty string` or `null`).  
* When configured with invalid parameters, it will set the SDK into an *unconfigured* state.

To configure/reconfigure the SDK, simply call the `oneConfigure` top-level Kotlin function or the `One.setConfiguration` Java method with the new parameters, as shown below:

Kotlin:
```kotlin
import com.thunderhead.android.api.oneConfigure
import com.thunderhead.OneModes

oneConfigure {
	siteKey = "ONE-XXXXXXXXXX-1022"
	apiKey = "f713d44a-8af0-4e79-ba7e-xxxxxxxxx"
	sharedSecret = "bb8bacb2-ffc2-4c52-aaf4-xxx"
	userId = "yourUsername@yourCompanyName"
	host = URI("https://xx.thunderhead.com")
	touchpoint = URI("myAppsNameURI")
	mode = OneModes.USER_MODE
}
```

Java:
```java
import com.thunderhead.android.api.configuration.OneConfiguration;
import com.thunderhead.One;
import com.thunderhead.OneModes;

final OneConfiguration oneConfiguration = new OneConfiguration.Builder()
        .siteKey(siteKey)
        .apiKey(apiKey)
        .sharedSecret(sharedSecret)
        .userId(userId)
        .host(URI.create(host))
        .touchpoint(URI.create(touchpointURI))
        .mode(OneModes.USER_MODE)
        .build();

One.setConfiguration(oneConfiguration);
```

## Questions or need help
Public documentation on the SDK can be found [here](https://github.com/thunderheadone/one-sdk-android)
To see what's available, every API is exposed in the `com.thunderhead.android.api` package.  Check that package source for guidance.

### Salesforce Interaction Studio support
_For Salesforce Marketing Cloud Interaction Studio questions, please submit a support ticket via https://help.salesforce.com/home_

### Thunderhead ONE support
_The Thunderhead team is available 24/7 to answer any questions you have. Just email [onesupport@thunderhead.com](mailto:onesupport@thunderhead.com) or visit our docs page for more detailed installation and usage information._

