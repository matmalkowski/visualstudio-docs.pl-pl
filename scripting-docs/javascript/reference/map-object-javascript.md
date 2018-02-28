---
title: "Map — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="map-object-javascript"></a>Map — Obiekt (JavaScript)
Kolekcja par klucz/wartość.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>Uwagi  
 Klucze i wartości w kolekcji mogą być dowolnego typu. Jeśli wartość zostanie dodana do kolekcji przy użyciu istniejącego klucza, nowa wartość zastąpi stara wartość.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `Map` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Konstruktor](../../javascript/reference/constructor-property-map.md)|Określa funkcję, która tworzy mapę.|  
|[Prototyp](../../javascript/reference/prototype-property-map.md)|Zwraca odwołanie do prototypu dla mapy.|  
|[rozmiar](../../javascript/reference/size-property-map-javascript.md)|Zwraca liczbę elementów na mapie.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Map` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Wyczyść](../../javascript/reference/clear-method-map-javascript.md)|Usuwa wszystkie elementy z mapy.|  
|[Usuń](../../javascript/reference/delete-method-map-javascript.md)|Usuwa określony element z mapy.|  
|[Instrukcja forEach](../../javascript/reference/foreach-method-map-javascript.md)|Wykonuje określoną akcję dla każdego elementu na mapie.|  
|[Pobierz](../../javascript/reference/get-method-map-javascript.md)|Zwraca określony element z mapy.|  
|[ma](../../javascript/reference/has-method-map-javascript.md)|Zwraca `true` Jeśli mapy zawiera określony element.|  
|[zestaw](../../javascript/reference/set-method-map-javascript.md)|Dodaje nowy element do mapy.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Zwraca reprezentację ciągu obiektu mapy.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Zwraca wartość pierwotnych określonego obiektu.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób dodawania elementów członkowskich do `Map` , a następnie je pobrać.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]