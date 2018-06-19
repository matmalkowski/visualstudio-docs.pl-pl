---
title: Pomocnicy zestawu SDK do debugowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e80344b8cec1bc013e044be39638879b049c8d0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135925"
---
# <a name="sdk-helpers-for-debugging"></a>Pomocnicy zestawu SDK do debugowania
Te funkcje i deklaracje są funkcje globalne pomocy wykonywania aparatami debugowania, ewaluatorów wyrażeń i dostawców symbol w języku C++.  
  
> [!NOTE]
>  Obecnie nie istnieje są ma zarządzanej wersji tych funkcji i deklaracji.  
  
## <a name="overview"></a>Omówienie  
 Aby aparatami debugowania, ewaluatorów wyrażeń i symbol dostawców ma być używany przez Visual Studio muszą być zarejestrowane. Odbywa się przez ustawienie rejestru podklucze i wpisy, znanej także jako "ustawienie metryki". Następujące funkcje globalne są przeznaczone do jej obsługi ułatwiają proces aktualizacji tych metryk. Zobacz sekcję dotyczącą lokalizacje rejestru, aby dowiedzieć się, układ każdego podklucza rejestru, która jest aktualizowana przez te funkcje.  
  
## <a name="general-metric-functions"></a>Funkcje Metryka ogólne  
 Są to ogólne funkcje używane przez aparaty debugowania. Specjalizowany funkcje dla ewaluatorów wyrażeń i dostawców symbol wyszczególnione później.  
  
### <a name="getmetric-method"></a>GetMetric — metoda  
 Pobiera wartość metryki z rejestru.  
  
```cpp  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametr|Opis|  
|---------------|-----------------|  
|pszMachine|[in] Nazwa komputera prawdopodobnie zdalnego, którego rejestru zostanie zapisany (`NULL` oznacza, że komputer lokalny).|  
|pszType|[in] Jeden z typów metryki.|  
|guidSection|[in] Identyfikator GUID aparat ewaluatora, wyjątek, itp. To ustawienie określa podsekcji metryki typu dla określonego elementu.|  
|pszMetric|[in] Metryki, które mają zostać uzyskane. Odpowiada nazwie określonej wartości.|  
|pdwValue|[in] Lokalizacja magazynu wartość metryki. Istnieje kilka odmian GetMetric mogą zwracać wartość typu DWORD (jak w poniższym przykładzie), BSTR, identyfikator GUID lub tablicę identyfikatorów GUID.|  
|pszAltRoot|[in] Alternatywny katalog główny rejestru do użycia. Ustaw `NULL` o użyciu domyślnej.|  
  
### <a name="setmetric-method"></a>SetMetric — metoda  
 Ustawia określoną wartość metryki w rejestrze.  
  
```cpp  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parametr|Opis|  
|---------------|-----------------|  
|pszType|[in] Jeden z typów metryki.|  
|guidSection|[in] Identyfikator GUID aparat ewaluatora, wyjątek, itp. To ustawienie określa podsekcji metryki typu dla określonego elementu.|  
|pszMetric|[in] Metryki, które mają zostać uzyskane. Odpowiada nazwie określonej wartości.|  
|dwValue|[in] Lokalizacja magazynu wartość metryki. Istnieje kilka odmian SetMetric, w którym można przechowywać wartość typu DWORD (w tym przykładzie), BSTR, identyfikator GUID lub tablicę identyfikatorów GUID.|  
|fUserSpecific|[in] Wartość TRUE, jeśli metryka jest specyficzne dla użytkownika i powinna być zapisana do gałęzi użytkownika zamiast gałąź komputera lokalnego.|  
|pszAltRoot|[in] Alternatywny katalog główny rejestru do użycia. Ustaw `NULL` o użyciu domyślnej.|  
  
### <a name="removemetric-method"></a>RemoveMetric — metoda  
 Usuwa określony Metryka z rejestru.  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametr|Opis|  
