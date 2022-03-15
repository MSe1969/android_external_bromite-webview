# android_external_bromite-webview
Prebuilt Android System Webview from www.bromite.org

Replaces the default Android System Webview with the 'Bromite' SystemWebView component in Custom ROM builds

## Credits
I have only taken the apk files (arm, arm64) from https://www.bromite.org/system_web_view  and created an 'Androik.mk' file around. 
All credits go to the Chromium project (https://www.chromium.org/Home) and the developers behind Bromite. Please visit the 
respective pages listed above for more information and the respective Copyright and License

## How to include into your Custom ROM build
- Include this repo into your local manifest (path does not matter, suggest external/bromite-webview)
- Specify `PRODUCT_PACKAGES += bromite-webview` in a 'product' .mk file (**not** in an Android.mk file)
- An 'elegant' way to do so without having to fork and track any specific device or vendor repository is to simply create an own product.mk file in directory vendor/extras (or to add the above statement into an existing one)
- It is not necessary to remove the default webview repo from the build tree
- **Take note about the next section !**

## Important info about the package name
As of release v97, Bromite Webview uses an [own package name 'org.bromite.webview'](https://www.bromite.org/news/2022-02-05-bromite-webview-package-name-change). This means, that you need to add it as webview provider to the configuration in your build tree. You can do so by overlaying the standard settings as shown in [this commit](https://github.com/lin18-microG/android_vendor_lineage/commit/56d45e0881ffbdcae8394835adbe160f23d6418a) (recommended approach) or by patching the respective configuration file in the frameworks/base repository directly. **Missing this step will prevent the webview functionality from being used in your build!**
