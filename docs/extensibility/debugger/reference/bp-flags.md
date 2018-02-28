---
title: BP_FLAGS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3c4818cca16ffb23429006267829b076d52069c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bpflags"></a>BP_FLAGS
Udostępnia flagi opcjonalne, które mogą być używane do określania dodatkowe informacje, gdy ustawienie punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BP_FLAG_NONE  
 Określa Brak flagi punktu przerwania.  
  
 BP_FLAG_MAP_DOCPOSITION  
 Określa, że aparat debugowania (DE) powinny być mapowane punkt przerwania za pomocą pozycji dokumentu. Dotyczy tylko punktów przerwania ustawionych w plikach źródłowych zorientowane na skryptu takich jak Active Server Pages (ASP).  
  
 BP_FLAG_DONT_STOP  
 Określa, czy punkt przerwania powinny być przetwarzane przez aparat debugowania, ale czy aparat debugowania ostatecznie nie należy zatrzymywać istnieje (to znaczy [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) obiekt zdarzenia nie mają być wysyłane). Ta flaga jest przeznaczone głównie z tracepoints.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `dwFlags` członkiem [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.  
  
 Te wartości mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)