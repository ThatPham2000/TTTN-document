# Elca job fair application

[<img src="https://www.elca.vn/themes/elca/new_logo_elca_vn.svg" width="200" />](https://www.elca.vn/en/about-us)

## Getting Started

This is a project consisting of two apps:

- A website to configure games, gifts, user statistics.
- A mobile app to play games.

## Prerequisites

Before you continue, ensure you meet the following requirements:

- You have installed the latest version of Flutter, Dart, NodeJs, Firebase CLI.
- You must use one of these options:
  - Windows 7 SP1 or later (64-bit), x86-64 based.
  - MacOS.
  - Linux (64-bit).
  - Chrome OS (64-bit) with Linux (Beta) turned on.
- You must have some knowledge of Firebase like: authentication, firestore database,
  realtime database, storage, hosting, remote config.
- You must have a Google account to use the Firebase.

## Preview

### Website back-office 🌐

### Mobile application 📱

## Installing

### Firebase configuration

#### Step 1: Create the Firebase project.

##### Step 1.1

Create the project on [Firebase](https://console.firebase.google.com/).

##### Step 1.2

Enter a name for the project. After that check two options below. Finally, we click "Continue" button.

<!-- (Hình 1.2) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/1.2.png" />

##### Step 1.3

Enable Google Analytics for this project. Then we click "Continue" button.

<!-- (Hình 1.3) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/1.3.png" />

##### Step 1.4

We choose analytics location is "Vietnam". After that check two options below. Finally, we click "Create project" button.

<!-- (Hình 1.4) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/1.4.png" />

##### Step 1.5

After creating project, click "Continue" button to naviagte to project screen.

<!-- (Hinh 1.5) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/1.5.png" />

#### Step 2: Create an admin account

##### Step 2.1

We choose "Authentication" tab and click "Get started" button.

<!-- (hinh 2.1) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/2.1.png" />

##### Step 2.2

In the "Sign-in method" tab, we choose a "Email/Password" provider.

<!-- (hinh 2.2) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/2.2.png" />

##### Step 2.3 

We enable "Email/Password". Then we click "Save" button.

<!-- (hinh 2.3) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/2.3.png" />

##### Step 2.4

In the "Users" tab, we click "Add user" button. Then we enter the email box with the value "admin@elca.vn" 
and the password box with the optional password. Then we click "Add user" button.

<!-- (hình 2.4) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/2.4.png" />

##### Step 2.5

After creating an admin account, we copy the admin's UID.

<!-- (Hinh 2.5) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/2.5.png" />

#### Step 3: Add the admin account to Firestore database

##### Step 3.1

We choose "Firestore Database" tab. Then we click "Create database" button.

<!-- (Hinh 3.1) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/3.1.png" />

##### Step 3.2

After clicking create database, the pop-up will show. We choose "Start in production mode" as default. We will configure it later. 
Then we click "Next" button.

<!-- (Hinh 3.2) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/3.2.png" />

##### Step 3.3

We choose the cloud firestore location is "asia-southeast1". Then we click "Enable" button.

<!-- (Hinh 3.3) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/3.3.png" />

##### Step 3.4

In the "Rules" tab, we add this rule:

```php

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /accounts/{account}{
    	allow read, write: if request.auth != null;
    }
    
    match /events/{event}{
    	allow read: if true;
    	allow write: if request.auth != null;
    }
    
    match /games/{game}{
    	allow read: if true;
    	allow write: if request.auth != null;
    }
    
    match /prizes/{prize}{
    	allow read: if true;
    	allow write: if request.auth != null;
    }
    
    match /question_images/{question_image}{
    	allow read: if true;
    	allow write: if request.auth != null;
    }
    
    match /students/{student}{
    	allow read: if request.auth != null;
    	allow write: if true;
    }
    
    match /user_win_game/{winner}{
    	allow read, write: if true;
    }
  }
}

```

Then we click "Publish" button to save the changes.

<!-- (Hinh 3.6) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/3.6.png" />

##### Step 3.5

In the "Data" tab, we choose "Start collection" button. And we enter the collection ID box with the value "accounts". 
Then we click "Next" button.

<!-- (Hinh 3.4) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/3.4.png" />

##### Step 3.6

The admin's UID copied in the step 2.5 is filled out into the Document ID box. 
Then we add two fields:

```php

{
  "email": "admin@elca.vn",
  "is_admin": true
}

```

Then we click the "Save" button.

<!-- (hinh 3.5) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/3.5.png" />

#### Step 4: Add values to the Firestore database

##### Step 4.1

In Firebase project, please select project settings.

<!-- (Hinh 4.1) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/4.1.png" />

##### Step 4.2

We choose the "Service accounts" tab. Then we choose "Node.js" in the Admin SDK configuration snippet. 
After that we click the "Generate new private key" button.

<!-- (Hinh 4.2) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/4.2.png" />

##### Step 4.3

A pop-up will show. We click the "Generate key" button in the pop-up. Once downloaded, rename it "newserver.json".

<!-- (hinh 4.3) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/4.3.png" />

##### Step 4.4

We download this file: [backup.json](https://drive.google.com/file/d/1iypw0YHmpsRR9qTlLB_YqDOpHRo97YWj/view?usp=sharing). 
Put two files newserver.json and backup.json in the same directory.

##### Step 4.5

At this directory, we open the command line and type the command:

```php

npx -p node-firestore-import-export firestore-import -a newserver.json -b backup.json

```

<!-- (hinh 4.5) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/4.5.png" />

##### Step 4.6

We enter the "y" key to proceed with import.

<!-- (Hinh 4.6) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/4.6.png" />

#### Step 5: Configure Realtime database

##### Step 5.1

We choose the "Realtime Database" tab. Then we click the "Create Database" button.

<!-- (hinh 5.1) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/5.1.png" />

##### Step 5.2

We choose "Singapore (asia-southeast1)" in the Realtime Database location. Then we click the "Next" button.

<!-- (Hinh 5.2) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/5.2.png" />

##### Step 5.3 

We choose the "Start in locked mode" as default. We will configure it later. After that we click the "Enable" button.

<!-- (hinh 5.3) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/5.3.png" />

##### Step 5.4

In the "Rules" tab, we paste this value into the realtime database rules:

```php

{
  "rules": {
       "events":{
         ".read":true,
         "$event_id":{
           "lucky_games":{
             "$game_id":{
               "prizes":{
                 "$prize_id":{
                   "quantity": {
            					".read": true,
                        ".write":"newData.val() >= 0",
      							}
                 }
               }
             }
           },
           "rank_games":{
             "$game_id":{
               "$rank_id":{
                 "prizes":{
                   "$prize_id":{
                     "quantity": {
                        ".read": true,
                          ".write":"newData.val() >= 0",
                      }
                   }
                 }
               }
             }
           },
          "quiz_games":{
             "ranks":{
               "$rank_id":{
                 "prizes":{
                   "$prize_id":{
                     "quantity": {
                        ".read": true,
                          ".write":"newData.val() >= 0",
                      }
                   }
                 }
               }
             }
           },
         }
       },
      ".write": "auth.token!=null",
      ".read" : "auth.token!=null"
  },
}

```

Then we click the "Publish" button.

<!-- (Hinh 5.4) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/5.4.png" />

#### Step 6: Configure hosting in Firebase

##### Step 6.1 

In the "Hosting" tab, we click the "Get started" button.

<!-- (hinh 6.1) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/6.1.png" />

##### Step 6.2

In the "Set up Firebase Hosting" page, we click the "Next" button in the "Install Firebase CLI" step.

<!-- (Hinh 6.2) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/6.2.png" />

##### Step 6.3

We click the "Next" button in the "Initialize your project" step.

<!-- (Hinh 6.3) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/6.3.png" />

##### Step 6.4

We click the "Continue to console" button in the "Deploy to Firebase Hosting" step.

<!-- (Hinh 6.4) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/6.4.png" />

##### Step 6.5

In the "Firebase Hosting supports multiple sites" part, we click the "Add another site" button.

<!-- (Hinh 6.5) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/6.5.png" />

##### Step 6.6

We enter the back-office url to the box. Then we click the "Add site" button.

<!-- (Hinh 6.6) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/6.6.png" />

##### Step 6.7

We click the "Add another site" button and enter the game url to the box. Then we click the "Add site" button.

<!-- (hinh 6.7) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/6.7.png" />

#### Step 7: Configure Remote config

##### Step 7.1

We choose the "Remote Config" tab. Then we click the "Create configuration" button.

<!-- (hinh 7.1) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/7.1.png" />

##### Step 7.2

We enter the parameter name with the value "url_game_app" and data type is String. Then we enter the default value with the value "https://${YourMobileHostingURL}/#/event/"

```php

"url_game_app": "https://${YourMobileHostingURL}/#/event/"
Example: "https://jobfairmobileapp.web.app/#/event/"

```

Then we click the "Save" button.

<!-- (hinh 7.2) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/7.2.png" />

##### Step 7.3

We click the "Publish changes" button to save the changes.

<!-- (Hinh 7.3) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/7.3.png" />

In the Hosting tab, we choose "Add another site". Then we create 2 sites one for back-office, one for mobile app.

#### Step 8: Configure Analytics

If we do not enable Analytics when creating project, we can also enable it in "Analytics" tab.

#### Step 9: Add Firebase to the app

We choose the "Project Overview tab". Then we will add the corresponding app.

<!-- (hinh 9.1) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.1.png" />

##### Add Firebase to the Apple app

- In the "Register app" step, we enter the Apple bundle ID to the box. Then we click the "Register app" button.

<!-- (Hinh 9.2) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.2.png" />

- In the "Download config file" step, we click the "Download GoogleService-Info.plist" button. Then we click the "Next" button.

<!-- (Hinh 9.3) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.3.png" />

- In the "Add Firebase SDK" step, we click the "Next" button.

<!-- (Hinh 9.4) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.4.png" />

- In the "Add initialization code" step, we click the "Next" button.

<!-- (Hinh 9.5) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.5.png" />

- In the "Next steps" step, we click the "Continue to console" button.

<!-- (Hinh 9.6) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.6.png" />

##### Add Firebase to the Android app

- In the "Register app" step, we enter the Android package name to the box. Then we click the "Register app" button.

<!-- (Hinh 9.7) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.7.png" />

- In the "Download config file" step, we click the "Download google-services.json" button. Then we click the "Next" button.

<!-- (Hinh 9.8) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.8.png" />

- In the "Add Firebase SDK" step, we click the "Next" button.

<!-- (Hinh 9.9) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.9.png" />

- In the "Next steps" step, we click the "Continue to console" button.

<!-- (Hinh 9.10) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.10.png" />

##### Add Firebase to the Web admin app

- In the "Register app" step, we enter the App nickname to the box. Then we click the "Register app" button.

<!-- (Hinh 9.11) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.11.png" />

- In the "Add Firebase SDK" step, we click the "Continue to console" button.

<!-- (Hinh 9.12) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.12.png" />

##### Add Firebase to the Web game app

- In the "Register app" step, we enter the App nickname to the box. Then we click the "Register app" button.

<!-- (Hinh 9.13) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.13.png" />

- In the "Add Firebase SDK" step, we click the "Continue to console" button.

<!-- (Hinh 9.14) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/9.14.png" />

### Back-office project 🌐

#### Step 1

Run the following npm command to install the CLI or update to the latest CLI version.

```php

npm install -g firebase-tools

```

#### Step 2

Open a terminal window and navigate to or create a root directory for your web app.
- Sign in to Google:

```php

firebase login

```

- If you want to add a new account, we can use: 

```php

firebase login:add youremail@gmail.com

```

#### Step 3

We delete the ".firebase" folder, the ".firebaserc" file, the "firebase.json" file.

#### Step 4

- Run this command from your app’s root directory:

```php

firebase init

```

- "Are you ready to proceed?". We enter the "y" button key.
- "Which Firebase features do you want to set up for this directory?". We choose "Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys".
- If you have more than one account, you must choose one account to proceed.
- We choose the "Use an existing project" options.
- "Select a default Firebase project for this directory". We choose the corresponding firebase project.
- "What do you want to use as your public directory?". We enter with the value "build/web".
- "Configure as a single-page app (rewrite all urls to /index.html)?". We enter the "n" button key.
- "Set up automatic builds and deploys with GitHub?". We enter the "n" button key.
- "File build/web/index.html already exists. Overwrite?". We enter the "y" button key.

#### Step 5

In the Firebase, you choose the "Project settings" tab. Then you get the "Project ID". Then you choose "admin Web App" to get Firebase config.

<!-- (hinh admin 1.5) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/admin%201.5.png" />

#### Step 6

Update firebase information into "mobile-job-fair-app\back_office_web_app\lib\resources\constants.firebase_web_config.dart". Example information includes:

```php

const firebaseOption = FirebaseOptions(
    apiKey: "${YOUR-API-KEY}",
    authDomain: "${YOUR-AUTH-DOMAIN}",
    databaseURL: "${YOUR-DATABASE-URL}",
    projectId: "${YOUR-PROJECT-ID}",
    storageBucket: "${YOUR-STORAGE-BUCKET}",
    messagingSenderId: "${YOUR-MESSAGING-SENDER-ID}",
    appId: "${YOUR-APP-ID}",
    measurementId: "${YOUR-MEASUREMENT-ID}");

```

#### Step 7

To config hosting, we change the value in:

- "mobile-job-fair-app\back_office_web_app\firebase.json":

  ```php

  {
    "hosting": {
      "target": "backoffice",
      "public": "build/web",
      "ignore": [
        "firebase.json",
        "**/.*",
        "**/node_modules/**"
      ]
    }
  }

  ```

- "mobile-job-fair-app\back_office_web_app\\.firebaserc":

  ```php

  {
    "projects": {
      "default": "${FirebaseProjectID}"
    },
    "targets": {
      "${FirebaseProjectID}": {
        "hosting": {
          "backoffice": [
            "${UrlBackoffice}"
          ]
        }
      }
    }
  }

  Example:
  
  {
    "projects": {
      "default": "job-fair-elcavn"
    },
    "targets": {
      "job-fair-elcavn": {
        "hosting": {
          "backoffice": [
            "elcaadmin"
          ]
        }
      }
    }
  }

  ```

#### Step 8

Open a terminal window and navigate to or create a root directory for your web app. Then we build in web using command:

```php

flutter build web

```

#### Step 9

Open a terminal window and navigate to or create a root directory for your web app. Then we deploy the web using command:

```php

firebase deploy

```

For further information, please visit: https://firebase.google.com/docs/hosting/multisites?hl=en&authuser=0

### Mobile application project 📱

#### Step 1

Import android\app\google-services.json into android directory "mobile-job-fair-app\src\android\app\google-services.json".

#### Step 2

If we use windows OS, we can ignore this step.

##### Step 2.1

We open the "Runner.xcworkspace" file with Xcode IDE. Then we right click to the root, we choose the "Add Files to Runner". After that you choose the "GoogleService-Info.plist" file.

##### Step 2.2

We delete the "Podfile.lock" file in "mobile-job-fair-app-uit/src/ios" folder.

##### Step 2.3

Open a terminal window and navigate to or create a root directory for your web app. Then we enter the command:

```php

flutter pub get

```

##### Step 2.4

Open a terminal and navigate to a ios directory. Then we enter the command:

```php

pod install

```

##### Step 2.5

Close the project and open the "Runner.xcworkspace" file with Xcode IDE. Then we enter the "Bundle Identifier" with the value you register the app on Firebase. Then we build and run project in the iOS device.

<!-- (hinh ios) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/ios.png" />

#### Step 3

We delete the ".firebase" folder, the ".firebaserc" file, the "firebase.json" file.

#### Step 4

- Run this command from your app’s root directory:

```php

firebase init

```

- "Are you ready to proceed?". We enter the "y" button key.
- "Which Firebase features do you want to set up for this directory?". We choose "Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys".
- If you have more than one account, you must choose one account to proceed.
- We choose the "Use an existing project" options.
- "Select a default Firebase project for this directory". We choose the corresponding firebase project.
- "What do you want to use as your public directory?". We enter with the value "build/web".
- "Configure as a single-page app (rewrite all urls to /index.html)?". We enter the "n" button key.
- "Set up automatic builds and deploys with GitHub?". We enter the "n" button key.
- "File build/web/index.html already exists. Overwrite?". We enter the "y" button key.

#### Step 5

In the Firebase, you choose the "Project settings" tab. Then you get the "Project ID". Then you choose "game Web App" to get Firebase config.

<!-- (hinh game 1.5) -->
<img src="https://raw.githubusercontent.com/ThatPham2000/Elca-step-config/master/hind%20game%201.5.png" />

#### Step 6

Update firebase information into "mobile-job-fair-app\src\lib\resources\constants.firebase_web_config.dart". Example information includes:

```php

const firebaseOption = FirebaseOptions(
    apiKey: "${YOUR-API-KEY}",
    authDomain: "${YOUR-AUTH-DOMAIN}",
    databaseURL: "${YOUR-DATABASE-URL}",
    projectId: "${YOUR-PROJECT-ID}",
    storageBucket: "${YOUR-STORAGE-BUCKET}",
    messagingSenderId: "${YOUR-MESSAGING-SENDER-ID}",
    appId: "${YOUR-APP-ID}",
    measurementId: "${YOUR-MEASUREMENT-ID}");

```

#### Step 7

To config hosting, we change the value in:

- "mobile-job-fair-app\src\firebase.json":

  ```php

  {
    "hosting": {
      "target": "mobile",
      "public": "build/web",
      "ignore": [
        "firebase.json",
        "**/.*",
        "**/node_modules/**"
      ]
    }
  }

  ```

- "mobile-job-fair-app\src\\.firebaserc":

  ```php

  {
    "projects": {
      "default": "${FirebaseProjectID}"
    },
    "targets": {
      "${FirebaseProjectID}": {
        "hosting": {
          "mobile": [
            "${UrlMobileApp}"
          ]
        }
      }
    }
  }

  Example:
  
  {
    "projects": {
      "default": "job-fair-elcavn"
    },
    "targets": {
      "job-fair-elcavn": {
        "hosting": {
          "mobile": [
            "elcagame"
          ]
        }
      }
    }
  }

  ```

#### Step 8

Open a terminal window and navigate to or create a root directory for your web app. Then we build in web using command:

```php

flutter build web

```

#### Step 9

Open a terminal window and navigate to or create a root directory for your web app. Then we deploy the web using command:

```php

firebase deploy

```

## Contributors 🤝

<table>
  <tr>
    <td align="center"><a href="https://bitbucket.svc.elca.ch/users/phat"><img src="https://avatars.githubusercontent.com/u/57900109?v=4" width="100px;" alt=""/><br /><sub><b>PHAT</b></sub></a></td>
    <td align="center"><a href="https://bitbucket.svc.elca.ch/users/phav"><img src="https://avatars.githubusercontent.com/u/47874420?v=4" width="100px;" alt=""/><br /><sub><b>PHAV</b></sub></a></td>
  </tr>
</table>
<br/>