|---------------|-----------------|  
|pszType|[in] Jeden z typów metryki.|  
|guidSection|[in] Identyfikator GUID aparat ewaluatora, wyjątek, itp. To ustawienie określa podsekcji metryki typu dla określonego elementu.|  
|pszMetric|[in] Metryka ma zostać usunięty. Odpowiada nazwie określonej wartości.|  
|pszAltRoot|[in] Alternatywny katalog główny rejestru do użycia. Ustaw `NULL` o użyciu domyślnej.|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections — metoda  
 Wylicza różnych sekcji metryki w rejestrze.  
  
```cpp  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametr|Opis|  
|---------------|-----------------|  
|pszMachine|[in] Nazwa komputera prawdopodobnie zdalnego, którego rejestru zostanie zapisany (`NULL` oznacza, że komputer lokalny).|  
|pszType|[in] Jeden z typów metryki.|  
|rgguidSections|[w, out] Przydzielony wstępnie tablicę identyfikatorów GUID zostać wypełnione.|  
|pdwSize|[in] Maksymalna liczba identyfikatorów GUID, które mogą być przechowywane w `rgguidSections` tablicy.|  
|pszAltRoot|[in] Alternatywny katalog główny rejestru do użycia. Ustaw `NULL` o użyciu domyślnej.|  
  
## <a name="expression-evaluator-functions"></a>Funkcje ewaluatora wyrażenia  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|GetEEMetric|Pobiera wartość metryki z rejestru.|  
|SetEEMetric|Ustawia określoną wartość metryki w rejestrze.|  
|RemoveEEMetric|Usuwa określony Metryka z rejestru.|  
|GetEEMetricFile|Pobiera nazwę pliku z określonej metryki i ładuje, zwracając zawartość pliku jako ciąg.|  
  
## <a name="exception-functions"></a>Funkcje wyjątku  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|GetExceptionMetric|Pobiera wartość metryki z rejestru.|  
|SetExceptionMetric|Ustawia określoną wartość metryki w rejestrze.|  
|RemoveExceptionMetric|Usuwa określony Metryka z rejestru.|  
|RemoveAllExceptionMetrics|Usuwa wszystkie metryki wyjątek z rejestru.|  
  
## <a name="symbol-provider-functions"></a>Symbol funkcji dostawcy  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|GetSPMetric|Pobiera wartość metryki z rejestru.|  
|SetSPMetric|Ustawia określoną wartość metryki w rejestrze.|  
|RemoveSPMetric|Usuwa określony Metryka z rejestru.|  
  
## <a name="enumeration-functions"></a>Funkcje — wyliczenie  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|EnumMetricSections|Wylicza wszystkie metryki dla określonego typu metryki.|  
|EnumDebugEngine|Wylicza aparaty debugowania w zarejestrowany.|  
|EnumEEs|Wylicza ewaluatorów wyrażeń zarejestrowany.|  
|EnumExceptionMetrics|Wylicza wszystkie metryki wyjątku.|  
  
## <a name="metric-definitions"></a>Definicje metryk  
 Te definicje może służyć do wstępnie zdefiniowanych nazw metryki. Nazwy odpowiadają różne klucze rejestru i wartości nazwy i są zdefiniowane jako ciągi znaków typu wide: na przykład `extern LPCWSTR metrictypeEngine`.  
  
|Wstępnie zdefiniowanych typów metryki|Opis: Podstawowy klucz dla...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Wszystkie debugowania aparatu metryki.|  
|metrictypePortSupplier|Wszystkie metryki portu dostawcy.|  
|metrictypeException|Wszystkie metryki wyjątku.|  
|metricttypeEEExtension|Wszystkie rozszerzenia ewaluatora wyrażenia.|  
  
|Właściwości aparatu debugowania|Opis|  
|-----------------------------|-----------------|  
|metricAddressBP|Ustaw wartość niezerową, aby wskazać obsługę punktów przerwania adresu.|  
|metricAlwaysLoadLocal|Ustaw wartość niezerową, aby zawsze załadować aparat debugowania lokalnie.|  
|metricLoadInDebuggeeSession|NIE JEST UŻYWANY|  
|metricLoadedByDebuggee|Ustaw wartość niezerową, aby wskazać, że aparat debugowania zawsze będzie można załadować z lub przez debugowany program.|  
|metricAttach|Ustaw wartość niezerową, aby wskazać obsługę dołączanie do istniejących programów.|  
|metricCallStackBP|Ustaw wartość niezerową, aby wskazać obsługę punktów przerwania stosu wywołań.|  
|metricConditionalBP|Ustaw wartość niezerową, aby wskazać obsługę ustawienie warunkowych punktów przerwania.|  
|metricDataBP|Ustaw wartość niezerową, aby wskazać, pomocy technicznej dla ustawienia punktów przerwania na temat zmian w danych.|  
|metricDisassembly|Ustaw do różną od zera, aby wskazać obsługę produkcji lista dezasemblacji.|  
|metricDumpWriting|Ustaw wartość niezerową, aby wskazać obsługę zrzutu zapisywania (zrzucanie pamięci na urządzeniach).|  
|metricENC|Ustaw do różną od zera, aby wskazać obsługę Edytuj i Kontynuuj. **Uwaga:** aparat debugowania niestandardowych nie należy konfigurować to lub zawsze należy ustawić na wartość 0.|  
|metricExceptions|Ustaw wartość niezerową, aby wskazać, obsługa wyjątków.|  
|metricFunctionBP|Ustaw wartość niezerową, aby wskazać obsługę nazwanego punktów przerwania (punktów kontrolnych, które Przerwij, gdy nosi nazwę funkcji).|  
|metricHitCountBP|Ustaw wartość niezerową, aby wskazać, pomocy technicznej dla ustawienia "trafień punktu" punktów przerwania (punkty przerwania, które są uruchamiane wyłącznie po trafienia wiele razy).|  
|metricJITDebug|Ustaw do różną od zera, aby wskazać, obsługę debugowania just in time (debugera jest uruchamiana po wystąpieniu wyjątku w proces uruchamiania).|  
|metricMemory|NIE JEST UŻYWANY|  
|metricPortSupplier|Ustaw identyfikator CLSID dostawcy portu Jeśli jedną jest zaimplementowana.|  
|metricRegisters|NIE JEST UŻYWANY|  
|metricSetNextStatement|Ustaw wartość niezerową, aby wskazać obsługę ustawienie następnej instrukcji (które pomija wykonywania instrukcji pośrednich).|  
|metricSuspendThread|Ustaw wartość niezerową, aby wskazać obsługę wstrzymywania wykonanie wątku.|  
|metricWarnIfNoSymbols|Ustaw wartość niezerową, aby wskazać, że użytkownik powiadomienia, jeśli istnieją żadnych symboli.|  
|metricProgramProvider|Ustaw identyfikator CLSID dostawcy programu.|  
|metricAlwaysLoadProgramProviderLocal|Ustaw tę wartość na niezerową, aby wskazać, że program powinien zawsze można załadować dostawcy lokalnie.|  
|metricEngineCanWatchProcess|Ustaw tę wartość na niezerową, aby wskazać, że aparat debugowania będzie oczekiwał na przetwarzania zdarzeń dostawcy programu.|  
|metricRemoteDebugging|Ustaw tę wartość na niezerową, aby wskazać, obsługę debugowania zdalnego.|  
|metricEncUseNativeBuilder|Ustaw tę wartość na niezerową, aby wskazać, że Edytuj i Kontynuuj Manager powinien używać encbuild.dll aparat debugowania dla Edytuj i Kontynuuj. **Uwaga:** aparat debugowania niestandardowych nie należy konfigurować to lub zawsze należy ustawić na wartość 0.|  
|metricLoadUnderWOW64|Ustaw tę wartość na niezerową, aby wskazać, że aparat debugowania powinny być ładowane w procesie debugowanego obiektu w środowisku WOW podczas debugowania procesu 64-bitowego; w przeciwnym razie aparat debugowania będą ładowane w procesie programu Visual Studio (co działa w emulatorze WOW64).|  
|metricLoadProgramProviderUnderWOW64|Ustaw tę wartość na niezerową, aby wskazać, że dostawca programu powinna być załadowany w procesie debugowanego obiektu podczas debugowania procesu 64-bitowe w środowisku WOW; w przeciwnym razie zostanie załadowany w procesie programu Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Ustaw tę wartość na niezerową, aby wskazać, że proces ma zostać zatrzymana, jeśli wystąpił nieobsługiwany wyjątek jest zgłaszany w granicach zarządzanych/niezarządzanych kodu.|  
|metricAutoSelectPriority|Ustaw tę wartość na priorytet dla wyboru automatycznego aparatu debugowania (wyższe wartości equals wyższy priorytet).|  
|metricAutoSelectIncompatibleList|Klucza rejestru zawierającego wpisów, które określone identyfikatory GUID dla aparatami debugowania mają być ignorowane w automatyczny wybór. Te wpisy są liczbą (0, 1, 2 itd.) z identyfikatorem GUID wyrażonej w postaci ciągu.|  
|metricIncompatibleList|Klucza rejestru zawierającego wpisów, które określić identyfikatory GUID dla aparatami debugowania, które nie są zgodne z tym aparatem debugowania.|  
|metricDisableJITOptimization|Ustaw tę wartość na niezerową, aby wskazać, że podczas debugowania powinny być wyłączone optymalizacje just in time (dla zarządzanego kodu).|  
  
|Właściwości ewaluatora wyrażenia|Opis|  
|-------------------------------------|-----------------|  
|metricEngine|To przechowuje liczbę aparatów debugowania, które obsługują ewaluatora określone wyrażenie.|  
|metricPreloadModules|Ustaw tę wartość na niezerową, aby wskazać, że modułów powinien załadowane po uruchomieniu ewaluatora wyrażeń względem programu.|  
|metricThisObjectName|Ustaw tę wartość na "this" Nazwa obiektu.|  
  
|Właściwości rozszerzenia ewaluatora wyrażenia|Opis|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Nazwa biblioteki dll, która obsługuje tego rozszerzenia.|  
|metricExtensionRegistersSupported|Lista rejestrów obsługiwane.|  
|metricExtensionRegistersEntryPoint|Punkt wejścia do uzyskiwania dostępu do rejestrów.|  
|metricExtensionTypesSupported|Lista obsługiwanych typów.|  
|metricExtensionTypesEntryPoint|Punkt wejścia do uzyskiwania dostępu do typów.|  
  
|Właściwości dostawcy portu|Opis|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Identyfikator CLSID selektora portu (okno dialogowe użytkownika umożliwia wybranie portów i dodać porty używane do debugowania).|  
|metricDisallowUserEnteredPorts|Różna od zera, jeśli portów wprowadzonych przez użytkownika nie można dodać do portu dostawcy (to sprawia, że okno dialogowe selektora portu zasadniczo tylko do odczytu).|  
|metricPidBase|Identyfikator procesu podstawowy używany przez port dostawcy podczas przydzielania identyfikatorów procesów.|  
  
|Wstępnie zdefiniowane SP typów magazynu|Opis|  
|-------------------------------|-----------------|  
|storetypeFile|Symbole są przechowywane w osobnym pliku.|  
|storetypeMetadata|Symbole są przechowywane jako metadanych w zestawie.|  
  
|Różne właściwości|Opis|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Ustaw tę wartość na niezerową, aby wyświetlić kod nonuser.|  
|metricJustMyCodeStepping|Ustaw tę wartość na niezerową, aby wskazać, że krokowego wykonywania może wystąpić tylko w kodzie użytkownika.|  
|metricCLSID|Identyfikator CLSID obiektu określonego typu metryki.|  
|metricName|Przyjazna nazwa dla obiektu określonego typu metryki.|  
|metricLanguage|Nazwa języka.|  
  
## <a name="registry-locations"></a>W lokalizacji rejestru  
 Metryki są odczytywane i zapisywane w rejestrze, w szczególności w `VisualStudio` podkluczu.  
  
> [!NOTE]
>  W większości przypadków, metryki zostanie zapisany w kluczu HKEY_LOCAL_MACHINE. Jednak czasami HKEY_CURRENT_USER będą klucz miejsca docelowego. Dbgmetric.lib obsługuje zarówno kluczy. Podczas pobierania metrykę, przeszukiwane HKEY_CURRENT_USER pierwszy, a następnie HKEY_LOCAL_MACHINE. Gdy to ustawienie metryki parametr określa klucz, do którego najwyższego poziomu do użycia.  
  
 *[klucz rejestru]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[wersja głównego]*\  
  
 *[metryki głównego]*\  
  
 *[typ metryki]*\  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[klucz rejestru]*|`HKEY_CURRENT_USER` lub `HKEY_LOCAL_MACHINE`.|  
|*[wersja głównego]*|Wersja programu Visual Studio (na przykład `7.0`, `7.1`, lub `8.0`). Jednak ten katalog główny może również zostać zmodyfikowany za pomocą **/rootsuffix** przełączyć się do **devenv.exe**. W przypadku VSIP, modyfikator jest zwykle **Exp**, więc głównej wersji może być na przykład 8.0Exp.|  
|*[metryki głównego]*|Jest to `AD7Metrics` lub `AD7Metrics(Debug)`, w zależności od tego, czy używana wersja debugowania dbgmetric.lib. **Uwaga:** czy dbgmetric.lib jest używana, tę konwencję nazewnictwa powinien wywiązuje się Jeśli masz różnice między debug i release wersje, które musi mieć odzwierciedlenie w rejestrze.|  
|*[typ metryki]*|Typ metryki do zapisania: `Engine`, `ExpressionEvaluator`, `SymbolProvider`itp. Są one wszystkie zdefiniowane jak dbgmetric.h jako `metricTypeXXXX`, gdzie `XXXX` jest nazwą określonego typu.|  
|*[Metryka]*|Nazwa wpisu do przypisania wartości w celu ustawienia metryki. Rzeczywiste organizacji metryki zależy od typu metryki.|  
|*[wartość metryki]*|Wartość przypisana do metryki. Metryka zależy od typu wartości powinny mieć (string, number, itp.).|  
  
> [!NOTE]
>  Wszystkie identyfikatory GUID są przechowywane w formacie `{GUID}`. Na przykład `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Aparaty debugowania  
 Poniżej znajduje się organizacja metryki aparaty debugowania w rejestrze. `Engine` jest nazwa typu metryki dla aparatu debugowania i odpowiada *[typ metryki]* w powyższym poddrzewo rejestru.  
  
 `Engine`\  
  
 *[identyfikator guid aparatu]*\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 `PortSupplier`\  
  
 `0` = *[port dostawcy guid]*  
  
 `1` = *[port dostawcy guid]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid aparatu]*|Identyfikator GUID aparat debugowania.|  
