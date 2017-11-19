---
title: "Hostowanie środowiska uruchomieniowego JavaScript | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30ec744e-57cc-4ef5-8fe1-d2c27b946548
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bf213bf262ede7642e05c66e424b860238dc57f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="hosting-the-javascript-runtime"></a>Hostowanie środowiska uruchomieniowego JavaScript
Interfejsy API środowiska wykonawczego języka JavaScript (JsRT) zapewniają sposób pulpitu, Sklep Windows i aplikacji po stronie serwera działa w systemie operacyjnym Windows umożliwiające dodanie funkcji obsługi skryptów do aplikacji przy użyciu aparatu Chakra JavaScript opartych na standardach jest również użyte przez Microsoft Edge i przeglądarki Internet Explorer. Te interfejsy API są dostępne na systemu Windows 10 i dowolna wersja systemu operacyjnego ma Internet Explorer w wersji 11.0 zainstalowane na tym komputerze. Aby uzyskać więcej informacji, zobacz [odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md). Aby uzyskać informacje na temat używania JsRT w aplikacjach w Sklepie Windows, zobacz [JsRT i platformy uniwersalnej systemu Windows](#Windows).  
  
> [!NOTE]
>  W tej dokumentacji przyjęto założenie, ogólne pracy znajomość języka JavaScript.  
  
## <a name="concepts"></a>Pojęcia  
 Opis sposobu hostowania aparat języka JavaScript przy użyciu interfejsów API JsRT zależy od dwóch podstawowych pojęć: kontekstów środowisk uruchomieniowych i wykonywanie.  
  
 A *środowiska uruchomieniowego* reprezentuje pełną środowiska wykonawczego języka JavaScript. Każdego środowiska uruchomieniowego, która jest tworzona ma własną izolowanego pamięci sterty zebranych i domyślnie własną just in time (JIT) kompilatora wątku i modułu zbierającego elementy bezużyteczne (GC) wątku. *Kontekstu wykonywania* reprezentuje środowisku JavaScript, które ma JavaScript własną globalny obiekt różne od innych kontekstach wykonywania. Jednego środowiska uruchomieniowego może zawierać wielu kontekstów wykonywania, a w takich przypadkach wszystkie konteksty wykonywania udostępniony kompilatora JIT i skojarzone ze środowiskiem uruchomieniowym wątku GC.  
  
 Środowisk uruchomieniowych reprezentuje wykonanie wątku pojedynczego. Tylko jeden środowiska uruchomieniowego mogą być aktywne w szczególności wątku w czasie, a moduł wykonawczy mogą być tylko aktywne w jednym wątku w czasie. Środowisk uruchomieniowych są wynajem wątków, dlatego moduł wykonawczy który nie jest aktualnie aktywne w wątku (tj. nie jest uruchomiona każdy kod JavaScript lub odpowiada do wywołań dowolnej z hosta) można używać na dowolnym wątku, który nie ma jeszcze active środowiska uruchomieniowego na nim.  
  
 Kontekst wykonywania są powiązane z konkretnym środowiska uruchomieniowego i wykonanie kodu w ramach tego środowiska wykonawczego. W przeciwieństwie do środowisk uruchomieniowych wielu kontekstów wykonywania mogą być aktywne w wątku, w tym samym czasie. Dzięki hosta można zadzwonić do kontekstu wykonywania, tego kontekstu wykonywania można wywołania zwrotnego do hosta, a hosta można zadzwonić do kontekstu wykonywania różnych.  
  
 ![Kontekst wykonywania wielu](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting")  
  
 W praktyce Jeśli jakiś host wymaga do uruchomienia kodu w środowiskach rozdzielonych kontekstu pojedynczego uruchomienia można. Podobnie jeśli jakiś host wymaga równoczesne uruchamianie wielu fragmentów kodu, jednego środowiska uruchomieniowego jest wystarczająca.  
  
## <a name="memory-management"></a>Zarządzanie pamięcią  
 JavaScript jest językiem bezużytecznych i w związku z tym istnieje kilka kwestii, które muszą być przechowywane na uwadze podczas pracy z interfejsami API JsRT z innego języka.  
  
 Główne zagadnienie to, że moduł zbierający elementy bezużyteczne JavaScript może zobaczyć tylko odwołania do wartości w dwóch miejscach: sterty jego środowiska uruchomieniowego i stosu. W związku z tym odwołaniem do wartość JavaScript, która znajduje się wewnątrz innej wartości JavaScript lub w zmiennej lokalnej na stosie zawsze będzie widoczna przez moduł garbage collector. Jednak przechowywane w innych lokalizacjach, takich jak stosów zarządzane przez hosta lub system odwołania nie będą widoczne przez moduł garbage collector i może spowodować przedwczesny zbiór wartości, które są nadal używane przez hosta.  
  
> [!IMPORTANT]
>  Niektóre Kompilatory języka (na przykład kompilatora Visual Studio C++) zoptymalizuje nieobecności zmiennych lokalnych, jeśli jest to możliwe. Musi być zadbać o upewnij się, że zmienne lokalne, które odwołują się do wartości JavaScript na stosie Jeśli oczekuje podtrzymywania tych wartości.  
  
 Jeśli odwołanie do wartości JavaScript będą przechowywane w lokalizacji nie są widoczne dla modułu zbierającego elementy bezużyteczne, host musi ręcznie Dodawanie i usuwanie odwołań za pomocą interfejsów API JsRT.  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 Po wystąpieniu wyjątku JavaScript podczas wykonywania skryptu, zawierającego środowiska uruchomieniowego jest ustawiany stan wyjątku. W stanie wyjątku, można uruchomić bez kodu i wszystkie wywołania interfejsu API zakończy się niepowodzeniem z kodem błędu `JsErrorInExceptionState` aż host pobiera i czyści wyjątków za pomocą `JsGetAndClearException` interfejsu API. Jeśli host zwraca wywołanie zwrotne JavaScript bez wyczyszczenie środowiska uruchomieniowego ze stanu wyjątek, następnie wyjątku JavaScript zostaną ponownie zgłoszone się, gdy formant przechodzi do aparatu JavaScript. Dzięki temu wywołania zwrotne hosta "throw" wyjątku JavaScript przez ustawienie środowiska uruchomieniowego w stan wyjątku i następnie powrotem z wywołania zwrotnego hosta.  
  
 Host nie może umożliwić własnego wewnętrznego wyjątki są propagowane na wywołanie zwrotne hosta — żadnych metod wywołania zwrotnego musi catch hosta wszystkie wyjątki, aby przed zwróceniem sterowania do środowiska wykonawczego.  
  
## <a name="runtime-resource-usage"></a>Użycie zasobów środowiska uruchomieniowego  
 Interfejsy API JsRT ujawnia szereg sposób monitorowania i zmodyfikować sposób środowisk uruchomieniowych korzystanie z zasobów. One zazwyczaj podzielić na następujące kategorie:  
  
-   **Użycie wątku**. Domyślnie każdy środowiska uruchomieniowego utworzy dedykowanym wątku kompilatora JIT i dedykowanym wątku GC, który usługa tego środowiska wykonawczego. Jeśli środowisko wykonawcze jest tworzony z `JsRuntimeAttributeDisableBackgroundWork` Flaga, a następnie pracy JIT i wykazu Globalnego odbędzie się w wątku czasu wykonywania zamiast wątki w tle osobne dla każdego z nich. Host może też podawać wątku usługi wywołania zwrotnego `JsCreateRuntime` wywołania pozwoli hosta do harmonogramu pracy JIT i wykazu Globalnego w żaden sposób za stosowny.  
  
-   **Użycie pamięci**. Istnieje kilka metod monitorowania i zmodyfikować użycie pamięci przez środowisko wykonawcze. Jeśli środowisko uruchomieniowe będą uruchomione przez długi czas, można określić hosta `JsRuntimeAttributeEnableIdleProcessing` Flaga podczas tworzenia środowiska uruchomieniowego, a następnie wywołać `JsIdle` Jeśli host znajduje się w stanie bezczynności. Dzięki temu aparat odroczenie niektórych pamięci oczyszczania i księgowości pracy czasu bezczynności.  
  
     Hosta można monitorować wyrzucania przez wywołanie metody `JsSetRuntimeBeforeCollectCallback`. Można również monitorować przydziałów wykonanych przez stos przez wywołanie metody `JsSetRuntimeMemoryAllocationCallback`. Należy pamiętać, że ten interfejs API nie wywołania zwrotnego przy każdej alokacji JavaScript tylko wtedy, gdy sterty środowiska uruchomieniowego potrzeba więcej miejsca, z których ma zostać przydzielony. Wywołanie zwrotne alokacji pamięci może odrzuciła żądanie, które wyzwoli wyrzucania elementów bezużytecznych i, jeśli brak pamięci nie jest dostępne błąd braku pamięci w czasie wykonywania.  
  
     Hosta można również wywołać `JsSetRuntimeMemoryLimit` ustawić limit ilości pamięci środowiska wykonawczego. Gdy moduł wykonawczy trafi limit, wyzwoli wyrzucania elementów bezużytecznych i, jeśli brak pamięci jest dostępny, błąd braku pamięci będą zgłaszane przez środowisko uruchomieniowe.  
  
-   **Skrypt przerwania i oceny**. Hosta można wywołać `JsDisableRuntimeExecution` zakończyć działanie w środowisku uruchomieniowym. To wywołanie jest możliwe w dowolnej chwili i z dowolnego wątku. Ponieważ przerwanie skryptu zależy osiągnięcia punktów guard wstawione do kodu, skrypt może nie zakończyć dokładnie w momencie, ale zostanie to bardzo krótko potem. Domyślnie punkty końcowe guard są umieszczane w wygenerowanym kodzie konserwatywnie i nie może obejmować każdej sytuacji, takich jak Pętla nieskończona. Tworzenie środowiska wykonawczego o `JsRuntimeAttributeAllowScriptInterrupt` flaga powoduje, że środowisko uruchomieniowe wstawić dodatkowe kontrole dla nieskończone pętle, często kosztem małe obciążenie.  
  
     Jeśli host zamierza nie zezwalaj na generowanie kodu natywnego przy użyciu kompilatora JIT, można określić `JsRuntimeAttributeDisableNativeCodeGeneration` flagi. Hosta można również nie zezwalaj skryptów z dynamicznie uruchamiania skryptów sam określając `JsRuntimeAttributeDisableEval` flagi.  
  
## <a name="debugging-and-profiling"></a>Debugowanie i profilowania  
 Interfejsy API JsRT obsługuje debugowanie i profilowania za pomocą technologii wykonywanie aktywnych skryptów.  
  
 Począwszy od systemu Windows 10, aparat JavaScript Chakra obsługuje starszego aparatu i aparat krawędzi, a można wskazać w JsRT (zobacz [krawędzi przeznaczonych dla wersji programu vs. Starsze aparaty](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md) szczegółowe informacje). Debugowanie skryptów w programie Visual Studio zmieniło między aparatu Edge i starszych. Z starszego aparatu, host musi podać [interfejs IDebugApplication](../winscript/reference/idebugapplication-interface.md) wskaźnika, który można uzyskać z [interfejs IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md) wystąpienia. Z aparatem krawędzi `IDebugApplication` jest przestarzały i Chakra aparat natywny umożliwia i wykonywanie skryptów możliwości debugowania za pomocą debugera programu Visual Studio bez konieczności stosowania `IDebugApplication` od użytkownika.  
  
 Aby wprowadzić możliwością debugowania skryptów w kontekście wykonywania, aparat Chakra ma rozpocząć korzystanie z mniej wydajne metody wykonywania kodu. Tak możliwością debugowania kodu zwykle działa wolniej niż bez możliwością debugowania kodu. W związku z tym ze starszego aparatu hosta mogą być uruchom debugowanie w kontekście wykonywania od samego początku, zapewniając `IDebugApplication` wskaźnik do góry `JsCreateContext`, lub można poczekać na debugowanie jest potrzebne, a następnie wywołać `JsStartDebugging`. Z aparatem krawędzi `JsCreateContext` nie przyjmuje `IDebugApplication` parametru, i w związku z tym skrypt jest możliwością debugowania tylko po `JsStartDebugging` jest wywoływana. Podczas debugowania za pomocą programu Visual Studio, musi być włączona opcja debugera "Skrypt".  
  
 W jednym z dwóch sposobów można sprofilować kodu JavaScript w kontekstu wykonywania. W wierszu polecenia programu Visual Studio profilera (vsperf.exe) może służyć w Windows 8.1 i nowszych wersjach z przełącznikiem /js, aby wygenerować raport, którego element docelowy uruchomienia kodu JavaScript w aplikacji. Lub host może bezpośrednio wywoływać `JsStartProfiling` i `JsStopProfiling` i podaj wywołania zwrotnego w celu profilowania samej siebie. Hosta można także sprawdzić stan pamięci sterty zebranych przez wywołanie metody `JsEnumerateHeap`. Profilowanie w JsRT działa w taki sam sposób między aparatu Edge i starszych. Jednakże, profilowanie API JsRT (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap`, i `JsIsEnumeratingHeap`) nie są dostępne dla uniwersalnych aplikacji systemu Windows.  
  
<a name="Windows"></a>   
## <a name="jsrt-and-the-universal-windows-platform"></a>Platforma uniwersalna systemu Windows i JsRT  
 Interfejsach API JsRT umożliwia dodanie funkcji obsługi skryptów do aplikacji uniwersalnej systemu Windows. Aplikacji uniwersalnej systemu Windows, który korzysta z interfejsów API JsRT należy docelowy API JSRT krawędzi, który z kolei target aparat Chakra krawędzi. Aby uzyskać więcej informacji, zobacz [krawędzi przeznaczonych dla wersji programu vs. Starsze aparaty](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md). Kompletne API JsRT jest dostępna dla aplikacji uniwersalnych systemu Windows, z wyjątkiem obsługi wyliczenie profilowania i sterty (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap`, i `JsIsEnumeratingHeap` nie są obsługiwane).  
  
 JsRT umożliwia również skrypty natywnie ma dostęp do wszystkich [Windows platformy Uniwersalnej interfejsów API](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx) po udostępnieniu przestrzeni nazw interfejsu API za pomocą interfejsu API JsRT krawędzi `JsProjectWinRTNamespace`. Podczas gdy uniwersalnych aplikacji systemu Windows wymagają ustawień oprócz projekcji niezbędne przestrzeni nazw w aplikacji Windows Classic (Win32), zainicjować modelu COM delegowane mechanizmu pompującego musi zostać włączona przy użyciu `JsSetProjectionEnqueueCallback` Aby włączyć zdarzenia i interfejsy API asynchronicznego. W poniższym przykładzie Win32 korzysta z dnia asynchroniczne UWP interfejsy API w celu utworzenia klient http do pobierania zawartości z identyfikatora Uri:  
  
```cpp  
typedef struct _jsCall {  
    JsProjectionCallback jsCallback;  
    JsProjectionCallbackContext jsContext;  
    HANDLE event;  
} jsCall;  
  
// Set up delegated pumping mechanism; not necessary in UWP applications.  
jsCall outstandingCall = {};  
CoInitializeEx(nullptr, COINIT_MULTITHREADED);  
JsSetProjectionEnqueueCallback([](JsProjectionCallback jsCallback,   
JsProjectionCallbackContext jsContext, void *callbackState) {  
    jsCall* call = (jsCall*)callbackState;  
    call->jsCallback = jsCallback;  
    call->jsContext = jsContext;  
    SetEvent(call->event);  
    },  
&outstandingCall);  
HANDLE event = CreateEventEx(NULL, NULL, CREATE_EVENT_MANUAL_RESET, EVENT_ALL_ACCESS);  
outstandingCall.event = event;  
  
// Project necessary namespaces.  
JsProjectWinRTNamespace(L"Windows.Foundation");  
JsProjectWinRTNamespace(L"Windows.Web");  
  
// Get content from an Uri.  
JsRunScript(L"var uri = new Windows.Foundation.Uri(\"http://somedatasource.com\"); " \  
    L"var httpClient = new Windows.Web.Http.HttpClient();" \  
    L"httpClient.getStringAsync(uri).done(function (content) { " \  
    L"    // do something with the string content " \    
    L"}, onError); " \  
    L"function onError(reason) { " \  
    L"    // error handling " \        
    L"}",   
    currentSourceContext, L"", &result);  
  
// Wait for async call to come in and then execute; not necessary in UWP applications.  
WaitForSingleObjectEx(outstandingCall.event, 10000, FALSE) == WAIT_OBJECT_0;  
outstandingCall.jsCallback(outstandingCall.jsContext);  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Środowisko uruchomieniowe JavaScript przykładowej aplikacji](http://go.microsoft.com/fwlink/p/?LinkID=306674&clcid=0x409)   
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)   
 [Hostowanie środowiska uruchomieniowego JavaScript](../chakra-hosting/javascript-runtime-hosting.md)