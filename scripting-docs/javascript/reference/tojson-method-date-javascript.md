---
title: "toJSON — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tojson-method-date-javascript"></a>toJSON — Metoda (Data) (JavaScript)
Używane przez [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) metodę umożliwiającą włączenie transformacja obiekt danych serializacji JavaScript Object Notation (JSON).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>Parametry  
 `objectname`  
 Wymagany. Obiekt, dla których JSON wyznaczony serializacji.  
  
## <a name="remarks"></a>Uwagi  
 `toJSON` Metoda jest używana przez `JSON.stringify` funkcji. `JSON.stringify`serializuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wartość na tekst w formacie JSON. Jeśli `toJSON` dostarczonego do metody `JSON.stringify`, `toJSON` metoda jest wywoływana, gdy `JSON.stringify` jest wywoływana.  
  
 `toJSON` Metoda jest elementem członkowskim wbudowanych [data](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu. Zwraca ciągu datę w formacie ISO strefą czasową UTC (wskazywane przez sufiks Z).  
  
 Można zastąpić `toJSON` metodę `Date` typu lub zdefiniuj `toJSON` metody innych obiektów w celu osiągnięcia przekształcania danych dla określonego typu obiektu przed serializacji JSON.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `toJSON` metody do serializacji wartości elementu członkowskiego ciągu pisane wielkimi literami. `toJSON` Metoda jest wywoływana, gdy `JSON.stringify` jest wywoływana.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia `toJSON` metodę, która jest elementem członkowskim wbudowanych [data](../../javascript/reference/date-object-javascript.md) obiektu.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**Ma zastosowanie do:** [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON.Parse — funkcja](../../javascript/reference/json-parse-function-javascript.md)   
 [Funkcja JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript — metody](../../javascript/reference/javascript-methods.md)