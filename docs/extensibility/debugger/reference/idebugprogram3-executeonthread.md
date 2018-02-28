---
title: IDebugProgram3::ExecuteOnThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 649b16c1b57b2f66772c2117b776e6b79ad862be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Wykonuje program debugera. Wątek jest zwracana do przekazywania informacji debugera w wątku, w którym użytkownik jest wyświetlana podczas wykonywania programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Istnieją trzy różne sposoby wznowić wykonywanie po zatrzymaniu debugera:  
  
-   Wykonaj: Anulowanie wszelkich w poprzednim kroku, a następnie uruchom aż do następnego punktu przerwania i tak dalej.  
  
-   Krok: Anuluj każdy krok starego i uruchomić do momentu ukończenia nowy krok.  
  
-   Nadal: Uruchom ponownie i pozostawianie aktywnej każdy krok stary.  
  
 Wątek przekazany do `ExecuteOnThread` jest przydatne podczas podejmowania decyzji o którym krok, aby anulować. Jeśli nie znasz wątek uruchamiający wykonania anuluje wszystkie kroki. Znajomości wątku wystarczy anulować krok w aktywnym.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonanie](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)