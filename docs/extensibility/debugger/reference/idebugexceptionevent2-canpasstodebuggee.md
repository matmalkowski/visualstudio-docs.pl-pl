---
title: IDebugExceptionEvent2::CanPassToDebuggee | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0ffea7be736cbf6d04c368ba6124d0faf22be61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Określa, czy aparat debugowania (DE) obsługuje opcja przekazywania ten wyjątek do debugowanego po wznowieniu pracy wykonywania programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną `S_OK` (wyjątek mogą zostać przekazane do programu) lub `S_FALSE` (wyjątku nie można przekazać).  
  
## <a name="remarks"></a>Uwagi  
 Niemcy musi mieć domyślnego działania dla przekazywanie do obiektu debugowanego. Może pojawić się IDE [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) zdarzeń i wywołanie [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metody bez wywoływania `CanPassToDebuggee` — metoda. W związku z tym DE powinien mieć przypadku domyślnego przekazywania wyjątek lub nie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)