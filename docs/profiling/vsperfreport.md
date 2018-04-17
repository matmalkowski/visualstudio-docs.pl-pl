---
title: VSPerfReport | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25272ee42af6bea1287d4902d130792cd46ca3d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vsperfreport"></a>VSPerfReport
VSPerfReport — narzędzie wiersza polecenia jest używany do tworzenia raportów za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania pliku danych profilowania. Domyślny format raportu jest plikiem CSV.  
  
 VSPerfReport używa następującej składni:  
  
```  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Należy pamiętać, że `filename` musi być prawidłowy plik Vsp lub vsps.  
  
 VSPerfReport — narzędzie wiersza polecenia jest również używane do porównywania plików Vsp lub vsps. Aby wygenerować raport różnica ("diff"), należy użyć następującej składni:  
  
```  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` musi być prawidłowy plik Vsp lub vsps plików.  
  
## <a name="symbol-files"></a>Pliki symboli  
 Aby wyświetlić informacje dotyczące symboli, takich jak funkcja nazwy i numery wierszy, VSPerfReport wymaga dostępu do symbolu (. Pliki PDB) PROFILOWANEGO składników i pliki symboli systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## <a name="general-report-options"></a>Opcje raportu ogólne  
 W poniższej tabeli opisano ogólne raportu, formatowanie i opcje, które wybrać dane do przekazania.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**U**|Raportu i konsoli przekierowane dane wyjściowe są zapisywane jako Unicode. Musi być pierwszą opcję określony.|  
|**Podsumowanie:**[*typy*]|Tworzy jeden lub więcej typów raportów.<br /><br /> -   `All` -generowane są wszystkie typy raportów.<br />-   `CallerCallee` -relacji nadrzędny/podrzędny między funkcji.<br />-   `Function` -Funkcje wywołane.<br />-   `CallTree` -hierarchię wywołanych funkcji.<br />-   `Counter` -wartości licznika wszystkie znaczniki wraz z wydajność systemu Windows.<br />-   `Ip` -instrukcje profilowaniu.<br />-   `Life` -istnienia przydzielonych obiektów (dostępne, gdy alokacji dane zostały zebrane.)<br />-   `Line` dane profilu wiersza kodu źródłowego.<br />-   `Header` -Raport zawiera informacje o nagłówku.<br />-   `Mark` wszystkie znaczniki.<br />-   `Module` -modułów profilowaniu.<br />-   `Process` -procesów profilowaniu.<br />-   `Thread` -wątków profilowaniu.<br />-   `Type` -przydzielone typy.<br />-   `Contention` -kontencji zasobów.<br />-   `RuleWarnings` -problemy z wydajnością reguły<br />-   `ETW` -wszystkie zdarzenia funkcji Śledzenie zdarzeń systemu Windows () zebranych podczas przebiegu profilowania. Plik etl danych musi być w jej oryginalnej lokalizacji lub do katalogu zawierającego plik Vsp lub vsps.|  
|**Xml**|Dane wyjściowe raportu w formacie XML.|  
|**CallTrace**|Tworzy listę funkcji wejścia i wyjścia, zdarzenia ETW i znaki.|  
|**ClearPackedSymbols**|Usuwa wcześniej osadzone symbole z pliku danych profilera. Uruchom to polecenie przed uruchomieniem PackSymbols drugi czasu.|  
|**SymbolPath:** `path`|Określa jeden lub więcej ścieżek wyszukiwania lub symbol serwerów, które zawierają symbole dla pliku danych profilera.|  
|**DebugSymPath**|Wyświetla lokalizacje, które są wyszukiwane symbole i czy zostały znalezione. Ta opcja jest przydatna rozwiązać problemy z rozpoznawaniem symbolu.|  
|**PackSymbols**|Zapisuje symboli do profilowania plik danych (Vsp), dzięki czemu plików symboli (.pdb) nie są wymagane do analizy.|  
|**Dane wyjściowe:** *ścieżki*&#124;*filename*|Określa alternatywną lokalizację plików wygenerowanego raportu. Domyślnie raporty są tworzone w bieżącym katalogu.|  
|**SummaryFile**|Analizuje i zapisuje przeanalizowane informacje w pliku podsumowania vsps.|  
|**PrintMarks**|Wyświetla nazwy i sygnatury czasowe dla wszystkich znaczników w pliku określonego raportu.|  
|**?**|Wyświetla informacje o użyciu.|  
|**NoLogo**|Ukrywa informacje o wersji, gdy raport jest uruchomiony.|  
|**UserRulesDirectory**|Określa katalog zawierający reguły wydajności zdefiniowanych przez użytkownika [nie została jeszcze zaimplementowana].|  
  
## <a name="filter-options"></a>Opcje filtru  
 W poniższej tabeli opisano opcje filtrowania dostępnych danych.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**JustMyCode**[**:**[`caller`] [,`callee`]]|Pokaż tylko użytkowników aplikacji wywołania funkcji; Ukryj wywołań systemowych.<br /><br /> -Brak parametrów - Ukryj wszystkie funkcje system.<br />-   `caller` — Pokaż jeden poziom funkcji systemu, które wywołują funkcje aplikacji.<br />-   `callee` — Pokaż jeden poziom funkcji systemu, które są wywoływane przez użytkownika funkcji aplikacji.|  
|**Czas rozpoczęcia:**[*wartość*]|Wyświetla tylko dane zebrane po wartości (w milisekundach).|  
|**Wartość EndTime:**[*wartość*]|Wyświetla tylko dane zebrane przed wartością (w milisekundach).|  
|**FilterFile:** `VSPFFile`|Określa lokalizację pliku filtru, który został wygenerowany z okna Raport dotyczący wydajności programu Visual Studio.|  
|**MsFilter:**[*starttime, czas trwania*]|Wyświetla tylko dane z `starttime` do długości `duration` (w milisekundach).|  
|**Proces:**[*pid*]|Wyświetla tylko dane z określonego procesu.|  
|**Wątek:**[*threadid*]|Wyświetla tylko dane z określonego wątku.|  
|**Wątek:**[*identyfikator_wątku, identyfikator_procesu*]|Wyświetla tylko dane z określonego wątku skojarzone z określonym procesem.|  
  
## <a name="difference-report-options"></a>Opcje raportu różnicy  
 W poniższej tabeli opisano opcje porównywanie plików raportów.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**różnicowego**  `vspfile1 vspfile2`|Porównuje dwa pliki (Vsp lub vsps) plików raportów. Opcje podsumowania zostaną zignorowane przy użyciu opcji różnic.|  
|**Diff:**[*wartość*]|Poniżej tego progu różnicy pomiędzy dwoma wartościami zostaną zignorowane. Ponadto nowe dane o wartościach poniżej tego progu nie będą wyświetlane.|  
|**DiffTable:**[*tablename*]|Użyj tej konkretnej tabeli do porównywania plików. Wartość domyślna to tabeli funkcji.|  
|**DiffColumn:**[*columnname*]|Użyj tej konkretnej kolumny Porównaj wartości. Wartość domyślna to kolumny procentową wyłącznych próbek.|  
|**Querydifftables zwraca**|Wyświetl listę prawidłowych tabel i kolumn dla dwóch plików raportu, pod warunkiem.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki raportu wydajności](../profiling/performance-report-views.md)