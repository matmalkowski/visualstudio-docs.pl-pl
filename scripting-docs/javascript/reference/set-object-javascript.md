---
title: Obiekt (JavaScript) | Dokumentacja firmy Microsoft
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
- Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Set — Obiekt (JavaScript)
Kolekcja unikatowe wartości, które mogą być dowolnego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli próbujesz dodać nie jest unikatowa wartość `Set`, nowa wartość nie zostanie dodany do kolekcji.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `Set` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Konstruktor](../../javascript/reference/constructor-property-set.md)|Określa funkcję, która tworzy zestaw.|  
|[Prototyp](../../javascript/reference/prototype-property-set.md)|Zwraca odwołanie do prototypu dla zestawu.|  
|[rozmiar](../../javascript/reference/size-property-set-javascript.md)|Zwraca liczbę elementów w zestawie.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Set` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dodaj](../../javascript/reference/add-method-set-javascript.md)|Dodaje element do zestawu.|  
|[Wyczyść](../../javascript/reference/clear-method-set-javascript.md)|Usuwa wszystkie elementy z zestawu.|  
|[Usuń](../../javascript/reference/delete-method-set-javascript.md)|Usuwa określony element z zestawu.|  
|[Instrukcja forEach](../../javascript/reference/foreach-method-set-javascript.md)|Wykonuje określoną akcję dla każdego elementu w zestawie.|  
|[ma](../../javascript/reference/has-method-set-javascript.md)|Zwraca `true` Jeśli zestaw zawiera określony element.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Zwraca reprezentację ciągu zestawu.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Zwraca wartość pierwotnych określonego obiektu.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można dodawać członków do zestawu, a następnie pobrać je.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]