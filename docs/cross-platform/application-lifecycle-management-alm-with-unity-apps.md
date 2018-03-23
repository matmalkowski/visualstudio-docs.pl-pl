---
title: Zarządzanie cyklem życia aplikacji (ALM) dla aplikacji Unity | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-unity-tools
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 05196d7c9e6b1b441db61f599dcfe39c4d5cba56
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) dla aplikacji Unity
Tworzenie aplikacji dla platformy nowoczesnych obejmuje wiele działań więcej niż tylko pisania kodu. Te działania określone jako DevOps (Programowanie + operations) obejmuje pełny cykl życia aplikacji i obejmują planowania i śledzenia elementów pracy, projektowania i wdrażania kodu, zarządzanie repozytorium kodu źródłowego, uruchomionych kompilacji, zarządzanie ciągłej integracji wdrożenia, testowania (w tym testów jednostkowych i interfejsu użytkownika), systemem różne rodzaje diagnostyki w środowiskach produkcyjnych i rozwoju i monitorowanie zachowania wydajności i użytkownika aplikacji w czasie rzeczywistym za pomocą telemetrii i analiza.

 Visual Studio oraz Team Foundation Server i Visual Studio Team Services zapewniają szeroką gamę możliwości DevOps, nazywana także zarządzanie cyklem życia aplikacji lub ALM. Wiele z tych mają zastosowanie do projektów i platform, łącznie z gier i bez ramek graficznego aplikacji utworzonych za pomocą platformy Unity — szczególnie w przypadku, gdy przy użyciu języka C# jako język skryptów. Jednak ponieważ Unity ma swoje własne Środowisko deweloperskie i aparatu wykonawczego, wiele funkcji ALM nie stosuj tak jak inne rodzaje projektów wbudowanych w programie Visual Studio.

 W poniższych tabelach identyfikuje sposób funkcje programu Visual Studio ALM zastosowania lub nie stosuj podczas pracy z Unity. Zajrzyj do dokumentacji połączone, szczegółowe informacje na temat funkcji samodzielnie.

