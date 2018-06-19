---
title: IDebugCanStopEvent2::GetReason | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c0eaefee714467084898182b338ceda63ebdc0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101992"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Pobiera przyczynę, dlaczego chce zatrzymać aparat debugowania (DE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcr`  
 [out] Zwraca wartość z zakresu od [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) wyliczenie opisujące przyczynę tego zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest zazwyczaj wywoływana przed [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metody, wywołujący można określić, czy do przekazania różna od zera (`TRUE`) do `IDebugCanStopEvent2::CanStop` metody.  
  
 Przyczyna zatrzymania mogą być `CANSTOP_ENTRYPOINT`, co oznacza, że DE został osiągnięty punkt wejścia lub `CANSTOP_STEPIN`, co oznacza, że DE opuścił funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [Wartości właściwości CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)