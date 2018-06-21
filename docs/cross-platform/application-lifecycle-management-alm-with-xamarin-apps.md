---
title: Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: f44ad3a7c44f9de592d3b4d4add261fca74f5c39
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36281303"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin

Xamarin umożliwia tworzenie wieloplatformowych aplikacji mobilnych przeznaczonych dla systemu Android, iOS i Windows za pomocą języka C# .NET i Visual Studio. Xamarin umożliwia dużej części kodu mogą być współużytkowane przez platformy, tylko na niewielkim odsetku muszą być specyficzne dla platformy. Aby uzyskać więcej informacji na Xamarin się w temacie [Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md).

Tworzenie aplikacji dla platformy nowoczesnych obejmuje wiele działań więcej niż tylko pisania kodu. Te działania określone jako DevOps (Programowanie + operacji), pełny cykl życia aplikacji obejmują i obejmują planowania i śledzenia elementów pracy, projektowania i wdrażania kodu, zarządzanie repozytorium kodu źródłowego, uruchomionych kompilacji, zarządzanie ciągłej integracji wdrożenia, testowania (w tym testów jednostkowych i interfejsu użytkownika), systemem różne rodzaje diagnostyki w środowiskach produkcyjnych i rozwoju i monitorowanie zachowania wydajności i użytkownika aplikacji w czasie rzeczywistym za pomocą telemetrii i analiza.

Visual Studio oraz Team Foundation Server i Visual Studio Team Services zapewniają szeroką gamę możliwości DevOps, nazywana także zarządzanie cyklem życia aplikacji lub ALM. Wiele z tych dotyczą całkowicie projektów i platform.

Jest to szczególnie istotne, przy użyciu aplikacji Xamarin, ponieważ zostały one utworzone z C# i platformy .NET, wokół którego niektórych ALM są wbudowane narzędzia. Inne narzędzia wymaga ścisłej integracji z środowiska kompilacji i środowiska wykonawczego. Ponieważ aplikacje platformy Xamarin uruchomienia na platformach z systemem innym niż Windows i użyj Mono implementacji programu .NET, Xamarin zawiera narzędzia specjalnych niektórych wymaga.

W poniższych tabelach identyfikuje funkcje programu Visual Studio ALM można oczekiwać działają prawidłowo w projekcie Xamarin i te, które podlegają ograniczeniom. Zajrzyj do dokumentacji połączone, szczegółowe informacje na temat funkcji samodzielnie.

## <a name="agile-tools"></a>Elastyczne narzędzia

Opis łącza:  **[o elastyczne narzędzia i Agile zarządzanie projektem](/vsts/work/backlogs/overview?view=vsts)**

Komentarz ogólny: wszystkie planowania i śledzenia funkcje są niezależne od języków programowania i typ projektu.

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|
|-------------|----------------------------|-------------------------|
|Zarządzanie zaległości i przebiegów|Tak||
|Śledzenie pracy|Tak||
|Współpraca pokoju zespołu|Tak||
|Tablice Kanban|Tak||
|Raport i wizualizowanie postępu|Tak||

## <a name="modeling"></a>Modelowanie

Opis łącza:  **[analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)**

Funkcje projektu są niezależne od języka programowania i pracować z .NET w językach C#. Zobacz [ról architektura i modelowanie diagramów w Software Development](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) dla elementów są związane z kodem.

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|
|-------------|----------------------------|-------------------------|
|Sekwencje — diagramy|Tak||
|Wykresy zależności|Tak||
|Hierarchia wywołań|Tak||
|Projektant klas|Tak||
|Eksploratora architektury|Tak||
|Diagramy UML (Użyj case, działania, klasy, składnika, sekwencji i DSL)|Tak||
|Diagramy warstw|Tak||
|Walidacja warstw|Tak||

## <a name="code"></a>Kod

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|
|-------------|----------------------------|-------------------------|
|[Korzystanie z kontroli wersji Team Foundation](/vsts/tfvc/overview?view=vsts) lub Visual Studio Team Services|Tak||
|[Rozpoczynanie pracy z usługą Git w usłudze Team Services](/vsts/git/gitquickstart?view=vsts&tabs=visual-studio)|Tak||
|[Podnoszenie jakości kodu](../test/improve-code-quality.md)|Tak||
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak|Poza granicami specyficzne dla platformy, gdzie implementacji nie zostanie rozwiązany do czasu wykonywania.|
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||

