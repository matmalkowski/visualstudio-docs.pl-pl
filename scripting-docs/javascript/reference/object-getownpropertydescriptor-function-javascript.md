---
title: "Object.getownpropertydescriptor — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: getOwnPropertyDescriptor method [JavaScript]
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: "45"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd147d567fc4d8a39d7a251d55772c40518e7a26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertydescriptor-function-javascript"></a>Object.getOwnPropertyDescriptor — Funkcja (JavaScript)
Pobiera deskryptor własnych właściwości określonego obiektu. Właściwość własnych deskryptora to taki, który jest zdefiniowany bezpośrednio na obiekt i nie dziedziczy z prototypu obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt, który zawiera właściwości.  
  
 `propertyname`  
 Wymagany. Nazwa właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Deskryptor właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Object.getOwnPropertyDescriptor` funkcji, aby uzyskać obiekt deskryptora, który opisano atrybuty elementu właściwości.  
  
 [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md) służy do dodawania lub modyfikowania właściwości.  
  
## <a name="data-property-example"></a>Przykład właściwości danych  
 Poniższy przykład pobiera deskryptor właściwości danych i używa go, aby właściwość tylko do odczytu.  
  
```JavaScript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Aby wyświetlić listę atrybutów właściwości, można dodać następujący kod do tego przykładu.  
  
```JavaScript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## <a name="requirements"></a>Wymagania  
 Wszystkie funkcje są obsługiwane w [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)]obsługuje obiekty modelu DOM, ale nie zdefiniowany przez użytkownika obiekty. `enumerable` i `configurable` można określić atrybuty, ale nie są one używane.  
  
## <a name="see-also"></a>Zobacz też  
 [Prototypy modelu obiektu dokumentu, część 2: Metoda dostępu (metody pobierającej/ustawiającej) pomocy technicznej](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md)