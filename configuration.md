### How to change the package name in reactnative

npx react-native-rename -b "your package name"


### How to change the App name in reactnative

npx react-native-rename "Your App Name"


### How to Clean App Cache in reactnative

1. Go to Android Folder
2. Run ./gradlew cleanBuildCache

### Setting up Gradle variables

    Place the my-upload-key.keystore file under the android/app directory in your project folder.
    Edit the file ~/.gradle/gradle.properties or android/gradle.properties, and add the following (replace ***** with the correct keystore password, alias and key     password),
    
    MYAPP_UPLOAD_STORE_FILE=my-upload-key.keystore
    MYAPP_UPLOAD_KEY_ALIAS=my-key-alias
    MYAPP_UPLOAD_STORE_PASSWORD=*****
    MYAPP_UPLOAD_KEY_PASSWORD=*****

### Adding signing config to your app's Gradle config#

    ...
    android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            if (project.hasProperty('MYAPP_UPLOAD_STORE_FILE')) {
                storeFile file(MYAPP_UPLOAD_STORE_FILE)
                storePassword MYAPP_UPLOAD_STORE_PASSWORD
                keyAlias MYAPP_UPLOAD_KEY_ALIAS
                keyPassword MYAPP_UPLOAD_KEY_PASSWORD
            }
        }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
    }
     ...

### Generating the release APK

    $ cd android
    $ ./gradlew bundleRelease

### Testing the release build of your app
    $ npx react-native run-android --variant=release

### Publishing to other stores
  You can create an APK for each CPU by changing the following line in android/app/build.gradle:
        
        - ndk {
        -   abiFilters "armeabi-v7a", "x86"
        - }
      - def enableSeparateBuildPerCPUArchitecture = false
        + def enableSeparateBuildPerCPUArchitecture = true
     
     - universalApk false  // If true, also generate a universal APK
     + universalApk true  // If true, also generate a universal APK
    
