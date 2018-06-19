---
title: Visual Studio for Mac samouczka
description: Program Visual Studio for Mac udostępnia zintegrowane środowisko programistyczne do tworzenia aplikacji .NET na macOS, łącznie z witryn sieci Web platformy ASP.NET Core i projektów platformy Xamarin dla systemu iOS, Android, Mac i platformy Xamarin.Forms.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.openlocfilehash: 024e58c1c217652c489ad9fe9e568cd21f687ae8
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34453992"
---
# <a name="visual-studio-for-mac-tour"></a>Visual Studio for Mac samouczka

Visual Studio for Mac rozwoju środowisko IDE skoncentrowane na telefon komórkowy w Xamarin, Xamarin Studio do pierwszej mobile, najpierw chmury środowisko programistyczne opartym na To narzędzie fokus developer umożliwia przy użyciu możliwości programu .NET do tworzenia aplikacji dla wszystkich platform wymagane przez użytkowników.

Środowisko użytkownika (UX) programu Visual Studio for Mac jest podobny do jego odpowiednika systemu Windows, ale o działaniu macOS macierzystego. Tworzenia, otwierania i tworzenia aplikacji będzie znane rozwiązanie dla każdego, kto ma korzystał już z programu Visual Studio w systemie Windows. Ponadto programu Visual Studio for Mac wykorzystuje wiele zaawansowane narzędzia, które umożliwiają jego odpowiednik Windows zaawansowanych IDE. Platforma kompilatora Roslyn jest używana do refaktoryzacji i IntelliSense. Użyj programu MSBuild, silnik systemu i kompilacji projektu i jego Edytor źródła obsługuje TextMate pakietów. Używa tego samego aparaty debuger dla aplikacji platformy Xamarin i .NET Core i tego samego projektantów dla platformy Xamarin.iOS i platformy Xamarin.Android.

Ten artykuł opisuje różne sekcje programu Visual Studio dla komputerów Mac, podając informacje o niektórych funkcji, które ułatwiają zaawansowane narzędzie do tworzenia aplikacji dla wielu platform.

## <a name="ide-tour"></a>Samouczek środowiska IDE

Visual Studio for Mac są zorganizowane w wielu sekcjach dla aplikacji pliki i ustawienia tworzenia kodu aplikacji i zarządzanie debugowania.

## <a name="welcome-screen"></a>Ekran powitalny

Podczas uruchomienia, Visual Studio for Mac Wyświetla *ekran powitalny*:

![Ekran powitalny](media/ide-tour-image1.png)

Ekran powitalny zawiera następujące sekcje:

- **Pasek narzędzi** — zapewnia szybki dostęp do pasek wyszukiwania. Po załadowaniu rozwiązania pasek narzędzi służy do konfiguracji aplikacji, debugowanie i wyświetlanie błędów.
- **Wprowadzenie** — zapewnia szybki dostęp do przydatnych tematów dla deweloperów rozpoczynających pracę z programem Visual Studio dla komputerów Mac.
- **Ostatnie rozwiązania** — zapewnia szybki dostęp do ostatnio otwartą rozwiązania, a także wygodny przycisków, aby otworzyć lub utworzyć projektów.
- **Wiadomości dla programistów** -kanału informacyjnego który powiadamia Cię o najnowsze informacje o Microsoft Developer.

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Na poniższej ilustracji przedstawiono Visual Studio dla komputerów Mac przy użyciu aplikacji załadowane:

![Załadowano programu Visual Studio for Mac za pomocą aplikacji](media/ide-tour-image17.png)

Poniższe sekcje zawierają omówienie głównych obszarów w programie Visual Studio dla komputerów Mac.

## <a name="solution-pad"></a>Konsola rozwiązania

Konsola rozwiązania organizuje projekty w rozwiązaniu:

![Projekty zorganizowane w konsoli rozwiązania](media/ide-tour-image18.png)

