---
title: toString — metoda (tablica) | Dokumentacja firmy Microsoft
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791632"
---
# <a name="tostring-method-array"></a>toString — Metoda (Array)
Zwraca ciąg reprezentujący tablicę.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>Parametry  
 `array`  
 Wymagany. Tablica do reprezentowania jako ciąg.  
  
## <a name="return-value"></a>Wartość zwracana  
 Reprezentacja ciągu tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Elementy `Array` są konwertowane na ciągi. Wynikowa ciągów są połączone i rozdzielonych przecinkami.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **toString** metody z tablicy.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]