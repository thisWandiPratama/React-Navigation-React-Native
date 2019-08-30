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
- createStackNavigator adalah sebuah ``function`` yang ``returns`` sesuatu ``React component.`` 
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

## TAB
```
import React from 'react'
import { StyleSheet, Image } from 'react-native'
import { createStackNavigator, createBottomTabNavigator } from 'react-navigation'
import Home from "../screen/Home";
import Search from "../screen/Search";
import Add from '../screen/Add'
import Like from '../screen/Like'
import Profile from '../screen/Profile'


const homeIcon = require('../assets/home.png')
const searchIcon = require('../assets/search.png')
const addIcon = require('../assets/plus.png')
const likeIcon = require('../assets/like.png')
const profileIcon = require('../assets/profile.png')


export default createBottomTabNavigator({
    Home: {
        screen: Home,
        navigationOptions: {
            header: null,
            tabBarIcon: ({ tintColor }) => (
                <Image source={homeIcon} style={[styles.icon, { tintColor }]} />
            )
        }
    },
    Search: {
        screen: Search,
        navigationOptions: {
            header: null,
            tabBarIcon: ({ tintColor }) => (
                <Image source={searchIcon} style={[styles.icon, { tintColor}]} />
            )
        }
    },
    Add: {
        screen: Add,
        navigationOptions: {
            header: null,
            tabBarIcon: ({ tintColor }) => (
                <Image source={addIcon} style={[styles.icon, { tintColor  }]} />
            )
        }
    },
    Like: {
        screen: Like,
        navigationOptions: {
            header: null,
            tabBarIcon: ({ tintColor }) => (
                <Image source={likeIcon} style={[styles.icon, { tintColor  }]} />
            )
        }
    },
    Profile: {
        screen: Profile,
        navigationOptions: {
            header: null,
            tabBarIcon: ({ tintColor }) => (
                <Image source={profileIcon} style={[styles.icon, { tintColor }]} />
            )
        }
    }
}, {
    tabBarOptions:{
        activeTintColor:"#00b4d5",
        inactiveTintColor:'#babec4',
        indicatorStyle : { backgroundColor:'red'},
        labelStyle:{
            fontSize:14
        },
        style:{
            backgroundColor: '#fff',
            height: 60,
            padding: 5
        },
        showLabel: false
    }
})

const styles = StyleSheet.create({
    icon:{
        height: 20,
        width: 20
    }
})
```

## Tab & Stack 

```
const AppTabNavigator = createMaterialTopTabNavigator({
    Beranda: {
        screen:MenuHome,
       
    },

    Education: {
        screen: Education
    },

    Status: {
        screen: Status
    },

    Absensi: {
        screen: Absensi
    },
        
},{
tabBarOptions: {
    activeTintColor: '#fff',

    labelStyle: {
      fontSize: 8,
    },
    style: {
      backgroundColor: '#009688',
    },
  }
});

  const AppPageBeranda = createStackNavigator({
    rootTab:{
      screen: AppTabNavigator,
      navigationOptions: () => ({
        header: null,
      }),
    
    },
      
    HomeEduc:{
        screen: HomeEduc,
        navigationOptions: () => ({
          header: null,
        }),
    },
    Modul:{
      screen: Modul,
      navigationOptions: () => ({
        title:'Modul Pembelajaran'
      }),
  },
})

const Beranda = createAppContainer(AppPageBeranda);
export default Beranda
```

##  

```
// Data di state di Screen 1
constructor(props) {
 
    super(props)
 
    this.state = {
        Nama: 'wandi pratama',
        
 
    }
 
  }
 
 Button
            this.props.navigation.navigate('HomeAbs', {NamaUser: Nama})
            
 // screen 2 
                   <Text>{his.props.navigation.state.params.NamaUser}</Text>

            
            
