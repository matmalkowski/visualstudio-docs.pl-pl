---
title: Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin | Dokumentacja firmy Microsoft
ms.date: 08/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: e4dea73bc3d3c1e7db77544b24be1525fca0a202
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282357"
---
# <a name="devops-with-xamarin-apps"></a>Metodyka DevOps z użyciem platformy Xamarin

Xamarin pozwala tworzyć aplikacje mobilne dla wielu platform przeznaczonych dla systemów Android, iOS i Windows przy użyciu języka C# .NET i Visual Studio. Dużą część kodu można współużytkować na różnych platformach, tylko na niewielkim odsetku przynależności do określonych platform dzięki środowisku Xamarin. Aby uzyskać więcej informacji na środowisku Xamarin, sama zobacz [Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md).

Tworzenie aplikacji dla nowoczesnych platformach obejmuje wiele działań więcej niż tylko pisania kodu. Działania te, określane jako DevOps (Programowanie + operations) obejmuje pełny cykl życia aplikacji i należy planowanie i śledzenie pracy, projektowanie i wdrażanie kodu, repozytorium kodu źródłowego, zarządzanie systemem kompilacji, zarządzanie ciągłej integracji wdrożenia, testowania (w tym testy jednostkowe i testy interfejsu użytkownika), uruchomione różne rodzaje diagnostykę w środowiskach środowisk deweloperskich i produkcyjnych i monitorowania aplikacji wydajności i zachowania użytkowników w czasie rzeczywistym za pośrednictwem danych telemetrycznych i analitycznych.

Wraz z usługom DevOps platformy Azure i serwera Team Foundation Server w programie Visual Studio udostępnia szereg możliwości środowiska DevOps. Wiele z nich są całkowicie mające zastosowanie do projektów dla wielu platform. Jest to szczególnie istotne, przy użyciu aplikacji Xamarin, ponieważ są one skompilowanych przy użyciu języka C# i .NET, wokół którego niektóre DevOps są wbudowane narzędzia. Inne narzędzia wymaga ścisłej integracji ze środowiskami kompilacji i czasu wykonywania. Ponieważ aplikacje platformy Xamarin działać na platformach innych niż Windows i użyć narzędzia Mono implementacji .NET, środowisko Xamarin zapewnia specjalistycznych narzędzi określonych potrzeb.

Poniższe tabele zidentyfikować, które funkcje DevOps w programie Visual Studio można oczekiwać, że do sprawnej współpracy z projektu Xamarin i te, które mają ograniczenia. Zapoznaj się z dokumentacją połączone, aby uzyskać szczegółowe informacje na temat funkcji, samodzielnie.

## <a name="agile-tools"></a>Narzędzia agile

Opis łącza:  **[zarządzanie projektem o Zwinne narzędzia i Agile](/azure/devops/boards/backlogs/overview?view=vsts)**

Komentarz ogólny: wszystkie planowania i śledzenia funkcji są niezależne od typu projektu i języków programowania.

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Zarządzanie zaległości i sprintów|Tak||
|Śledzenie pracy|Tak||
|Współpraca pokoju zespołu|Tak||
|Tablice Kanban|Tak||
|Tworzenie raportów i wizualizowanie postępu|Tak||

## <a name="modeling"></a>Modelowanie

Opis łącza:  **[analiza i architektura modelu](../modeling/analyze-and-model-your-architecture.md)**

Projektowe są niezależne od języka programowania, lub pracować z języków .NET, takich jak C#. Zobacz [role architektury i diagramów modelowania w tworzeniu oprogramowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) dla jakich aspekty są związane z kodem.

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Diagramy sekwencji|Tak||
|Wykresy zależności|Tak||
|Hierarchia wywołań|Tak||
|Projektant klas|Tak||
|Eksplorator architektury|Tak||
|Diagramy UML (Użyj przypadek, działania, klasy, składnika, sekwencja i DSL)|Tak||
|Diagramy warstwowe|Tak||
|Sprawdzanie poprawności warstwy|Tak||

