---
title: includes — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790618"
---
# <a name="includes-method-string-javascript"></a>includes (String) — metoda (JavaScript)
Zwraca wartość logiczną, wskazującą, czy przekazano ciągu znajduje się w obiekcie string.  
  
## <a name="syntax"></a>Składnia  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. Obiekt ciągu do przetestowania.  
  
 `substring`  
 Wymagany. Ciąg do testowania.  
  
 `position`  
 Opcjonalny. Pozycja pierwszego znaku w celu przetestowania w obiekcie string, począwszy od 0.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli przekazany w ciągu znajduje się w obiekcie string `includes` metoda zwraca `true`; w przeciwnym razie zwraca `false`.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]