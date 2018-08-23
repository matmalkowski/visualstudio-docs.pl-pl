---
title: EVALFLAGS | Dokumentacja firmy Microsoft
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
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 088c63fb1683bdf277ed1c3c5aba06a3156efbbf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678528"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [EVALFLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/evalflags).  
  
Określa flagi, które kontrolują Obliczanie wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Określa, że wartość zwracana, jeśli istnieje, można obliczyć.  
  
 EVAL_NOSIDEEFFECTS  
 Określa, że efekty uboczne niemożliwe.  
  
 EVAL_ALLOWBPS  
 Określa zatrzymywanie punktów przerwania.  
  
 EVAL_ALLOWERRORREPORT  
 Określa raportów o błędach do hosta mają być dozwolone. Używane głównie do obliczenia wyrażenia w skrypcie w programie Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Funkcje wymusza, aby zostały uznane za adresów, zamiast wywoływania funkcji.  
  
 EVAL_NOFUNCEVAL  
 Funkcja zapobiega oceniane. Na przykład, rozważmy `int` tokenu w wyrażeniu `myExpression(int) + 10`. Ta funkcja może być poprawnie określona jako adres, ale nie jako wartość.  
  
 EVAL_NOEVENTS  
 Flaga wskazująca, że zdarzenia, które wystąpiły podczas obliczania wyrażenia nie powinny być wysyłane, Menedżer debugowania sesji (SDM) lub środowiska IDE.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są przekazywane jako argument do [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) i [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metody.  
  
 Te flagi mogą być łączone z bitowe OR.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

