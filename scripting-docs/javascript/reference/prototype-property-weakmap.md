---
title: "prototype — właściwość (WeakMap) | Dokumentacja firmy Microsoft"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakmap"></a>prototype — Właściwość (WeakMap)
Zwraca odwołanie do prototypu dla `WeakMap` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `weakmap` Argument jest nazwą `WeakMap` obiektu.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `WeakMap` obiekt, który zwraca wartość największego elementu `WeakMap`, zadeklarować funkcję, dodaj go do `WeakMap.prototype`i przy jego użyciu.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]