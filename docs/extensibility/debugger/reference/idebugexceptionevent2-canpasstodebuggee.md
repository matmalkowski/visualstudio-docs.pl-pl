---
title: IDebugExceptionEvent2::CanPassToDebuggee | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords: IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef10fd3ca7f41c2afd1c827fb71ca2178782e3d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)