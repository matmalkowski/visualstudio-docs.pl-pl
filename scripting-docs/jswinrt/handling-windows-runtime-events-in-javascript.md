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
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302815"
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
  
Inna różnica między .NET/C++ i JavaScript jest liczba parametrów podjęte przez program obsługi zdarzeń. W .NET/C++, program obsługi ma dwa: zdarzenia i dane zdarzenia. W języku JavaScript, dwa są powiązane jako pojedynczy `Event` obiektu. W poniższym przykładzie `ev` parametr zawiera nadawcę zdarzenia ( `target` właściwości) i właściwości danych zdarzeń (w tym miejscu, po prostu `position`). Właściwości danych zdarzeń są te, które są udokumentowane dla każdego zdarzenia.
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  Funkcje środowiska wykonawczego systemu Windows nie są dostępne dla aplikacji, które są uruchamiane w programie Internet Explorer.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie środowiska wykonawczego systemu Windows w języku JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
