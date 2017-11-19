---
title: "Object.getownpropertysymbols — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Object.getOwnPropertySymbols — funkcja (JavaScript)
Zwraca symbol własnych właściwości obiektu. Symbol własnych właściwości obiektu są te, które są zdefiniowane bezpośrednio z tym obiektem, a nie są dziedziczone z obiektu prototypu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt, który zawiera własnych symboli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica zawiera własnych symbole obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Należy użyć `Object.getOwnPropertySymbols` można uzyskać właściwości obiektu symbolu. `Object.getOwnPropertyNames`nie zwróci właściwości symbolu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak można uzyskać właściwości obiektu symbolu.  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]