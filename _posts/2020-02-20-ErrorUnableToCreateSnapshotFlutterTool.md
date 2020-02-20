---
layout: post
title: Error: Unable to create dart snapshot for flutter tool.
date: 2020-02-20 13:49:00
tags: error fluttertool snapshot
author: jorge
---
Ejecutar las siguientes líneas desde el directorio de instalación de Flutter:

```java
git clean -xfd
git stash save --keep-index
git stash drop
git pull
flutter doctor
```
