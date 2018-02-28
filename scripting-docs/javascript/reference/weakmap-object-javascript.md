---
title: "WeakMap — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
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
- WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="weakmap-object-javascript"></a>WeakMap — Obiekt (JavaScript)
Kolekcja par klucz/wartość, w których każdy klucz jest odwołanie do obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>Uwagi  
 A `WeakMap` nie można wyliczyć obiektów.  
  
 Jeśli wartość zostanie dodana do kolekcji przy użyciu istniejącego klucza, nowa wartość zastąpi stara wartość.  
  
 W `WeakMap` obiekt odwołania do obiektów kluczy są przechowywane "słabo". Oznacza to, że `WeakMap` nie zapobiega wyrzucania elementów bezużytecznych zapobiec klucza obiektów. Jeśli istnieją żadnych odwołań (inne niż `WeakMap`) do klucza obiektów modułu zbierającego elementy bezużyteczne może zbierać obiektów kluczy.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `WeakMap` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Konstruktor](../../javascript/reference/constructor-property-weakmap.md)|Określa funkcję, która tworzy `WeakMap`.|  
|[Prototyp](../../javascript/reference/prototype-property-weakmap.md)|Zwraca odwołanie do prototypu dla `WeakMap`.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `WeakMap` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Wyczyść](../../javascript/reference/clear-method-weakmap-javascript.md)|Usuwa wszystkie elementy z `WeakMap`.|  
|[Usuń](../../javascript/reference/delete-method-weakmap-javascript.md)|Usuwa określony element z `WeakMap`.|  
|[Pobierz](../../javascript/reference/get-method-weakmap-javascript.md)|Zwraca określony element z `WeakMap`.|  
|[ma](../../javascript/reference/has-method-weakmap-javascript.md)|Zwraca `true` Jeśli `WeakMap` zawiera określony element.|  
|[zestaw](../../javascript/reference/set-method-weakmap-javascript.md)|Dodaje nowy element `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Zwraca reprezentację ciągu `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Zwraca wartość pierwotnych określonego obiektu.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób dodawania elementów członkowskich do `WeakMap` obiekt, a następnie pobrać je.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]