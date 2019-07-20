# appium-wdio-node

# appium-boilerplate

> **NOTE:**
> This boilerplate is for Webdriver V5

Boilerplate project to run Appium tests together with WebdriverIO for:

- Android Native App - Astro Syok

> The apk of the app can be found in the following location : https://apkpure.com/syok-free-radio-videos-and-podcasts/net.amp.era and also available in Google Playstore and Apple Appstore
> Before running tests, please create a `./apps` directory, download the app and move the zip files into that directory

> **Note:**
> This boilerplate only handles local execution on 1 em/simulator at a time, not parallel execution. For more info about that Google on setting up a grid with Appium.

![webdriverio-demo-app-ios.ios](./docs/assets/appium-tests.gif)

## Based on
This boilerplate is currently based on:
- **WebdriverIO:** `5.7.#`
- **Appium:** `1.14.0`
- **Allure:** TBD
- **NodeJs:**  v8.11.3


## Installing Appium on a local machine
See [Installing Appium on a local machine](./docs/APPIUM.md)

## Setting up Android- Android mobile with version 9 has been used for the test.

## Quick start

1. Clone the git repo — `git clone https://TBD`

2. Then copy the files to your project directory (all files in `/tests` and the `wdio.conf`-files in the `config`-folder)

3. Merge project dev dependencies with your projects dev dependencies in the `package.json`

4. merge the scripts to `package.json` scripts

5. Run the tests for iOS with `npm run ios.app` and for Android with `npm run android.app`

## Config
This boilerplate uses a specific config for Android, see [configs](./config/) and are based on `wdio.conf.js`.
This config holds all the defaults so the Android configs only need to hold the capabilities and specs that are needed for running on Android.

> **Note:** The `@wdio/appium-service` has been integrated in this boilerplate so you don't need to start an Appium server yourself, WebdriverIO will do that for you.

Since we do not have Appium installed as part of this package, this has been configured to use the global Appium installation. This is configured in wdio.shared.conf.js
```
appium: {
    command : 'appium'
},
```

## Locator strategy for Syok app
The locator strategy for this boilerplate is to use `xpath`'s and 'id's, see also the [WebdriverIO docs](http://webdriver.io/guide/usage/selectors.html#Accessibility-ID) or this newsletter on [AppiumPro](https://appiumpro.com/editions/20).
xpath has been used where resource ids did not work. [though xpath is not the best way]

In few cases where xpath could not be clicked co-ordinates have been used. A function called custom-tap has been define in the utility-function


## Cloud vendors - TBD

### Sauce Labs Real Device Cloud
This boilerplate now also provides a setup for testing with the Real Device Cloud (RDC) of Sauce Labs. Please check the [SauceLabs](./config/saucelabs)-folder to see the setup for iOS and Android.

> With the latest version of WebdriverIO (`5.4.13` and higher) the iOS and Android config holds: 
> - automatic US or EU RDC cloud selection by providing a `region` in the config, see the [iOS](./config/saucelabs/wdio.ios.rdc.app.conf.js) and the [Android](./config/saucelabs/wdio.ios.rdc.app.conf.js) configs 
> - automatic update of the teststatus in the RDC cloud without using a customer script

Make sure you install the latest version of the `@wdio/sauce-service` with

```shell
$ npm install --save-dev @wdio/sauce-service
```

and add `services: ['sauce'],` to the config. If no `region` is provided it will automatically default to the US-RDC cloud.
If you provide `region: 'us'` or `region: 'eu'` it will connect to the US or the EU RDC cloud

There are 2 scripts that can be used, see the [`package.json`](./package.json), to execute the tests in the cloud:

    // For iOS
    $ npm run ios.sauce.rdc.app
    
    // For Android
    $ npm run android.sauce.rdc.app

## FAQ
See [FAQ](./docs/FAQ.md)

## Tips and Tricks
See [Tips and Tricks](./docs/TIPS_TRICKS.md)
