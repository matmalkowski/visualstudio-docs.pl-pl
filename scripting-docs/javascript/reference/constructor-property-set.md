---
title: "constructor — właściwość (Set) | Dokumentacja firmy Microsoft"
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
ms.assetid: f350b7eb-8994-40bf-9011-f8b20fcef34f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea9af6d60c2ae8bc8a383c4cebbf0955e183895e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-set"></a>constructor — Właściwość (Set)
Określa funkcję, która tworzy zestaw.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
set.constructor  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `set` jest nazwą zestawu.  
  
 `constructor` Właściwości jest elementem członkowskim prototypu każdy obiekt, który ma prototypu. Obejmuje wszystkie obiekty wewnętrzne JavaScript z wyjątkiem `Global` i `Math` obiektów. `constructor` Właściwość zawiera odwołanie do funkcji, która tworzy wystąpienie określonego obiektu.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]