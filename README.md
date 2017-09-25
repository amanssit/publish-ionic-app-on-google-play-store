# publish-ionic-app-on-google-play-store
### its very easy to publis ionic app for play store , use these simple steps to publish your ionic app for android

* step -1 --> configer Your app setting for publish ,like app package name,description and othere information into the config.xml file

* step-2 --> you need to add the android platform using this command

### $ ionic platform add android

* step-3 --> After adding the android platform use this command to generate the unsigned APK 

### $ cordova build --release android

* step-4--> After executing the above command you will get and unsigned APK insde the "platforms\android\build\outputs\apk\android-release-unsigned.apk"

* step-5--> now create a folder in any drive and copy android-release-unsigned.apk file to this foler 

* step-6--> now you have to generate demo-key.keystore file using this command it will ask app info with org info provide that and don't forget password 
,this password will be use when you will update the Your app later

### $ keytool -genkey -v -keystore demo-key.keystore -alias DemoApp -keyalg RSA -keysize 2048 -validity 10000

* step-7--> now use the jarsigner command for signed apk

### $ jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore demo-key.keystore android-release-unsigned.apk DemoApp

* step-8--> now use this final command to get signed APK with aligned , if u will get zipalign internal external command error copy zipalign.exe to current folder from C:\Users\USER_NAME\AppData\Local\Android\sdk\build-tools\22.0.1 

### $ zipalign -v 4 android-release-unsigned.apk DemoApp.apk
