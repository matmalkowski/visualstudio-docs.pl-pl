---
title: DOCCONTEXT_COMPARE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DOCCONTEXT_COMPARE
helpviewer_keywords: DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2074e5abe688ecb8f796099cf23309ec0cfe954d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Określa kryteria do porównywania dwóch kontekstów dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DOCCONTEXT_EQUAL  
 Znajdź pierwszy kontekstu dokumentu na liście równą docelowy kontekstu dokumentu.  
  
 DOCCONTEXT_LESS_THAN  
 Znajdź na liście, która jest mniejsza niż docelowy kontekstu dokumentu pierwszy kontekstu dokumentu.  
  
 DOCCONTEXT_GREATER_THAN  
 Znajdź na liście, która jest większa niż docelowy kontekstu dokumentu pierwszy kontekstu dokumentu.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Znajdź pierwszy kontekstu dokumentu na liście, który znajduje się w tym samym dokumencie jako docelowy kontekstu dokumentu.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako argument [porównania](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) metody.  
  
 Te wartości są używane do kryteria porównania do znajdowania pierwszego kontekstu dokumentu w postaci listy. Kontekstu dokumentu znajduje się lista kontekstów dokumentu do porównania się przed za pośrednictwem `IDebugDocumentContext2::Compare` metody. Pierwszy kontekstu dokumentu na liście, dla którego jest operator porównania `true` jest następnie zwracany.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Porównaj](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)