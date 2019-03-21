## Other Components

These components may come in handy for certain applications. For an exhaustive list of components and APIs, check out the sidebar to the left.

- **[Activity Indicator](https://facebook.github.io/react-native/docs/activityindicator.html)**
  - Displays a circular loading indicator.
  - e.g.
    ```js
    <ActivityIndicator size="large" color="#0000ff" />
    ```

- **[Alert]()**
  - Launches an alert dialog with the specified title and message.
  - iOS
    - On iOS you can specify any number of buttons. 
    - Each button can optionally specify a style, which is one of 'default', 'cancel' or 'destructive'.
  - Android
    - Up to 3 buttons can be specified.
    - 1 is positive
    - 2 is negative, positive
    - 3 is neutral, negative, positive
  - Methods
    - ```alert```
      ```js
      static alert(title, message?, buttons?, options?, type?)
      ```
  - e.g.
    ```js
    Alert.alert(
      'Alert Title',
      'My Alert Msg',
      [
        {text: 'Ask me later', onPress: () => console.log('Ask me later pressed')},
        {
          text: 'Cancel',
          onPress: () => console.log('Cancel Pressed'),
          style: 'cancel',
        },
        {text: 'OK', onPress: () => console.log('OK Pressed')},
      ],
      {cancelable: false},
    );
    ```

- **[Animated](https://facebook.github.io/react-native/docs/animated.html)**
  - A library for creating fluid, powerful animations that are easy to build and maintain.
  - See [animated component](./animated_comp.md) page for full reference.

- **[CameraRoll]()**
  - Provides access to the local camera roll / gallery.
  - iOS
    - CameraRoll API requires RCTCameraRoll library.
    - See [linking libraries](https://facebook.github.io/react-native/docs/linking-libraries-ios).
    - User permission is required to access the device's camera roll
  - Methods
    - ```saveToCameraRoll```
      ```js
      CameraRoll.saveToCameraRoll(tag, [type]);
      ```
    - ```getPhotos```
      ```js
      CameraRoll.getPhotos(params);
      ```
  - e.g.
    ```js
    // Loading Images
    
    _handleButtonPress = () => {
       CameraRoll.getPhotos({
           first: 20,
           assetType: 'Photos',
         })
         .then(r => {
           this.setState({ photos: r.edges });
         })
         .catch((err) => {
            //Error Loading Images
         });
       };
    render() {
     return (
       <View>
         <Button title="Load Images" onPress={this._handleButtonPress} />
         <ScrollView>
           {this.state.photos.map((p, i) => {
           return (
             <Image
               key={i}
               style={{
                 width: 300,
                 height: 100,
               }}
               source={{ uri: p.node.image.uri }}
             />
           );
         })}
         </ScrollView>
       </View>
     );
    }
    ```

- **[Clipboard]()**
  - Provides an interface for setting and getting content from the clipboard on both iOS and Android.
  - Methods
    - ```getString```
      ```js
      static getString()
      ```
    - ```setString```
      ```js
      static setString(content)
      ```
  - e.g.
    ```js
    // Get content of string type
    
    async _getContent() {
      var content = await Clipboard.getString();
    }
    ```
    ```js
    // Set content of string type
    
    _setContent() {
      Clipboard.setString('hello world');
    }
    ```

- **[Dimensions]()**
  - Provides an interface for getting device dimensions.
  - e.g.
    ```js
    
    ```

- **[KeyboardAvoidingView]()**
  - Provides a view that moves out of the way of the virtual keyboard automatically.
  - e.g.
    ```js
    
    ```

- **[Linking]()**
  - Provides a general interface to interact with both incoming and outgoing app links.
  - e.g.
    ```js
    
    ```

- **[Modal]()**
  - Provides a simple way to present content above an enclosing view.
  - e.g.
    ```js
    
    ```

- **[PixelRatio]()**
  - Provides access to the device pixel density.
  - e.g.
    ```js
    
    ```

- **[RefreshControl]()**
  - This component is used inside a ScrollView to add pull to refresh functionality.
  - e.g.
    ```js
    
    ```

- **[StatusBar]()**
  - Component to control the app status bar.
  - e.g.
    ```js
    
    ```

- **[WebView]()**
  - A component that renders web content in a native view.
  - e.g.
    ```js
    
    ```
