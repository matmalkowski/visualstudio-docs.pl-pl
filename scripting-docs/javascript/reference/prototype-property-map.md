---
title: "prototype — właściwość (Map) | Dokumentacja firmy Microsoft"
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
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45601bdff2dfc8047f2499ab07dcdedd66662fc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-map"></a>prototype — Właściwość (Map)
Zwraca odwołanie do prototypu dla mapy.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
map.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `map` Argument jest nazwą mapy.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `Map` obiektów, która zwraca wartość największego elementu zestawu, zadeklarować funkcję, dodaj go do `Map.prototype`, a następnie użyć go.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]