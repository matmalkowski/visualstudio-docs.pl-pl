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
ms.openlocfilehash: b711c6c67eb7466d642048f2546c532b9b2e2926
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231859"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin

Xamarin pozwala tworzyć aplikacje mobilne dla wielu platform przeznaczonych dla systemów Android, iOS i Windows przy użyciu języka C# .NET i Visual Studio. Dużą część kodu można współużytkować na różnych platformach, tylko na niewielkim odsetku przynależności do określonych platform dzięki środowisku Xamarin. Aby uzyskać więcej informacji na środowisku Xamarin, sama zobacz [Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md).

Tworzenie aplikacji dla nowoczesnych platformach obejmuje wiele działań więcej niż tylko pisania kodu. Działania te, określane jako DevOps (Programowanie + operations) obejmuje pełny cykl życia aplikacji i należy planowanie i śledzenie pracy, projektowanie i wdrażanie kodu, repozytorium kodu źródłowego, zarządzanie systemem kompilacji, zarządzanie ciągłej integracji wdrożenia, testowania (w tym testy jednostkowe i testy interfejsu użytkownika), uruchomione różne rodzaje diagnostykę w środowiskach środowisk deweloperskich i produkcyjnych i monitorowania aplikacji wydajności i zachowania użytkowników w czasie rzeczywistym za pośrednictwem danych telemetrycznych i analitycznych.

Visual Studio wraz z Visual Studio Team Services i serwera Team Foundation Server zapewniają szeroką gamę możliwości środowiska DevOps, zwaną także zarządzanie cyklem życia aplikacji lub ALM. Wiele z nich są całkowicie mające zastosowanie do projektów dla wielu platform.

Jest to szczególnie istotne, przy użyciu aplikacji Xamarin, ponieważ są one tworzone za pomocą języka C# i .NET, wokół którego niektóre ALM są wbudowane narzędzia. Inne narzędzia wymaga ścisłej integracji ze środowiskami kompilacji i czasu wykonywania. Ponieważ aplikacje platformy Xamarin działać na platformach innych niż Windows i użyć narzędzia Mono implementacji .NET, środowisko Xamarin zapewnia specjalistycznych narzędzi określonych potrzeb.

W poniższych tabelach identyfikuje funkcji programu Visual Studio ALM, które można oczekiwać, że do sprawnej współpracy z projektu Xamarin i te, które mają ograniczenia. Zapoznaj się z dokumentacją połączone, aby uzyskać szczegółowe informacje na temat funkcji, samodzielnie.

## <a name="agile-tools"></a>Narzędzia agile

Opis łącza:  **[zarządzanie projektem o Zwinne narzędzia i Agile](/vsts/work/backlogs/overview?view=vsts)**

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
|[Użyj kontroli wersji serwera Team Foundation](/vsts/tfvc/overview?view=vsts) lub Visual Studio Team Services|Tak||
|[Wprowadzenie do usługi Git w usłudze Team Services](/vsts/git/gitquickstart?view=vsts&tabs=visual-studio)|Tak||
|[Podnoszenie jakości kodu](../test/improve-code-quality.md)|Tak||
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak|Poza granice specyficzne dla platformy, których implementacja nie zostanie rozwiązany do czasu wykonywania.|
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||

## <a name="build"></a>Kompilacja

Opis łącza:  **[kompilowania i wydawania](/vsts/pipelines/index?view=vsts)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Lokalny serwer TFS|Tak|Maszyny kompilacji musi być zainstalowany program Xamarin i mogą być połączone do komputera systemu OSX kompilacji dla systemu iOS. Zobacz [użyć TFVC](/vsts/tfvc/overview?view=vsts)|
|Serwer kompilacji w środowisku lokalnym, połączone z Visual Studio Team Services|Tak|Zobacz [Build and release agents i](/vsts/pipelines/agents/agents?view=vsts) instrukcje.|
|Usługa hostowana kontrolera programu Visual Studio Team Services|Tak|Zobacz [kompilowania aplikacji platformy Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts).|
|Tworzenie definicji przy użyciu wstępnego i skryptu używanego po utworzeniu|Tak||
|W tym ciągłą integrację warunkowych zaewidencjonowań|Tak|Warunkowych zaewidencjonowań w przypadku repozytorium TFVC, tylko wtedy, gdy usługa Git działa w modelu żądania ściągnięcia, a nie do zaewidencjonowania.|

## <a name="test"></a>Test

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Planowanie testów, tworzenie przypadków testowych i porządkowanie zestawów testów|Tak||
|Testowanie ręczne|Tak||
|Test Manager (nagrywanie i odtwarzanie testów)|Tak|Urządzenia Windows i emulatory systemu Android tylko w programie Visual Studio. Nagrywanie dla wszystkich urządzeń jest możliwe dzięki [Xamarin Test Recorder](/appcenter/test-cloud/uitest/).|
|Pokrycie kodu|n/d||
|[Kod testu jednostkowego](../test/unit-test-your-code.md)|Tak|Windows i Android elementów docelowych można wbudowane narzędzia MSTest. Aby uruchomić testy jednostkowe w Windows, Android i iOS, Xamarin zaleca NUnit. Zobacz [użyć TFVC](/vsts/tfvc/overview?view=vsts).|
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Tylko Windows|Rejestrator testu interfejsu użytkownika programu Visual Studio jest Windows tylko. Dla wszystkich platform, zobacz [Xamarin.UITest](/appcenter/test-cloud/uitest/).|

## <a name="improve-code-quality"></a>Poprawianie jakości kodu

Opis łącza:  **[poprawić jakość kodu](../test/improve-code-quality.md)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|[Analizowanie jakości kodu zarządzanego](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak||
|[Znajdowanie kodu zduplikowanego przy użyciu wykrywania klonu kodu](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak||
|[Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak||
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [Xamarin Profiler](/xamarin/cross-platform/deploy-test/) za pomocą programu Xamarin Studio zamiast tego. Należy pamiętać, że Profiler platformy Xamarin jest obecnie dostępna w wersji zapoznawczej, a jeszcze nie działa dla celów Windows.|
|[Analizowanie problemów pamięci .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|Nie|Narzędzia programu Visual Studio nie ma punktów zaczepienia w Mono framework do profilowania.|

## <a name="release-management"></a>Release Management

Opis łącza:  **[kompilowania i wydawania w usłudze VSTS i TFS](/vsts/pipelines/overview?view=vsts)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Zarządzanie procesów tworzenia wersji|Tak||
|Wdrażanie serwerów na potrzeby ładowania bezpośredniego za pośrednictwem skryptów|Tak||
|Przekazywanie do sklepu z aplikacjami|Częściowe|Rozszerzenia są dostępne, można zautomatyzować ten proces dla niektóre sklepy z aplikacjami.  Zobacz [rozszerzenia programu Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), na przykład [rozszerzenia do witryny Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorowanie za pomocą platformy HockeyApp

Opis łącza:  **[monitorowanie za pomocą platformy HockeyApp](https://www.hockeyapp.net/features/)**

|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|
|-------------|----------------------------|-------------------------|
|Awarii dystrybucji analizy i telemetrię oraz wersji beta|Tak||