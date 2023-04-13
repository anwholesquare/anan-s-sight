---
title: "Flutter Fast Implementation: Forms Building,
and Sign Up Page Widgets"
datePublished: Thu Apr 13 2023 04:09:35 GMT+0000 (Coordinated Universal Time)
cuid: clgelq0ju000b09l90gyo3jlv
slug: flutter-fast-implementation-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681356163798/9aeb81e2-6098-4b2a-a4ae-9cfaa727c01a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1681358875188/cb833c7d-679b-4560-9b60-40976122af3c.png
tags: flutter, mobile-development, flutter-examples, flutter-widgets, signup-page

---

Here is the UI that we want to build ultimately in this blog.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681357013086/d6a59615-0afb-4dfe-81da-088f0db29d9a.png align="center")

### Required Flutter packages

Open pubspec.yaml and add these packages under dependencies:

```yaml
dependencies:
  flutter:
    sdk: flutter
  # add these packages in your flutter project first
  google_fonts:
  shared_preferences:
  intl:
  sign_button:
```

**Google Fonts** is used for custom fonts. **Shared Preferences**, this package is used for storing small data such as current\_theme\_mode, is\_user\_logged\_in, etc. **Intl** is widely used to convert DateTime to our desired date string. The **Sign\_button** package is used to design social media login buttons with proper design guidelines.

### Import Necessary Assets

To use local assets, we must add this line to the pubspec.yaml: assets:

```yaml
flutter:
  uses-material-design: true  
# add this line and create a new folder named assets and inside the folder, create another folder named images
  assets:
    - assets/images/
```

