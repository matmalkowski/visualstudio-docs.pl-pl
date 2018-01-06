---
title: IDebugCanStopEvent2::GetReason | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::GetReason
helpviewer_keywords: IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 934ae1192a76cd7bd090c0cf2db384d28b61d6df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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