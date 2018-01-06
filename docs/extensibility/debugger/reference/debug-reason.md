---
title: DEBUG_REASON | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_REASON
helpviewer_keywords: DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fda733db5a70d88d5029c4001c632c234d32a823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugreason"></a>DEBUG_REASON
Określa, dlaczego został uruchomiony proces do debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 DEBUG_REASON_ERROR  
 Wystąpił ogólny błąd (są one używane jako domyślnego warunku, gdy żaden z innych powodów, dla których dopasowanie).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Proces został uruchomiony na żądanie użytkownika.  
  
 DEBUG_REASON_USER_ATTACHED  
 Proces już działa, był dołączony do przez użytkownika.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Proces został dołączony do automatycznie, gdy została ona uruchomiona.  
  
 DEBUG_REASON_CAUSALITY  
 Proces został uruchomiony z powodu *Just In Time* zdarzenia debugowania (JIT).  
  
## <a name="remarks"></a>Uwagi  
 Zwrócony z [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)