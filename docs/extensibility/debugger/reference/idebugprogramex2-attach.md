---
title: IDebugProgramEx2::Attach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 440a4ce6b008efe541187d1d99d886f4c7c5f9ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Dołącz sesji programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który reprezentuje funkcję wywołania zwrotnego, który aparat debugowania dołączone wysyła zdarzenia do.  
  
 `dwReason`  
 [in] Wartość z zakresu od [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) wyliczenie opisujące przyczynę operacji dołączania.  
  
 `pSession`  
 [in] Wartość, która unikatowo identyfikuje sesji, która jest dołączenie do programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Ta metoda powinna zwrócić `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` Jeśli program jest już dołączony.  
  
## <a name="remarks"></a>Uwagi  
 Port, który zawiera program można użyć wartości w `pSession` do określenia, które sesji próbuje dołączyć do programu. Na przykład jeśli port zezwala na tylko jedną debugowanie można dołączyć do procesu w czasie, port można określić, jeśli ta sama sesja jest już dołączony do innych programów w procesie.  
  
> [!NOTE]
>  Przekazany interfejs `pSession` powinien być traktowany jako plik cookie wartość, która unikatowo identyfikuje Menedżera debugowania sesji dołączania do tego programu; żaden z metod interfejsu podany nie jest funkcjonalności.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)