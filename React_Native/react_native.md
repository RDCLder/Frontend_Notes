# React Native

## General

- [Documentation](https://facebook.github.io/react-native/)

- React Native is an open-source, cross-platform mobile app framework created by Facebook.
  - Allows mobile developers to use React alongside native platform capabilities
    - Uses native components instead of web components (e.g. view instead of div)
    - "Learn once, write everywhere"
  - Supports Android, iOS, and Universal Windows Platform
  
- React Native Compilation
  - UI
    - React Native does not support HTML or CSS.  Everything is written in JS.
    - React Native uses its own version of the virtual DOM
    - DOM elements are abstracted into either cross-platform components (e.g. views for divs) or platform-specific components
    - These components are compiled into their native equivalents
  - Logic
    - Creates JavaScript environment on the native platform in which JavaScript can be run (much like Node running JS off the browser)

- Cross-Platform Component Examples
  - ```<div>```
    - Android: ```android.view```
    - iOS: ```UIView```
    - React Native: ```<View>```
  - ```<input>```
    - Android: ```EditText```
    - iOS: ```UITextField```
    - React Native: ```<TextInput>```

- UI and logic communicate using a "bridge"
  - If the bridge is too slow, the logic can be implemented using the native language (e.g. Java, Kotlin, Swift, etc.)
  - Native code can increase performance at the cost of compatibility
    - JavaScript can have compatibility issues with native languages

- Limitations
  - Very little cross-platform styling of components
    - Each platform might require some amount of custom styling specific to that platform
  - Only a basic set of pre-built components
    - Although there are component libraries, they aren't as extensive as those in native libraries
  - No inherent responsive design
    - Requires custom logic or outside tools
  - Still in beta and active development
    - Version 0.59 has been released as of this writing
  - Overall worse performance than true native apps
  - There are ways to overcome these limitations

- Alternatives
  - Real native apps using native languages
    - Android:  Java, Kotlin
    - iOS: Swift, Objective-C
  - Progressive Web App
    - Users might not use a browser/OS which supports PWAs
  - Similar cross-platform libraries/frameworks
    - Ionic or Cordova which takes a web app and wraps it in a WebView
    - Worse performance due to WebView

## Create New Project

- [Create React Native App](https://github.com/react-community/create-react-native-app)
  - ```create-react-native-app appName``` or ```expo init appName```
  - Creates project directory with iOS or Android directories
  - Commands
    ```npm start```: Runs app in development mode with interactive prompt
      - Creates QR code that can be scanned to link mobile device with Expo app installed to development app
    ```npm test```:  Runs jest test runner on your tests
    ```npm run ios/android```:  Runs either iOS or Android simulator if appropriate tools are installed
    ```npm run eject```:  Ejects project from Create React Native App's build scripts and allows you to specify how to build your project.

- React Native CLI Quickstart
  - ```react-native init projectName```
  - Creates ```projectName``` directory with iOS and Android directories
  - Commands
    ```react-native run-ios/android```:  Run iOS or Android simulator.
