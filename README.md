# Please contact us before using this library. 
# If you're working on a new integration, please use our [React Native Wrapper](https://github.com/berbix/berbix-react-native-wrapper) instead.

# Berbix React SDK

This Berbix React Native library provides simple interfaces to interact with the Berbix Verify flow.

## Installation

This library is dependent on the [react-native-camera](https://github.com/react-native-community/react-native-camera) component. Due to this dependency, you may need to follow their more detailed [installation instructions](https://github.com/react-native-community/react-native-camera/blob/master/docs/installation.md) if the basic instructions here are insufficient.

### Install the SDK

    npm install berbix-react-native

### Set up dependencies

    react-native link react-native-camera

Add the following line to `android/app/build.gradle` in the `defaultConfig` block.

    missingDimensionStrategy 'react-native-camera', 'general'

### Set up permissions

Add an entry for camera access to your `Info.plist` for iOS access.

    <key>NSCameraUsageDescription</key>
    <string>Your message to user when the camera is accessed for the first time</string>

## Usage

### Basic usage

```jsx
import React from "react";
import BerbixVerify from "berbix-react-native";

class ExampleComponent extends React.Component {
  render() {
    return (
      <BerbixVerify
        clientId="your_client_id"
        onComplete={event => {
          // send event.value to backend to fetch user verification data
        }}
      />
    );
  }
}
```

### Full propTypes

```js
BerbixVerify.propTypes = {
  // Required
  clientId: PropTypes.string.isRequired,

  // Configurations
  templateKey: PropTypes.string,
  clientToken: PropTypes.string,

  // Event handlers
  onComplete: PropTypes.func.isRequired,
  onError: PropTypes.func,
  onDisplay: PropTypes.func,
  onStateChange: PropTypes.func
};
```

## Publishing

    # Update the version in package.json
    npm run build
    npm publish
