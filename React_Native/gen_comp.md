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
  - Methods
    - ```scrollTo```
    - ```scrollToEnd```
    - ```scrollWithoutAnimationTo```
    - ```flashScrollIndicators```

- **[StyleSheet](https://facebook.github.io/react-native/docs/stylesheet.html)**
  - Provides an abstraction layer similar to CSS stylesheets.
  - e.g.
    ```js
    // Creating a StyleSheet

    const styles = StyleSheet.create({
      container: {
        borderRadius: 4,
        borderWidth: 0.5,
        borderColor: '#d6d7da',
      },
      title: {
        fontSize: 19,
        fontWeight: 'bold',
      },
      activeTitle: {
        color: 'red',
      },
    });
    ```
    ```js
    // Using a StyleSheet

    <View style={styles.container}>
      <Text style={[styles.title, this.props.isActive && styles.activeTitle]} />
    </View>
    ```

## User Interface

Components that render common UI controls on any platform.

- **[Button](https://facebook.github.io/react-native/docs/button.html)**
  - A basic button component for handling touches that should render nicely on any platform.
  - e.g.
    ```js
    <Button
      onPress={onPressLearnMore}
      title="Learn More"
      color="#841584"
      accessibilityLabel="Learn more about this purple button"
    />
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

- **[Switch](https://facebook.github.io/react-native/docs/switch.html)**
  - Renders a boolean input.
  
## List Views

List view components only render elements that are currently showing on the screen. Good choice for displaying long lists of data

- **[FlatList](https://facebook.github.io/react-native/docs/flatlist.html)**
  - Renders performant, scrollable lists
  - Methods
    - scrollToEnd
    - scrollToIndex
    - scrollToItem
    - scrollToOffset
    - recordInteraction
    - flashScrollIndicators
  - e.g.
    ```js
    <FlatList
      data={[{key: 'a'}, {key: 'b'}]}
      renderItem={({item}) => <Text>{item.key}</Text>}
    />
    ```

- **[SectionList](https://facebook.github.io/react-native/docs/sectionlist.html)**
  - Like **FlatList** but for sectioned lists
  - Methods
    - scrollToLocation
    - recordInteraction
    - flashScrollIndicators
  - Type Definitions
    - Section
  - e.g.
    ```js
    // Homogeneous Rendering
    
    <SectionList
      renderItem={({item, index, section}) => <Text key={index}>{item}</Text>}
      renderSectionHeader={({section: {title}}) => (
        <Text style={{fontWeight: 'bold'}}>{title}</Text>
      )}
      sections={[
        {title: 'Title1', data: ['item1', 'item2']},
        {title: 'Title2', data: ['item3', 'item4']},
        {title: 'Title3', data: ['item5', 'item6']},
      ]}
      keyExtractor={(item, index) => item + index}
    />
    ```
    ```js
    // Heterogeneous Rendering / No Section Headers
    
    const overrideRenderItem = ({ item, index, section: { title, data } }) => <Text key={index}>Override{item}</Text>

    <SectionList
      renderItem={({ item, index, section }) => <Text key={index}>{item}</Text>}
      sections={[
        { title: 'Title1', data: ['item1', 'item2'], renderItem: overrideRenderItem },
        { title: 'Title2', data: ['item3', 'item4'] },
        { title: 'Title3', data: ['item5', 'item6'] },
      ]}
    />
    ```
