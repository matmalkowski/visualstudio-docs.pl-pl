---
title: "Strona opcji, debugowanie — właściwości węzła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba6bb51d32ea249ba573733babcb7c9ed0cf0dde
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="options-page-debugging-node-properties"></a>Strona opcji, debugowanie — Właściwości węzła
W poniższych tabelach opisano stron (lub kolekcji właściwości) które są skojarzone z **debugowanie** kategorii, `DTE.Properties("Debugging", <Property Page>)` z **opcje** okno dialogowe.  
  
## <a name="general"></a>Ogólne  
 `DTE.Properties("Debugging", "General")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|PromptOnBreakpointDelete|Get/Set (wartość logiczna)|Określa, czy debuger wyświetli monit o zgodę przed usunięciem wszystkich punktów przerwania w projekcie.|  
|BreakAllProcesses|Get/Set (wartość logiczna)|Określa, czy debuger dzieli wszystkie procesy zawsze, gdy przerwania jednego procesu.|  
|BreakAtBoundaries|Get/Set (wartość logiczna)|Określa, czy debuger dzieli wykonywania, gdy wyjątek przecina obramowanie między elementami AppDomain lub między zarządzanego i kodu natywnego.|  
|EnableAddressLevelDebugging|Get/Set (wartość logiczna)|Określa, czy są włączone funkcje debugowania na poziomie adresu.|  
|ShowDisassemblyIfNoSource|Get/Set (wartość logiczna)|Określa, czy debuger wyświetla kod dezasemblacji, gdy kod źródłowy jest niedostępny.|  
|EnableBreakpointFilters|Get/Set (wartość logiczna)|Określa, czy punkt przerwania filtrowanie jest włączone.|  
|EnableExceptionAssistant|Get/Set (wartość logiczna)|Określa, czy Asystenta wyjątków jest używany dla zarządzanych wyjątków.|  
|UnwindCallstack|Get/Set (wartość logiczna)|Określa, czy debuger cofa nieobsługiwany wyjątek w stosie wywołań.|  
|EnableJustMyCode|Get/Set (wartość logiczna)|Określa, czy tylko mój kod jest włączone dla C# i kod Visual Basic.|  
|ShowAllMembers|Get/Set (wartość logiczna)|Dla obiektów nienależących do użytkownika określa, czy debuger wyświetla wszystkich elementach członkowskich obiektu w oknach zmiennych. Ta opcja nie ma znaczenia, chyba że włączono opcję tylko mój kod.|  
|WarnIfNoUserCode|Get/Set (wartość logiczna)|Określa, czy debuger emituje ostrzeżenie, gdy użytkownik próbuje dołączyć do procesu, który nie ma kodu użytkownika. Ta opcja nie ma znaczenia, chyba że włączono opcję tylko mój kod.|  
|EnablePropertyEvaluation|Get/Set (wartość logiczna)|Określa, czy debuger automatycznie oblicza właściwości i niejawna funkcja wywołuje w kodzie zarządzanym.|  
|CallStringConversion|Get/Set (wartość logiczna)|Określa, czy debuger niejawnie wywołuje funkcję konwersji ciągów na obiektach w oknach zmiennych. Ta opcja dotyczy tylko kodu C# i JScript.|  
|EnableSourceServer|Get/Set (wartość logiczna)|Określa, czy debuger może kodu dostępu z serwera źródłowego.|  
|PrintSourceServerDiagnostics|Get/Set (wartość logiczna)|Określa, czy w oknie danych wyjściowych zawiera komunikatów diagnostycznych związane z serwera źródłowego. Ta opcja nie ma znaczenia, chyba że jest włączony dostęp do serwera źródłowego.|  
|HighlightEntireLine|Get/Set (wartość logiczna)|Określa, czy debuger wyróżnia cały wiersz dla punktów przerwania i bieżącej instrukcji.|  
|RequireSourceToMatch|Get/Set (wartość logiczna)|Określa, czy debuger wymaga plików źródłowych jest zgodna z wersją oryginalną podczas otwierania plików do debugowania.|  
|RedirectOutputToImmediate|Get/Set (wartość logiczna)|Określa, czy dane wyjściowe z okna danych wyjściowych jest przekierowywany do okna bezpośredniego.|  
|ShowRawVariableStructure|Get/Set (wartość logiczna)|Określa, czy obiekty w oknach zmiennych są wyświetlane w postaci raw.|  
|SuppressJitOptimization|Get/Set (wartość logiczna)|Określa, czy optymalizacji just in time jest pomijane przez debuger dla kodu zarządzanego.|  
|WarnIfNoSymbols|Get/Set (wartość logiczna)|Określa, czy debuger wyświetli ostrzeżenie, jeśli symboli debugowania nie są dostępne po uruchomieniu procesu.|  
|WarnIfScriptDisabled|Get/Set (wartość logiczna)|Określa, czy debuger wyświetli ostrzeżenie, jeśli debugowanie skryptu nie jest włączona po uruchomieniu procesu.|  
|ShowMarkersForAllThreads|Get/Set (wartość logiczna)|Określa, czy debuger wyświetla znaczniki wątku.|  
|StepOverPropertiesAndOperators|Get/Set (wartość logiczna)|Określa, czy Przekrocz nad właściwościami i operatorami w tylko kodu zarządzanego.|  
  
## <a name="edit-and-continue"></a>Edytuj i kontynuuj  
 `DTE.Properties("Debugging", "EditAndContinue")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|EnableEditAndContinue|Get/Set (wartość logiczna)|Określa, czy włączono Edytuj i Kontynuuj. Ta opcja ma zastosowanie do wszystkich języków, które obsługuje funkcji Edytuj i Kontynuuj.|  