|*[identyfikator guid klasy]*|Identyfikator GUID klasy, która implementuje ten aparat debugowania.|  
|*[port dostawcy guid]*|Identyfikator GUID dostawcy port, jeśli istnieje. Wiele aparatami debugowania przy użyciu domyślnego portu dostawcy, a w związku z tym nie należy określać własne dostawcy. W tym przypadku podklucz `PortSupplier` będą nieobecne.|  
  
### <a name="port-suppliers"></a>Port dostawcy  
 Poniżej znajduje się organizacja metryki dostawcy portu w rejestrze. `PortSupplier` jest nazwa typu metryki dla dostawcy portu i odpowiada *[typ metryki]*.  
  
 `PortSupplier`\  
  
 *[port dostawcy guid]*\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[port dostawcy guid]*|Identyfikator GUID dostawcy portu|  
|*[identyfikator guid klasy]*|Identyfikator GUID klasy, która implementuje ten dostawca portu|  
  
### <a name="symbol-providers"></a>Symbol dostawców  
 Poniżej znajduje się organizacja metryki dostawcy symbol w rejestrze. `SymbolProvider` jest nazwa typu metryki dla dostawcy symboli i odpowiada *[typ metryki]*.  
  
 `SymbolProvider`\  
  
 *[identyfikator guid dostawcy symbol]*\  
  
 `file`\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 `metadata`\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid dostawcy symbol]*|Identyfikator GUID dostawcy symbol|  
