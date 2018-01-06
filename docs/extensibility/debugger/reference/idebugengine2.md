---
title: IDebugEngine2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2
helpviewer_keywords: IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 95a1a8c48bd6eab0f21ccc85a125b5d10f42ef4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2"></a>IDebugEngine2
Ten interfejs reprezentuje aparat debugowania (DE). Służy zarządzania różnych aspektów sesji debugowania, od utworzenia punktów przerwania do ustawiania i czyszczenia wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez niestandardowe DE do zarządzania debugowanie programów. Ten interfejs musi być implementowana przez Niemcy.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest wywoływana przez menedżera sesji debugowania (SDM) do zarządzania sesji debugowania, w tym Zarządzanie wyjątkami, tworzenie punktów przerwania i odpowiada na wysyłane przez DE zdarzenia synchroniczne.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugEngine2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Tworzy moduł wyliczający dla wszystkich programów, które jest debugowane URZ.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Dołącza URZ do programu.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Tworzy oczekującym punktem przerwania w DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Określa sposób obsługi DE dany wyjątek.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Usuwa określony wyjątek, aby nie jest już obsługiwany przez aparat debugowania.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Usuwa listy wyjątków ustawione dla konkretnego środowiska wykonawczego architektura lub języka IDE.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Pobiera identyfikator GUID DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informuje, DE, że nietypowo zakończone określonego programu, a DE należy wyczyścić wszystkie odwołania do programu i wysyłać programu zniszczyć zdarzeń.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Metoda wywoływana przez SDM, aby wskazać, że zdarzenia synchroniczne debugowania wcześniej wysłanego przez Niemcy do SDM, został odbierany i przetwarzany.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Ustawia DE ustawień regionalnych.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Ustawia katalog główny rejestru aktualnie używany przez Niemcy.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Ustawia metryki.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Żądania, że wszystkie programy, które jest debugowane tego DE zatrzymuje wykonywanie przy następnym jednej z ich wątków próbuje uruchomić.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)