|InvokedByCommands|Get/Set (wartość logiczna)|Określa, czy Edytuj i Kontynuuj automatycznie stosuje zmiany kodu, gdy użytkownik wybierze polecenie debugowania **krok** lub **Kontynuuj**. Ta opcja dotyczy tylko kodu natywnego.|  
|InvokedByCommandsAskFirst|Get/Set (wartość logiczna)|Określa, czy Edytuj i Kontynuuj monituje użytkownika o zgodę na zastosowanie zmian kodu, gdy użytkownik wybierze polecenie debugowania **krok** lub **Kontynuuj**. Ta opcja dotyczy tylko kodu natywnego.|  
|WarnAboutStaleCode|Get/Set (wartość logiczna)|Określa, czy debuger wystawiać komunikat ostrzegawczy, gdy wykonywanie kodu nieaktualne ani starych, spowoduje Edytuj i Kontynuuj. Ta opcja dotyczy tylko kodu natywnego.|  
|RelinkChangesOnStop|Pobierz/Ustaw (Short)|Określa, czy program Visual Studio relinks zmiany kodu zostały zastosowane przez Edytuj i Kontynuuj po przerwaniu wykonywania aplikacji. Ta opcja dotyczy tylko kodu natywnego.|  
|AllowPrecompiling|Pobierz/Ustaw (Short)|Określa, czy ładowanie prekompilowanych nagłówków w tle jest dozwolone Edytuj i Kontynuuj. Ta opcja dotyczy tylko kodu natywnego.|  
  
## <a name="just-in-time"></a>just in time  
 `DTE.Properties("Debugging", "JustInTime")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|JitManaged|Get/Set (wartość logiczna)|Określa, czy włączone jest debugowanie just in Time dla kodu zarządzanego.|  
|JitNative|Get/Set (wartość logiczna)|Określa, czy włączone jest debugowanie just in Time dla kodu natywnego.|  
|JitScript|Get/Set (wartość logiczna)|Określa, czy włączone jest debugowanie just in Time dla kodu skryptu.|  
  
## <a name="native"></a>Natywny  
 `DTE.Properties("Debugging", "Native")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|LoadDllExports|Get/Set (wartość logiczna)|Określa, czy debuger ładuje tabele eksportu biblioteki DLL.|  
|EnableRPC|Get/Set (wartość logiczna)|Określa, czy debuger może Wkrocz COM zdalnych wywołań procedur.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie opcji ustawienia](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Określanie nazwy właściwości elementów na stronach opcje](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Strona opcji, czcionki i kolory — właściwości węzła](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Strona opcji, Edytor tekstu — właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md)   
 [Edytuj i Kontynuuj, debugowanie, opcje — Okno dialogowe](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)   
 [Just-In-Time, debugowanie, opcje — Okno dialogowe](../../debugger/just-in-time-debugging-options-dialog-box.md)