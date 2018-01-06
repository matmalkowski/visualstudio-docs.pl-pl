---
title: CONTEXT_COMPARE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_COMPARE
helpviewer_keywords: CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: beba9f612024a63f8f302411982442df19e0bbd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Określa kryteria do porównywania dwóch kontekstów pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 CONTEXT_EQUAL  
 Znajdź pierwszy kontekstu pamięci na liście równą kontekst pamięci docelowy.  
  
 CONTEXT_LESS_THAN  
 Znajdź pierwszy kontekstu pamięci na liście, która jest mniejsza niż kontekst pamięci docelowy.  
  
 CONTEXT_GREATER_THAN  
 Znajdź pierwszy kontekstu pamięci na liście, która jest większa niż kontekst docelowy pamięci.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Znajdź pierwszy kontekstu pamięci na liście, która jest mniejsza lub równa kontekst pamięci docelowy.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Znajdź pierwszy kontekstu pamięci na liście jest większa niż lub równa kontekst pamięci docelowy.  
  
 CONTEXT_SAME_SCOPE  
 Znajdź pierwszy kontekstu pamięci na liście, który znajduje się w tym samym zakresie co kontekst pamięci docelowy.  
  
 CONTEXT_SAME_FUNCTION  
 Znajdź pierwszy kontekstu pamięci na liście w taką samą funkcję jak zasięg docelowy w pamięci.  
  
 CONTEXT_SAME_MODULE  
 Znajdź pierwszy kontekstu pamięci na liście, który znajduje się w tym samym module jako docelowy kontekst pamięci.  
  
 CONTEXT_SAME_PROCESS  
 Znajdź pierwszy kontekstu pamięci na liście, który znajduje się w ten sam proces jako docelowy kontekst pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako argument [porównania](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) metody.  
  
 Te wartości są używane można znaleźć na liście, który spełnia kryteria porównania określony pierwszy kontekstu pamięci. Kontekst pamięci uzyskuje listę konteksty pamięci do porównania się przed za pośrednictwem `IDebugMemoryContext2::Compare` metody. Kontekst pamięci pierwszy na liście, dla którego jest operator porównania `true` jest następnie zwracany.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Porównaj](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)