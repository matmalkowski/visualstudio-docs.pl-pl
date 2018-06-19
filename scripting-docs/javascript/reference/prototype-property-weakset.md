---
title: prototype — właściwość (WeakSet) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c66c7854a83dcf3128025350a7fcdd17f4dfaf5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791257"
---
# <a name="prototype-property-weakset"></a>prototype (WeakSet) — właściwość
Zwraca odwołanie do prototypu dla `WeakSet`.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
weakset.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `weakset` Argument jest nazwą zestawu.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `WeakSet` obiektów, która zwraca wartość największego elementu zestawu, zadeklarować funkcję, dodaj go do `WeakSet.prototype`, a następnie użyć go.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]