## <a name="code"></a>Kod

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|[Użyj Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) lub repozytoriów platformy Azure|Tak||
|[Wprowadzenie do usługi Git w repozytoriach platformy Azure](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Tak||
|[Podnoszenie jakości kodu](../test/improve-code-quality.md)|Tak||
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak|Poza granice specyficzne dla platformy, których implementacja nie zostanie rozwiązany do czasu wykonywania.|
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||

## <a name="build"></a>Kompilacja

Opis łącza:  **[potoki usługi Azure](/azure/devops/pipelines/index?view=vsts)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Lokalny serwer TFS|Tak|Maszyny kompilacji musi być zainstalowany program Xamarin i mogą być połączone do komputera systemu OSX kompilacji dla systemu iOS. Zobacz [użyć TFVC](/azure/devops/repos/tfvc/overview?view=vsts)|
|Serwer kompilacji w środowisku lokalnym, połączone z potoków usługi Azure|Tak|Zobacz [Build and release agents i](/azure/devops/pipelines/agents/agents?view=vsts) instrukcje.|
|Usługa hostowana kontrolera potoków usługi Azure|Tak|Zobacz [kompilowania aplikacji platformy Xamarin](/azure/devops/pipelines/languages/xamarin?view=vsts&tabs=vsts).|
|Tworzenie definicji przy użyciu wstępnego i skryptu używanego po utworzeniu|Tak||
|W tym ciągłą integrację warunkowych zaewidencjonowań|Tak|Warunkowych zaewidencjonowań w przypadku repozytorium TFVC, tylko wtedy, gdy usługa Git działa w modelu żądania ściągnięcia, a nie do zaewidencjonowania.|

## <a name="test"></a>Test

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Planowanie testów, tworzenie przypadków testowych i porządkowanie zestawów testów|Tak||
|Testowanie ręczne|Tak||
|Test Manager (nagrywanie i odtwarzanie testów)|Tak|Urządzenia Windows i emulatory systemu Android tylko w programie Visual Studio. Nagrywanie dla wszystkich urządzeń jest możliwe dzięki [Xamarin Test Recorder](/appcenter/test-cloud/uitest/).|
|Pokrycie kodu|n/d||
|[Kod testu jednostkowego](../test/unit-test-your-code.md)|Tak|Windows i Android elementów docelowych można wbudowane narzędzia MSTest. Aby uruchomić testy jednostkowe w Windows, Android i iOS, Xamarin zaleca NUnit. Zobacz [użyć TFVC](/azure/devops/repos/tfvc/overview?view=vsts).|
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Tylko Windows|Rejestrator testu interfejsu użytkownika programu Visual Studio jest Windows tylko. Dla wszystkich platform, zobacz [Xamarin.UITest](/appcenter/test-cloud/uitest/).|

## <a name="improve-code-quality"></a>Poprawianie jakości kodu

Opis łącza:  **[poprawić jakość kodu](../test/improve-code-quality.md)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|[Analizowanie jakości kodu zarządzanego](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak||
|[Znajdowanie kodu zduplikowanego przy użyciu wykrywania klonu kodu](https://msdn.microsoft.com/library/hh205279.aspx)|Tak||
|[Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak||
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [Xamarin Profiler](/xamarin/cross-platform/deploy-test/) za pomocą programu Xamarin Studio zamiast tego. Należy pamiętać, że Profiler platformy Xamarin jest obecnie dostępna w wersji zapoznawczej, a jeszcze nie działa dla celów Windows.|
|[Analizowanie problemów pamięci .NET Framework](https://msdn.microsoft.com/library/dn342825.aspx)|Nie|Narzędzia programu Visual Studio nie ma punktów zaczepienia w Mono framework do profilowania.|

## <a name="release-management"></a>Release Management

Opis łącza:  **[kompilowania i wydawania w potokach platformy Azure i TFS](/azure/devops/pipelines/overview?view=vsts)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Zarządzanie procesów tworzenia wersji|Tak||
|Wdrażanie serwerów na potrzeby ładowania bezpośredniego za pośrednictwem skryptów|Tak||
|Przekazywanie do sklepu z aplikacjami|Częściowe|Rozszerzenia są dostępne, można zautomatyzować ten proces dla niektóre sklepy z aplikacjami.  Zobacz [rozszerzeń dla usługi Azure DevOps Services](https://marketplace.visualstudio.com/VSTS), na przykład [rozszerzenia do witryny Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorowanie za pomocą platformy HockeyApp

Opis łącza:  **[monitorowanie za pomocą platformy HockeyApp](https://www.hockeyapp.net/features/)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Awarii dystrybucji analizy i telemetrię oraz wersji beta|Tak||
