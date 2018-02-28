---
title: "Używanie metod asynchronicznych środowiska wykonawczego systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime asynchronous methods
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 215a04a2f3f875743a7fbf910a3a565cf34fb558
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="using-windows-runtime-asynchronous-methods"></a>Używanie metod asynchronicznych środowiska wykonawczego systemu Windows
Wiele metod środowiska wykonawczego systemu Windows, zwłaszcza tych metod, co może zająć dużo czasu, są asynchroniczne. Te metody zwracają zazwyczaj operacji lub akcja asynchroniczna (na przykład `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress`, lub `Windows.Foundation.IAsyncOperationWithProgress`). Te metody są reprezentowane w języku JavaScript za [CommonJS/ze zobowiązania/A](http://go.microsoft.com/fwlink/p/?LinkId=244434) wzorca. Oznacza to, że oba operatory zwracają obiekt Promise, który ma [następnie](https://msdn.microsoft.com/en-us/library/windows/apps/br229728.aspx) funkcja, dla której należy podać `completed` funkcja obsługująca wynik, jeśli operacja zakończy się powodzeniem. Jeśli nie chcesz zapewnić program obsługi błędów, należy użyć [gotowe](https://msdn.microsoft.com/en-us/library/windows/apps/hh701079.aspx) funkcji zamiast `then` funkcji.  
  
> [!IMPORTANT]
>  Funkcje środowiska wykonawczego systemu Windows nie są dostępne dla aplikacji, które są uruchamiane w programie Internet Explorer.  
  
## <a name="examples-of-asynchronous-methods"></a>Przykłady metod asynchronicznych  
 W poniższym przykładzie `then` funkcja przyjmuje parametr, który reprezentuje wartość ukończone `createResourceAsync` metody.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 W tym przypadku jeśli `createResourceAsync` metoda kończy się niepowodzeniem, to zwraca obietnicę w stanie błędu, ale nie zgłasza wyjątek. Błąd można obsługiwać przy użyciu `then` działają w następujący sposób.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Jeśli nie chcesz jawnie obsługi błędu, ale chce, aby zgłosić wyjątek, możesz użyć `done` zamiast tego działania.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 Można również wyświetlić postęp dokonany w kierunku ukończenia za pomocą funkcji trzecich.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 Aby uzyskać więcej informacji na temat programowania asynchronicznego, zobacz [asynchronicznego programowania w języku JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [W języku JavaScript za pomocą środowiska wykonawczego systemu Windows](../jswinrt/using-the-windows-runtime-in-javascript.md)