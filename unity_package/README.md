# Ad4Game Unity Package - AdMob Mediation Adapter

> Ad4Game-1.0.3.unitypackage (legacy Google Mobile Ads SDK) · Ad4Game-NextGen-1.0.0.unitypackage (GMA Next-Gen SDK)

## Overview

These Unity packages integrate the Ad4Game AdMob mediation adapter for both Android and iOS platforms, enabling you to monetize your Unity games through Ad4Game's ad network via Google AdMob mediation.

## Which package should I use?

It depends on the Android SDK setting of the [Google Mobile Ads Unity plugin](https://developers.google.com/admob/unity/android-next):

| Google Mobile Ads Unity plugin, Android | Ad4Game package | Android adapter |
|---|---|---|
| Legacy SDK (`play-services-ads`, the default) | [Ad4Game-1.0.3.unitypackage](./Ad4Game-1.0.3.unitypackage) | `com.Ad4game:admobmanager:1.1.8` |
| GMA Next-Gen SDK enabled (`ads-mobile-sdk`) | [Ad4Game-NextGen-1.0.0.unitypackage](./Ad4Game-NextGen-1.0.0.unitypackage) | `com.Ad4game:admobmanager-nextgen:1.0.0` |

⚠️ Package 1.0.3 does **not** work with the GMA Next-Gen SDK: you get Gradle duplicate class errors, or R8 missing class errors once `play-services-ads` is excluded. If you enable Next-Gen in the Google Mobile Ads plugin, switch to the NextGen package.

Both packages write the same file, `Assets/Ad4Game/Ad4GameAdMobDependencies.xml`, so importing one replaces the other. A project never ends up with both adapters.

## Package Version Information

### Ad4Game-1.0.3 (legacy SDK)

- **Unity Package Version**: 1.0.3
- **Android Adapter Version**: [1.1.8](https://github.com/ad4game/a4g-admob/) (`com.Ad4game:admobmanager`)
- **iOS Adapter Version**: [1.0.3](https://github.com/ad4game/a4g-admob-ios) (⚡ use tag: 1.0.3 on your Podfile)

### Ad4Game-NextGen-1.0.0 (GMA Next-Gen SDK)

- **Unity Package Version**: NextGen 1.0.0
- **Android Adapter Version**: [1.0.0](https://github.com/ad4game/a4g-admob/) (`com.Ad4game:admobmanager-nextgen`)
- **iOS Adapter Version**: [1.0.3](https://github.com/ad4game/a4g-admob-ios) (unchanged; Next-Gen in the Unity plugin only affects Android)
- **Requirements**: Google Mobile Ads Unity plugin 10.6.0 or higher with Android Next-Gen enabled, Android minimum API level 24.

The NextGen package does not add a Google ads SDK on Android: the Google Mobile Ads Unity plugin supplies `ads-mobile-sdk` when Next-Gen is enabled.

## Switching to the GMA Next-Gen SDK

1. Enable Next-Gen for Android in the Google Mobile Ads Unity plugin, following [Google's guide](https://developers.google.com/admob/unity/android-next) (plugin 11.1.0+: **Assets > Google Mobile Ads > Settings**).
2. Set **Player Settings > Android > Minimum API Level** to 24 or higher.
3. Import `Ad4Game-NextGen-1.0.0.unitypackage` (it overwrites `Assets/Ad4Game/Ad4GameAdMobDependencies.xml`).
4. Run **Assets > External Dependency Manager > Android Resolver > Force Resolve**.
5. Check that `com.Ad4game:admobmanager-nextgen:1.0.0` is resolved and that neither `com.Ad4game:admobmanager` nor `play-services-ads` is present, then rebuild.

Your AdMob mediation configuration does not change: the Custom Event class name is still `com.ad4game.admobadapter.AdmobCustomEventManager`.

To switch back to the legacy SDK, disable Next-Gen in the plugin, import `Ad4Game-1.0.3.unitypackage`, and run **Force Resolve** again.

## Upgrading from 1.0.2

⚠️ Package 1.0.2 ships Android adapter 1.1.6, which crashes with `java.lang.NoSuchMethodError` on `MediationAdLoadCallback.onFailure` when the app resolves Google Mobile Ads SDK 24.9.0 or higher. Upgrade to 1.0.3:

1. Import `Ad4Game-1.0.3.unitypackage` (it overwrites `Assets/Ad4Game/Ad4GameAdMobDependencies.xml`).
2. Run **Assets > External Dependency Manager > Android Resolver > Force Resolve**.
3. Check that `com.Ad4game:admobmanager:1.1.8` is the resolved version, then rebuild.

## Supported Ad Formats

- ✅ Banner Ads
- ✅ Interstitial Ads
- ✅ Rewarded Ads
- ✅ Native Ads