|*[identyfikator guid klasy]*|Identyfikator GUID klasy, która implementuje dostawcę tego symbolu|  
  
### <a name="expression-evaluators"></a>Ewaluatory wyrażeń  
 Poniżej znajduje się organizacja metryki ewaluatora wyrażenia w rejestrze. `ExpressionEvaluator` jest nazwa typu metryki dla ewaluatora wyrażeń i odpowiada *[typ metryki]*.  
  
> [!NOTE]
>  Typem metryki dla `ExpressionEvaluator` nie jest zdefiniowany w dbgmetric.h, ponieważ zakłada się, że wszystkie zmiany metryki dla ewaluatorów wyrażeń zostanie wysłany za pomocą funkcji metryki ewaluatora wyrażenia odpowiednie (układ `ExpressionEvaluator` podklucz jest nieco skomplikowane, więc szczegóły są ukryte wewnątrz dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[identyfikator guid języka]*\  
  
 *[identyfikator guid dostawcy]*\  
  
 `CLSID` = *[identyfikator guid klasy]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 `Engine`\  
  
 `0` = *[identyfikator guid aparatu debugowania]*  
  
 `1` = *[identyfikator guid aparatu debugowania]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid języka]*|Identyfikator GUID języka|  
|*[identyfikator guid dostawcy]*|Identyfikator GUID dostawcy|  
|*[identyfikator guid klasy]*|Identyfikator GUID klasy, która implementuje ten Ewaluator wyrażeń|  
|*[identyfikator guid aparatu debugowania]*|Identyfikator GUID aparat debugowania, który działa ta ewaluatora wyrażenia z|  
  
