---
title: IDebugProcess3 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 89fc02ecec75d229b4cb743b9d1f4b2b0857ddc2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3"></a>IDebugProcess3
Ten interfejs reprezentuje uruchomionego procesu i jego programów. Ten interfejs istnieje zastępuje kilka metod w [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu. Zapewnia kontrolę nad wszystkie programy w procesie.  
  
> [!NOTE]
>  [Kontynuować](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), i [krok](../../../extensibility/debugger/reference/idebugprogram2-step.md) metody są przestarzałe i nie powinna być używana. Użyj odpowiedniej metody na `IDebugProcess3` zamiast tego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawcę niestandardowego numeru portu do zarządzania programami jako grupa. Gdy programy są zarządzane jako grupę, można kontrolować ich wykonanie i ustanowienia język dla ewaluatora wyrażeń. Ten interfejs musi być implementowana przez dostawcę portu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest wywoływana przede wszystkim przez Menedżera debugowania sesji (SDM) w celu interakcji z grupy programów, które zostały zidentyfikowane w tym procesie.  
  
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfejs do uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz dziedziczone z metody [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementuje następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Kontynuuje wykonywanie lub wykonywanie krok po kroku w procesie.|  
|[Wykonanie](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Rozpoczyna wykonanie procesu.|  
|[Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Kroki przekazywania jednej instrukcji lub instrukcji w procesie.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Pobiera przyczyny, że proces został uruchomiony do debugowania.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Określa język hostingu, tak, aby aparat debugowania mogą ładować ewaluatora wyrażenia odpowiednie.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Pobiera język aktualnie ustawione dla tego procesu.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Wyłącza funkcję Edytuj i Kontynuuj (ENC) dla tego procesu.<br /><br /> Dostawcy niestandardowego numeru portu nie implementuje tę metodę (zawsze powinien zwrócić `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Pobierz stan ENC dla tego procesu.<br /><br /> Dostawcy niestandardowego numeru portu nie implementuje tę metodę (zawsze powinien zwrócić `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Pobiera tablicę unikatowych identyfikatorów dla aparatami debugowania dostępne.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)