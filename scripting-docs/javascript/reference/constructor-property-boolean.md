---
title: "constructor — właściwość (wartość logiczna) | Dokumentacja firmy Microsoft"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-boolean"></a>constructor — Właściwość (Wartość logiczna)
Określa funkcja, która tworzy wartość typu Boolean.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>Parametry  
 `boolean`  
 Nazwa typu Boolean.  
  
 `value`  
 Opcjonalny. Określa wartość typu Boolean. Może to być numer 1 lub 0, albo ciągi "true" lub "false".  
  
## <a name="remarks"></a>Uwagi  
 `constructor` Właściwość zawiera odwołanie do funkcji, która tworzy wystąpienia obiektu Boolean.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie właściwości konstruktora.  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]