### <a name="expression-evaluator-extensions"></a>Rozszerzenia ewaluatora wyrażenia  
 Poniżej znajduje się organizacja metryki rozszerzenia ewaluatora wyrażenia w rejestrze. `EEExtensions` jest nazwa typu metryki dla wyrażenia rozszerzeń ewaluatora i odpowiada *[typ metryki]*.  
  
 `EEExtensions`\  
  
 *[identyfikator guid rozszerzenia]*\  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid rozszerzenia]*|Identyfikator GUID rozszerzenia ewaluatora wyrażenia|  
  
### <a name="exceptions"></a>Wyjątki  
 Poniżej znajduje się organizacja metryki wyjątków w rejestrze. `Exception` jest nazwa typu metryki dla wyjątków i odpowiada *[typ metryki]*.  
  
 `Exception`\  
  
 *[identyfikator guid aparatu debugowania]*\  
  
 *[typów wyjątków]*\  
  
 *[wyjątek]*\  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
 *[wyjątek]*\  
  
 *[Metryka] = [wartość metryki]*  
  
 *[Metryka] = [wartość metryki]*  
  
|Symbol zastępczy|Opis|  
|-----------------|-----------------|  
|*[identyfikator guid aparatu debugowania]*|Identyfikator GUID aparat debugowania, który obsługuje wyjątków.|  
|*[typów wyjątków]*|Ogólne tytuł podklucza identyfikacji klasy wyjątków, które są obsługiwane. Typowe nazwy są **wyjątków języka C++**, **wyjątki Win32**, **wspólnego języka środowiska uruchomieniowego wyjątki**, i **natywnego sprawdza Run-Time**. Te nazwy są również używane do identyfikowania danej klasy wyjątku dla użytkownika.|  
|*[wyjątek]*|Nazwa wyjątku: na przykład **_com_error** lub **Ctrl-Break**. Te nazwy są również używane do identyfikowania określonego wyjątku dla użytkownika.|  
  
## <a name="requirements"></a>Wymagania  
 Te pliki znajdują się w [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] katalogu instalacyjnego zestawu SDK (domyślnie *[dysk]* \Program Files\Microsoft programu Visual Studio 2010 SDK\\).  
  
 Nagłówek: includes\dbgmetric.h  
  
 Biblioteki: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)