---
title: Symbol.for — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791407"
---
# <a name="symbolfor-function-javascript"></a>Symbol.for — funkcja (JavaScript)
Zwraca symbol dla określonego klucza, lub jeśli klucz nie jest obecny, tworzy nowy obiekt symbol za pomocą nowego klucza.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Wymagany. Klucz dla symbolu, który jest również używany jako opis.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wyszukiwanie symboli w rejestrze globalnego symbolu. Jeśli serializować symboli jako ciągi, umożliwia rejestru symbol globalnego upewnij się, że określony ciąg mapowana poprawne symbol dla wszystkich wyszukiwań.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]