---
title: Wyliczenie JsDebugReadMemoryFlags | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796267"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Wyliczenie JsDebugReadMemoryFlags
Flagi określające zachowanie podczas odczytu pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Wskazuje, że obiekt wywołujący chce operacja odczytu została wykonana pomyślnie, jeśli tylko część pamięci odczytać zakończyło się pomyślnie. Jeśli ta opcja jest ustawiona, błąd E_JsDEBUG_INVALID_MEMORY_ADDRESS tylko zostanie wygenerowany, jeśli "Address" jest nieprawidłowy. Jeśli ta flaga nie zostanie zaznaczone, błąd E_JsDEBUG_INVALID_MEMORY_ADDRESS zostanie wygenerowany, jeśli nie można go odczytać został jakiejkolwiek jego części żądaną ilość pamięci.|  
|`None`|Wskazuje, że obiekt wywołujący potrzebuje domyślne zachowanie dla ReadMemory.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)