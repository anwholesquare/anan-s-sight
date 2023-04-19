---
title: "Flutter Login With Google | Apple | Email / Password with Firebase and FlutterFire CLI"
seoTitle: "Flutter Login With Google | Apple | Email / Password with Firebase and"
seoDescription: "This tutorial or guide demonstrates how to implement a login system in a Flutter application using popular authentication methods like Google Sign-In, Apple"
datePublished: Wed Apr 19 2023 01:02:31 GMT+0000 (Coordinated Universal Time)
cuid: clgmzojqm00050aky6b2o6sg8
slug: flutter-login-with-google-apple-email-password-with-firebase-and-flutterfire-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681860784943/e1e842f1-a6f3-4142-a7d2-638575a9bcb1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1681866115116/0c4fa3e4-32c1-40dd-b2ec-e0ab50b0e2ef.png
tags: firebase, flutter, firebaseauth, signinwithapple, flutterfire

---

This tutorial or guide demonstrates how to implement a login system in a Flutter application using popular authentication methods like Google Sign-In, Apple Sign-In, and traditional Email/Password authentication. The tutorial also showcases how to leverage Firebase Authentication and FlutterFire CLI to build the authentication logic, including handling user sign-in and sign-out. This comprehensive guide can be useful for Flutter developers looking to integrate a secure and efficient user authentication mechanism in their applications.

### Demo

%[https://youtube.com/shorts/TtO8PIuA4o0?feature=share] 

### List of commands

1. Download the [Firebase CLI](https://firebase.google.com/docs/cli#setup_update_cli)
    
2. Open VSCode and create a new flutter project using this command:
    
    ```apache
    flutter create --org com.khandokeranan -i swift -a kotlin app_name
    ```
    
3. Now run VSCode current folder terminal
    
    ```apache
    firebase login
    dart pub global activate flutterfire_cli
    flutterfire configure
    ```
    
4. FlutterFire automatically configures the project and extra layers of security for you. Now, add this line if you want to use the google\_sign\_in system to `ios/Runner/Info.plist.`
    
    ```apache
    <key>CFBundleURLTypes</key>
    	<array>
    		<dict>
    			<key>CFBundleTypeRole</key>
    			<string>Editor</string>
    			<key>CFBundleURLSchemes</key>
    			<array>
                    # you will find the code in ios/Runner/GoogleService-Info.plist -> REVERSED_CLIENT_ID
    				<string>com.googleusercontent.apps.128343086777-lo0d43u57fbc6irsvp719ne025ok8a2g</string>
    			</array>
    		</dict>
    	</array>
    ```
    
5. Now enable Google or other sign-in methods. Please visit the Firebase console and enable it.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681861530332/5b3e7e8c-7476-4996-b4ec-0727773ec216.png align="center")
    
6. We need to add the SHA-1 and SHA-256 string to the Firebase for Android.  
    Now right-click on gradlew under the android folder of the project folder and click ‘open in terminal’ and run this command:
    
    ```bash
    gradlew signingReport
    ```
    
7. Now you can implement login features with these plugins:
    
    ```yaml
      firebase_core: ^2.9.0
      firebase_auth: ^4.4.1
      google_sign_in: ^6.1.0
    ```
    

### Flutter Dart codes for the signing flow

```dart
import 'package:firebase_auth/firebase_auth.dart';
import 'package:google_sign_in/google_sign_in.dart';
import 'package:flutter/material.dart';

class AuthService {

  signInWithGoogle () async {
    final GoogleSignInAccount? user = await GoogleSignIn().signIn();
    if (user == null) return; 
    final GoogleSignInAuthentication auth = await user.authentication;
    final credential = GoogleAuthProvider.credential(
      idToken: auth.idToken,
      accessToken: auth.accessToken
    );
    return await FirebaseAuth.instance.signInWithCredential(credential); 
  }

  void userSignOut() {
    FirebaseAuth.instance.signOut();
  }

  void signUserInWithEmailPass(String email, String pass, BuildContext context) async{
    showDialog(context: context, builder: (context) {
        return const Center(child: CircularProgressIndicator());
    });
    try{
      await FirebaseAuth.instance.signInWithEmailAndPassword(email: email, password: pass);
    } catch (e) {
      Navigator.pop(context);
      ScaffoldMessenger.of(context).showSnackBar(const SnackBar(content: Text("Please use the correct username/password or login with Google or Apple id.")));
    }
  }


  void signUserUpWithEmailPass(String email, String pass) async {
      showDialog(context: context, builder: (context) {
        return const Center(child: CircularProgressIndicator());
      });
      try {
      final credential = await FirebaseAuth.instance.createUserWithEmailAndPassword(
        email: email,
        password: pass,
      );
    } on FirebaseAuthException catch (e) {
      if (e.code == 'weak-password') {
        ScaffoldMessenger.of(context).showSnackBar(const SnackBar(content: Text("The password provided is too weak.")));
      } else if (e.code == 'email-already-in-use') {
        ScaffoldMessenger.of(context).showSnackBar(const SnackBar(content: Text("The account already exists for that email.")));
      }
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(const SnackBar(content: Text("Something went wrong. please try again with proper internet connection and strong password")));
    }
  }

  // Before you begin, configure Sign In with Apple and enable Apple as a sign-in provider.
  // Next, make sure that your Runner apps have the "Sign in with Apple" capability.
  // Link : https://firebase.google.com/docs/auth/ios/apple#configure-sign-in-with-apple
  // Link for enabling apple provider: https://firebase.google.com/docs/auth/ios/apple#enable-apple-as-a-sign-in-provider
  signInWithApple() async {
    final appleProvider = AppleAuthProvider();
    await FirebaseAuth.instance.signInWithProvider(appleProvider);
  }
}
```

### Important: Read this carefully

<mark>Sign-in with Apple must be implemented if you are using any social media authentication providers to publish the app in Apple App Store.</mark>

To use the sign-in with Apple, you need to subscribe Apple Developer Program (PAID) and go through these links to implement the feature:  
[*Configure Sign In with Apple*](https://firebase.google.com/docs/auth/ios/apple#configure-sign-in-with-apple) *and* [*enable Apple as a sign-in provider*](https://firebase.google.com/docs/auth/ios/apple#enable-apple-as-a-sign-in-provider)*. Make sure that your* `Runner` *apps have the "Sign in with Apple" capability.*  
  
*For Google sign-in flow, make sure that ios/runner has a file named* `GoogleService-Info.plist` and android/app has a file named `google-services.json`

If you are using Github public repository for the source control system, add these lines in `gitignore` to prevent using the files by others.

```bash
# Firebase Credentials
/android/app/google-services.json
/ios/Runner/GoogleService-Info.plist
```

### Github link

GitHub link: [https://github.com/anwholesquare/firebase\_google\_apple\_emailpass\_auth\_flutter\_flutterfire](https://github.com/anwholesquare/firebase_google_apple_emailpass_auth_flutter_flutterfire)