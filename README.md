# Scroll Date Picker

A customizable and easy-to-use date picker library for Flutter. 

Compatible with Android & iOS & Web. :heart_eyes:

[![pub](https://img.shields.io/pub/v/scroll_date_picker)](https://pub.dev/packages/scroll_date_picker)


<br>

# Showcase

<img src = "https://user-images.githubusercontent.com/55150540/104117038-4df88d80-5361-11eb-9f93-8d6c3b99b50b.gif" width = 200> <img src = "https://user-images.githubusercontent.com/55150540/104117042-4fc25100-5361-11eb-8aaa-05ca8cf6aa6b.gif" width = 200>

<br> 

# Getting Started

In the pubspec.yaml of your flutter project, add the following dependency:

```yaml
dependencies:
  scroll_date_picker : "^lastest_version"
```

<br>

# Usage
Need to include the import the package to the dart file where it will be used, refer the below command
```dart
import 'package:scroll_date_picker/scroll_date_picker.dart';
```

<br>

# Complete example
```dart
import 'package:flutter/material.dart';
import 'package:scroll_date_picker/scroll_date_picker.dart';

void main() {
  runApp(MaterialApp(home: MyApp()));
}

class MyApp extends StatefulWidget {
  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  DateTime selectedDate = DateTime.now();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Scroll Date Picker Example"),
        centerTitle: true,
      ),
      body: Column(
        children: [
          Container(
            height: 150.0,
            alignment: Alignment.center,
            child: Text(
              "$selectedDate",
              style: TextStyle(fontSize: 20.0, fontWeight: FontWeight.w500),
            ),
          ),
          ScrollDatePicker(
            itemExtent: 45.0,
            minimumYear: 2010,
            maximumYear: 2050,
            initialDateTime: DateTime.parse("2020-05-01"),
            isLoop: false,
            locale: DatePickerLocale.ko_kr,
            selectedBoxDecoration: BoxDecoration(border: Border.all(color: Colors.blueAccent, width: 2.0)),
            onChanged: (value) {
              setState(() {
                selectedDate = value;
              });
            },
          ),
        ],
      ),
    );
  }
}

```
<br>

- `Controller` can now be used inside `outside the widget`
```dart

  late FixedExtentScrollController _yearController;
  late FixedExtentScrollController _monthController;
  late FixedExtentScrollController _dayController;

  DateTime _selectedDate = DateTime.now();

  int _minimumYear = 2010;
  int _maximumYear = 2050;

  @override
  void initState() {
    super.initState();
    _yearController = FixedExtentScrollController(
        initialItem: _selectedDate.year - _minimumYear);
    _monthController =
        FixedExtentScrollController(initialItem: _selectedDate.month - 1);
    _dayController =
        FixedExtentScrollController(initialItem: _selectedDate.day - 1);
  }

```

<br>

# License
```
Copyright 2020, the Flutter project authors. All rights reserved.

Redistribution and use in source and binary forms, with or without modification,
are permitted provided that the following conditions are met:

    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above
      copyright notice, this list of conditions and the following
      disclaimer in the documentation and/or other materials provided
      with the distribution.
    * Neither the name of Google Inc. nor the names of its
      contributors may be used to endorse or promote products derived
      from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON
ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```
