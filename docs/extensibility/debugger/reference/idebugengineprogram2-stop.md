---
title: IDebugEngineProgram2::Stop | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4004ca92b32e63565a71a3a6971ebb4ae073b9f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Zatrzymuje wszystkie wątki uruchomione w tym programie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, gdy ten program jest debugowany w środowisku wielu programów. Po odebraniu zdarzeniem zatrzymującym z inny program, ta metoda jest wywoływana dla tego programu. Implementacja tej metody powinna być asynchroniczne; oznacza to, że nie wszystkie wątki należy wymagać być zatrzymana zanim ta metoda zwraca wartość. Implementacja tej metody może być równie proste co wywołanie [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) metody dla tego programu.  
  
 Brak zdarzenia debugowania jest wysyłany w odpowiedzi na tę metodę.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)