## <a name="agile-tools"></a>Elastyczne narzędzia
 Opis łącza: **[pracy](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (przy użyciu programu Visual Studio Team Services lub TFS, w tym programu Team Explorer Everywhere)

 Komentarz ogólny: wszystkie planowania i śledzenia funkcje są niezależne od języków programowania i typ projektu.

|Funkcja|Obsługiwane z Unity|Dodatkowe uwagi|
|-------------|--------------------------|-------------------------|
|Zarządzanie zaległości i przebiegów|Tak||
|Śledzenie pracy|Tak||
|Współpraca pokoju zespołu|Tak||
|Tablice Kanban|Tak||
|Raport i wizualizowanie postępu|Tak||

## <a name="modeling"></a>Modelowanie
 Opis łącza:  **[analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)**

 Komentarz ogólny: Mimo że te funkcje projektu są albo niezależnie od języka programowania i pracować z .NET w językach C#, działają na modelu tradycyjnych aplikacji, z hierarchie obiektów i relacji klas. Projektowanie grę w Unity obejmuje różne modelu, czyli relacje obiektów graficznych, dźwięki programów do cieniowania, skrypty i tak dalej. Z tego powodu Visual Studio modelowania diagram narzędzia nie są szczególnie istotne dla całego projektu platformy Unity. Ewentualnie można można użyć do zarządzania relacjami w języku C# skrypty, ale jest tylko jedna część całości.

|Funkcja|Obsługiwane z Unity|Dodatkowe uwagi|
|-------------|--------------------------|-------------------------|
|Sekwencje — diagramy|Nie||
|Wykresy zależności|Nie||
|Hierarchia wywołań|Nie||
|Projektant klas|Nie||
|Eksploratora architektury|Nie||
|Diagramy UML (Użyj case, działania, klasy, składnika, sekwencji i DSL)|Nie||
|Diagramy warstw|Nie||
|Walidacja warstw|Nie||

## <a name="code"></a>Kod

|Funkcja|Obsługiwane z Unity|Dodatkowe uwagi|
|-------------|--------------------------|-------------------------|
|[Korzystanie z kontroli wersji Team Foundation](http://msdn.microsoft.com/Library/1d629052-c65d-4c5d-81eb-eaa4413fe285) lub Visual Studio Team Services|Tak|Projekty platformy Unity są po prostu kolekcji plików, które mogą być umieszczane w systemów kontroli wersji, jak inny projekt, ale istnieje kilka uwagi opisanych pod tą tabelą.|
|[Rozpoczynanie pracy z usługą Git w usłudze Team Services](http://msdn.microsoft.com/Library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Tak|Zobacz uwagi pod tabelą.|
|[Podnoszenie jakości kodu](/visualstudio/test/improve-code-quality)|Tak||
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak||
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||

 Uwagi dotyczące kontroli wersji z Unity:

1.  Unity śledzi metadane dotyczące gier zasoby w jednej, nieprzezroczyste biblioteki, która jest domyślnie ukryty. Aby zachować synchronizację plików i metadanych, jest niezbędne, aby wyświetlić metadane i zapisz go w innych partiach łatwych do. Aby uzyskać więcej informacji, zapoznaj się [przy użyciu systemów usługi kontroli wersji zewnętrznych z Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentacja Unity).

2.  Nie wszystkie pliki i foldery w projekcie platformy Unity są odpowiednie do kontroli źródła, jest również opisane w artykule łącze powyżej. Foldery zasobów i ProjectSettings powinny zostać dodane, ale folderów biblioteki i Temp nie powinien. Dodatkowa Lista wygenerowanych plików, które nie przejdzie do kontroli źródła, można znaleźć w omówieniu [sposobu użycia Git do kontroli źródła Unity3D?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) w witrynie StackOverflow. Wielu deweloperów muszą również blogged na ten temat niezależnie.

3.  Binarny zasobów w projekcie platformy Unity — takie jak tekstury lub plików audio — może zająć dużo pamięci. Różnych systemów kontroli źródła, takich jak Git przechowywać unikatową kopię pliku dla każdej zmiany, które zostało utworzone, nawet jeśli zmiana dotyczy tylko niewielką część pliku. Może to spowodować repozytorium Git, aby stać się przeglądarek. Aby rozwiązać ten problem, deweloperzy Unity często zdecydować się na dodać zasoby tylko końcowego ich repozytorium i używać różnych oznacza pozostawienie historię pracy ich zasobów, takich jak OneDrive, DropBox lub załączniku git. Ta metoda działa, ponieważ takie zasoby zwykle nie trzeba być wersjonowany wraz z zmiany kodu źródłowego. Deweloperzy zwykle także Ustaw tryb serializacji zasobów Edytor projektu życie tekstu do przechowywania plików sceny tekstowym zamiast formatu binarnego, co umożliwia obsługę scalenia w kontroli źródła. Aby uzyskać więcej informacji, zobacz [ustawienia edytora](http://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentacja Unity).

## <a name="build"></a>Kompilacja
 Opis łącza:  **[kompilacji i wydania](/vsts/build-release/index)**

|Funkcja|Obsługiwane z Unity|Dodatkowe uwagi|
|-------------|--------------------------|-------------------------|
|Lokalny serwer TFS|Możliwe|Projekty platformy Unity są tworzone za pomocą środowiska Unity i nie za pomocą programu Visual Studio kompilacji systemu (Tworzenie w programie Visual Studio Tools dla Unity będzie skompilować skrypty, ale nie tworzy plik wykonywalny). Istnieje możliwość [kompilacji projektów środowiska Unity w wierszu polecenia](http://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentacja Unity), więc możliwe jest Konfigurowanie procesu programu MSBuild na serwerze TFS można wykonać odpowiednie Unity poleceń, pod warunkiem, że Unity sam jest zainstalowany na tego komputera.<br /><br /> Oferuje również Unity [jednolitości chmury kompilacji](https://build.cloud.unity3d.com/landing/), który monitoruje repozytorium Git lub SVN i uruchamia okresowe kompilacji. Obecnie działa z kontroli wersji Team Foundation i Visual Studio Team Services.|
|Lokalny serwer kompilacji połączone z Visual Studio Team Services|Możliwe|Podany samych warunków dodatkowo jest możliwe bezpośrednie kompilacje wyzwalane za pomocą programu Visual Studio Team Services, aby lokalnie na komputerze TFS.  Zobacz [kompilacji i wydania agentów](/vsts/build-release/concepts/agents/agents) instrukcje.|
|Usługa kontrolera hostowanej programu Visual Studio Team Services|Nie|Kompilacje Unity nie są obecnie obsługiwane.|
|Tworzenie definicji przed i po skryptów|Tak|Można również skonfigurować definicję kompilacji niestandardowej, która używa Unity wiersza polecenia do uruchomienia kompilacji dla skryptów przed i po kompilacji.|
|W tym ciągłą integrację warunkowych zaewidencjonowań|Tak|Warunkowych zaewidencjonowań dla TFVC tylko wtedy, gdy działa Git modelu żądania ściągnięcia zamiast zaewidencjonowania.|

## <a name="testing"></a>Testowanie

|Funkcja|Obsługiwane z Unity|Dodatkowe uwagi|
|-------------|--------------------------|-------------------------|
|Planowanie testów, tworzenie przypadków testowych i organizowanie zestawów testów|Tak||
|Testów ręcznych|Tak||
|Test Manager (rekordu i odtwarzanie testów)|Urządzenia z systemem Windows i Android emulatorów tylko||
|Pokrycie kodu|n/d|Nie dotyczy jako jednostka testowania to następuje w Unity i nie Visual Studio, zobacz poniżej.|
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|W ramach Unity, ale nie w programie Visual Studio|Udostępnia Unity własną jednostkę test framework jako część [narzędzia testowe Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity zasobów magazynu). Wyniki testów jednostkowych są zgłaszane w ramach platformy Unity i nie zostaną wyświetlone w programie Visual Studio.|
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Nie|Kodowane testy interfejsu użytkownika zależą od formantów do odczytu w Interfejsie użytkownika aplikacji; Aplikacji Unity są graficznych i dlatego zawartość nie jest możliwy za pomocą narzędzi testu kodowanego interfejsu użytkownika.|

## <a name="improve-code-quality"></a>Podnoszenie jakości kodu

Opis łącza:  **[poprawy jakości kodu](/visualstudio/test/improve-code-quality)**

|Funkcja|Obsługiwane z Unity|Dodatkowe uwagi|
|-------------|--------------------------|-------------------------|
|[Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak|Można analizować kodu skryptu C# w programie Visual Studio.|
|[Znajdowanie zduplikowanego kodu za pomocą narzędzia do wykrywania klonu kodu](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak|Można analizować kodu skryptu C# w programie Visual Studio.|
|[Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak|Można analizować kodu skryptu C# w programie Visual Studio.|
|[Performance Explorer](../profiling/performance-explorer.md)|Nie|Użyj [profilera Unity](http://docs.unity3d.com/Manual/Profiler.html) (Unity witryny sieci Web).|
|[Analiza problemów pamięci .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|Nie|Narzędzia programu Visual Studio nie mają punkty zaczepienia w ramach Mono (używano Unity) do profilowania. Użyj [profilera Unity](http://docs.unity3d.com/Manual/Profiler.html) (dokumentacja Unity).|

## <a name="release-management"></a>Release Management
 Opis łącza:  **[Automatyzacja wdrażania przy użyciu zarządzania zleceniami](https://msdn.microsoft.com/library/vs/alm/release/overview)**

|Funkcja|Obsługiwane z Unity|Dodatkowe uwagi|
|-------------|--------------------------|-------------------------|
|Zarządzanie procesami zlecenia|Tak||
|Wdrażanie serwerów w celu ładowania bezpośredniego za pomocą skryptów|Tak||
|Przekaż do sklepu z aplikacjami|Częściowe|Rozszerzenia są dostępne który można zautomatyzować ten proces niektóre sklepy z aplikacjami.  Zobacz [rozszerzeń dla programu Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), na przykład [rozszerzenia do witryny Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorowanie za pomocą aplikacji HockeyApp
 Opis łącza:  **[monitora z HockeyApp](https://www.hockeyapp.net/features/)**

|Funkcja|Obsługiwane z Unity|Dodatkowe uwagi|
|-------------|--------------------------|-------------------------|
|Awarii dystrybucji analizy i telemetrię oraz w wersji beta|Tak|HockeyApp jest szczególnie przydatne w przypadku obsługi rozkład beta i uzyskiwanie raportów o awarii.<br /><br /> Dla danych telemetrycznych z skrypty języka C# prawdopodobnie pod warunkiem, że jest uruchamiany na wersji platformy .NET, który jest używany przez Unity za pomocą dowolnej architektury analytics. Jednak dzięki temu analytics tylko w obrębie gier skryptów, a nie głębsze wewnątrz aparat Unity. Obecnie nie jest brak wtyczki dla usługi Application Insights, ale wtyczek są dostępne dla innych rozwiązań analitycznych przykład [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) i [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Usługi, takie jak Analytics Unity, które rozumieją rodzaj projektu Unity będzie, podaj bardziej zrozumiały analizy niż ogólny struktury.|