I have saved a .gif image named 'boring.gif' inside the folder named 'images.' The link to the file is [HERE](https://github.com/anwholesquare/uPromise/blob/2547cfccfb85ae555423d1b0661f18b097b871d7/assets/images/boring.gif).

### Import dart files to main.dart

For the project, we need these importations inside the **main.dart** file:

```dart
// ignore_for_file: prefer_const_constructors
import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';
import 'package:intl/intl.dart';
import 'package:http/http.dart' as http;
import 'dart:convert';
import 'package:sign_button/sign_button.dart';
```

### Widgets we need to use

The list of widgets we will use:

1. HomePage
    
    1. DropdownButtonFormField
        
    2. TextFormField
        
    3. showDatePicker()
        
    4. ElevatedButton
        
    5. Others: Container, Column, Material, Scaffold, Center, Row, Icon, Text, BoxDecoration, Navigator.push(), SizedBox, Padding, SingleChildListView, Flexible
        
2. ThankYouPage
    
    1. Image.asset
        
    2. Text
        
    3. Scaffold
        

### Full main.dart code

```dart
// ignore_for_file: prefer_const_constructors

import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';
import 'package:intl/intl.dart';
import 'package:http/http.dart' as http;
import 'dart:convert';
import 'package:sign_button/sign_button.dart';

void main () {
    runApp(MyApp());
}

class MyApp extends StatefulWidget {
  const MyApp({super.key});

  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  int appColor = 3;
  void update (int status, dynamic data) {
      if (status == 1 && data is int) {
        appColor = data % 4;
        setState(() {});
      }
  }
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        theme: ThemeData(
            primarySwatch: appColor == 3 ? Colors.blue : appColor == 2 ? Colors.green : Colors.red,
            fontFamily: GoogleFonts.poppins().fontFamily
        ),
        debugShowCheckedModeBanner: false,
        home: HomePage(updateMyApp: update)

    );
  }
}

class HomePage extends StatefulWidget {
  final void Function (int, dynamic)? updateMyApp;
  const HomePage({super.key, required this.updateMyApp});

  @override
  State<HomePage> createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  String dob = DateFormat.yMd().format (DateTime.now());
  List<DropdownMenuItem<String>> countries = [DropdownMenuItem(child: Text("No Country"))];
  String? selectedCountry;
  bool _isChecked = true;
  int appColor = 3;

  Widget TextBox (String label, String hint, {bool security = false}) => TextField(
    obscureText: security,
    decoration: InputDecoration (
      labelText: label,
      hintText: hint,
      prefixIcon:  Icon (security ? Icons.pin : Icons.person),
      border: UnderlineInputBorder()
    )
  );

  void getCountries () async {

    final response = await http.get(Uri.parse("https://raw.githubusercontent.com/anwholesquare/form-building-json/main/countries.json"));
    countries = [DropdownMenuItem(child: Text("No Country"))];
    if (response.statusCode == 200) {
        var cntr = json.decode(response.body);
        for (dynamic k in cntr) {
            String nText = k["text"].toString();
            countries.add(DropdownMenuItem(value: k["value"], child: Text(nText)));
        }
        setState(() {
          
        });
    }
  }

  @override
  void initState() {
    super.initState();
    getCountries();
  }

  @override
  Widget build(BuildContext context) {
    return Material(
      child:SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(24),
          child: Container(
              width: double.infinity,
              child: SingleChildScrollView(
                  child: Column (children: [
                      Row (children: [
                        Icon(Icons.arrow_back_ios_new_rounded),
                        SizedBox(height:20),
                        Text("Coursido Login", style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold) )
                       ],),
                       SizedBox(height: 20,),
                       TextBox("Email", "Enter Email Address"),
                       SizedBox(height: 20,),
                       Row (children: [
                          Flexible (
                            flex:4,
                            child: 
                          DropdownButtonFormField<String>(
                              items: countries,
                              isExpanded: true,
                              onChanged: (String? ne) {
                                debugPrint(ne);
                              },
                              decoration: InputDecoration(
                                labelText: "Country",
                                prefixIcon: Icon(Icons.public_rounded)
                              ),

                          ),),
                          SizedBox(width: 5,),
                          Flexible(
                            flex:3,
                            child: TextFormField(
                              onTap:() async {
                                  final DateTime? pickDate = await showDatePicker(context: context, initialDate: DateTime.now(), firstDate: DateTime(1900), lastDate: DateTime.now());

                                  if (pickDate != null) {
                                      setState(() {
                                        dob = DateFormat.yMd().format(pickDate);
                                      });
                                  }
                              },
                              readOnly: true,
                              controller: TextEditingController(text:dob),
                              decoration: InputDecoration(
                                labelText: "Date of Birth",
                                prefixIcon: Icon(Icons.calendar_month_sharp),
                                border: UnderlineInputBorder()
                              )
                            )
                          )

                       ],),
                      SizedBox(height:20),
                      TextBox(security: true, "PIN", "Enter PIN"),
                      SizedBox(height: 20,),
                      Row (children: [
                        Checkbox(
                          value: _isChecked,
                          onChanged: (val) => setState(() {
                            _isChecked = val!;
                          }),
                        ),
                        SizedBox(width: 10,),
                        Text("I agree with terms and conditions")


                      ],),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          InkWell(
                            onTap: () => setState(() {
                              appColor = 1; widget.updateMyApp!(1, appColor);
                            }),
                            child: Container (
                              height: 32,
                            width: 32,
                            decoration: BoxDecoration(shape:BoxShape.circle, color: Colors.red),
                            child: (appColor == 1) ? Icon(Icons.check_rounded, color: Colors.white,) : null,
                            
                            ),
                          ),
                          SizedBox(width: 10,),
                          InkWell(
                            onTap: () => setState(() {
                              appColor = 2; widget.updateMyApp!(1, appColor);
                            }),
                            child: Container (
                              height: 32,
                            width: 32,
                            decoration: BoxDecoration(shape:BoxShape.circle, color: Colors.green),
                            child: (appColor == 2) ? Icon(Icons.check_rounded, color: Colors.white,) : null,
                            
                            ),
                          ),
                          SizedBox(width: 10,),
                          InkWell(
                            onTap: () => setState(() {
                              appColor = 3; widget.updateMyApp!(1, appColor);
                            }),
                            child: Container (
                              height: 32,
                            width: 32,
                            decoration: BoxDecoration(shape:BoxShape.circle, color: Colors.blue),
                            child: (appColor == 3) ? Icon(Icons.check_rounded, color: Colors.white,) : null,
                            
                            ),
                          ),
                          
                          
                        ]
                      ),
                      SizedBox(height: 20,),
                      Center (child: ElevatedButton(
                        onPressed: () {
                          Navigator.push(context, MaterialPageRoute(builder: (context) => ThankYouPage()));
                        },
                        child: Text("Create a New Account")
                      ),),
                      SizedBox(height: 20,),
                      Center(child: Text("OR",style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),),),
                      SizedBox(height: 20,),
                      Center(
                        child: SignInButton(buttonType: ButtonType.google, buttonSize: ButtonSize.small,
                        onPressed: () {
                          Navigator.push(context, MaterialPageRoute(builder: (context) => ThankYouPage()));
                        },
                        ),
                      )


                  ],)
              ),
            ),
        )
      )
      
    );
  }
}


class ThankYouPage extends StatelessWidget {
  const ThankYouPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Coursido")),
      body: Center(child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        crossAxisAlignment: CrossAxisAlignment.center,
        children: [
          Image.asset("assets/images/boring.gif", height: 300,),
          SizedBox(height: 20,),
          Text("Thank you for the registration", style: TextStyle(fontWeight: FontWeight.bold),)

      ],)),
    );
  }
}
```

### Youtube Fast Flutter Implementation

%[https://www.youtube.com/watch?v=BshcEvl3pzw] 

### Project GitHub link

[https://github.com/anwholesquare/flutter-testdesign/tree/680d8d52a2a71ee1daec099bc5629073e71a62c7](https://github.com/anwholesquare/flutter-testdesign/tree/680d8d52a2a71ee1daec099bc5629073e71a62c7)