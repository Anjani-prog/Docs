#### After cloning project for running in android device

     $ npm install 
     $ npx npx react-native run-android

#### **Please be carefull while editing android folder if there any updates done on that folder 
####    mention them in this page 

####  React Native Custom Fonts

        Creating react-native.config.js file on root project with the following code:

        module.exports = {
            project: {
            ios: {},
            android: {},
            },
            assets: ['./src/assets/fonts']
        };


        Run $ npx react-native link
        
####  For Splash Screen follow this link
  

   https://dev.to/cmcodes/how-to-add-splash-screen-in-a-react-native-android-app-287l
   NB: Dont forget to change package .name to our app package name in splashactivity.java



####  App Icon in React Native (IOS and Android) (https://appicon.co/)


        Android Icon Measurements
        Size: 512px x 512px
        Format: 32-bit PNG
        Color space: sRGB
        Max file size: 1024KB
        Shape: Full square


        IOS Icon Measurements
        Format: PNG
        Color space: sRGB/P3
        Layers: Flattened with no transparency
        Shape: Square with no rounded corners.

        
####  For textinput scrolling (problem in KeyboardAwareScrollView view changed)



  this line in android/app/src/main/androidmanifest.xml -> activity
        android:windowSoftInputMode="adjustResize" 
  into this line
        android:configChanges="keyboard|keyboardHidden|orientation|screenSize|uiMode"
        
