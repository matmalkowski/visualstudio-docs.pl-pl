---
title: "prototype — właściwość (Intl.DateTimeFormat) | Dokumentacja firmy Microsoft"
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64dff17e4aaf62940f4c9c5f8b422fcbceb7212a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intldatetimeformat"></a>prototype — Właściwość (Intl.DateTimeFormat)
Zwraca odwołanie do prototypu dla elementu formatującego.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
dateTimeFormat.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `dateTimeFormat` Argument jest nazwą elementu formatującego.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `Intl.DateTimeFormat` obiektów, która zwraca wartość największego elementu zestawu, zadeklarować funkcję, dodaj go do `Intl.DateTimeFormat.prototype`, a następnie użyć go.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]