---
title: PARSEFLAGS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PARSEFLAGS
helpviewer_keywords: PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c96eb60c397093fb5ec3291a0b02ee7cbd07e34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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