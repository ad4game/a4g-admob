# Ad4Game Unity Package - AdMob Mediation Adapter

> Ad4Game-1.0.3.unitypackage

## Overview

This Unity package ([Ad4Game-1.0.3.unitypackage](./Ad4Game-1.0.3.unitypackage)) integrates the Ad4Game AdMob mediation adapter for both Android and iOS platforms, enabling you to monetize your Unity games through Ad4Game's ad network via Google AdMob mediation.

## Package Version Information

- **Unity Package Version**: 1.0.3
- **Android Adapter Version**: [1.1.8](https://github.com/ad4game/a4g-admob/)
- **iOS Adapter Version**: [1.0.3](https://github.com/ad4game/a4g-admob-ios) (⚡ use tag: 1.0.3 on your Podfile)

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
