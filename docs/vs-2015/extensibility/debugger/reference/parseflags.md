---
title: PARSEFLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ccf50c5bd85ae6a69a24da3a3d830009e3297be8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685601"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [PARSEFLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/parseflags).  
  
Określa, jak można przeanalizować wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Wskazuje, czy wyrażenie nie jest instrukcja.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Wskazuje, czy wyrażenie jest analizowany (i później oceniane) jako adres.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Wskazuje, czy wyrażenie jest analizowana w czasie projektowania (oznacza to, gdy projektant jest otwarty).  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako parametr do [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analizy](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

