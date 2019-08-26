# React-Navigation-React-Native
Dokumentasi React Navigation untuk santri Pondok IT Divisi Mobile React Native 

## Mengenalan React Navigation
React Navigation adalah salah satu solusi kita untuk menavigasi tampilan di React Native. 
Topik Utama Belajar React Navigation Yaitu Tab, Stack dan Modal 

## Instalasi React Navigation

### React Navigation
```
npm install react-navigation
```
### Gesture Handler
```
npm install react-native-gesture-handler
```
### React Native Reanimated
```
npm install react-native-reanimated.
```
### Depends On Your React Native Version

- React Native 0.60 and higher
On newer versions of React Native, [linking is automatic](https://github.com/react-native-community/cli/blob/master/docs/autolinking.md)

- React Native 0.59 and lower
```
react-native link react-native-reanimated
react-native link react-native-gesture-handler
```
Selesai Instalasi ``react-native-gesture-handler`` untuk android perlu modifikasi pada ``MainActivity.java``

```
package com.reactnavigation.example;

import com.facebook.react.ReactActivity;
 import com.facebook.react.ReactActivityDelegate;                                   //Tambahkan Ini 
 import com.facebook.react.ReactRootView;                                           //Tambahkan Ini         
 import com.swmansion.gesturehandler.react.RNGestureHandlerEnabledRootView;         //Tambahkan Ini 

public class MainActivity extends ReactActivity {

  @Override
  protected String getMainComponentName() {
    return "Example";
  }

  @Override                                                                    //Tambahkan Ini 
  protected ReactActivityDelegate createReactActivityDelegate() {              //Tambahkan Ini 
    return new ReactActivityDelegate(this, getMainComponentName()) {           //Tambahkan Ini 
      @Override                                                                //Tambahkan Ini 
      protected ReactRootView createRootView() {                               //Tambahkan Ini 
       return new RNGestureHandlerEnabledRootView(MainActivity.this);          //Tambahkan Ini 
      }                                                                        //Tambahkan Ini 
    };                                                                         //Tambahkan Ini 
  }                                                                            //Tambahkan Ini 
}
```

## React Navigation stack navigator
- createStackNavigator adalah sebuah ``function`` yang returns sesuatu React component. 
 #### ``App.js``
```
import React from "react";
import { View, Text } from "react-native";
import { createStackNavigator, createAppContainer } from "react-navigation";   //import createStackNavigator, createAppContainer

//Buat Class Home Screen tanpa di Export 
class HomeScreen extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
        <Text>Home Screen</Text>
      </View>
    );
  }
}

const AppNavigator = createStackNavigator({
  Home: {
    screen: HomeScreen
  }
});

export default createAppContainer(AppNavigator);
```
