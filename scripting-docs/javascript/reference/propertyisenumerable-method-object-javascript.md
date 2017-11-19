---
title: "propertyIsEnumerable — metoda (obiekt) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="propertyisenumerable-method-object-javascript"></a>propertyIsEnumerable — Metoda (Obiekt) (JavaScript)
Określa, czy określona właściwość jest wyliczalny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Wystąpienie obiektu.  
  
 `proName`  
 Wymagany. Wartość Nazwa właściwości ciągu.  
  
## <a name="remarks"></a>Uwagi  
 `propertyIsEnumerable` Metoda zwraca `true` Jeśli `proName` istnieje w `object` i mogą być wyliczane przy użyciu `For` pętli. `propertyIsEnumerable` Metoda zwraca `false` Jeśli `object` nie ma właściwości o określonej nazwie lub jeśli określona właściwość nie jest wyliczalny. Zazwyczaj wstępnie zdefiniowanych właściwości nie są wyliczalny, ale są zawsze wyliczalny właściwości zdefiniowane przez użytkownika.  
  
 `propertyIsEnumerable` — Metoda nie należy wziąć pod uwagę obiektów w łańcuchu prototypów.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [prototype — właściwość (obiekt)](../../javascript/reference/prototype-property-object-javascript.md)