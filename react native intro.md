

# ReactNative 

https://medium.com/the-react-native-log/organizing-a-react-native-project-9514dfadaa0

## CREATE APP

### Method 1 : 

    create-react-native-app MyApp
    npm start 
    npm run ios
  
### Method 2 : 

    react-native init reactTutorialApp
    cd reactTutorialApp

## Running APP
    react-native start
    react-native run-ios  // ios
    react-native run-ios --simulator="iPhone X"  //ios
    react-native run-android

## Install Dependencise

    npm install

### Changes to Android

   When you rebuild the Android folder, Follow these steps :
   1. Create a file "local.properties" in android folder
   2. Add the following line : sdk.dir = /Users/prime/Library/Android/sdk
   3. Follw the link : https://github.com/wuxudong/react-native-charts-wrapper/tree/master/installation_guide
   OR Simply Use this :
   echo "sdk.dir = /Users/$(whoami)/Library/Android/sdk" > android/local.properties

   Best Practice:
    export ANDROID_HOME=/Users/<username>/Library/Android/sdk/
    export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools


### Remote Debugging
     http://localhost:8081/debugger-ui/
 
   Press Cmd + M on emulator screen
   Dev settings > Debug server host & port for device
   Set localhost:8081
   Rerun the android app: react-native run-android
   (first open the debugger and then enable debugger mode)

### Emulator Running

  Example :
  cd ~/Android/Sdk/tools/bin && ./avdmanager list avd
  cd ~/Android/Sdk/tools && ./emulator -avd Nexus_5X_API_23

  To Run :
  cd  ~/Library/Android/sdk/tools/bin && ./emulator -avd Nexus_5X_API_28_x86

  cd  ~/Library/Android/sdk/tools/ && ./emulator -list-avds
  Nexus_5X_API_28_x86
  cd  ~/Library/Android/sdk/tools/ && ./emulator -avd Nexus_5X_API_28_x86

  cd  ~/Library/Android/sdk/tools/ && ./emulator -avd Nexus_5X
  
 ### SetUp a Device(Mobile) for Development
 
   - settings->Dev Options->USB Debugging
  
 #### Test ADB and Install Your Phone’s Drivers (if Needed)
      (android debug bridge)
      
      $ sudo apt-get install adb
      $ adb devices (will list all devices connected)
      
      adb - no permission issue
      
      $ killall adb
      $ sudo adb kill-server
      $ sudo adb start-server
      $ adb devices 

#### using local database
      python3 manage.py runserver 0:8000


