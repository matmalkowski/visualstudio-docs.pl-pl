---
title: "set — metoda (WeakMap) (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-weakmap-javascript"></a>set — Metoda (WeakMap) (JavaScript)
Dodaje nowy element `WeakMap` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parametry  
 `weakmapObj`  
 Wymagany. A `WeakMap` obiektu.  
  
 `key`  
 Wymagany. Obiekt reprezentujący klucz elementu do dodania. Musi to być odwołanie do obiektu.  
  
 `value`  
 Wymagany. Wartość elementu do dodania.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Zwraca `WeakMap` obiekt, który zawiera nową parę klucz wartość.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość zostanie dodana do kolekcji przy użyciu istniejącego klucza, nowa wartość zastąpi stara wartość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób dodawania elementów członkowskich do `WeakMap` obiektu.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]