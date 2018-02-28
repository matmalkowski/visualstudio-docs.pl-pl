---
title: BP_FLAGS90 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: af59e06ad31b56c04127ca89b43a903db36d3615
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bpflags90"></a>BP_FLAGS90
Wylicza flagi opcjonalne prawidłowe wartości. Flagi opcjonalne może służyć do określenia dodatkowych informacji w przypadku ustawienia punktu przerwania. To wyliczenie rozszerza [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 BP90_FLAG_NONE  
 Określa Brak flagi punktu przerwania.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Określa aparat debugowania (DE) należy mapować punkt przerwania za pomocą pozycji dokumentu. Dotyczy tylko punktów przerwania ustawionych w plikach źródłowych zorientowane na skryptu takich jak Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Określa, czy punkt przerwania powinny być przetwarzane przez aparat debugowania, ale czy aparat debugowania ostatecznie nie należy zatrzymywać oznacza to [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) nie należy wysyłać zdarzenia obiektu. Ta flaga jest przeznaczone głównie z punktami śledzenia.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Używany przez aparat debugowania natywnego w celu określenia, czy stan wykonywania krokowego powinny zostać wyczyszczone. Różni się od BP90_FLAG_DONT_STOP ponieważ BP90_FLAG_DONT_STOP nie jest ustawiona, jeśli punktu śledzenia wykonuje makra.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)