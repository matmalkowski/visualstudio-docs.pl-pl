---
title: "Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 41fe8afba19939dfbbbd5c055f5ebd53e9fc2e04
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin
Xamarin umożliwia tworzenie wieloplatformowych aplikacji mobilnych przeznaczonych dla systemu Android, iOS i Windows za pomocą języka C# .NET i Visual Studio. Xamarin umożliwia dużej części kodu mogą być współużytkowane przez platformy, tylko na niewielkim odsetku muszą być specyficzne dla platformy. Aby uzyskać więcej informacji na Xamarin się w temacie [Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Tworzenie aplikacji dla platformy nowoczesnych obejmuje wiele działań więcej niż tylko pisania kodu. Te działania określone jako DevOps (Programowanie + operacji), pełny cykl życia aplikacji obejmują i obejmują planowania i śledzenia elementów pracy, projektowania i wdrażania kodu, zarządzanie repozytorium kodu źródłowego, uruchomionych kompilacji, zarządzanie ciągłej integracji wdrożenia, testowania (w tym testów jednostkowych i interfejsu użytkownika), systemem różne rodzaje diagnostyki w środowiskach produkcyjnych i rozwoju i monitorowanie zachowania wydajności i użytkownika aplikacji w czasie rzeczywistym za pomocą telemetrii i analiza.  
  
 Visual Studio oraz Team Foundation Server i Visual Studio Team Services zapewniają szeroką gamę możliwości DevOps, nazywana także zarządzanie cyklem życia aplikacji lub ALM. Wiele z tych dotyczą całkowicie projektów i platform.  
  
 Jest to szczególnie istotne, przy użyciu aplikacji Xamarin, ponieważ zostały one utworzone z C# i platformy .NET, wokół którego niektórych ALM są wbudowane narzędzia. Inne narzędzia wymaga ścisłej integracji z środowiska kompilacji i środowiska wykonawczego. Ponieważ aplikacje platformy Xamarin uruchomienia na platformach z systemem innym niż Windows i użyj Mono implementacji programu .NET, Xamarin zawiera narzędzia specjalnych niektórych wymaga.  
  
 W poniższych tabelach identyfikuje funkcje programu Visual Studio ALM można oczekiwać działają prawidłowo w projekcie Xamarin i te, które podlegają ograniczeniom. Zajrzyj do dokumentacji połączone, szczegółowe informacje na temat funkcji samodzielnie.  
  
## <a name="agile-tools"></a>Elastyczne narzędzia  
 Opis łącza:  **[pracy](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)**  (przy użyciu programu Visual Studio Team Services lub TFS, w tym programu Team Explorer Everywhere)  
  
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
|[Korzystanie z kontroli wersji Team Foundation](http://msdn.microsoft.com/Library/1d629052-c65d-4c5d-81eb-eaa4413fe285) lub Visual Studio Team Services|Tak||  
|[Rozpoczynanie pracy z usługą Git w usłudze Team Services](http://msdn.microsoft.com/Library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Tak||  
|[Podnoszenie jakości kodu](/visualstudio/test/improve-code-quality)|Tak||  
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak|Poza granicami specyficzne dla platformy, gdzie implementacji nie zostanie rozwiązany do czasu wykonywania.|  
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||  
  
## <a name="build"></a>Kompilacja  
 Opis łącza:  **[kompilacji](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|  
|-------------|----------------------------|-------------------------|  
|Lokalny serwer TFS|Tak|Maszyny kompilacji musi być zainstalowany program Xamarin i może odnosić się do komputera systemu OS x w celu kompilacji dla systemu iOS. Zobacz [Konfigurowanie TFS xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin witryny sieci Web)|  
|Lokalny serwer kompilacji połączone z Visual Studio Team Services|Tak|Zobacz [serwera kompilacji](http://msdn.microsoft.com/Library/2d258a0a-f178-4e93-9da1-eba61151af3c) instrukcje.|  
|Usługa kontrolera hostowanej programu Visual Studio Team Services|Tak|Zobacz [tworzenie aplikacji platformy Xamarin](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin).|  
|Tworzenie definicji przed i po skryptów|Tak||  
|W tym ciągłą integrację warunkowych zaewidencjonowań|Tak|Warunkowych zaewidencjonowań dla TFVC tylko wtedy, gdy działa Git modelu żądania ściągnięcia zamiast zaewidencjonowania.|  
  
## <a name="testing"></a>Testowanie  
 Opis łącza:  **[testowanie aplikacji](/devops-test-docs/test/test-apps-early-and-often)**  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|  
|-------------|----------------------------|-------------------------|  
|Planowanie testów, tworzenie przypadków testowych i organizowanie zestawów testów|Tak||  
|Testów ręcznych|Tak||  
|Test Manager (rekordu i odtwarzanie testów)|Tak|Urządzenia z systemem Windows i Android emulatorów tylko w programie Visual Studio. Nagrywanie dla wszystkich urządzeń jest możliwe za pomocą [Rejestrator testu Xamarin](https://www.xamarin.com/test-cloud/recorder).|  
|Pokrycie kodu|n/d||  
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|Tak|Dla systemów Windows i Android elementy docelowe można użyć wbudowane narzędzia MSTest. Aby uruchomić testy jednostkowe systemu Windows, Android i iOS, Xamarin zaleca NUnit. Zobacz [Konfigurowanie TFS xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin witryny sieci Web).|  
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Tylko w systemie Windows|Rejestrator testu interfejsu użytkownika programu Visual Studio jest tylko systemu Windows. Dla wszystkich platform, zobacz [Rejestrator testu Xamarin](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Podnoszenie jakości kodu  
 Opis łącza:  **[poprawy jakości kodu](/visualstudio/test/improve-code-quality)**  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe uwagi|  
|-------------|----------------------------|-------------------------|  
|[Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak||  
|[Znajdowanie zduplikowanego kodu za pomocą narzędzia do wykrywania klonu kodu](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak||  
|[Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak||  
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [profilera Xamarin](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) za pomocą platformy Xamarin Studio zamiast tego. Należy pamiętać, że Xamarin Profiler jest obecnie w wersji zapoznawczej i jeszcze nie działa dla celów systemu Windows.|  
|[Analiza problemów pamięci .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|Nie|Narzędzia programu Visual Studio nie mają punkty zaczepienia do Mono framework do profilowania.|  
  
## <a name="release-management"></a>Release Management  
 Opis łącza:  **[Automatyzacja wdrażania przy użyciu zarządzania zleceniami](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
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