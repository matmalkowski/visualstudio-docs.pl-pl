---
title: Object.is — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d4c281fdafbfacb0b1f6061ef4a90bfac99234
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791119"
---
# <a name="objectis-function-javascript"></a>Object.is — funkcja (JavaScript)
Zwraca wartość wskazującą, czy dwie wartości są identyczne.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
Object.is(value1, value2)  
```  
  
#### <a name="parameters"></a>Parametry  
 `value1`  
 Wymagany. Pierwsza wartość do testowania.  
  
 `value2`  
 Wymagany. Druga wartość do testowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli wartość jest taka sama wartość; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 W odróżnieniu od == — operator, `Object.is` nie przekształcić żadnych typów, podczas testowania wartości.  
  
 Porównanie stosowane przez `Object.is` jest podobny do porównania stosowane przez === operatora, z wyjątkiem `Object.is` traktuje `Number.isNaN` jako taką samą wartość jak `NaN`. On również traktuje + 0 i - 0 jako różne wartości.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]