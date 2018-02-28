---
title: PARSEFLAGS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ae1237efe578bdd51c6ed148a1dab7a7617fee30
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="parseflags"></a>PARSEFLAGS
Określa, jak można przeanalizować wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 PARSE_EXPRESSION  
 Wskazuje, czy wyrażenie nie jest oświadczenie.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Wskazuje, czy wyrażenie jest analizowana (i później oceniane) jako adres.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Wskazuje, czy wyrażenie jest przetwarzane w czasie projektowania (oznacza to, gdy projektant jest otwarty).  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako parametr [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analizy](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)