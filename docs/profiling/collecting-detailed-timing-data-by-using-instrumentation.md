---
title: Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 156e3c45c0ccbc9ad9393a2baf7536bf317335bc
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Metody Instrumentacji w narzędziach profilowania injects profilowania kodu do kopii modułu. Każdy wpis, zakończenia i wywołanie funkcji funkcji w module kod rejestruje podczas przebiegu profilowania. Metoda Instrumentacji jest przydatne do zbierania czasu szczegółowe informacje o sekcji kodu i zrozumienie wpływu wejściowymi i wyjściowymi operacje na wydajność aplikacji.  
  
 Metoda Instrumentacji można określić za pomocą jednej z następujących procedur:  
  
-   Na pierwszej stronie kreatora profilowania, wybierz **Instrumentacji**.  
  
-   Na **Eksplorator wydajności** paska narzędzi w **metody** kliknij **Instrumentacji**.  
  
-   Na **ogólne** strony okna dialogowego właściwości sesji wydajności, wybierz opcję **Instrumentacji**.  
  
## <a name="common-tasks"></a>Wspólne zadania
 Możesz określić dodatkowe opcje w *sesji wydajności *** strony właściwości** okno dialogowe sesji wydajności. Aby otworzyć okno dialogowe:  
  
-   W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.  
  
 Zadania w poniższej tabeli opisano opcje, które można określić w *sesji wydajności *** strony właściwości** okno dialogowe, gdy profilu przy użyciu metody instrumentacji.  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|Na **ogólne** strony, Dodaj alokacji pamięci .NET i okres istnienia obiektu i określ szczegóły nazewnictwa profilowania wygenerowany plik danych (Vsp).|-   [Zbieranie danych pamięci .NET alokacji i okresem istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na **uruchamianie** strony, jeśli masz wiele projektów .exe w Twojej solution.specify aplikację do uruchomienia i ich kolejność uruchamiania.|-   [Porady: Określanie plików binarnych do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|  
|Na **plików binarnych** Określ lokalizację kopii instrumentowanych modułów. Domyślnie oryginalnych danych binarnych są przenoszone do folderu kopii zapasowej.|-   [Porady: przemieszczanie instrumentowanych plików binarny](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Na **interakcja warstwowa** Dodaj ADO.NET data wywołania do uruchomienia profilowania.|-   [Zbieranie danych o interakcji między warstwy](../profiling/collecting-tier-interaction-data.md)|  
|Na **Instrumentacji** strony, Wyklucz małe funkcje z profilowanie, aby zmniejszyć profilowania Profiluj kod JavaScript na stronach sieci Web ASP.NET w nakładów pracy i określić polecenia uruchamiane w wierszu polecenia przed i po nich proces instrumentacji.|-   [Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Porady: kodu JavaScript profilu na stronach sieci web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Porady: Określanie poleceń pre-i POST-instrumentalnych](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Na **liczniki CPU** strony, określ co najmniej jeden liczniki wydajności procesora do dodania do danych profilowania.|-   [Porady: zbieranie danych licznika Procesora](../profiling/how-to-collect-cpu-counter-data.md)|  
|Na **zdarzeń systemu Windows** wybierz co najmniej jednego zdarzenia funkcji Śledzenie zdarzeń systemu Windows () do zbierania danych próbkowania.|-   [Porady: zbieranie zdarzenia śledzenia dla danych systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na **liczników systemu Windows** strony, określ co najmniej jeden liczników wydajności systemu operacyjnego można dodać do danych profilowania jako znaczniki.|-   [Porady: zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na **zaawansowane** Określ dodatkowe opcje, które mają zostać przekazane do programu Instrumentacji VSInstr, takich jak opcje, aby dołączyć lub wykluczyć określone funkcje.|-   [Porady: Określanie dodatkowych opcji Instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Porady: ograniczanie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Narzędzie VSInstr](../profiling/vsinstr.md)|