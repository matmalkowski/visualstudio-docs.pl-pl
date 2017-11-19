---
title: "Obsługa zdarzeń środowiska wykonawczego systemu Windows w języku JavaScript | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Obsługa zdarzeń środowiska wykonawczego systemu Windows w języku JavaScript
Zdarzenia środowiska uruchomieniowego systemu Windows nie są reprezentowane w taki sam sposób, w języku JavaScript, jak w języku C++ i .NET Framework. Nie są właściwościami klasy, ale raczej są reprezentowane jako identyfikatory ciągów, które są przekazywane do klasy `addEventListener` i `removeEventListener` metody. Na przykład można dodać obsługi zdarzeń dla [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) zdarzenia przez przekazanie do ciągu "positionchanged" `Geolocator.addEventListener` metody:  
  
```JavaScript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Można również ustawić `locator.onpositionchanged` właściwości.  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 W języku JavaScript argumenty zdarzenia środowiska uruchomieniowego systemu Windows są reprezentowane jako obiekt pojedynczego zdarzenia. W poniższym przykładzie metoda obsługi zdarzeń `ev` parametr jest obiekt, który zawiera nadawcy (właściwość target) i inne argumenty zdarzeń. Argumenty zdarzeń są te, które są udokumentowane dla każdego zdarzenia.  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Funkcje środowiska wykonawczego systemu Windows nie są dostępne dla aplikacji, które są uruchamiane w programie Internet Explorer.  
  
## <a name="see-also"></a>Zobacz też  
 [W języku JavaScript za pomocą środowiska wykonawczego systemu Windows](../jswinrt/using-the-windows-runtime-in-javascript.md)