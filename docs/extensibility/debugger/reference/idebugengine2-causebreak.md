---
title: IDebugEngine2::CauseBreak | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::CauseBreak
helpviewer_keywords: IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eeb8c262d6e1abc88e40f027d921ae2d4ae12cf2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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