Jest to, gdzie pliki kodu źródłowego, zasobów, interfejs użytkownika i zależności są zorganizowane w projektach specyficzne dla platformy.

Aby uzyskać więcej informacji na temat używania projektów i rozwiązań w programie Visual Studio dla komputerów Mac, zobacz [projekty i rozwiązania](projects-and-solutions.md) artykułu.

## <a name="assembly-references"></a>Odwołania do zestawów
 
Odwołania do zestawów dla każdego projektu są dostępne w folderze odwołania:

![Odwołania do folderu w konsoli rozwiązania](media/ide-tour-image19.png)

Dodatkowe informacje są dodawane przy użyciu **edytować odwołania** okna dialogowego, która jest wyświetlana, klikając dwukrotnie plik do folderu odwołań lub wybierając **edytować odwołania** na swoich działań menu kontekstowe:
 
![Edytowanie okna dialogowego odwołania](media/ide-tour-image20.png)

Aby uzyskać więcej informacji na temat używania odwołań w programie Visual Studio dla komputerów Mac, zobacz [Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md) artykułu.

## <a name="dependencies--packages"></a>Zależności / pakietów

Wszystkie zależności zewnętrzne używane w aplikacji są przechowywane w folderze zależności lub pakietów, w zależności od tego, czy są w .net Core lub Xamarin.iOS/Xamarin.Android projektu. Te zwykle są zawarte w formie NuGet.

NuGet jest najbardziej popularnych Menedżer pakietów dla rozwoju platformy .NET. Z obsługą NuGet programu Visual Studio można łatwo wyszukiwać i dodawanie pakietów do projektu do aplikacji.

Aby dodać zależności do aplikacji, kliknij prawym przyciskiem myszy zależności / pakietów folder, a następnie wybierz **Dodawanie pakietów**:

![Dodaj pakiet NuGet](media/ide-tour-image21.png)

Informacje o użyciu pakietu NuGet w aplikacji można znaleźć w [projektu w tym NuGet w projekcie](nuget-walkthrough.md) artykułu.

## <a name="refactoring"></a>Refaktoryzacja

Visual Studio for Mac udostępnia dwa sposoby przydatne do Refaktoryzuj kodu: kontekstu akcji i analizy źródła. Więcej o nich w [Refactoring](refactoring.md) artykułu.

## <a name="debugging"></a>Debugowanie

Visual Studio for Mac ma debuger natywny umożliwiająca obsługę debugowania dla aplikacji platformy Xamarin.iOS Xamarin.Mac i platformy Xamarin.Android. Visual Studio for Mac używa Mono nietrwałego debugera, implementowana w czasie wykonywania Mono, umożliwiając IDE do debugowania kodu zarządzanego na wszystkich platformach. Aby uzyskać dodatkowe informacje na temat debugowania, odwiedź stronę [debugowanie](debugging.md) artykułu.

Debuger zawiera bogaty wizualizatorów dla typów specjalnych, takich jak ciągów, kolory, adresy URL, a także rozmiary, współrzędne i krzywych Beziera.

Aby uzyskać więcej informacji na wizualizacje danych debugera, odwiedź stronę [wizualizacje danych](data-visualizations.md) artykułu.

## <a name="version-control"></a>Kontrola wersji

Visual Studio for Mac integruje się z usługi Git i Podwersją systemów kontroli źródła. Projekty pod kontrolą źródła są oznaczone symbolem gałęzi wyświetlane obok nazwy rozwiązań: 

![Nazwa gałęzi, aby wskazać projektu pod kontrolą źródła](media/ide-tour-image22.png)

Zmienione pliki z niezatwierdzone ma adnotację na ich ikony w okienku rozwiązania, jak pokazano na poniższej ilustracji:

![Niezatwierdzone pliki w konsoli rozwiązania](media/ide-tour-image23.png)

Aby uzyskać więcej informacji na temat używania kontroli wersji w programie Visual Studio, zobacz [kontroli wersji](version-control.md) artykułu.