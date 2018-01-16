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
ms.openlocfilehash: 2cc47ae365841332f11cb02da1469a4c9fff80c3
ms.sourcegitcommit: abae48f476832f79cc2c5bac43bb1226d3fe4e48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
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
  
console.log(symbols[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]