---
layout: post
title: Animación 1 - Ejemplo de los círculos
date: 2020-02-14 23:29:00
tags: Animation circles example
author: jorge
---
Partiendo del ejemplo <a href="https://dartpad.dartlang.org/40308e0a5f47acba46ba62f4d8be2bf4" target="_blank">"Implicit animations" en DartPad</a>

Importamos la librería dart:async

```java
import 'dart:async';
```

Añadimos un temporizador al final del método initState():

```java
    Timer.periodic(Duration(milliseconds: 1350), (timer) {
      setState(() {
        _makeDiscs();
      });
    });
```

Cambiamos la duración a 900 milisegundos y la curva de aimación a bounceOut de AnimatedAlign:

```java
              AnimatedAlign(
                duration: Duration(milliseconds: 900),
                curve: Curves.bounceOut,
```

Y la duración a 900 milisegundos y añadimos una curva de aimación bounceIn a AnimatedContainer:

```java
              AnimatedContainer(
                  curve: Curves.bounceIn,
                  duration: Duration(milliseconds: 900),
```

Por útimo, aunque no he eliminado el evento onTap, he cambiado el texto "Click a disc!" por "¡Discos locos!"

```java
            child: Text(
              '¡Discos locos!',
              style: TextStyle(color: Colors.white, fontSize: 50),
            ),
```


El código quedaría así (podéis copiarlo diréctamente en <a href="https://dartpad.dartlang.org" >DartPad</a> y ejecutarlo):

```java
import 'package:flutter/material.dart';
import 'dart:math';
import 'dart:async';

class DiscData {
  static final _rng = Random();

  double size;
  Color color;
  Alignment alignment;

  DiscData() {
    color = Color.fromARGB(
      _rng.nextInt(200),
      _rng.nextInt(255),
      _rng.nextInt(255),
      _rng.nextInt(255),
    );
    size = _rng.nextDouble() * 40 + 50;
    alignment = Alignment(
      _rng.nextDouble() * 2 - 1,
      _rng.nextDouble() * 2 - 1,
    );
  }
}

void main() async {
  runApp(
    MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        body: Container(
          color: Color(0xFF15202D),
          child: SizedBox.expand(
            child: VariousDiscs(50),
          ),
        ),
      ),
    ),
  );
}

class VariousDiscs extends StatefulWidget {
  final numberOfDiscs;

  VariousDiscs(this.numberOfDiscs);

  @override
  _VariousDiscsState createState() => _VariousDiscsState();
}

class _VariousDiscsState extends State<VariousDiscs> {
  final _discs = <DiscData>[];

  @override
  void initState() {
    super.initState();
    _makeDiscs();
    Timer.periodic(Duration(milliseconds: 1350), (timer) {
      setState(() {
        _makeDiscs();
      });
    });
  }

  void _makeDiscs() {
    _discs.clear();
    for (int i = 0; i < widget.numberOfDiscs; i++) {
      _discs.add(DiscData());
    }
  }

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: () => setState(() {
        _makeDiscs();
      }),
      child: Stack(
        children: [
          Center(
            child: Text(
              '¡Discos locos!',
              style: TextStyle(color: Colors.white, fontSize: 50),
            ),
          ),
          for (final disc in _discs)
            Positioned.fill(
              child: AnimatedAlign(
                duration: Duration(milliseconds: 900),
                curve: Curves.bounceOut,
                alignment: disc.alignment,
                child: AnimatedContainer(
                  curve: Curves.bounceIn,
                  duration: Duration(milliseconds: 900),
                  decoration: BoxDecoration(
                    color: disc.color,
                    shape: BoxShape.circle,
                  ),
                  height: disc.size,
                  width: disc.size,
                ),
              ),
            ),
        ],
      ),
    );
  }
}

```
