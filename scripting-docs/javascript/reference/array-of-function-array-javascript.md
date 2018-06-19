---
title: Funkcja Array.of (Array) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 042315bbc3b956e92fff866f7d403b6f87726a74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789067"
---
# <a name="arrayof-function-array-javascript"></a>Array.of (Array) — funkcja (JavaScript)
Zwraca tablicę z przekazano argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `element0,...,elementN`  
 Opcjonalny. Elementy, które mają zostać umieszczone w tablicy. Spowoduje to utworzenie tablicy z n + 1 elementów i długość n + 1.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest podobny do wywoływania `new Array(args)`, ale `Array.of` nie ma specjalnego zachowania, gdy jeden argument jest przekazywany w.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy tablicę z przekazano liczb.  
  
```JavaScript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1   
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano różnicę między przy użyciu `Array.of` i `new Array`.  
  
```JavaScript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]