---
title: IDebugProgram2::CauseBreak | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::CauseBreak
helpviewer_keywords: IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48029ed4e925073b0d121a88846aa2f0af0a51cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Czy program zatrzymuje wykonywanie kolejnego żądania czasu jednego z jego próby uruchomienia wątków.  
  
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
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) zdarzeń jest wysyłany, gdy program obok podejmie próbę uruchomienia kodu po ta metoda jest wywoływana.  
  
 Ta metoda jest asynchroniczne, metoda zwraca się natychmiast bez niekoniecznie oczekiwanie na zatrzymanie programu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)