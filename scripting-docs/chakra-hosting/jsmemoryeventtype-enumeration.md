---
title: "Jsmemoryeventtype — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsMemoryEventType
helpviewer_keywords:
- JsMemoryEventType enumeration
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef39008ba84337cebdc9613db17cc9fbdfc8aa79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryeventtype-enumeration"></a>JsMemoryEventType — Wyliczenie
Typ zdarzenia wywołania zwrotnego alokacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum JsMemoryEventType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`JsMemoryAllocate`|Wskazuje żądanie alokacji pamięci.|  
|`JsMemoryFailure`|Wskazuje zdarzenie błąd alokacji.|  
|`JsMemoryFree`|Wskazuje pamięci zwalnianie zdarzeń.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)