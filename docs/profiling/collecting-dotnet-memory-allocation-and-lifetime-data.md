---
title: "Zbieranie alokacji pamięci .NET i okres istnienia obiektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 5607f5a2828b7589cbe803732262a52d9e760421
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-net-memory-allocation-and-lifetime-data"></a>Zbieranie alokacji pamięci .NET i okres istnienia obiektu
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Narzędzia profilowania obsługuje zbieranie alokacji pamięci .NET i danych o okresie istnienia obiektu, które pomaga wykrywać problemy z wydajnością związane z pamięcią w aplikacji.  
  
-   Dane dotyczące alokacji pamięci .NET obejmuje rozmiaru i liczby obiektów pamięci .NET Framework, które zostały przydzielone.  
  
-   Danych o okresie istnienia obiektu zawiera, rozmiar i liczba obiektów pamięci .NET Framework, które zostały odzyskane w trzy generacje wyrzucania elementów w kolekcji.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Można zbierać dane za pomocą próbki lub metoda profilowania instrumentacji.  
  
-   Przy użyciu metody próbkowania profilera śledzi wszystkie alokacji pamięci .NET i obiekty, które są generowane przez proces, która została uruchomiona lub dołączony do.  
  
-   Przy użyciu metody Instrumentacji profilera śledzenie tylko alokacji pamięci .NET i obiekty, które są generowane przez moduły Instrumentacją.  
  
> [!IMPORTANT]
>  Gdy są zbieranie danych pamięci .NET (alokacji, okresy istnienia obiektu lub oba), za pomocą metody pobierania próbek, wszystkie zdarzenia próbkowania określone przez użytkownika są ignorowane, a zdarzenia alokacji odpowiedniej ilości pamięci są używane do zbierania danych.  
  
 Włączenie profilowania alokacji pamięci of.NET, należy również włączyć widok alokacji. Włączenie profilowania danych o okresie istnienia .NET, należy również włączyć widok okresu istnienia obiektów. Aby uzyskać więcej informacji, zobacz [Widok alokacji](../profiling/dotnet-memory-allocations-view.md) i [widok okresu istnienia obiektu](../profiling/object-lifetime-view.md).  
  
 Aby uzyskać informacje dotyczące zbierania danych pamięci .NET przy użyciu narzędzia wiersza polecenia narzędzi profilowania, zobacz za pomocą metod .NET pamięci zbieranie alokacji pamięci oraz danych o okresie istnienia obiektu w [przy użyciu profilowania metody z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### <a name="to-collect-net-memory-data"></a>Zbieranie danych pamięci .NET  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
2.  Na *sesji wydajności***strony właściwości** okno dialogowe, kliknij przycisk **ogólne** , a następnie wybierz **.NET zbierać informacje dotyczące alokacji obiektów** pole wyboru.  
  
3.  Do zbierania danych o okresie istnienia obiektu platformy .NET, wybierz **również zbierać informacje dotyczące okresu istnienia obiektu platformy .NET** pole wyboru.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Możesz określić dodatkowe opcje w *sesji wydajności***strony właściwości** okno dialogowe sesji wydajności. Aby otworzyć okno dialogowe:  
  
-   W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.  
  
 Zadania w poniższej tabeli opisano opcje, które można określić w *sesji wydajności***strony właściwości** okno dialogowe podczas zbierania danych pamięci .NET.  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|Na **ogólne** Określ szczegóły nazewnictwa dla profilowania wygenerowany plik danych (Vsp).|-   [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na **uruchamianie** wybierz aplikację do uruchomienia, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|-   [Zbieranie danych o interakcji między warstwy](../profiling/collecting-tier-interaction-data.md)|  
|Na **interakcja warstwowa** Dodaj ADO.NET data wywołania do uruchomienia profilowania.|-   [Zbieranie danych o interakcji między warstwy](../profiling/collecting-tier-interaction-data.md)|  
|Na **zdarzeń systemu Windows** Określ co najmniej jednego zdarzenia funkcji Śledzenie zdarzeń systemu Windows () do zbierania danych próbkowania.|-   [Porady: zbieranie zdarzeń śledzenia dla danych systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na **liczników systemu Windows** strony, określ co najmniej jeden liczników wydajności systemu operacyjnego można dodać do danych profilowania jako znaczniki.|-   [Porady: zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na **zaawansowane** strony, określ wersję środowiska uruchomieniowego .NET Framework do profilowania, jeśli moduły aplikacji używać wielu wersji. Domyślnie jest profilowane pierwszej wersji załadowane.|-   [Porady: Określanie środowiska wykonawczego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## <a name="instrumentation-tasks"></a>Zadania Instrumentacji  
 Zadania w poniższej tabeli są opcje w **strony właściwości** okno dialogowe, które są specyficzne dla profilowania przy użyciu metody instrumentacji.  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|Na **plików binarnych** Określ lokalizację kopii instrumentowanych modułów. Domyślnie oryginalnych danych binarnych są przenoszone do folderu kopii zapasowej.|-   [Porady: przemieszczanie instrumentowanych plików binarny](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Na **Instrumentacji** strony, Wyklucz małe funkcje z profilowanie, aby zmniejszyć profilowania Profiluj kod JavaScript na stronach sieci Web ASP.NET w nakładów pracy i określić polecenia uruchamiane w wierszu polecenia przed i po nich proces instrumentacji.|-   [Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Porady: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Porady: Określanie poleceń Pre-i POST-instrumentalnych](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Na **liczniki CPU** strony, określ co najmniej jeden liczniki wydajności procesora do dodania do danych profilowania.|-   [Porady: zbieranie danych licznika Procesora](../profiling/how-to-collect-cpu-counter-data.md)|  
|Na **zaawansowane** określ wszelkie dodatkowe VSInstr.exe opcje, że chcesz, takich jak opcje, aby dołączyć lub wykluczyć określone funkcje. Aby uzyskać więcej informacji na temat opcji VSInstr, zobacz [VSInstr](../profiling/vsinstr.md)|-   [Porady: Określanie dodatkowych opcji Instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Porady: ograniczanie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)