---
title: IDebugQueryEngine2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugQueryEngine2
helpviewer_keywords: IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a54b6f6ab5667993553074f1ca2511a544a0eaea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Ten interfejs umożliwia sesji debugowania manager (SDM) pobrać interfejs, który reprezentuje aparat debugowania (DE).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs na obiektach, które implementują interfejsy DE najbardziej typowe (takich jak [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), i [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) w Aby zezwolić na dostęp do [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejsu DE, do samej siebie.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) typowe interfejs DE, aby uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugQueryEngine2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Pobiera interfejs (DE) Aparat debugowania niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest zwykle implementowany w obiekcie, który implementuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu w celu zapewnienia obsługi uporządkowane przyczynowości krokowe wykonywanie funkcji, oznacza to, gdy debuger jest krokowe wykonywanie funkcji, Funkcja Next do wykonania nie może być poprzedniej funkcji na stosie, ale funkcja w innym wątku całkowicie. Dla definicji "przyczynowości", zobacz [programu Visual Studio Debugger słownik](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)