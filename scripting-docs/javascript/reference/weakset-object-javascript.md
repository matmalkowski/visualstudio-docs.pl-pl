---
title: "Weakset — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="weakset-object-javascript"></a>WeakSet — obiekt (JavaScript)
Kolekcja unikatowych obiektów, które mogą być dowolnego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli próbujesz dodać obiekt nie jest unikatowa w celu `WeakSet`, nowy obiekt nie zostanie dodany do kolekcji.  
  
 W odróżnieniu od `Set`, tylko obiekty mogą być dodane do kolekcji. Dowolne wartości nie można dodać do kolekcji.  
  
 W `WeakSet` obiekt odwołania do obiektów w zestawie są przechowywane "słabo". Oznacza to, że `WeakSet` nie zapobiega wyrzucania elementów bezużytecznych zapobiec obiektów. Jeśli istnieją żadnych odwołań (inne niż `WeakSet`) do obiektów, moduł zbierający elementy bezużyteczne może zbierać obiektów.  
  
 `WeakSet`(lub `WeakMap`) mogą być pomocne w niektórych scenariuszach obejmujących buforowania obiektów lub metadane obiektu. Na przykład metadanych obiektów extensible może być przechowywany w `WeakSet`, lub możesz utworzyć pamięci podręcznej obrazów użytkownika przy użyciu `WeakSet`.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `WeakSet` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|— konstruktor|Określa funkcję, która tworzy zestaw.|  
|Prototyp|Zwraca odwołanie do prototypu dla zestawu.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `WeakSet` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|add|Dodaje element do zestawu.|  
|Usuń|Usuwa określony element z zestawu.|  
|ma|Zwraca `true` Jeśli zestaw zawiera określony element.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodawać członków do zestawu, a następnie sprawdź, czy zostały one dodane.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]