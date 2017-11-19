---
title: "has — metoda (Map) (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-map-javascript"></a>has — Metoda (Map) (JavaScript)
Zwraca `true` Jeśli mapy zawiera określony element.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parametry  
 `mapObj`  
 Wymagany. A `Map` obiektu.  
  
 `key`  
 Wymagany. Klucz elementu do testowania.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 `true`Jeśli mapy zawiera określony element.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodać członka do `Map` , a następnie sprawdź, czy mapa go zawiera.  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]