# react-native-collapsible-header
<img src="https://raw.githubusercontent.com/sonaye/react-native-collapsible-header/master/demo.gif" width="400">

[Inspiration](https://medium.com/appandflow/react-native-collapsible-navbar-e51a049b560a).

# Installation
`yarn add react-native-collapsible-header`

# Definition
```javascript
type collapsible = {
  headerBackgroundColor?: string,
  headerHeight?: number,          // default = 44
  noStatusBar?: boolean,          // default = false
  renderHeader: any,              // <Component />
  renderContent: any              // <Component />
                                  // ScrollView props can be passed
 };
```

## Example
```javascript
import React, { Component } from 'react';
import { Platform, StatusBar, Text, View } from 'react-native';

import Collapsible from './collapsible';

const Header = () => (
  <View
    style={{
      alignItems: 'center',
      flex: 1,
      justifyContent: 'center'
    }}>
    <Text style={{ color: '#fff' }}>
      Header
    </Text>
  </View>
);

const Content = ({ gray }) => (
  <View
    style={{
      alignItems: 'center',
      backgroundColor: gray ? '#f7f7f7' : null,
      justifyContent: 'center'
    }}>
    <Text style={{ color: '#444', padding: 40 }}>Content</Text>
  </View>
);

export default class Example extends Component {
  componentWillMount() {
    StatusBar.setBarStyle('light-content', true);

    if (Platform.OS === 'android')
      StatusBar.setBackgroundColor('#0f9d58', true);
  }

  render() {
    return (
      <Collapsible
        headerBackgroundColor="#0f9d58"
        renderHeader={<Header />}
        renderContent={
          <View>
            <Content />
            <Content gray />
            <Content />
            <Content gray />
            <Content />
            <Content gray />
            <Content />
            <Content gray />
            <Content />
            <Content gray />
          </View>
        }
      />
    );
  }
}
```