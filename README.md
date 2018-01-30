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

If you have XCode or Android Studio installed, you can run Expo on the emulator.  Use `yarn run ios` or `yarn run android` for this.  It works more consistently if the emulator or simulator is already running.  If you do not have XCode or Android Studio installed, you can run Expo on your own phone using `yarn start`.

## Add Analytics

1. Change directory to your project directory.
2. Run `awsmobile init`.
  * Where is your project's source directory: (src) **src**
  * Where is your project's distribution directory that stores build artifacts: (build) _Enter_
  * What is your project's build command: (npm run-script build) _Enter_
  * What is your project's start command for local test run: (npm run-script start) **yarn start**
  * What awsmobile projexct name would you like to use: (...) **notes-app**
3. Run `yarn add aws-amplify-react-native`
4. Add the following code to the `App.js` file (under the other imports):

```
import Amplify from 'aws-amplify-react-native';
import awsconfig from './src/aws-exports';

Amplify.configure(awsconfig);
```

5. Run the application again.
6. Run `awsmobile console`:
  * Click **Analytics** in the top right corner.
  * Click **Analytics** in the top left corner (side menu).
  * Validate that there is one endpoint recorded.

Add custom events to your app.  In this section, we add an "add-note" and "delete-note" event when those events happen in your app:

1. Edit `./src/screens/NoteListScreen.js`.  At the top of the file, add the following import:

```
import { Analytics } from 'aws-amplify-react-native';
```

2. Edit the `onAddNote()` method to be the following:

```
    static onAddNote(navigate) {
        Analytics.record('add-note');
        navigate('details', { noteId: uuid.v4() });
    }
```

3. Edit the `onDeleteNote()` method to be the following:

```
    onDeleteNote(item) {
        Analytics.record('delete-note');
        this.props.deleteNote(item.noteId);
    }
```

4. Run the app again.  Make some changes (add/delete notes).  Then view the analytics again.  In the **Events** page, you should see the appropriate events.  (You must refresh the page to get the new events to show up by name).

## Add Authentication

1. Run `awsmobile user-signin enable`.
2. Run `awsmobile pushy`.
3. Replace the Amplify import in `App.js` with the following:

```
import Amplify, { withAuthenticator } from 'aws-amplify-react-native';
```

4.  Replace the `export default` line at the bottom of `App.js` with the following:

```
export default withAuthenticator(App);
```

5. Run the app.

You will be prompted with the username/password prompt.  You can sign up first, then use the same information to sign in.  Also, check the Analytics - you will now see 1 daily active user.










