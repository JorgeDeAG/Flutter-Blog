---
layout: post
title: Inicio rápido
date: 2020-01-31 12:00:00
tags: instalación quickstart ejemplo
author: jorge
---
Instala Flutter <a href="https://flutter.dev/docs/get-started/install" target="_blank">Flutter &gt; Docs &gt; Get started &gt; Install</a>

Crear un proyecto y ejecútalo

#### Android Studio:
Crear proyecto:
**File -&gt; New -&gt; New Flutter Project... -> Flutter Application**


<amp-img src="{{ site.baseurl }}assets/images/play.png" width="56" height="23" layout="fixed" alt="" class="mb3"></amp-img>Ejecuta el proyecto **(Shift + F10)**:
**Run -&gt; Run 'main.dart'**  

El código que se ejecuta, está en **'lib/main.dart'** (es el punto de entrada por defecto)

La única funcionalidad del ejemplo se encuentra en el **FAB (Floating Action Button)**
```java
floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ), 
```

**(Ctrl - B)** Para ir a la definición de _incrementCounter

setState indica al Framework de Flutter que algo ha cambiado en el estado, lo que provoca que se vuelva a ejecutar el método build para que la pantalla pueda reflejar los valores actualizados. Si cambiasemos _counter sin llamar a SetState, el cambio no se redibujaría.

```java
  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }
```

Lo que hay dentro de setState() es una **función anónima**.
```java
(){
  _counter++;
}
```

Podemos pasar también por referencia el nombre de cualquier función (la función sin los paréntesis)
```java
  void _incrementCounter() {
    setState(incCont);
  }

  incCont(){
    _counter++;
  }
```



El ejemplo se puede crear y ejecutar también desde línea de comandos:
```shell
 $ flutter create myapp
 $ cd myapp
 $ flutter run
```

#### Operador **=>**

```java
void main() => runApp(MyApp());
```
Se utiliza cuando la función devuelve un único valor. **Es lo mismo que poner**:
```java
void main() {
  return runApp(MyApp());
}
```


<!--hr />

### Image With Heading
<figure class="ampstart-image-with-heading  m0 relative mb4">
<amp-img src="{{ site.baseurl }}assets/images/shiva.jpg" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<figcaption class="absolute right-0 bottom-0 left-0">
<header class="ampstart-image-heading px2 py2 line-height-4"><h1>Shiva</h1></header>
</figcaption>
</figure>

<hr/>

### Image With Caption
<figure class="ampstart-image-with-caption m0 relative mb4">
<amp-img src="{{ site.baseurl }}assets/images/shiva.jpg" width="656" height="400" layout="responsive" alt="" class="mb3"></amp-img>
<figcaption class="h5 mt1 px3">Duis nec dolor et quam vulputate sagittis. Nam arcu ex, suscipit nec cursus a, volutpat sit amet felis.
<span class="ampstart-image-credit block bold">
Taken by
<a href="#" role="author">Parvati</a>
</span>
</figcaption>
</figure>

<hr/>

### Video

Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

<amp-youtube width="480"
  height="270"
  layout="responsive"
  data-videoid="lBTCB7yLs8Y">
</amp-youtube>

<hr />

### Audio

Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

<amp-audio width="auto"
  height="50"
  src="https://ia801402.us.archive.org/16/items/EDIS-SRP-0197-06/EDIS-SRP-0197-06.mp3">
  <div fallback>
    <p>Your browser doesn’t support HTML5 audio</p>
  </div>
</amp-audio-->
