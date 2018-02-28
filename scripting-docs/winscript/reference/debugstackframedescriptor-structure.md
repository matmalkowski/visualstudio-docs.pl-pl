---
title: Struktura DebugStackFrameDescriptor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugstackframedescriptor-structure"></a>Struktura DebugStackFrameDescriptor
Wylicza ramki stosu i scala dane wyjściowe z kilku modułów wyliczających w tym samym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `pdsf`  
 Obiekt ramki stosu.  
  
 `dwMin`  
 Reprezentacja zależne od maszyny niższy zakres adresów fizycznych skojarzonych z tą ramką stosu.  
  
 `dwLim`  
 Reprezentacja zależne od maszyny Górny zakres adresów fizycznych skojarzonych z tą ramką stosu.  
  
 `fFinal`  
 Flaga wskazująca, że ramki jest przetwarzana.  
  
 `punkFinal`  
 Jeśli ten parametr nie jest `NULL`, powinna zostać przerwana w bieżącym modułu wyliczającego scalanie i nowy powinny być uruchamiane. Obiekt wskazuje, jak można uruchomić nowego wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesu używa tej struktury sortowania ramek stosu z wielu aparatów skryptów. Według Konwencji stosy rosnąć w dół. W rezultacie na architektury, gdzie stosy zwiększa się, adresy powinna być uzupełniony parami.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)