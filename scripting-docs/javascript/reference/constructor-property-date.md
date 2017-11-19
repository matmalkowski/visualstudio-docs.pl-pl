---
title: "constructor — właściwość (Data) | Dokumentacja firmy Microsoft"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 798064117e17ee5b2988396de3c6545917373b10
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-date"></a>constructor — Właściwość (Data)
Określa funkcję, która tworzy datę.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
date.constructor  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `date` to nazwa obiektu daty.  
  
 `constructor` Właściwości jest elementem członkowskim prototypu każdy obiekt, który ma prototypu. `constructor` Właściwość zawiera odwołanie do funkcji, która tworzy wystąpienie określonego obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie właściwości konstruktora.  
  
```JavaScript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]