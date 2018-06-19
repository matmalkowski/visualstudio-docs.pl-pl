---
title: Używanie metody bind (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d185801cc5bba355751147edb79b9c47d21f8eed
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2018
ms.locfileid: "28987870"
---
# <a name="using-the-bind-method-javascript"></a>Używanie metody bind (JavaScript)
Kod JavaScript `bind` metoda ma kilka zastosowań. Zazwyczaj służy do zachowania kontekstu wykonania dla funkcji, która jest wykonywana w innym kontekście. `bind`Tworzy nową funkcję, która ma tego samego treść funkcji oryginalnego. Pierwszy argument przekazany do `bind` określa wartość `this` — słowo kluczowe w powiązanej funkcji. Można również przekazać dodatkowe, opcjonalne argumenty `bind`. Przykłady dodatkowe funkcje, zobacz [bind — metoda (funkcja)](../../javascript/reference/bind-method-function-javascript.md). Na przykład za pomocą `bind` częściowo zastosować funkcji, zobacz [programowania asynchronicznego wzorców i wskazówek w języku JavaScript Hilo (w Sklepie Windows)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx).  
  
## <a name="preserving-the-execution-context-using-bind"></a>Zachowywanie kontekstu wykonania za pomocą bind  
 `bind` Funkcja jest często używana podczas dodawania odbiorników zdarzeń. W poniższym przykładzie kodu `bind` jest używane w celu zachowania kontekst bieżącego obiektu (`DataObject`). Obiekt danych jest przekazywany do `bind` za pomocą `this` — słowo kluczowe, która zapewnia dostęp do właściwości obiektu danych i funkcji podczas obsługi zdarzeń (`dataReadyHandler`) działa. Aby zilustrować jak `bind` działa, ten kod tworzy niestandardowe zdarzenie.  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 Jeśli możesz przekształcić w komentarz wiersz kodu, który używa `bind`, usuń znaczniki komentarza wiersza kodu, który wywołuje `addEventListener` bez `bind`, a następnie ponownie uruchom kod, `dataReadyHandler` funkcja zakończy się niepowodzeniem. Na przykład w `dataReadyHandler`, `this.name` jest niezdefiniowana, i `this.data()` spowoduje błąd, ponieważ `this` obiektu nie odwołuje się do obiektu danych.  
  
## <a name="see-also"></a>Zobacz też  
 [bind, metoda (Function)](../../javascript/reference/bind-method-function-javascript.md)
