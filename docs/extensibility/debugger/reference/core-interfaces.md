---
title: Podstawowe interfejsy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 367917032b836ce6a7d07cf3eba85db14464a957
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="core-interfaces"></a>Interfejsy Core
Następujące interfejsy są interfejsów podstawowych do rozszerzania debugera za pomocą [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Omówienie  
 Te interfejsy są głównie używane do tworzenia aparat debugowania (DE). Są tu zorganizowane według kategorii:  
  
-   [Punkty przerwania](#Breakpoints)  
  
-   [Konteksty](#Contexts)  
  
-   [W trybie Server Core](#CoreServer)  
  
-   [Aparaty debugowania](#DebugEngines)  
  
-   [Dokumenty](#Documents)  
  
-   [Zdarzenia](#Events)  
  
-   [Wyrażenia](#Expressions)  
  
-   [Pamięci](#Memory)  
  
-   [Moduły](#Modules)  
  
-   [Porty](#Ports)  
  
-   [Procesy](#Processes)  
  
-   [Programy](#Programs)  
  
-   [Właściwości](#Properties)  
  
-   [Ramki stosu](#StackFrames)  
  
-   [Wątki](#Threads)  
  
-   [Wizualizatorach typu](#TypeVisualizers)  
  
 Obiekty, które można zaimplementować interfejsów to:  
  
-   Debugowanie aparat (DE)  
  
-   Port dostawcy (PS)  
  
-   Ewaluator wyrażeń (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a>Punkty przerwania  
 Te interfejsy są powiązane do implementacji i śledzenia punktów przerwania.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|NIEMCY|Reprezentuje punkt przerwania powiązany z lokalizacji w pamięci.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|NIEMCY|Wysyłany przez DE, gdy punkt przerwania jest powiązany z lokalizacji w pamięci.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Reprezentuje dokumentu sumy kontrolnej dla żądania punktu przerwania.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|NIEMCY|Wysyłane przez DE, gdy punkt przerwania nie może być powiązane z lokalizacji w pamięci.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|NIEMCY|Wysyłane przez DE, po osiągnięciu punktu przerwania.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Reprezentuje żądanie dla punktu przerwania; używany podczas tworzenia oczekującym punktem przerwania.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Reprezentuje żądanie dla punktu przerwania; używany podczas tworzenia oczekującym punktem przerwania.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|NIEMCY|Reprezentuje informacje używane do powiązania punktu przerwania.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|NIEMCY|Wysyłany przez DE, gdy punkt przerwania jest niezwiązany z lokalizacji w pamięci.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|NIEMCY|Reprezentuje nieprawidłowy punkt przerwania (zwrócony przez `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|NIEMCY|Reprezentuje informacje rozpoznawania nieprawidłowy punkt przerwania.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|NIEMCY|Reprezentuje pozycji w funkcji, w których ustawiony jest punkt przerwania.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|NIEMCY|Reprezentuje punkt przerwania, który ma zostać powiązany; używany podczas tworzenia powiązania punktu przerwania.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|NIEMCY|Reprezentuje wyliczenie w zestawie powiązane punkty przerwania.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|NIEMCY|Reprezentuje wyliczenie dla zestawu punktów kontrolnych, które nie może być powiązane z lokalizacji w pamięci.|  
  
##  <a name="Contexts"></a>Konteksty  
 Te interfejsy reprezentuje różne rodzaje kontekstów w programie debugowany.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|NIEMCY|Reprezentuje pozycję początkową instrukcji kodu.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|NIEMCY|Rozszerza [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfejsu, aby włączyć pobieranie interfejsów modułu i procesu.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|PROGRAMU VS, DE|Reprezentuje pozycji w dokumencie.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|NIEMCY|Reprezentuje kontekst, w którym można obliczyć wyrażenia.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|NIEMCY|Reprezentuje początkowy lokalizacji w pamięci to zbiór bajtów.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|NIEMCY|Reprezentuje kontekst ramki stosu w punkcie przerwania lub wyjątku.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|NIEMCY|Reprezentuje kontekst ramki stosu w punkcie przerwania lub wyjątku.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|NIEMCY|Reprezentuje wyliczenie w zestawie kontekstów kodu.|  
  
##  <a name="CoreServer"></a>W trybie Server Core  
 Te interfejsy reprezentować komputer, na którym jest debugowany program. Są one zaimplementowane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , ale może być wywoływana w przez aparaty debugowania.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Zapewnia dostęp do portów i dostawców portu, a także informacje o komputerze.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Reprezentuje [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) obsługującej zdalnego debugowania.|  
  
##  <a name="DebugEngines"></a>Aparaty debugowania  
 Te interfejsy reprezentują aparatami debugowania i ich skojarzonych zdarzeniach.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|NIEMCY|Reprezentuje aparat debugowania niestandardowych.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|NIEMCY|Reprezentuje aparat debugowania niestandardowego, który obsługuje ładowanie symboli, JustMyCode i wyjątki.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|NIEMCY|Wysyłane przez każdego nowego wystąpienia DE wskazująca, że jest gotowy do obsługi zadań debugowania.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|NIEMCY|Reprezentuje aparat debugowania niestandardowego, który obsługuje uruchamiania programów.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|NIEMCY, PS|Reprezentuje węzeł program, który obsługuje wielu aparaty debugowania.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|NIEMCY|Umożliwia SDM można uzyskać interfejsu do aparatu debugowania z wątku, program lub ramki stosu.|  
  
##  <a name="Documents"></a>Dokumenty  
 Te interfejsy reprezentują dokumenty (pliki źródłowe) i ich skojarzonych elementów.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|NIEMCY|Wysyłany przez Niemcy do żądania można otworzyć dokumentu.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|NIEMCY|Reprezentuje strumienia asemblerze instrukcji z dokumentu.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|PROGRAMU VS, DE|Reprezentuje dokumentu dostarczonych przez DE, określając nazwę i identyfikator klasy (CLSID).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|NIEMCY, EE|Reprezentuje sumy kontrolnej dla dokumentu debugowania i umożliwia przekazywanie sumy kontrolnej między składnikami.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|PROGRAMU VS, DE|Reprezentuje kontekst dokumentu, pozycja w dokumencie odpowiadający określonym kontekście instrukcji i kod.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|PROGRAMU VS, DE|Reprezentuje ogólne pozycji w dokumencie.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Reprezentuje pozycji w pliku źródłowym jako przesunięcie znaków.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|PROGRAMU VS, DE|Reprezentuje dokument tekstowy dostarczonych przez DE (pochodną [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), podając tekstu.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|NIEMCY|Wysyłane przez DE, aby określić zmiany do pliku źródłowego, który znajduje się w pamięci.|  
  
##  <a name="Events"></a>Zdarzenia  
 Te interfejsy reprezentuje wszystkie zdarzenia, które są przesyłane między Urządzeniom i Menedżer debugowania sesji (SDM).  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|NIEMCY|Wysyłany przez Niemcy do żądania można otworzyć dokumentu.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|NIEMCY|Aparat debugowania (DE) wysyła ten interfejs do menedżera sesji debugowania (SDM), aby ustawić stan paska komunikatów podczas obciążenia symbolu.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|NIEMCY|Wysyłane przez DE podział w programie została ukończona.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|NIEMCY|Wysyłany przez DE, gdy punkt przerwania jest powiązany.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|NIEMCY|Wysyłany przez DE, gdy nie można powiązać punktu przerwania.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|NIEMCY|Wysyłane przez DE, po osiągnięciu punktu przerwania.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|NIEMCY|Wysyłany przez DE, gdy punkt przerwania jest niepowiązany.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|NIEMCY|Wysyłane przez DE, aby określić, czy należy zatrzymać w określonej lokalizacji.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|NIEMCY|Wysyłane przez DE, aby określić zmiany do pliku źródłowego, który znajduje się w pamięci.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|NIEMCY|Wysyłane przez każdego nowego wystąpienia DE wskazująca, że jest gotowy do obsługi zadań debugowania.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|NIEMCY|Wysyłane przez DE, aby wskazać, że debugowany program jest gotowy do wykonania pierwszej instrukcji.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|NIEMCY|Interfejs, który jest używany przez inne interfejsy zdarzeń, które mogą zwracać błąd, aby zapewnić czytelny dla człowieka komunikaty.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|NIEMCY, PS|Interfejs podstawowy, z których wszystkie inne zdarzenia są uzyskiwane interfejsów.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Reprezentuje interfejs implementowany przez SDM, do którego są wysyłane zdarzenia (wyrażony jako obiekty implementowania interfejsu danego zdarzenia).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|NIEMCY|Wystąpił wyjątek w programie debugowany wysyłane przez Niemcy.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|NIEMCY|Wysyłane przez DE, po zakończeniu asynchronicznego wyrażenia.|  
|IDebugFindSymbolEvent2||PRZESTARZAŁE. NIE UŻYWAJ.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|NIEMCY|Wysyłane przez DE przetwarzanie wyjątku przechwycone zostało ukończone.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|NIEMCY|Wysyłany przez DE, gdy program zakończeniu ładowania.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|NIEMCY|Wysyłane przez DE wyświetlone IDE komunikat informacyjny dla użytkownika.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|NIEMCY|Wysyłane przez DE, podczas ładowania lub zwalnianie modułu.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|NIEMCY|Sygnały [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugera interfejsu użytkownika z ostrzeżeniem, że symboli nie można zlokalizować dla uruchomionego pliku wykonywalnego.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|NIEMCY|Wysyłane przez DE wyświetlone IDE dowolny ciąg.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PROGRAMU VS, DE|Wysyłane przez port do przekazywania zdarzenia portu żadnych odbiornika.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|NIEMCY, PS|Wysyłany przez DE lub portu, gdy proces został utworzony.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|NIEMCY, PS|Wysyłany przez DE lub portu, gdy proces został zlikwidowany.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|NIEMCY, PS|Wysyłany przez DE lub portu, gdy program został utworzony.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|NIEMCY, PS|Wysyłany przez DE lub portu, gdy program został zlikwidowany.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|NIEMCY|Umożliwia to aparat debugowania zastąpić domyślne zachowanie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika podczas kończenia sesji debugowania.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|NIEMCY|Wysyłane z aparatu debugowania (DE) z menedżerem sesji debugowania (SDM) po zmianie nazwy programu.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|NIEMCY|Wysyłany przez DE, gdy nową właściwość (reprezentowane przez `IDebugProperty2` interfejsu) został utworzony.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|NIEMCY|Wysyłany przez DE, gdy właściwość został zlikwidowany.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|NIEMCY|Wysyłane przez DE przy przechodzeniu poza lub za pośrednictwem funkcji, dlatego zwracana wartość mogą być niepoprawnie wyświetlane.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Włącza debugowanie aparaty można odczytać ustawień metryki zdalnie.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|NIEMCY|Wysyłane przez DE, po wykonaniu kroku do, za pośrednictwem lub z instrukcji.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|NIEMCY|Wysyłane przez Niemcy w celu wskazania powodzenia lub niepowodzenia ładowania symboli dla modułu.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|NIEMCY|Wysyłany przez DE, gdy wątek został utworzony.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|NIEMCY|Wysyłany przez DE, gdy wątek został zlikwidowany.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|NIEMCY|Wysyłany przez DE, gdy wątek została zmieniona jego nazwa.|  
  
##  <a name="Expressions"></a>Wyrażenia  
 Te interfejsy reprezentują wyrażeń, które ma zostać obliczone dla danego kontekstu.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|NIEMCY|Reprezentuje wyrażenie do obliczenia. Uzyskane z [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|NIEMCY|Reprezentuje kontekst, w jakiej są oceniane wyrażenie. Uzyskane z [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|NIEMCY|Wysyłane przez DE, po zakończeniu asynchronicznego wyrażenia.|  
  
##  <a name="Memory"></a>Pamięci  
 Te interfejsy reprezentowania sekwencji bajtów w pamięci.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|NIEMCY|Reprezentuje sekwencję bajtów w pamięci, która może być z zapisu lub odczytu.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|NIEMCY|Reprezentuje lokalizację w pamięci sekwencji bajtów.|  
  
##  <a name="Modules"></a>Moduły  
 Te interfejsy reprezentują moduł, który odpowiada plik wykonywalny lub. Plik DLL.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|NIEMCY|Reprezentuje pojedynczy plik wykonywalny lub biblioteka DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|NIEMCY|Reprezentuje [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) obsługującej symboli.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|NIEMCY|Wysyłane przez DE, podczas ładowania lub zwalnianie modułu.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|NIEMCY|Reprezentuje informacji o serwerze źródłowym, który jest zawarty w pliku PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|NIEMCY|Reprezentuje wyliczenie dla zestawu modułów, które są określane przez [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a>Porty  
 Te interfejsy reprezentują portów i portu dostawcy.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|PROGRAMU VS, PS|Reprezentuje domyślny port na komputerze lokalnym.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Umożliwia to aparat debugowania, który używa modelu DCOM, aby zadać [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika, aby upewnić się, że Zapora nie blokuje debugowanie zdalne.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|PROGRAMU VS, PS|Reprezentuje port.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Wysyłane przez port do przekazywania zdarzenia portu żadnych odbiornika.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Reprezentuje port, który można uruchomić i zakończenie procesów.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Używany do rejestrowania i wyrejestrowania programy z portem; Umożliwia portu do śledzenia aktualnie debugowanych programów.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Reprezentuje dostosowany interfejs użytkownika wyboru portu.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Reprezentuje żądanie dla portu, w którym zostanie utworzony lub znajduje się nowy port.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Reprezentuje dostawcę portów.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Reprezentuje dostawcę portów, które można utrwalić (Zapisz na dysku) informacji o portach go utworzyć.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Umożliwia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika Służącego do wyświetlania tekstu wewnątrz **informacji transportu** sekcji **dołączyć do procesu** okno dialogowe.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Umożliwia wykonanie zapytania dotyczącego informacji o komputerze docelowym.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|PROGRAMU VS, PS|Reprezentuje wyliczenie dla zestawu portów.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Reprezentuje wyliczenie w zestawie portu dostawcy.|  
  
##  <a name="Processes"></a>Procesy  
 Te interfejsy reprezentują procesów, pojedynczy plik wykonywalny, który zawiera jeden lub więcej programów.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Reprezentuje proces, który jest uruchomiony na komputerze.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Reprezentuje proces, który obsługuje aktywnie debugowania (używany do zastępowania krok, kontynuować i wykonywanie metod na [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejs).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|NIEMCY, PS|Wysyłany przez DE lub portu, gdy proces został utworzony.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|NIEMCY, PS|Wysyłany przez DE lub portu, gdy proces został zlikwidowany.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Reprezentuje proces, który musi śledzić sesji, który jest dołączony do niego.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Reprezentuje wyliczenie zestaw procesów na porcie.|  
  
##  <a name="Programs"></a>Programy  
 Te interfejsy reprezentują programy, jednostki logiczne wykonywania, które nie muszą odpowiadać fizycznego pliku wykonywalnego lub modułu.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|NIEMCY|Reprezentuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) która musi działać w porozumieniu z innych programów debugowany w tym samym czasie.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|NIEMCY, PS|Reprezentuje jednostkę logiczną wykonywania.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|NIEMCY, PS|Wysyłany przez DE lub portu, gdy program został utworzony.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|NIEMCY, PS|Wysyłany przez DE lub portu, gdy program został zlikwidowany.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|NIEMCY, PS|Reprezentuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) mogą być obsługiwane przez wiele aparaty debugowania.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Reprezentuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) który musi mieć możliwość śledzenia sesji, który jest dołączony do niego.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|NIEMCY, PS|Reprezentuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) które zwracają informacje na temat procesu, w którym jest uruchomiony.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|NIEMCY, PS|Reprezentuje program, który może być debugowany.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|NIEMCY, PS|Umożliwia węzła program ma być powiadamiany o podjęto próbę dołączenia do skojarzonego programu.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|NIEMCY|Umożliwia SDM zbadać DE o programach steruje tym DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Używany przez DEs rejestrowania programy z SDM, że są debugowane.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|NIEMCY, PS|Reprezentuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) która może kierować interfejsów w granicach wątku lub procesu.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|NIEMCY, PS|Reprezentuje wyliczenie zestaw programów.|  
  
##  <a name="Properties"></a>Właściwości  
 Te interfejsy reprezentuje właściwości i wartość skojarzoną z określonym kontekstem, zazwyczaj wynikiem wyrażenia.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Reprezentuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) wyświetlający jego wartość w niestandardowy sposób.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|NIEMCY|Reprezentuje wartość ramki stosu, dokumentu lub wynik Obliczanie wyrażenia.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|NIEMCY|Reprezentuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obsługującej arbitralnie długich ciągów.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|NIEMCY|Wysyłany przez DE, gdy nową właściwość (reprezentowane przez [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejsu) został utworzony.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|NIEMCY|Wysyłany przez DE, gdy właściwość został zlikwidowany.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|NIEMCY|Reprezentuje odwołanie do właściwości, które mogą znajdować się poza żadnej ramce stosu określonego.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|NIEMCY|Reprezentuje wyliczenie w zestawie [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury, których opisano zmienne, rejestrów, parametry i wyrażenia.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|NIEMCY|Reprezentuje wyliczenie w zestawie [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury.|  
  
##  <a name="StackFrames"></a>Ramki stosu  
 Te interfejsy reprezentują ramki stosu, kontekst, w której punkt przerwania lub wyjątek wystąpił.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|NIEMCY|Reprezentuje kontekst, w której punkt przerwania lub wyjątek wystąpił.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|NIEMCY|Reprezentuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) które może obsłużyć przechwyceniu wyjątków.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|NIEMCY|Reprezentuje wyliczenie nad zestaw [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) struktury, które określają funkcji wywołania używane w ramce stosu określonej sekwencji.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|NIEMCY|Reprezentuje wyliczenie w zestawie [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktur, które opisują ramki stosu.|  
  
##  <a name="Threads"></a>Wątki  
 Te interfejsy reprezentują wątków i ich skojarzonych zdarzeniach.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|NIEMCY|Reprezentuje wykonanie wątku.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|NIEMCY|Wysyłany przez DE, gdy wątek został utworzony.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|NIEMCY|Wysyłany przez DE, gdy wątek został zlikwidowany.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|NIEMCY|Wysyłany przez DE, gdy wątek została zmieniona jego nazwa.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|NIEMCY|Reprezentuje wyliczenie w zestawie wątków.|  
  
##  <a name="TypeVisualizers"></a>Wizualizatorach typu  
 Te interfejsy zapewniają obsługę wizualizatorach typu. Te interfejsy są zwykle implementowany przez ewaluatora wyrażeń.  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Reprezentuje tablicę bajtów, które mają być przedstawiane wizualizatora typu.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Udostępnia metody do uzyskiwania dostępu do danych do przekazania do wizualizatora typu.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Reprezentuje właściwość, która zapewnia dostęp do [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implementacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Tworzenie aparat debugowania niestandardowych](../../../extensibility/debugger/creating-a-custom-debug-engine.md)