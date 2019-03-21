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
  - Methods
    - ```set```
      ```static set(dims)
    - ```get```
      ```static get(dim)```
    - ```addEventListener```
      ```static addEventListener(type, handler)```
    - ```removeEventListener```
      ```static removeEventListener(type, handler)```

- **[KeyboardAvoidingView]()**
  - Provides a view that moves out of the way of the virtual keyboard automatically.
  - e.g.
    ```js
    <KeyboardAvoidingView style={styles.container} behavior="padding" enabled>
      ... your UI ...
    </KeyboardAvoidingView>;
    ```

- **[Linking]()**
  - Provides a general interface to interact with both incoming and outgoing app links.
  - Methods
    - ```constructor```
    - ```addEventListener```
    - ```removeEventListener```
    - ```openURL(url)```
    - ```canOpenURL(url)```
      - Returns a promise object
    - ```getInitialURL()```
      - If the app launch was triggered by an app link, it will give the link url
      - Otherwise it will give null
  - e.g.
    ```js
    componentDidMount() {
      Linking.getInitialURL().then((url) => {
        if (url) {
          console.log('Initial url is: ' + url);
        }
      }).catch(err => console.error('An error occurred', err));
    }
    ```

- **[Modal]()**
  - Provides a simple way to present content above an enclosing view.
  - e.g.
    ```js
    <Modal
      animationType="slide"
      transparent={false}
      visible={this.state.modalVisible}
      onRequestClose={() => {
        Alert.alert('Modal has been closed.');
      }}>
      <View style={{marginTop: 22}}>
        <View>
          <Text>Hello World!</Text>

          <TouchableHighlight
            onPress={() => {
              this.setModalVisible(!this.state.modalVisible);
            }}>
            <Text>Hide Modal</Text>
          </TouchableHighlight>
        </View>
      </View>
    </Modal>
    ```

- **[PixelRatio]()**
  - Provides access to the device pixel density.
    - Rule thumb is to mutliply image size by pixel ratio for image resolution
  - Methods
    - ```get```
    - ```getFontScale```
    - ```getPixelSizeForLayoutSize```
      - Converts layout size (dp) to pixel size (px)
      ```js
      static getPixelSizeForLayoutSize(layoutSize)
      ```
    - ```roundToNearestPixel```
      - Rounds a layout size (dp) to the nearest layout size that corresponds to an integer number of pixels.
      ```js
      static roundToNearestPixel(layoutSize)
      ```
      ```js
      PixelRatio.roundToNearestPixel(8.4) = 8.33
      // 8.33 is the closest layout size that has a corresponding pixel integer of 25.
      ```
  - e.g.
    ```js
    var image = getImage({
      width: PixelRatio.getPixelSizeForLayoutSize(200),
      height: PixelRatio.getPixelSizeForLayoutSize(100),
    });
    ```

- **[RefreshControl]()**
  - This component is used inside a ScrollView to add pull to refresh functionality.
    - When the ScrollView is at scrollY: 0, swiping down triggers an onRefresh event.
  - e.g.
    ```js
    <ScrollView
      refreshControl={
        <RefreshControl
          refreshing={this.state.refreshing}
          onRefresh={this._onRefresh}
        />
      }
      ...
    />
    ```

- **[StatusBar]()**
  - Component to control the app status bar.
  - Constants
    - ```currentHeight``` (Android only)
      - Height of status bar
  - Methods
    - ```setHidden```
    - ```setBarStyle```
    - ```setNetworkActivityIndicatorVisible```
    - ```setBackgroundColor```
    - ```setTranslucent```
  - Type Definitions
    - ```StatusBarStyle```
    - ```StatusBarAnimation```
  - e.g.
    ```js
    <View>
      <StatusBar backgroundColor="blue" barStyle="light-content" />
      <View>
        <StatusBar hidden={route.statusBarHidden} />
        ...
      </View>
    </View>
    ```

- **[WebView]()**
  - A component that renders web content in a native view.
  - Note:  Only use the [React Native WebView fork](https://github.com/react-native-community/react-native-webview) of this component.
  - e.g.
    ```js
    <WebView
      source={{ uri: "https://facebook.github.io/react-native/" }}
    />
    ```
