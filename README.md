# expo-dev-launcher-keywindow-bug-demo
Reproduction of a bug in expo-dev-launcher

## Installation

```
yarn install
```


## Build
Issue is related to iOS, so it's best to detach and open the XCode project to se where it fails
```
npx expo prebuild --clean -p ios
```

Then open iOS project `expodevlauncherkeywindowbugdemo` in XCode


## Run

Run on a iOS device from XCode and it should fail with this error

```
2023-08-17 09:34:25.210676+0200 expodevlauncherkeywindowbugdemo[34619:2882658] EXDevLauncher/ExpoDevLauncherAppDelegateSubscriber.swift:12: Fatal error: Cannot find the keyWindow. Make sure to call `window.makeKeyAndVisible()`.
(lldb) 
```

