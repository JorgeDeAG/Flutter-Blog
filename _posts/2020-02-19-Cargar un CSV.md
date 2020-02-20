---
layout: post
title: Cargar un CSV
date: 2020-02-19 16:53:00
tags: flutter carga csv
author: jorge
---
Poner el CSV como asset en el fichero pubspec.yaml

```java
flutter:
  assets:
    - assets/datos.csv
```

Desde Flutter:

```java
Future<String> cargaAsset(String ruta) async {
   return await rootBundle.loadString(ruta);
}

void cargaCSV() {
  cargaAsset('assets/datos.csv').then((dynamic output) {
    csv = output;
  });
}
```
