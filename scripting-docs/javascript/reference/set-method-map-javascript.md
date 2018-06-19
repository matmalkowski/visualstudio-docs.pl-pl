---
title: set — metoda (Map) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a84a5b2714fde55fba03d581faa851d7245e001
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791338"
---
# <a name="set-method-map-javascript"></a>set — Metoda (Map) (JavaScript)
Dodaje nowy element do mapy.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
mapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parametry  
 `mapObj`  
 Wymagany. A `Map` obiektu.  
  
 `key`  
 Wymagany. Klucz dla nowego elementu.  
  
 `value`  
 Wymagany. Wartość elementu do dodania.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Zwraca `Map` obiekt, który zawiera nową parę klucz wartość.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość zostanie dodana do kolekcji przy użyciu istniejącego klucza, nowa wartość zastąpi stara wartość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób dodawania elementów członkowskich do `Map` , a następnie je pobrać.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]