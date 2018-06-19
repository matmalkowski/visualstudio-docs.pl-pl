---
title: JsMemoryAllocationCallback — Typedef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788518"
---
# <a name="jsmemoryallocationcallback-typedef"></a>JsMemoryAllocationCallback — Typedef
Użytkownik zaimplementowana procedura wywołania zwrotnego dla zdarzenia alokacji pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 callbackState  
 Stan przekazany do jssetruntimememoryallocationcallback —.  
  
 allocationEvent  
 Typ zdarzenia alokacji typu.  
  
 allocationSize  
 Rozmiar alokacji.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Zdarzenia JsMemoryAllocate zwrócenie wartości true umożliwia środowiska uruchomieniowego kontynuować alokacji. Zwrócenie wartości false oznacza, że żądanie alokacji zostało odrzucone. Wartość zwracana jest ignorowana w inne zdarzenia alokacji.  
  
## <a name="remarks"></a>Uwagi  
 Jssetruntimememoryallocationcallback — umożliwia rejestrowanie tego wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)