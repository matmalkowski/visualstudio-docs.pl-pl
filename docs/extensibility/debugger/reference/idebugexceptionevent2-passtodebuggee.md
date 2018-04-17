---
title: IDebugExceptionEvent2::PassToDebuggee | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8e6b53a07f191d967bbd676e6fcfc96b53dc14
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Określa, czy wyjątek powinny być przekazywane do programu debugowany po wznowieniu pracy wykonywania, czy wyjątek powinien zostać odrzucone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fPass`  
 [in] Różna od zera (`TRUE`) Jeśli wyjątek powinien zostać przekazany do debugowanego, po wznowieniu pracy wykonanie programu, lub wartość zero (`FALSE`) Jeśli wyjątek powinien zostać odrzucone.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej metody nie faktycznie powoduje dowolny kod do wykonania w programie debugowany. Wywołanie jest tylko do ustawiania stanu dalej wykonywanie kodu. Na przykład wywołań [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) metoda może zwracać `S_OK` z [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` wartość pola `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 Może pojawić się IDE [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) zdarzeń i wywołanie [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md) metody. Aparat debugowania (DE) ma domyślne zachowanie do obsługi w przypadku, gdy `PassToDebuggee` nie jest wywoływana metoda.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)