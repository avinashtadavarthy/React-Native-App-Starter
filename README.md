# React-Native-App-Starter

Code editor used: Visual Studio Code with extension 'React Native Full Pack'

## 1. Setting up the app and folder structure

1. To initialise the app 

```react-native init <App Name>```

2. Open up package.json. Add a 'postinstall' tag inside 'scripts'.

```"postinstall": "rm -f ./node_modules/react-native/local-cli/core/__fixtures__/files/package.json"```

3. Replace 

```metro-babel-preset-react-native": "v.v.v"``` 

inside devDependencies into:

```"babel-preset-react-native": "4.0.0"```

4. Add the 'app' folder to the root directory with the following folders inside it:

```
(root directory)
    |
    +--- app
        |
        +--- components (to house all the components that would be frequently reused on the app)
        +--- screens (to house all the screens within the app)
        +--- config (to house global variables / utility functions / global style components)
        +--- redux (if redux is being used, to house the various reducers etc.)
```

## 2. Setting up navigation in the app

Refer to notes on https://reactnavigation.org/docs/en/getting-started.html
Tip to remember: react-navigation sets up its own navigation bar in the app, so we would have to customise it / override it on our own.

1. Install react-navigation package in project

```npm install --save react-navigation```

2. Install react-native-gesture-handler package in project (both 1 and 2 are mandatory packages)

```npm install --save react-native-gesture-handler```

3. Link all native dependencies

```react-native link react-native-gesture-handler```

4. Create a file called as 'AppNavigator.js' to set up a stack navigator within the app

```
import { createStackNavigator, createAppContainer } from 'react-navigation';
import Home from './app/screens/Home'; // Home.js is any randomly created sample screen file

const AppNavigator = createStackNavigator({
  Home: { screen: Home }, 
});

export default createAppContainer(AppNavigator);
```

5. Our display content is currently inside 'App.js'. If we simply put our StackNavigator inside App.js, our app will be modular and much cleaner. From there we add additional screens to their respective files.

```
import React from 'react';
import AppNavigator from './AppNavigator';

export default class App extends React.Component {
  render() {
    return (
      <AppNavigator/>
    );
  }
}
```

## 3. Setting up a git connection to the project

1. Make a .gitignore file in the root directory of the project

```
hyperlink to file
```

2. git init in project directory

