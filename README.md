# Expo Version of the React Native Notes Tutorial

This is an Expo version of the React Native Notes Tutorial.

## Pre-requisites

1. [Node](https://nodejs.org) - any version at the LTS version or beyond is good enough.
2. A JavaScript Editor ([Visual Studio Code](https://code.visualstudio.com/) or [Nuclide](https://nuclide.io/) is recommended.  Ensure you add any packages appropriate to React Native development).
3. The [Expo](https://expo.io) App installed on an iOS or Android Device

## Install awsmobile CLI

```
npm install -g awsmobile-cli
awsmobile configure
```

You may need to add a PATH.  On MacOS, global modules are stored in /usr/local/bin and may need `sudo` privileges to install.  On Windows, global modules are stored in %APPDATA%\\npm.

When running awsmobile configure, a process is started that links the awsmobile CLI to your AWS account.  This requires that you log in to the AWS console.

## Download the Repository

Download [the GitHub repo](https://github.com/adrianhall/react-native-expo-notes).

1. Go to [the GitHub repo](https://github.com/adrianhall/react-native-expo-notes).
2. Click **Clone or download**.
3. Click **Download ZIP**.
4. Unpack the ZIP file.
5. Open a terminal in the new directory.  Run `yarn install`.
6. Run `yarn start` to start the app.

If you have XCode or Android Studio installed, you can run Expo on the emulator.  If not, you can run Expo on your own phone.

## Add Analytics

1. Change directory to your project directory.
2. Run `awsmobile init`.
  * When prompted, enter `src` for the source dir


