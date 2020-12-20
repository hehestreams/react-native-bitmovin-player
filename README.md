# react-native-bitmovin-player

![npm (scoped)](https://img.shields.io/npm/v/react-native-bitmovin-player.svg)&nbsp;&nbsp;![npm](https://img.shields.io/npm/dt/react-native-bitmovin-player.svg)&nbsp;&nbsp;![NpmLicense](https://img.shields.io/npm/l/react-native-bitmovin-player.svg)


#### Attention! This plugin is not official, the code is not provided or maintained by [Bitmovin](https://bitmovin.com)!

## Getting started

1. Disable auto link, create `react-native.config.js` archive in root folder.

```js
module.exports = {
  dependencies: {
    'react-native-bitmovin-player': {
      platforms: {
        android: null,
        ios: null,
      },
    },
  },
};
```

2. Install react-native-bitmovin-player fork.
```bash
  $ yarn add https://github.com/fhugoduarte/react-native-bitmovin-player.git
```

### Manual installation

#### iOS

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `react-native-bitmovin-player` and add `RNBitmovinPlayer.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libRNBitmovinPlayer.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)

#### Android

1. Open up `android/app/src/main/java/[...]/MainApplication.java`
  - Add `import com.xxsnakerxx.RNBitmovinPlayer.RNBitmovinPlayerPackage;` to the imports at the top of the file
  - Add `new RNBitmovinPlayerPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
   ```java
   include ':react-native-bitmovin-player'
   project(':react-native-bitmovin-player').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-bitmovin-player/android')
   ```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
   ```java
   implementation project(':react-native-bitmovin-player')
   ```

### Add BitmovinPlayer iOS SDK

Add line to your Podfile

`pod 'BitmovinPlayer', git: 'https://github.com/bitmovin/bitmovin-player-ios-sdk-cocoapod.git', tag: '2.36.0'`.

After that, install the pod using `pod install`.

### Add BitmovinPlayer Android SDK

Add a link to our release repository to your __application's__ `build.gradle` file. In addition to that, the google maven repository must be added.

```
allprojects {
    repositories {
        ...
        google()
        maven {
            url 'http://bitmovin.bintray.com/maven'
        }
    }
}
```

### Setup Project

Add the Bundle identifier of the iOS application which is using the SDK as an allowed domain to the       Bitmovin licensing backend. This can also be done under `Player -> Licenses` when logging in into https://dashboard.bitmovin.com with your account.

When you do not do this, you'll get a license error when starting the application which contains the player.

#### iOS

Add your Bitmovin player license key to the `Info.plist` file as __BitmovinPlayerLicenseKey__.

#### Android

Add your Bitmovin player license key to the `AndroidManifest.xml`.

```xml
<meta-data android:name="BITMOVIN_PLAYER_LICENSE_KEY" android:value="YOUR_KEY_HERE" />
```

Your player license key can be found when logging in into https://dashboard.bitmovin.com and navigating to `Player -> Licenses`.

Add permissions to the `AndroidManifest.xml`.

```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.DOWNLOAD_WITHOUT_NOTIFICATION" />
```

Enable allowBackup to the `AndroidManifest.xml`.

```xml
<application
      ...
      android:allowBackup="true">
```

## Usage
```javascript
import BitmovinPlayer from 'react-native-bitmovin-player';

// please follow to index.js for available props
<BitmovinPlayer
  configuration={{
    source: {
      title: 'It works',
      url: 'https://bitdash-a.akamaihd.net/content/sintel/hls/playlist.m3u8',
    },
  }}
/>
```
