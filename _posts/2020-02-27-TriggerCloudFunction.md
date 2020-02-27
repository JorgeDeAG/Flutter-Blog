---
layout: post
title: Trigger Cloud Function
date: 2020-02-27 16:41:00
tags: cloud_function trigger
author: jorge
---
Cloud Function (estilo Trigger) para incrementar o decrementar un contador y con el número de documentos almacenados en una colección de Cloud Firestore

```java
export const triggerEscritura = 
    functions.firestore.document('coleccion/{idDocumento}')
    .onWrite((change, context) => {
		if (!change.before.exists) {
			// Nuevo documento: sumar uno al contador
			db.doc(docRef).update({nroDocumentos: FieldValue.increment(1)});
			
		} else if (change.before.exists && change.after.exists) {
			// Documento ya existía: No hacer nada
			
		} else if (!change.after.exists) {
			// Eliminación de documento: restar uno al contador
			db.doc(docRef).update({nroDocumentos: FieldValue.increment(-1)});
		}
		return;
	});
```