## <a name="build"></a>Kompilacja

Opis łącza:  **[kompilacji i wydania](/vsts/pipelines/index?view=vsts)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|
|-------------|----------------------------|-------------------------|
|Lokalny serwer TFS|Tak|Maszyny kompilacji musi być zainstalowany program Xamarin i może odnosić się do komputera systemu OS x w celu kompilacji dla systemu iOS. Zobacz [Użyj programu TFVC](/vsts/tfvc/overview?view=vsts)|
|Lokalny serwer kompilacji połączone z Visual Studio Team Services|Tak|Zobacz [kompilacji i wydania agentów](/vsts/pipelines/agents/agents?view=vsts) instrukcje.|
|Usługa kontrolera hostowanej programu Visual Studio Team Services|Tak|Zobacz [tworzenie aplikacji platformy Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts).|
|Tworzenie definicji przed i po skryptów|Tak||
|W tym ciągłą integrację warunkowych zaewidencjonowań|Tak|Warunkowych zaewidencjonowań dla TFVC tylko wtedy, gdy działa Git modelu żądania ściągnięcia zamiast zaewidencjonowania.|

## <a name="test"></a>Test

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|
|-------------|----------------------------|-------------------------|
|Planowanie testów, tworzenie przypadków testowych i organizowanie zestawów testów|Tak||
|Testów ręcznych|Tak||
|Test Manager (rekordu i odtwarzanie testów)|Tak|Urządzenia z systemem Windows i Android emulatorów tylko w programie Visual Studio. Nagrywanie dla wszystkich urządzeń jest możliwe za pomocą [Rejestrator testu Xamarin](/appcenter/test-cloud/uitest/).|
|Pokrycie kodu|n/d||
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|Tak|Dla systemów Windows i Android elementy docelowe można użyć wbudowane narzędzia MSTest. Aby uruchomić testy jednostkowe systemu Windows, Android i iOS, Xamarin zaleca NUnit. Zobacz [Użyj TFVC](/vsts/tfvc/overview?view=vsts).|
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Tylko w systemie Windows|Rejestrator testu interfejsu użytkownika programu Visual Studio jest tylko systemu Windows. Dla wszystkich platform, zobacz [Xamarin.UITest](/appcenter/test-cloud/uitest/).|

## <a name="improve-code-quality"></a>Podnoszenie jakości kodu

Opis łącza:  **[poprawy jakości kodu](../test/improve-code-quality.md)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|
|-------------|----------------------------|-------------------------|
|[Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak||
|[Znajdowanie zduplikowanego kodu za pomocą narzędzia do wykrywania klonu kodu](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak||
|[Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak||
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [profilera Xamarin](/xamarin/cross-platform/deploy-test/) za pomocą platformy Xamarin Studio zamiast tego. Należy pamiętać, że Xamarin Profiler jest obecnie w wersji zapoznawczej i jeszcze nie działa dla celów systemu Windows.|
|[Analiza problemów pamięci .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|Nie|Narzędzia programu Visual Studio nie mają punkty zaczepienia do Mono framework do profilowania.|

## <a name="release-management"></a>Release Management

Opis łącza:  **[kompilacji i wydania programu VSTS i TFS](/vsts/pipelines/overview?view=vsts)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|
|-------------|----------------------------|-------------------------|
|Zarządzanie procesami zlecenia|Tak||
|Wdrażanie serwerów w celu ładowania bezpośredniego za pomocą skryptów|Tak||
|Przekaż do sklepu z aplikacjami|Częściowe|Rozszerzenia są dostępne który można zautomatyzować ten proces niektóre sklepy z aplikacjami.  Zobacz [rozszerzeń dla programu Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), na przykład [rozszerzenia do witryny Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorowanie za pomocą aplikacji HockeyApp

Opis łącza:  **[monitora z HockeyApp](https://www.hockeyapp.net/features/)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|
|-------------|----------------------------|-------------------------|
|Awarii dystrybucji analizy i telemetrię oraz w wersji beta|Tak||