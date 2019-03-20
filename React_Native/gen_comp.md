# General Components

[Documentation](https://facebook.github.io/react-native/docs/components-and-apis.html)

## Basic

Most apps will use the following components.

- **[View](https://facebook.github.io/react-native/docs/view.html)**
  - The most fundamental component for building a UI.
    - Equivalent to ```<div>``` in HTML
  - e.g.
    ```js
    <View
      style={{
        flexDirection: 'row',
        height: 100,
        padding: 20,
      }}>
      <View style={{backgroundColor: 'blue', flex: 0.3}} />
      <View style={{backgroundColor: 'red', flex: 0.5}} />
      <Text>Hello World!</Text>
    </View>
    ```

- **[Text](https://facebook.github.io/react-native/docs/text.html)**
  - A component for displaying text.
  - e.g.
    ```js
    <Text style={styles.baseText}>
      <Text style={styles.titleText} onPress={this.onPressTitle}>
        {this.state.titleText}{'\n'}{'\n'}
      </Text>
      <Text numberOfLines={5}>
        {this.state.bodyText}
      </Text>
    </Text>
    ```

- **[Image](https://facebook.github.io/react-native/docs/image.html)**
  - A component for displaying images.
  - e.g.
    ```js
    <Image
      source={require('/react-native/img/favicon.png')}
    />
    <Image
      style={{width: 50, height: 50}}
      source={{uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png'}}
    />
    <Image
      style={{width: 66, height: 58}}
      source={{uri: 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADMAAAAzCAYAAAA6oTAqAAAAEXRFWHRTb2Z0d2FyZQBwbmdjcnVzaEB1SfMAAABQSURBVGje7dSxCQBACARB+2/ab8BEeQNhFi6WSYzYLYudDQYGBgYGBgYGBgYGBgYGBgZmcvDqYGBgmhivGQYGBgYGBgYGBgYGBgYGBgbmQw+P/eMrC5UTVAAAAABJRU5ErkJggg=='}}
    />
    ```

- **[TextInput](https://facebook.github.io/react-native/docs/textinput.html)**
  - A component for inputting text into the app via a keyboard.
  - e.g.
    ```js
    <TextInput
      style={{height: 40, borderColor: 'gray', borderWidth: 1}}
      onChangeText={(text) => this.setState({text})}
      value={this.state.text}
    />
    ```

- **[ScrollView](https://facebook.github.io/react-native/docs/scrollview.html)**
  - Provides a scrolling container that can host multiple components and views.
  - e.g.
    ```js
    
    ```

- **[StyleSheet](https://facebook.github.io/react-native/docs/stylesheet.html)**
  - Provides an abstraction layer similar to CSS stylesheets.

## User Interface

Components that render common UI controls on any platform.

- **[Button](https://facebook.github.io/react-native/docs/button.html)**
  - A basic button component for handling touches that should render nicely on any platform.
  - e.g.
    ```js
    
    ```

- **[Picker](https://facebook.github.io/react-native/docs/picker.html)**
  - Renders the native picker component on iOS and Android.
  - Common Props
    - ```onValueChange```
    - ```selectedValue```
  - e.g.
    ```js
    <Picker
      selectedValue={this.state.language}
      style={{height: 50, width: 100}}
      onValueChange={(itemValue, itemIndex) =>
        this.setState({language: itemValue})
      }>
      <Picker.Item label="Java" value="java" />
      <Picker.Item label="JavaScript" value="js" />
    </Picker>
    ```

- **[Slider](https://facebook.github.io/react-native/docs/slider.html)**
  - A component used to select a single value from a range of values.
  - e.g.
    ```js
    
    ```

- **[Switch](https://facebook.github.io/react-native/docs/switch.html)**
  - Renders a boolean input.
  - e.g.
    ```js
    
    ```
  
## List Views

List view components only render elements that are currently showing on the screen. Good choice for displaying long lists of data

- **[FlatList](https://facebook.github.io/react-native/docs/flatlist.html)**
  - Renders performant, scrollable lists
  - e.g.
    ```js
    
    ```

- **[SectionList](https://facebook.github.io/react-native/docs/sectionlist.html)**
  - Like **FlatList** but for sectioned lists
  - e.g.
    ```js
    
    ```
