---
layout: post
title: Preferencias compartidas (shared_preferences)
date: 2020-01-31 12:15:00
tags: plugin shared_preferences
author: jorge
---
Añadir **shared_preferences** como dependencia en el fichero **pubspec.yaml** (carpeta raíz del proyecto)
```java
dependencies:
  flutter:
    sdk: flutter
  shared_preferences:
```
(Al no dejar fijo un número de versión **shared_preferences: ^0.5.6+1**, la dependencia se actualizará a la última versión cada vez que descarguemos las dependencias)

  

Ejecutar **Tools -&gt; Flutter -&gt; Flutter Packages Get**

Importar el nuevo paquete en el código:

```java
import 'package:shared_preferences/shared_preferences.dart';
```

Y modificar el código de la aplicación de ejemplo de la siguiente forma:
```java
class _MyHomePageState extends State<MyHomePage> {
  int _counter = -1;

  void getCounter() async {
    _counter = (await SharedPreferences.getInstance()).getInt('counter') ?? 0;
    setState((){});
  }

  void _incrementCounter() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    _counter = (prefs.getInt('counter') ?? 0) + 1;
    await prefs.setInt('counter', _counter);
    setState(() {
      print('Pressed $_counter times.');
    });
  }
  @override
  void initState() {
    getCounter();
    super.initState();
  }

```

El código completo quedaría así:
```java
import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';

void main() {
  return runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = -1;

  void getCounter() async {
    _counter = (await SharedPreferences.getInstance()).getInt('counter') ?? 0;
    setState((){});
  }

  void _incrementCounter() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    _counter = (prefs.getInt('counter') ?? 0) + 1;
    await prefs.setInt('counter', _counter);
    setState(() {
      print('Pressed $_counter times.');
    });
  }
  @override
  void initState() {
    getCounter();
    super.initState();
  }
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'You have pushed the button this many times:',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.display1,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}
```