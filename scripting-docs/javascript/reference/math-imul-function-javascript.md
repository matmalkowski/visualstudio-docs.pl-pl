---
title: "Math.imul — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57820d0926d574c75924f4eef6265ef7fa0766da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="mathimul-function-javascript"></a>Math.imul — funkcja (JavaScript)
Zwraca iloczyn dwóch liczb, które są traktowane jako 32-bitowych liczb całkowitych ze znakiem.  
  
## <a name="syntax"></a>Składnia  
  
```  
Math.imul(x, y);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wymagany. Pierwsza liczba.  
  
 `y`  
 Wymagany. Druga liczba.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja służy do kompilatory, takich jak Emscripten i Mandreel, które nie implementują mnożenia całkowitą w taki sam sposób jak JavaScript.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób mnożenie liczb przy użyciu `Math.imul`.  
  
```JavaScript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2   
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]