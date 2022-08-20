# flutter_d9_share_snapshot

- main.dart
```dart
import 'package:flutter/material.dart';
import 'package:screenshot/screenshot.dart';
import 'package:share/share.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatefulWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  State<StatefulWidget> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  final _screenshotController = ScreenshotController();

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Screenshot(
                controller: _screenshotController,
                child: Card(
                  child: Padding(
                    padding: const EdgeInsets.all(16),
                    child: Column(
                      children: [
                        Image.asset('images/codepassionately.png'),
                        const Text(
                          'Code Passionately',
                          style: TextStyle(
                              fontSize: 30, fontWeight: FontWeight.bold),
                        ),
                      ],
                    ),
                  ),
                ),
              ),
              TextButton(
                child: const Text('Take Screenshot and Share'),
                onPressed: _takeScreenshot,
              ),
            ],
          ),
        ),
      ),
    );
  }

  void _takeScreenshot() async {
    final imageFile = await _screenshotController.capture();
    print(imageFile!.path);
    // Share.shareFiles([imageFile.path], text: "Shared from #SexyFlutterApp");
  }
}
```

---

```
Copyright 2022 M. Fadli Zein
```