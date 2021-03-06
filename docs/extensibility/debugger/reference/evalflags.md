---
title: EVALFLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c718414749bb6c748f25fb90837644fe984a274
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102005"
---
# <a name="evalflags"></a>EVALFLAGS
Określa flagi sterujące Obliczanie wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Elementy członkowskie  
 EVAL_RETURNVALUE  
 Określa przyjąć wartość zwracaną, jeśli istnieje.  
  
 EVAL_NOSIDEEFFECTS  
 Określa, że efekty uboczne nie jest dozwolone.  
  
 EVAL_ALLOWBPS  
 Określa zatrzymywania punktów przerwania.  
  
 EVAL_ALLOWERRORREPORT  
 Określa raportów o błędach do hosta mogą być. Głównie używane do obliczania wyrażenia w skrypcie w programie Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Funkcje wymusza ma zostać obliczone jako adresy, zamiast wywoływania funkcji.  
  
 EVAL_NOFUNCEVAL  
 Funkcja zapobiega oceniane. Rozważmy na przykład `int` tokenu w wyrażeniu `myExpression(int) + 10`. Ta funkcja może zostać poprawnie oceniony jako adres, ale nie jako wartość.  
  
 EVAL_NOEVENTS  
 Flaga wskazująca, że zdarzeń występujących podczas obliczania wyrażenia nie powinny być wysyłane do menedżera sesji debugowania (SDM) lub do środowiska IDE.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są przekazywane jako argument [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) i [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metody.  
  
 Te flagi mogą być łączone z bitowego OR.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)