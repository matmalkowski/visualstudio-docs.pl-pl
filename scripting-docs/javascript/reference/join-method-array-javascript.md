---
title: JOIN — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790792"
---
# <a name="join-method-array-javascript"></a>join — Metoda (Tablica) (JavaScript)
Dodaje wszystkie elementy rozdzielone ciąg separatora określonej tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. `Array` Obiektu.  
  
 `separator`  
 Opcjonalny. Ciąg używany do rozdzielania jednego elementu tablicy od następnego w wynikowym `String`. Pominięcie elementów tablicy są oddzielone przecinkami.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dowolny element tablicy jest **Niezdefiniowany** lub `null`, jest ona traktowana jako ciąg pusty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **sprzężenia** metody.  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [String — obiekt](../../javascript/reference/string-object-javascript.md)