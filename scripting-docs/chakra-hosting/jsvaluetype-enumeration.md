---
title: Jsvaluetype — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsValueType
helpviewer_keywords:
- JsValueType enumeration
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4f61cf9118c19a0fc35e7505af422b812d0b43
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788626"
---
# <a name="jsvaluetype-enumeration"></a>JsValueType — Wyliczenie
Typ JavaScript JsValueRef.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`JsUndefined`|Wartość jest `undefined` wartość.|  
|`JsNull`|Wartość jest `null` wartość.|  
|`JsNumber`|Wartość jest JavaScript wartość liczbową.|  
|`JsString`|Wartość jest wartością ciągu JavaScript.|  
|`JsBoolean`|Wartość jest wartością logiczną JavaScript.|  
|`JsObject`|Wartość jest wartością obiektu JavaScript.|  
|`JsFunction`|Wartość jest wartością obiektu funkcji JavaScript.|  
|`JsError`|Wartość jest wartością obiektu błąd JavaScript.|  
|`JsArray`|Wartość jest wartością obiektu JavaScript tablicy.|  
|`JsSymbol`|Wartość jest wartością symbolu języka JavaScript.<br /><br /> Ta wartość wyliczenia jest obsługiwana tylko w trybie krawędzi.|  
|`JsArrayBuffer`|Wartość jest JavaScript `ArrayBuffer` obiektu wartości.<br /><br /> Ta wartość wyliczenia jest obsługiwana tylko w trybie krawędzi.|  
|`JsTypedArray`|Wartość jest JavaScript wpisane wartości obiektu tablicy.<br /><br /> Ta wartość wyliczenia jest obsługiwana tylko w trybie krawędzi.|  
|`JsDataView`|Wartość jest JavaScript `DataView` obiektu wartości.<br /><br /> Ta wartość wyliczenia jest obsługiwana tylko w trybie krawędzi.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)