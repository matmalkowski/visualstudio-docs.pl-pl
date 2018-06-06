---
title: Zaawansowane funkcje programu Visual Studio 2017 r.
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e50bd5231387261e56a62234858d10c3806de3dc
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34694115"
---
# <a name="features-of-visual-studio-2017"></a>Funkcje programu Visual Studio 2017 r.

[Omówienie programu Visual Studio IDE](../ide/visual-studio-ide.md) temat zawiera podstawowe wprowadzenie do programu Visual Studio. W tym artykule opisano funkcje, które mogą być bardziej odpowiednie dla doświadczonych programistów lub osoby, które już są zaznajomieni z programem Visual Studio.

## <a name="modular-installation"></a>Moduły instalacji

Moduły Instalator Visual Studio umożliwia wybierz i zainstaluj *obciążeń*, które są grup funkcji potrzebnych do programowania języka lub platformy wolisz. Ta strategia pomaga zachować rozmiaru instalacji programu Visual Studio mniejsze, co oznacza instalowany i uaktualni szybciej.

Jeśli nie została jeszcze zainstalowana Visual Studio 2017, przejdź do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

Aby dowiedzieć się więcej o konfigurowaniu programu Visual Studio w systemie, zobacz [zainstalować program Visual Studio 2017](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Tworzenie aplikacji z włączoną obsługą chmury platformy Azure

Program Visual Studio oferuje zestaw narzędzi, które umożliwiają łatwe tworzenie aplikacji z obsługą chmury obsługiwane przez usługę Microsoft Azure. Można skonfigurować, tworzenia, debugowania pakietu i wdrożyć aplikacje i usługi Microsoft Azure bezpośrednio z IDE. Aby uzyskać narzędzia Azure i szablony projektów, wybierz **Azure programowanie** obciążenia podczas instalowania programu Visual Studio.

![Programowanie Azure obciążenia](../data-tools/media/azure-development-workload.png)

Po zainstalowaniu **Azure programowanie** obciążenie, następujące **chmury** szablonów dla języka C# są dostępne w **nowy projekt** okna dialogowego:

![Szablony projektów chmury dla programu Visual Studio](media/cloud-project-templates.png)

Visual Studio [Eksplorator chmury](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) umożliwia wyświetlanie i zarządzanie zasobami w chmurze bazujących na platformie Azure w programie Visual Studio. Te zasoby mogą obejmować maszyn wirtualnych, tabel, baz danych i inne. **Cloud Explorer** pokazuje zasobów platformy Azure w ramach kont zarządzanych w ramach subskrypcji platformy Azure jest zalogowany. A jeśli określonej operacji są wymagane w portalu Azure **Eksplorator chmury** linki prowadzące do miejsca w portalu, gdzie musisz przejść.

![Eksplorator chmury w programie Visual Studio](media/cloud-explorer.png)

Wykorzystanie usług platformy Azure dla aplikacji za pomocą **usług połączonych** takich jak:

- [Usługi Active Directory połączona usługa](/azure/active-directory/develop/vs-active-directory-add-connected-service) , użytkownicy mogą używać swoich kont z [usługi Azure Active Directory](/azure/active-directory/active-directory-whatis) do nawiązania połączenia aplikacji sieci web
- [Usługa Azure Storage połączone usługi](/azure/vs-azure-tools-connected-services-storage) magazynu obiektów blob, kolejek i tabel
- [Magazyn kluczy połączona usługa](/azure/key-vault/vs-key-vault-add-connected-service) do zarządzania klucze tajne dla aplikacji sieci web

Dostępne **usług połączonych** są zależne od typu projektu. Dodaj usługę, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj** > **podłączonej usługi**.

![Visual Studio połączone usługi](media/connected-services.png)

Aby uzyskać więcej informacji, zobacz [przenosić do chmury z programu Visual Studio i Azure](https://www.visualstudio.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Tworzenie aplikacji dla sieci web

Nasze współczesnym świecie dyski sieci web i Visual Studio ułatwia pisanie aplikacji dla niego. Można utworzyć aplikacji sieci web ASP.NET, Node.js, Python, JavaScript i TypeScript. Visual Studio rozumie struktur sieci web, takich jak kątową, jQuery, Express i inne. Oprogramowanie .NET Core i ASP.NET Core uruchomienia w systemach operacyjnych Windows, Mac i Linux. [Platformy ASP.NET Core](http://www.asp.net/core/overview) jest dużej aktualizacji MVC, WebAPI i SignalR i działa w systemie Windows, Mac i Linux.  Platformy ASP.NET Core ma został zaprojektowany od podstaw zapewnienie, że program .NET gotowa i zezwala na składanie stosu do tworzenia aplikacji sieci web opartych na chmurze nowoczesnych i usług.

Aby uzyskać więcej informacji, zobacz [nowoczesnych witryn sieci web narzędzia](https://www.visualstudio.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Tworzenie wieloplatformowych aplikacji i gier

Można użyć programu Visual Studio do tworzenia aplikacji i gier dla macOS, Linux i Windows, a także dla systemu Android, iOS oraz inne [urządzeń przenośnych](https://www.visualstudio.com/vs/mobile-app-development/).

- Tworzenie [.NET Core](/dotnet/core/) aplikacji uruchamianych w systemie Windows, system macOS i Linux.

- Tworzenie aplikacji mobilnych dla systemu iOS, Android i Windows w języku C# i F # za pomocą [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Użyj technologii sieci web standard&mdash;HTML, CSS i JavaScript&mdash;do tworzenia aplikacji mobilnych dla systemu iOS, Android i Windows za pomocą [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/).

- Tworzenie gier 2W i 3W w języku C# za pomocą [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md).

- Aplikacje natywne C++ kompilacji dla systemów iOS, Android i Windows i udziału typowy kod w bibliotekach skompilowany dla systemu iOS, Android i Windows, przy użyciu [C++ dla aplikacji dla wielu platform](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md).

- Wdrażanie, testowanie i debugowanie aplikacji systemu Android z [emulatora systemu Android](../cross-platform/visual-studio-emulator-for-android.md).

## <a name="connect-to-databases"></a>Połączenie z bazami danych

**W Eksploratorze serwera** ułatwia przeglądanie i zarządzanie wystąpień programu SQL Server i zasobami lokalnie, zdalnie i na witryny Salesforce.com, Office 365, Azure i witryn sieci Web. Aby otworzyć **Eksploratora serwera**, w menu głównym wybierz **widoku** > **Eksploratora serwera**. Zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md) Aby uzyskać więcej informacji na temat używania Eksploratora serwera.

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) jest wydajne środowisko projektowe dla programu SQL Server, bazy danych SQL Azure i usługi Azure SQL Data Warehouse. Umożliwia tworzenie, debugowanie, obsługa i Refaktoryzuj baz danych. Możesz pracować z projektem bazy danych lub bezpośrednio z bazy danych połączonych wystąpienia na — lub poza siedzibą firmy.

**Eksplorator obiektów SQL Server** w programie Visual Studio udostępnia widok obiektów bazy danych podobny do programu SQL Server Management Studio. Eksplorator obiektów SQL Server można wykonywać zadania zarządzania i projektowania lekkich bazy danych, takich jak edytowanie danych w tabeli, porównanie schematów, wykonywanie zapytań przy użyciu menu kontekstowe bezpośrednio w Eksploratorze obiektów SQL Server i inne.

![Eksplorator obiektów SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Debugowanie, testowanie i poprawić kod

Podczas pisania kodu, należy ją uruchomić i przetestować go do błędów i wydajności. Najnowocześniejsze systemu debugowania Visual Studio umożliwia debugowania kodu uruchamianego w środowisku lokalnym projektu, na urządzeniu zdalnym lub na [urządzenia emulatora](../cross-platform/visual-studio-emulator-for-android.md). Możesz kroków opisanych w jedną instrukcję kodu w czasie i sprawdzić zmiennych w trakcie pracy. Można ustawić punktów przerwania, które są osiągane tylko, gdy określony warunek jest spełniony. Wszystkie te można zarządzać w edytorze kodu, dzięki czemu nie trzeba pozostaw kodu. Aby uzyskać więcej informacji na temat debugowania w programie Visual Studio, zobacz [debugera samouczek funkcji](../debugger/debugger-feature-tour.md).

Aby dowiedzieć się więcej na temat zwiększania wydajności aplikacji, wyewidencjonowania limit Visual Studio [profilowania](../profiling/profiling-feature-tour.md) funkcji.

Aby uzyskać [testowania](../test/improve-code-quality.md), program Visual Studio oferuje testy jednostkowe, Live testów jednostkowych IntelliTest, obciążenia i testowanie wydajności i więcej. Visual Studio również udostępnia zaawansowane [analiza kodu](../code-quality/code-analysis-for-managed-code-overview.md) możliwości catch projektowania, zabezpieczeń i inne typy błędów.

## <a name="deploy-your-finished-application"></a>Wdrażanie aplikacji Zakończono

Gdy aplikacja jest gotowa do wdrożenia użytkownicy lub klienci, Visual Studio zawiera narzędzia w tym, czy w witrynie programu SharePoint lub technologii InstallShield lub Instalator Windows jest wdrażany Microsoft Store. Jest on wszystkie dostępne za pośrednictwem IDE. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Zarządzanie kodu źródłowego i współpracę z innymi osobami

Możesz zarządzać kodu źródłowego w obsługiwanych przez dowolnego dostawcy, w tym GitHub repozytoriów Git. Lub użyj [programu Visual Studio Team Services (VSTS)](/vsts/index) do zarządzania kodu obok usterek i elementy pracy dla całego projektu. Zobacz [wprowadzenie do usługi Git i zespołu usług (VSTS)](/vsts/git/gitquickstart?tabs=visual-studio) Aby dowiedzieć się więcej o zarządzaniu repozytoriów Git w programie Visual Studio przy użyciu programu Team Explorer. Visual Studio ma również inne funkcje kontroli źródła wbudowanych. Aby dowiedzieć się więcej o nich, zobacz [Git nowych funkcji w programie Visual Studio 2017 (blog)](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/).

Visual Studio Team Services to usługa oparta na chmurze dla hostingu oprogramowania projektów i umożliwianie współpracy w zespołach. VSTS obsługuje systemów zarówno Git i kontroli źródła programu Team Foundation, a także Scrum, CMMI i Agile metodologii programowanie. Team Foundation wersji formantu (TFVC) używa pojedynczy serwer scentralizowane repozytorium do śledzenia i wersji plików. Lokalne zmiany są zawsze ewidencjonowane na centralnym serwerze, gdy inni deweloperzy mogą pobrać najnowsze zmiany.

Team Foundation Server (TFS) jest Centrum zarządzania cyklem życia aplikacji dla programu Visual Studio. Dzięki temu wszyscy pracownicy z procesem tworzenia do udziału za pomocą jednego rozwiązania. TFS jest przydatne w przypadku za zarządzanie heterogenicznym zespołów i projektów.

Jeśli masz konto usługi Visual Studio Team Services lub Team Foundation Server w sieci, należy się z nim połączyć za pośrednictwem **Team Explorer** okna w programie Visual Studio. Z tego okna można sprawdzić kod do lub z kontroli źródła, zarządzania elementami pracy, kompilacji i rozpoczęcia pokoje zespołów dostępu oraz obszarów roboczych. Możesz otworzyć **Team Explorer** z **Szybkie uruchamianie** okno, lub w menu głównym z **widoku** > **Team Explorer** lub **Zespołu** > **Zarządzanie połączeniami**.

Poniższy obraz przedstawia **Team Explorer** okna dla rozwiązania, które znajduje się w VSTS.

![Program Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer.png)

Można również zautomatyzować procesu kompilacji do kompilacji kodu, który zaznaczono devs Twojego zespołu w kontroli wersji. Można na przykład skompilować jeden lub więcej projektów w nocy lub za każdym razem, kiedy kod jest zaewidencjonowany. Aby uzyskać więcej informacji, zobacz [kompilacji i wydania (VSTS i TFS)](/vsts/build-release/index).

## <a name="extend-visual-studio"></a>Rozszerzanie funkcjonalności programu Visual Studio

Visual Studio nie ma dokładnie funkcji potrzebne, można dodać go! Można personalizowanie środowiska IDE są oparte na przepływie pracy i stylu, Dodaj obsługę dla zewnętrznych narzędzi nie została jeszcze zintegrowany z programem Visual Studio i modyfikować istniejące funkcje, aby zwiększyć wydajność. Aby uzyskać najnowszą wersję programu Visual Studio Tools rozszerzalności (VS SDK), zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Kompilator platformy .NET ("Roslyn") służy do pisania własnych analizatorów kodu i generatory kodu. Znajdź wszystkie elementy potrzebne w [Roslyn](https://github.com/dotnet/Roslyn).

Znajdź [istniejące rozszerzenia](https://marketplace.visualstudio.com/vs) dla programu Visual Studio utworzone przez deweloperzy firmy Microsoft, a także naszą społeczność programowanie.

Aby dowiedzieć się więcej na temat rozszerzania programu Visual Studio, zobacz [rozszerzenia programu Visual Studio IDE](https://www.visualstudio.com/vs/extend/).

## <a name="see-also"></a>Zobacz także

- [Visual Studio IDE — omówienie](../ide/visual-studio-ide.md)
- [Co to jest nowa w programie Visual Studio 2017 r.](../ide/whats-new-in-visual-studio.md)