```run-dartpad:theme-light:mode-flutter:split-60:width-100%:height-500px
{$ begin main.dart $}
import 'dart:async';
import 'package:flutter/material.dart';

class BouncingBallDemo extends StatefulWidget {
  _BouncingBallDemoState createState() => _BouncingBallDemoState();
}

class _BouncingBallDemoState extends State<BouncingBallDemo> {
  double marginTop;

  void changePosition(Timer t) async {
    setState(() {
      marginTop = marginTop == 0 ? 100 : 0;
    });
  }

  void initState() {
    super.initState();
    marginTop = 0;
    new Timer.periodic(const Duration(seconds: 1), changePosition);
  }

  @override
  Widget build(BuildContext context) {
    return Container(
      margin: EdgeInsets.only(top:marginTop),
        child: Container(
      decoration: BoxDecoration(
        shape: BoxShape.circle,
        color: Colors.green,
      ),
      width: 40.0,
      height: 40.0,
    ));
  }
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        body: Center(
          child: BouncingBallDemo(),
        ),
      ),
    );
  }
}

Future<void> main() async {
  runApp(
    MyApp(),
  );
}
{$ end main.dart $}
```