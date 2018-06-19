---
title: Zarządzanie odbiornikiem zdarzeń | Dokumentacja firmy Microsoft
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
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a97c579716b9964b8dfb93db419e9a70160d33a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788887"
---
# <a name="managing-event-listeners"></a>Zarządzanie odbiornikiem zdarzeń
Jeśli okres istnienia elementem modelu DOM lub obiekt różni się od ważności jego odbiornika skojarzone ze zdarzeniem, być może należy użyć [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx)przecieków metody w celu uniknięcia pamięci.  
  
## <a name="event-listeners-and-object-scope"></a>Odbiorniki zdarzeń i zakres obiektu  
 W poniższym przykładzie kodu pokazano kod, który może spowodować pamięci podczas wyciek `dataObjFactory()` funkcja jest wywoływana. W tym kodzie odbiornik zdarzeń jest zarejestrowany dla obiekt danych zawsze tworzony jest nowy obiekt danych. Aby udostępnić bieżącego obiektu danych w `dataReady()` program obsługi zdarzeń, [bind — metoda (funkcja)](../../javascript/reference/bind-method-function-javascript.md) jest używany w `addEventListener`.  
  
```JavaScript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 Odbiornika dla każdego obiektu danych został zarejestrowany za pomocą `document` obiektu, który ma inny czas istnienia niż obiekty danych. Odbiornik zdarzeń zarejestrowanych dla każdego obiektu danych uniemożliwia jako elementu bezużytecznego zebranych tak długo, jak `document` obiekt pozostaje w zakresie. (W niektórych nowoczesnych wzorce projektowe JavaScript obiektu dokumentu pozostaną w zakresie przez czas ich istnienia aplikacji sieci web). Aby zapobiec przeciek pamięci `removeEventListener` jest wywoływana `dataObjFactory` funkcji. Jednak ten kod nie powiedzie się, ponieważ `removeEventListener` nie została wywołana w wersji powiązanej obsługi zdarzeń, który jest zwracany przez `bind`funkcji.  
  
 Aby rozwiązać ten kod i udostępnić wyrzucanie elementów bezużytecznych obiekty danych, należy najpierw przechowywania odwołanie do wersji powiązanej obsługi zdarzeń, jak pokazano w tym kodzie, a następnie przekazać przechowywane odwołanie do `addEventListener`. Oto kod poprawiony `DataObject`:  
  
```JavaScript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 Na koniec należy wywołać `removeEventListener` dla przechowywanych odwołania (`handlerRef`) powiązanej funkcji. Oto kod poprawiony `dataObjFactory`:  
  
```JavaScript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 Teraz można wywołać `removeEventListener` działa prawidłowo, a obiekty zbędnych danych mogą być zbierane nawet podczas odzyskiwania pamięci `document` obiekt pozostaje w zakresie.