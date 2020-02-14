---
layout: post
title: Detectar Plataforma (Android / IOS)
date: 2020-02-01 00:40:00
tags: plataforma android ios
author: jorge
---
Importar **dart:io**

```java
import 'dart:io' show Platform;
```

Utilizar **Platform**

```java
Platform.isIOS?"IOS":"Android";
```