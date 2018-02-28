---
title: "Przegląd debugowania skryptów aktywnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9aebdc3f8fa4df0f4386609e632e1a8611c87f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-debugging-overview"></a>Przegląd debugowania aktywnego skryptu
Interfejsy debugowania skryptów aktywnych zezwolenia na debugowanie niezależny od języka, niezależny od hosta i obsługuje szeroką gamę środowisk deweloperskich.  
  
 ![Proces hosta skryptów](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Rysunek 1  
  
 Środowisku debugowania niezależny od języka może obsługiwać dowolnego języka lub różnych języków programowania, bez informacji o dowolnej z tych języków programowania. Środowisko debugowania obsługuje również krokowe wykonywanie wielu języków oraz punktów przerwania. (W tym omówieniu skupiono się głównie na obsługę języków, takich jak VBScript skryptów i [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].)  
  
 Debuger niezależny od hosta można automatycznie z dowolnym hostem wykonywanie aktywnych skryptów, takich jak program Internet Explorer lub hosta niestandardowego. Kontrolki hosta debuger stanowi dla użytkownika, struktura drzewa dokumentu z zawartością i kolorowanie składni dokumentów debugowania. Dzięki temu kod źródłowy debugowanym ma być wyświetlany w kontekście dokumentu hosta. Na przykład program Internet Explorer można wyświetlać skrypt na stronie HTML.  
  
 W poniższych podsekcjach omówiono poszczególnych składników klucza Active debugowania i skojarzone interfejsy. Jednak przed kontynuacją, muszą być zdefiniowane kilka kluczowych założeń Active debugowania:  
  
 Host aplikacji  
 Aplikacji, która obsługuje skrypt silników i udostępnia skryptowe zestaw obiektów (lub "model obiektów").  
  
 aparat języka  
 Składnik, który zapewnia analizy, wykonanie i debugowanie obiektów abstrakcyjnych odpowiadających określonym języku.  
  
 Debuger IDE  
 Aplikacja, która umożliwia debugowanie interfejsu użytkownika przy komunikacji z aparaty aplikacji i języka hosta.  
  
 Menedżer debugowania maszyny  
 Składnik, który przechowuje rejestr procesów możliwością debugowania aplikacji.  
  
 Menedżer debugowania procesu  
 Składnik, który przechowuje drzewa możliwością debugowania dokumentów dla określonej aplikacji, śledzi uruchomionych wątków i tak dalej.  
  
 kontekstu dokumentu  
 Kontekstu dokumentu jest abstrakcję reprezentujący określonego zakresu w kodzie źródłowym dokumentu hosta.  
  
 kontekst kodu  
 Kontekst kodu reprezentuje określonej lokalizacji w uruchomiony kod języka silnika ("wskaźnik instrukcji wirtualne".)  
  
 kontekst wyrażenia  
 Określonego kontekstu (na przykład ramki stosu) w którym mogą być oceniane wyrażenia przez aparat języka.  
  
 Przeglądanie obiektu  
 Strukturalne, niezależny od języka reprezentacja obiektu nazwę, typ, wartość i podobiektów odpowiedniego stosowania "okna czujki" interfejsu użytkownika.  
  
 Poniżej przedstawiono najważniejsze składniki Active debugowania i odpowiednie skojarzone interfejsy, następuje szczegóły tych interfejsów.  
  
## <a name="language-engine"></a>Aparat języka  
 Zapewnia aparat języka:  
  
-   Analiza kodu języka i wykonywanie.  
  
-   Obsługa debugowania (punkty przerwania i tak dalej).  
  
-   Obliczanie wyrażenia.  
  
-   Kolorowanie składni.  
  
-   Obiekt przeglądania.  
  
-   Wyliczenie stosu i analizowania.  
  
 Poniżej przedstawiono interfejsów, które aparat skryptu musi obsługiwać zapewnienie debugowania, wyrażenia i przeglądanie obiektu. Te interfejsy są używane przez aplikację hosta do mapowania jej kontekstu dokumentu i konteksty kodu aparatu, również przez debuger interfejsu użytkownika w celu oceny wyrażenia stosu wyliczenia oraz obiekt przeglądania.  
  
 [Interfejs IActiveScriptDebug](../winscript/reference/iactivescriptdebug-interface.md)  
 Zawiera wyliczenie kontekstu kolorowanie i kod składni.  
  
 [Interfejs IActiveScriptErrorDebug](../winscript/reference/iactivescripterrordebug-interface.md)  
 Zwraca dokumentu konteksty i ramek stosu błędów.  
  
 [Interfejs IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md)  
 Łącze hosta dostarczone z aparatu skryptu do debugera.  
  
 [Interfejs IDebugCodeContext](../winscript/reference/idebugcodecontext-interface.md)  
 Udostępnia wirtualny "wskaźnik instrukcji" w wątku.  
  
 [Interfejs IEnumDebugCodeContexts](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 Wylicza kontekstach kodu, które odpowiadają kontekstu dokumentu.  
  
 [Interfejs IDebugStackFrame](../winscript/reference/idebugstackframe-interface.md)  
 Reprezentuje ramka stosu logiczne na stosie wątku.  
  
 [Interfejs IDebugExpressionContext](../winscript/reference/idebugexpressioncontext-interface.md)  
 Udostępnia kontekst, w którym można oszacować wyrażenia.  
  
 [Interfejs IDebugStackFrameSniffer](../winscript/reference/idebugstackframesniffer-interface.md)  
 Zapewnia sposób wyliczyć ramek stosu logiczne.  
  
 [Interfejs IDebugExpression](../winscript/reference/idebugexpression-interface.md)  
 Reprezentuje asynchronicznie obliczane wyrażenie.  
  
 [Interfejs IDebugSyncOperation](../winscript/reference/idebugsyncoperation-interface.md)  
 Udostępnia aparat skryptu abstrakcyjnej operację, która musi zostać wykonana podczas zagnieżdżona w szczególności wątku zablokowanych.  
  
 [Interfejs IDebugAsyncOperation](../winscript/reference/idebugasyncoperation-interface.md)  
 Udostępnia asynchroniczne operacji synchronicznych debugowania.  
  
 [Interfejs IDebugAsyncOperationCallBack](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 Zawiera stan zdarzenia związane z postęp `IDebugAsyncOperation` interfejsu oceny.  
  
 [Interfejs IEnumDebugExpressionContexts](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 Wylicza Kolekcja `IDebugExpressionContexts` obiektów.  
  
 [Interfejs IProvideExpressionContexts](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 Umożliwia wyliczenie znane przez składnik niektórych kontekstach wyrażenia.  
  
 [Interfejs IDebugFormatter](../winscript/reference/idebugformatter-interface.md)  
 Umożliwia języka lub IDE dostosować konwersji wartości z WARIANTU lub typy VARTYPE i ciągów.  
  
 [Interfejs IDebugStackFrameSnifferEx](../winscript/reference/idebugstackframesnifferex-interface.md)  
 Wylicza ramek stosu logiczne dla PDM.  
  
## <a name="hosts"></a>Hosty  
 Host:  
  
-   Obsługuje aparaty języka.  
  
-   Udostępnia model obiektowy (zestaw obiektów, które mogą być przetwarzane przez skrypty).  
  
-   Definiuje drzewo dokumentów, które może być debugowany i ich zawartość.  
  
-   Organizuje skryptów w aplikacji wirtualnych.  
  
 Istnieją dwa rodzaje hostów:  
  
-   Bez hosta obsługuje tylko podstawowe interfejsy usługi wykonywanie aktywnych skryptów. Go nie ma kontroli nad strukturę dokumentu lub organizacji; jest to określane całkowicie przez skrypty dostarczony do aparaty języka.  
  
-   Host inteligentny obsługuje większy zestaw interfejsów, która pozwala na definiowanie drzewa dokumentu, zawartości dokumentu i kolorowanie składni. Istnieje zestaw interfejsów pomocnika, opisane w podsekcji, które ułatwiają znacznie hosta jako hosta inteligentnego.  
  
### <a name="smart-host-helper-interfaces"></a>Interfejsy pomocnika inteligentnych hosta  
 `IDebugDocumentHelper` Metody udostępniają znacznie prostsze zestaw interfejsów hosta za pomocą korzyści wynikające z hosting inteligentnej bez dotykania pełne złożoności (i zasilania) interfejsów pełne hosta.  
  
 Host jest nie trzeba używać tych interfejsów oczywiście. Jednak za pomocą tych interfejsów można uniknąć implementowania lub za pomocą numeru interfejsów bardziej skomplikowane.  
  
 [Interfejs IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md)  
 Wykonane przez PDM i zapewnia implementacji dla wielu interfejsy niezbędne do obsługi inteligentne.  
  
 [Interfejs IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md)  
 Implementowany (opcjonalnie) przez hosta do udostępnienia funkcje specyficzne dla hosta, takie jak kolorowania do debugera.  
  
 Aby uzyskać więcej informacji, zobacz [implementacja interfejsów pomocnika hosta inteligentnego](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Interfejsy inteligentnych hosta  
 Poniżej jest pełny zestaw interfejsów, które hostem inteligentnych musi implementować albo użyj nie używa interfejsów pomocnika.  
  
 Interfejsy implementowane przez hosta:  
  
 [Interfejs IDebugDocumentInfo](../winscript/reference/idebugdocumentinfo-interface.md)  
 Zawiera informacje dotyczące dokumentów, które mogą lub nie można utworzyć wystąpienia.  
  
 [Interfejs IDebugDocumentProvider](../winscript/reference/idebugdocumentprovider-interface.md)  
 Zapewnia metodę dla wystąpienia dokumentu na żądanie.  
  
 [Interfejs IDebugDocument](../winscript/reference/idebugdocument-interface.md)  
 Podstawowy interfejs dla wszystkich dokumentów debugowania.  
  
 [Interfejs IDebugDocumentText](../winscript/reference/idebugdocumenttext-interface.md)  
 Zapewnia dostęp do wersji tylko tekst dokumentu debugowania.  
  
 [Interfejs IDebugDocumentTextAuthor](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Umożliwia edycję wersji tylko tekst dokumentu debugowania.  
  
 [Interfejs IDebugDocumentContext](../winscript/reference/idebugdocumentcontext-interface.md)  
 Udostępnia abstrakcyjną reprezentacją części dokumentu debugowany.  
  
 Interfejsy implementowane przez PDM imieniu hosta:  
  
 [Interfejs IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Rozszerza funkcjonalność `IDebugDocumentProvider` interfejsu, zapewniając kontekstu w drzewie projektu.  
  
## <a name="debugger-ide"></a>Debuger IDE  
 IDE jest niezależny od języka debugowania interfejsu użytkownika. Udostępnia ona:  
  
-   Edytorów podglądy dokumentu.  
  
-   Zarządzanie punktu przerwania.  
  
-   Wyrażenie oceny i obejrzyj systemu windows.  
  
-   Stos, przeglądanie ramki.  
  
-   / Klasy obiektów przeglądania.  
  
-   Przeglądanie struktury aplikacji wirtualnej.  
  
 Interfejsy implementowane przez debuger:  
  
 [Interfejs IApplicationDebugger](../winscript/reference/iapplicationdebugger-interface.md)  
 Podstawowy interfejs udostępniany przez debuger sesji IDE.  
  
 [Interfejs IApplicationDebuggerUI](../winscript/reference/iapplicationdebuggerui-interface.md)  
 Zapewnia większą kontrolę nad interfejsu użytkownika (UI) debugera składnik zewnętrzny.  
  
 [Interfejs IDebugExpressionCallBack](../winscript/reference/idebugexpressioncallback-interface.md)  
 Dostarcza zdarzenia stanu dla `IDebugExpression` oceny postępu.  
  
 [Interfejs IDebugDocumentTextEvents](../winscript/reference/idebugdocumenttextevents-interface.md)  
 Dostarcza zdarzenia wskazujące zmiany w dokumencie tekstu.  
  
 [Interfejs IDebugApplicationNodeEvents](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 Udostępnia interfejs zdarzeń dla `IDebugApplicationNode` interfejsu.  
  
### <a name="machine-debug-manager"></a>Machine Manager debugowania  
 Menedżer debugowania maszyny udostępnia punkt podłączenie między aplikacjami wirtualnymi i debugery za utrzymanie i wyliczania listę aktywnych aplikacji wirtualnych.  
  
 [Interfejs IDebugSessionProvider](../winscript/reference/idebugsessionprovider-interface.md)  
 Ustanawia sesję debugowania dla działającej aplikacji.  
  
 [Interfejs IMachineDebugManager](../winscript/reference/imachinedebugmanager-interface.md)  
 Podstawowy interfejs do machine manager debugowania.  
  
 [Interfejs IMachineDebugManagerCookie](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Podobnie jak `IMachineDebugManager` interfejsu, ale ten interfejs obsługuje pliki cookie z debugowania.  
  
 [Interfejs IMachineDebugManagerEvents](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Sygnalizuje zmiany w działaniu listy aplikacji przez Menedżera maszyny debugowania.  
  
 [Interfejs IEnumRemoteDebugApplications](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Wylicza uruchamianie aplikacji na komputerze.  
  
### <a name="process-debug-manager"></a>Menedżer debugowania procesu  
 PDM wykonuje następujące czynności:  
  
-   Synchronizuje debugowania wiele aparatów języka.  
  
-   Przechowuje drzewa możliwością debugowania dokumentów.  
  
-   Scala stosu ramki.  
  
-   Współrzędne punktów przerwania, a następnie przez aparaty języka.  
  
-   Śledzenie wątków.  
  
-   Przechowuje wątku debugera do przetwarzania asynchronicznego.  
  
-   Komunikuje się z menedżerem debugowania maszyny i debuger IDE.  
  
 Poniżej przedstawiono interfejsy zapewnione przez Menedżera debugowania procesu.  
  
 [Interfejs IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md)  
 Podstawowy interfejs do Menedżera debugowania procesu. Ten interfejs można utworzyć, dodać lub usunąć aplikację wirtualną z procesem.  
  
 [Interfejs IRemoteDebugApplication](../winscript/reference/iremotedebugapplication-interface.md)  
 Reprezentuje działającej aplikacji.  
  
 [Interfejs IDebugApplication](../winscript/reference/idebugapplication-interface.md)  
 Opisuje metody debugowania nie obsługują uruchamiania zdalnego, do użytku przez aparaty języka i hostów.  
  
 [Interfejs IRemoteDebugApplicationThread](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 Reprezentuje wątku do wykonania w ramach określonej aplikacji.  
  
 [Interfejs IDebugApplicationThread](../winscript/reference/idebugapplicationthread-interface.md)  
 Umożliwia aparaty języka i hosty synchronizacja wątku i przechowywać informacje właściwe dla wątków, stan debugowania.  
  
 [Interfejs IEnumRemoteDebugApplicationThreads](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 Wylicza uruchomionych wątków w aplikacji.  
  
 [Interfejs IDebugThreadCall](../winscript/reference/idebugthreadcall-interface.md)  
 Międzyprocesowe wysyłki.  
  
 [Interfejs IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Przechowuje pozycji dla dokumentu w hierarchii.  
  
 [Interfejs IEnumDebugApplicationNodes](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 Wylicza węzłów podrzędnych węzła skojarzone z aplikacją.  
  
 [Interfejs IEnumDebugStackFrames](../winscript/reference/ienumdebugstackframes-interface.md)  
 Wylicza ramek stosu odpowiadający wątku scalone z silników.  
  
 [Interfejs IDebugCookie](../winscript/reference/idebugcookie-interface.md)  
 Umożliwia cookie debugowania w debugery skryptu.  
  
 [Interfejs IDebugHelper](../winscript/reference/idebughelper-interface.md)  
 Służy jako fabryki dla obiekt przeglądarek i punkty połączenia proste aparatów skryptu.  
  
 [Interfejs ISimpleConnectionPoint](../winscript/reference/isimpleconnectionpoint-interface.md)  
 Zapewnia prostą metodę opisujące i wyliczania zdarzenia wywoływane punktu połączenia określonego dla aparatów skryptu umieszczonych w.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugera aktywnego skryptu](../winscript/reference/active-script-debugger-interfaces.md)