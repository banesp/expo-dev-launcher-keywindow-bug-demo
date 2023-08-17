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

Then open iOS project `ios/expodevlauncherkeywindowbugdemo.xcworkspace` in XCode


## Run

Run on a iOS device from XCode and it should fail with this error

```
2023-08-17 09:34:25.210676+0200 expodevlauncherkeywindowbugdemo[34619:2882658] EXDevLauncher/ExpoDevLauncherAppDelegateSubscriber.swift:12: Fatal error: Cannot find the keyWindow. Make sure to call `window.makeKeyAndVisible()`.
(lldb) 
```

## Cause of crash
In `app.json` there is a definition to support multiple scenes (Which is configuration necessary to support CarPlay). If this configuration is removed the project builds fine.

```
...,
"infoPlist": {
  "UIApplicationSceneManifest": {
    // "UIApplicationSupportsMultipleScenes": true,
    // "UISceneConfigurations": {
    //   // "CPTemplateApplicationSceneSessionRoleApplication": [
    //   //   {
    //   //     "UISceneClassName": "CPTemplateApplicationScene",
    //   //     "UISceneConfigurationName": "CarPlaySceneConfiguration",
    //   //     "UISceneDelegateClassName": "TemplateSceneDelegate"
    //   //   }
    //   // ],
    //   "UIWindowSceneSessionRoleApplication": [
    //     {
    //       "UISceneClassName": "UIWindowScene",
    //       "UISceneConfigurationName": "AppSceneConfiguration",
    //       "UISceneDelegateClassName": "WindowSceneDelegate",
    //       "UISceneStoryboardFile": "SplashScreen"
    //     }
    //   ]
    // }
  }
},
...,
```



