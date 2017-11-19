---
title: "Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5369397adc0da3d4fb4b8da3aa7beec1f0ba3f67
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="collecting-detailed-timing-data-by-using-instrumentation"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Metody Instrumentacji w narzędziach profilowania injects profilowania kodu do kopii modułu. Każdy wpis, zakończenia i wywołanie funkcji funkcji w module kod rejestruje podczas przebiegu profilowania. Metoda Instrumentacji jest przydatne do zbierania czasu szczegółowe informacje o sekcji kodu i zrozumienie wpływu wejściowymi i wyjściowymi operacje na wydajność aplikacji.  
  
 Metoda Instrumentacji można określić za pomocą jednej z następujących procedur:  
  
-   Na pierwszej stronie kreatora profilowania, wybierz **Instrumentacji**.  
  
-   Na **Eksplorator wydajności** paska narzędzi w **metody** kliknij **Instrumentacji**.  
  
-   Na **ogólne** strony okna dialogowego właściwości sesji wydajności, wybierz opcję **Instrumentacji**.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Możesz określić dodatkowe opcje w *sesji wydajności***strony właściwości** okno dialogowe sesji wydajności. Aby otworzyć okno dialogowe:  
  
-   W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.  
  
 Zadania w poniższej tabeli opisano opcje, które można określić w *sesji wydajności***strony właściwości** okno dialogowe, gdy profilu przy użyciu metody instrumentacji.  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|Na **ogólne** strony, Dodaj alokacji pamięci .NET i okres istnienia obiektu i określ szczegóły nazewnictwa profilowania wygenerowany plik danych (Vsp).|-   [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na **uruchamianie** strony, jeśli masz wiele projektów .exe w Twojej solution.specify aplikację do uruchomienia i ich kolejność uruchamiania.|-   [Porady: Określanie plików binarnych do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|  
|Na **plików binarnych** Określ lokalizację kopii instrumentowanych modułów. Domyślnie oryginalnych danych binarnych są przenoszone do folderu kopii zapasowej.|-   [Porady: przemieszczanie instrumentowanych plików binarny](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Na **interakcja warstwowa** Dodaj ADO.NET data wywołania do uruchomienia profilowania.|-   [Zbieranie danych o interakcji między warstwy](../profiling/collecting-tier-interaction-data.md)|  
|Na **Instrumentacji** strony, Wyklucz małe funkcje z profilowanie, aby zmniejszyć profilowania Profiluj kod JavaScript na stronach sieci Web ASP.NET w nakładów pracy i określić polecenia uruchamiane w wierszu polecenia przed i po nich proces instrumentacji.|-   [Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Porady: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Porady: Określanie poleceń Pre-i POST-instrumentalnych](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Na **liczniki CPU** strony, określ co najmniej jeden liczniki wydajności procesora do dodania do danych profilowania.|-   [Porady: zbieranie danych licznika Procesora](../profiling/how-to-collect-cpu-counter-data.md)|  
|Na **zdarzeń systemu Windows** wybierz co najmniej jednego zdarzenia funkcji Śledzenie zdarzeń systemu Windows () do zbierania danych próbkowania.|-   [Porady: zbieranie zdarzeń śledzenia dla danych systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na **liczników systemu Windows** strony, określ co najmniej jeden liczników wydajności systemu operacyjnego można dodać do danych profilowania jako znaczniki.|-   [Porady: zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na **zaawansowane** Określ dodatkowe opcje, które mają zostać przekazane do programu Instrumentacji VSInstr, takich jak opcje, aby dołączyć lub wykluczyć określone funkcje.|-   [Porady: Określanie dodatkowych opcji Instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Porady: ograniczanie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Narzędzie VSInstr](../profiling/vsinstr.md)|