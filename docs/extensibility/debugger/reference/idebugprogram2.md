---
title: IDebugProgram2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7f02d099fe680006966219bb626e17bc7a7114b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2"></a>IDebugProgram2
Ten interfejs reprezentuje program, który działa w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) i dostawcy niestandardowego numeru portu należy zaimplementować ten interfejs do reprezentowania program w procesie. Menedżer debugowania sesji (SDM) również implementuje ten interfejs, aby zapewnić informacje [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzeń zwraca ten interfejs dla nowy program. Ten interfejs jest również używany jako parametr dla wielu metod w wielu interfejsach.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProgram2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Wylicza wątków, które są uruchomione w tym programie.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Pobiera nazwę programu.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Pobiera proces tego programu.|  
|[Zakończenie](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Przerywa ten program.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Dołącza do tego programu.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Określa, czy aparat debugowania (DE) można odłączyć od program.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Odłącza debugera z tego programu.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Pobiera unikatowy identyfikator globalny tego programu.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Pobiera program właściwości.|  
|[Wykonanie](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Jest nadal uruchomiony ten program w stanie zatrzymania. Wszelkie poprzedniego stanu wykonywania jest wyczyszczone.|  
|[Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Jest nadal uruchomiony ten program w stanie zatrzymania. Zachowana jest żadnych poprzedniego stanu wykonywania.|  
|[Krok](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje kroku.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Czy ten program zatrzymuje wykonywanie kolejnego żądania czasu jednego z jego uruchomienie wątków kodu.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Pobiera nazwę i identyfikator aparat debugowania (DE) uruchomieniem tego programu.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Wylicza kontekstów kodu dla danej pozycji w pliku źródłowym.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Pobiera liczbę bajtów pamięci dla tego programu.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Pobiera strumień dezasemblacji dla tego programu lub częścią tego programu.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Wylicza modułów, w których ten program został załadowany i jest wykonywany.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Pobiera aktualizację Edytuj i Kontynuuj (ENC) dla tego programu.<br /><br /> Aparat debugowania niestandardowych nie implementuje tę metodę (zawsze powinien zwrócić `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Wylicza same ścieżki kodu tego programu.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Zapisuje plik zrzutu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Uwagi  
 Program jest kontenerem wątku uruchomiony w ramach określonej architektury środowiska wykonawczego podczas procesu składa się z jednego lub wielu programów.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)