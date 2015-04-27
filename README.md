Auth0 Ionic ADFS Sample
=======================
This example is to demostrate the auth dialog for ADFS using Auth0 and Ionic. This example is best to test on an actual device (e.g. not `ionic serve`) to test the ADFS authentication dialog from a non-domain computer/device.

Based on Cordova 5, Cordova Android 4.0.0, Cordova InAppBrowser plugin (with customization), MSOpenTech's cordova-plugin-auth-dialog and Auth0's Ionic example.

Pre-requisites
--------------
1. Ensure that NodeJS, NPM (included with NodeJS) is installed.
2. Create an account on [auth0](https://auth0.com/) if you have not already.
3. Create / Configure ADFS which uses **integrated windows login**.
4. Create an App and configure to use ADFS setup in step above.
5. replace auth0 client id and domain in www/js/auth0-variables.js

Steps
-----
1. run `ionic start myApp blank`, this would create a blank ionic project template.
2. run `ionic setup sass`, this would setup this project to use Sass
3. add a platform (e.g. android, ios)
4. run `ionic plugin add cordova-plugin-whitelist` (see Caveats #1)
5. run `ionic plugin add https://github.com/adrianchia/cordova-plugin-inappbrowser.git`, this is because the inappbrowser does not support auth dialog (at the time of this writing), we would have to customize it.
6. run `ionic plugin add https://github.com/msopentech/cordova-plugin-auth-dialog.git` to add the auth dialog. (See Caveats #2).
7. copy the **www** directory from the *refresh-token* example in auth0 ionic.
8. run `ionic build android`
9 run `ionic emulate android` (or `ionic run android` if you are running on an actual device or Genymotion)


Caveats
-------
1. Since Cordova 5, Cordova Whitelist plugin has been moved externally, you may need to add the new whitelist plugin via `ionic plugin add cordova-plugin-whitelist`
2. You may need to disable / remove duplicate strings in **platforms/android/res/values/authdialog-strings.xml** in step 6. search for `SD` in the xml files (~ line 764).