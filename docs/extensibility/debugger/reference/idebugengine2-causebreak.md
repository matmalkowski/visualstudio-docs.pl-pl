---
title: IDebugEngine2::CauseBreak | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ba10e167246ce2467f2faebf157e46306749bdb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105213"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Wszystkie programy jest debugowane ten aparat debugowania (DE), aby zatrzymać wykonanie przy następnym żądań, jeden z wątków ich podejmie próbę uruchomienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest asynchroniczne: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) zdarzeń jest wysyłany, gdy program obok podejmuje próbę wykonania po ta metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)