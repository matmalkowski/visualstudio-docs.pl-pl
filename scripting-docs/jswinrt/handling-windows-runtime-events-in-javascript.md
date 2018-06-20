---
title: Obsługa zdarzeń środowiska wykonawczego systemu Windows w języku JavaScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1118fa4e6408698187e7f50ca6f9b61bf596a6e
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234949"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Obsługa zdarzeń środowiska wykonawczego systemu Windows w języku JavaScript
Zdarzenia środowiska uruchomieniowego systemu Windows nie są reprezentowane w taki sam sposób, w języku JavaScript, jak w języku C++ i .NET Framework. Nie są właściwościami klasy, ale raczej są reprezentowane jako identyfikatory ciągów (małej), które są przekazywane do klasy `addEventListener` i `removeEventListener` metody. Na przykład można dodać obsługi zdarzeń dla [Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) zdarzenia przez przekazanie do ciągu "positionchanged" `Geolocator.addEventListener` metody:  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Można również ustawić `locator.onpositionchanged` właściwości:  
  
```JavaScript  
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
 [Używanie środowiska wykonawczego systemu Windows w języku JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)