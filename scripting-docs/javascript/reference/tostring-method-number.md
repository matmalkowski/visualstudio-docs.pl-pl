---
title: "toString — metoda (numer) | Dokumentacja firmy Microsoft"
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6be170061faf4c2782c7247c80c55065c3a6742
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-number"></a>toString — Metoda (Numer)
Zwraca reprezentację ciągu dla danej liczby.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
number.toString()  
```  
  
## <a name="parameters"></a>Parametry  
 `number`  
 Wymagany. Numer do reprezentowania jako ciąg.  
  
## <a name="return-value"></a>Wartość zwracana  
 Reprezentacja ciągu numer.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **toString** metody z liczbą.  
  
```JavaScript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]