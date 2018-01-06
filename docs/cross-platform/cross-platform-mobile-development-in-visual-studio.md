---
title: "Obsługujący wiele Platform Mobile Development w Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/06/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: "64"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e12acc12559b4295958906fd182c381933bb5d45
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Obsługujący wiele Platform Mobile Development w Visual Studio
Można tworzyć aplikacje dla urządzeń z systemem Android, iOS i Windows za pomocą programu Visual Studio.  Podczas projektowania aplikacji, użyj narzędzia w programie Visual Studio ułatwia dodawanie podłączonych usług takich jak Office 365, Azure App Service i usługi Application Insights.

 Tworzenie aplikacji przy użyciu języka C# i .NET Framework, HTML i JavaScript lub C++. Udostępnianie kodu, ciągi, obrazy, a w niektórych przypadkach nawet interfejsu użytkownika.

 Jeśli chcesz utworzyć graficzny aplikacji gry lub bez ramek, instalowanie narzędzi Visual Studio tools for Unity i korzysta z pełni najnowsze funkcje programu Visual Studio z Unity, popularnych i platform gry grafiki środowiska aparatu i rozwoju aplikacji który Uruchom w systemach iOS, Android, Windows i innych platform.

 **W tym artykule:**

-   [Tworzenie aplikacji dla systemu Android, iOS i Windows (.NET Framework)](#NET)

    -   [Z jednej bazy kodu docelową systemu Android, iOS i Windows](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

    -   [Docelowych urządzeń z systemem Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

-   [Tworzenie aplikacji dla systemu Android, iOS i Windows (HTML/JavaScript)](#HTML)

-   [Tworzenie aplikacji dla systemu Android i Windows (C++)](#CPP)

-   [Tworzenie gier i platform dla systemu Android, iOS i Windows za pomocą narzędzi Visual Studio tools for Unity](#Unity)

##  <a name="NET"></a>Tworzenie aplikacji dla systemu Android, iOS i Windows (.NET Framework)
 ![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

 Za pomocą platformy Xamarin można kierować systemu Android, iOS i Windows w tym samym rozwiązaniu, udostępnianie kodu i nawet interfejsu użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Więcej informacji na temat platformy Xamarin w programie Visual Studio](http://www.visualstudio.com/explore/xamarin-vs) (VisualStudio.com)|
|[Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md) (Biblioteka MSDN)|
|[Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (Biblioteka MSDN)|
|[Więcej informacji na temat uniwersalnych aplikacji systemu Windows w programie Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Dowiedz się więcej o podobieństwa między Swift i C#](http://aka.ms/scposter) (witrynie download.microsoft.com)|
|[Dowiedz się więcej o programie Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

###  <a name="AndroidHTML"></a>Z jednej bazy kodu docelową systemu Android, iOS i Windows
 Można tworzyć natywne aplikacje dla systemu Android, iOS i Windows za pomocą języka C# lub języka F # (Visual Basic nie jest obsługiwana w tej chwili).  Aby rozpocząć, zainstaluj program Visual Studio 2015, wybierz **niestandardowy** opcji w Instalatorze, a następnie zaznacz pole w obszarze **Cross Platform Mobile Development > C# / .NET (Xamarin)**. Można też uruchomić z [Instalator Xamarin](https://www.xamarin.com/download), który jest wymagany do zainstalowania programu Xamarin dla Visual Studio 2013.

 Jeśli masz już zainstalowany program Visual Studio 2015, uruchom Instalatora z **Panel sterowania > programy i funkcje** i wybierz taki sam **niestandardowy** opcji xamarin jak powyżej.

 Gdy wszystko będzie gotowe, szablony projektu są wyświetlane w **nowy projekt** okno dialogowe. Najprostszym sposobem Xamarin szablonów jest po prostu wyszukaj "Xamarin."

 Xamarin dostęp do natywnych funkcji systemu Android, iOS i Windows jako obiekty .NET. W związku z tym aplikacje mają pełny dostęp do natywnych interfejsów API i formantów macierzysty użytkownika, i są one tylko jako reakcji jako aplikacji napisanych w języku macierzystym platformy.

 Po utworzeniu projektu będzie wykorzystać wszystkie funkcje produktywności programu Visual Studio. Na przykład zostanie tworzenie stron za pomocą projektanta i użyj IntelliSense do eksplorowania natywnych interfejsów API platform przenośnych. Gdy wszystko jest gotowe do uruchamiania aplikacji i zobacz, jak wygląda, możesz użyć emulatora programu Visual Studio dla systemu Android lub w emulatorze systemu Android SDK, działania aplikacji systemu Windows lub uruchamianie aplikacji systemu Windows na emulatorze Windows Phone. Powiązane urządzeń z systemami Android i Windows można również korzystać bezpośrednio. Dla projektów dla systemu iOS nawiązać połączenie sieciowe Mac i uruchom Mac emulator w programie Visual Studio lub Połącz z urządzenia powiązanego.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projekt jeden zestaw stron, które renderują dla wszystkich urządzeń za pomocą platformy Xamarin.Forms
 W zależności od złożoności projektu aplikacji, należy rozważyć skompilowanie go za pomocą *platformy Xamarin.Forms* szablonów w **Mobile Apps** grupy szablonów projektu. Platformy Xamarin.Forms jest zestaw narzędzi interfejsu użytkownika, które pozwala utworzyć jeden interfejs, który można udostępniać między Android, iOS i Windows.  Podczas kompilowania rozwiązania platformy Xamarin.Forms uzyskasz aplikacji systemu Android, aplikację systemu iOS i aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

####  <a name="ShareHTML"></a>Współużytkowanie kodu dla systemu Android, iOS i aplikacji systemu Windows
 Jeśli nie używasz platformy Xamarin.Forms i projektować osobno dla każdej platformy można udostępniać większość kodu bez interfejsu użytkownika między projektami platform (Android, iOS i Windows). W tym wszelka logika biznesowa, integracja chmury, dostęp do bazy danych lub inny kod, przeznaczonego dla programu .NET Framework. Nie można udostępniać tylko kod jest kodu przeznaczonego dla określonej platformy.

 ![Współużytkowanie kodu systemu Windows, iOs i Android interfejsu użytkownika](../cross-platform/media/sharecode.png "ShareCode")

 Możesz udostępniać kodu za pomocą udostępnionego projektu i projektu biblioteki klas przenośnych. Może się okazać, że niektóre kodu mieści się przez więcej najlepiej w projekcie udostępnionym i kodu znaczeniu wewnątrz projektu biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|Wybierz opcję Udostępnianie kodu przy użyciu udostępnionych projektów i/lub projektów przenośnej biblioteki klas.<br /><br /> [Udostępnianie kodu na platformach](http://blogs.msdn.com/b/dotnet/archive/2014/04/21/sharing-code-across-platforms.aspx) (blog .NET Framework)<br /><br /> [Udostępnianie kodu opcje](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (Xamarin)<br /><br /> [Kod opcje udostępniania w środowisku .NET Framework](http://msdn.microsoft.com/library/dn720832.aspx) (Biblioteka MSDN)|

###  <a name="WindowsHTML"></a>Docelowych urządzeń z systemem Windows 10
 ![Urządzenia z systemem Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Jeśli chcesz utworzyć tylko jednej aplikacji, którego celem jest rozmaitych urządzeń z systemem Windows 10, należy utworzyć uniwersalną aplikację systemu Windows. Będzie projektowania aplikacji przy użyciu jednego projektu i będą wyświetlane prawidłowo niezależnie od tego, jakiego urządzenia można je wyświetlić.

 Uruchom z szablonem projektu aplikacji uniwersalnej systemu Windows. Wizualnego projektowania stron, a następnie otwórz je w oknie Podgląd, aby sprawdzić, jak są wyświetlane dla różnych typów urządzeń. Jeśli nie lubisz, jak zostanie wyświetlona strona na urządzeniu, aby zoptymalizować strony w celu lepszego dopasowania rozmiaru ekranu, rozwiązania lub różnych orientacji, takim jak tryb pozioma lub pionowa. Można wykonywać wszystkie na tym, za pomocą menu łatwo dostępne opcje i intuicyjne narzędzia systemu windows w programie Visual Studio. Gdy wszystko jest gotowe do uruchamiania aplikacji i krok za pomocą kodu, można znaleźć wszystkie urządzenia emulatorów i symulatorów dla różnych typów urządzeń razem na jednej liście rozwijanej, który znajduje się na **standardowe** paska narzędzi.

 Windows 10 jest stosunkowo nowe, więc tam również szablony projektów przeznaczonych Windows 8.1. Za pomocą tych szablonów projektu i aplikacja zostanie uruchomiona na telefony, tablety i komputery z systemem Windows 10. Jednak wszystkie urządzenia z systemem Windows 8.1 będą otrzymywać automatyczne uaktualnienia do systemu Windows 10, więc w przypadku braku określonych przyczyn, dlaczego czy raczej target Windows 8.1, firma Microsoft zaleca użycie szablony projektów, które odnoszą się do systemu Windows 10.

|**Dowiedz się więcej**|
|--------------------|
|[Więcej informacji na temat uniwersalnych aplikacji systemu Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Centrum deweloperów systemu Windows)|
|[Tworzenie pierwsza](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Centrum deweloperów systemu Windows)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrowanie aplikacji platformy uniwersalnej systemu Windows (UWP)](https://msdn.microsoft.com/en-us/library/mt148501.aspx)|

##  <a name="HTML"></a>Tworzenie aplikacji dla systemu Android, iOS i Windows (HTML/JavaScript)
 ![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

 Jeśli jesteś deweloperem sieci web i znasz kodu HTML i JavaScript, można kierować systemu Windows, Android i iOS za pomocą narzędzi Visual Studio Tools for Apache Cordova. Te aplikacje można wskazać wszystkie trzy platformy i można je utworzyć za pomocą umiejętności i procesy, które znasz najbardziej.

 Apache Cordova to platforma, która zawiera model dodatku plug-in. Ten model wtyczek udostępnia jeden interfejs API JavaScript, która umożliwia dostęp do możliwości urządzenie z natywnym wszystkich trzech platform (Android, iOS i Windows).

 Ponieważ te interfejsy API są międzyplatformowa, można udostępniać większość zapisu między wszystkich trzech platform. Pozwala to ograniczyć koszty rozwoju i konserwacji. Ponadto jest niepotrzebna od samego początku. Jeśli po utworzeniu innych typów aplikacji sieci web, można udostępniać te pliki aplikacji platformy Cordova bez konieczności modyfikowania lub zmodyfikowanie je w dowolny sposób.

 ![Obsługa wielu &#45; aplikacje hybrydowe dla urządzeń](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Aby rozpocząć, zainstalować program Visual Studio 2015 i wybrać **HTML/JavaScript (Apache Cordova)** funkcji podczas instalacji. Jeśli używasz programu Visual Studio 2013, należy zainstalować Visual Studio Tools for Apache Cordova rozszerzenia. W obu przypadkach narzędzia Cordova automatycznie zainstalować wszystkie oprogramowania innych firm, które są wymagane do utworzenia aplikacji w wielu platform.

 Po zainstalowaniu rozszerzenia, Otwórz program Visual Studio i utworzyć **pusta aplikacja (Apache Cordova)** projektu. Następnie możesz utworzyć aplikację przy użyciu języka JavaScript i Typescript. Możesz także dodać wtyczki, aby rozszerzyć funkcjonalność aplikacji i interfejsów API z dodatków plug-in są wyświetlane w IntelliSense podczas pisania kodu.

 Gdy wszystko jest gotowe do uruchamiania aplikacji i krok za pomocą kodu, należy wybrać emulator, takich jak emulatorze Apache Ripple lub Visual Studio Emulator (Android i Windows Phone), przeglądarki lub urządzeń, które zostały podłączone bezpośrednio do komputera. Następnie uruchom aplikację. Jeśli projektujesz aplikacji na komputerach z systemem Windows, możesz nawet uruchamiać go na tym. Wszystkie te opcje są wbudowane w program Visual Studio jako część programu Visual Studio Tools for Apache Cordova.

 Szablony projektu dla tworzenia uniwersalnych aplikacji systemu Windows są nadal dostępne w programie Visual Studio tak najbliższym z nich korzystać, jeśli planujesz pod kątem tylko urządzeń z systemem Windows. Jeśli zechcesz później target Android i iOS, należy zawsze portu swój kod projektu oprogramowania Cordova. Brak wersji open source WinJS interfejsów API, więc można używać kodu, który korzysta z tych interfejsów API. Inaczej mówiąc, jeśli planujesz innych platform docelowych w przyszłości, zaleca się uruchomić program Visual Studio Tools for Apache Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Wprowadzenie do programu Visual Studio Tools for Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/) (docs.microsoft.com)|
|[Dowiedz się więcej o programie Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

##  <a name="CPP"></a>Tworzenie aplikacji dla systemu Android i Windows (C++)
 ![Użyj & C &43; 43; Aby tworzyć dla systemu Android, iOS i Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw należy zainstalować program Visual Studio 2015 i Visual C++ for Cross Platform Mobile Development tools. Następnie można utworzyć aplikacji działania natywnego dla systemu Android lub aplikacji, która jest przeznaczony dla systemu Windows. Szablonów języka C++, które są przeznaczone dla systemu iOS nie są jeszcze dostępne. Android i Windows można kierować w tym samym rozwiązaniu Jeśli, a następnie udostępnić kod między nimi przy użyciu wielu platform statyczne lub dynamiczne biblioteki współużytkowanej.

 Jeśli potrzebujesz do tworzenia aplikacji dla systemu Android, które wymaga dowolny rodzaj manipulowanie grafiki zaawansowanych, takich jak gier, można użyć C++ aby wykonać to zadanie. Rozpoczynać **aplikacji klasy Nativeactivity (Android)** projektu. Ten projekt zawiera pełną obsługę łańcuch narzędzi Clang.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat_cpp_native.png "Plat_CPP_Native między")

 Gdy wszystko jest gotowe do uruchamiania aplikacji i zobacz, jak wygląda, należy użyć emulatora programu Visual Studio dla systemu Android. Jest szybkie, niezawodne i łatwe do instalowania i konfigurowania.

 Można także utworzyć aplikację, która dotyczy rozmaitych urządzeń z systemem Windows 10 za pomocą języka C++ i szablon projektu uniwersalnej aplikacji systemu Windows. Dowiedz się więcej o tym w [urządzeń docelowych systemu Windows 10](#WindowsHTML) sekcji, która występuje wcześniej w tym temacie.

 Kod w języku C++ między systemami Android i Windows można udostępniać tworząc statyczne lub dynamiczne biblioteki udostępnionej.

 ![Współużytkowanych bibliotekach statycznych i dynamicznych](../cross-platform/media/cross_plat_cpp_libraries.png "Cross_Plat_CPP_Libraries")

 Będzie można korzystać z tej biblioteki w systemie Windows lub projekt systemu Android, jak firma opisana wcześniej w tej sekcji. Można również korzystać go w aplikacji, podczas tworzenia za pomocą platformy Xamarin, Java lub dowolnego języka, który pozwala wywoływać funkcje w niezarządzanej bibliotece DLL.

 Podczas pisania kodu w tych bibliotek, można użyć IntelliSense do eksplorowania macierzystych interfejsów API platformy systemu Android i Windows. Te projekty biblioteki są w pełni zintegrowane z debuger programu Visual Studio, można ustawić punktów przerwania, kroki do kodu i znajdowanie i rozwiązywanie problemów przy użyciu wszystkich zaawansowanych funkcji debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobierz program Visual Studio.](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Zainstaluj Visual C++ for Cross Platform Mobile Development tools.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o języku C++ do wielu platform docelowych.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj co i następnie tworzenie aplikacji natywnych działania dla systemu Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o programie Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|
|[Dowiedz się więcej o udostępnianiu kod w języku C++ aplikacji systemu Android i Windows](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Wiele platform przenośnych przykłady dla języka C++](https://msdn.microsoft.com/library/dn707596.aspx) (Biblioteka MSDN)|
|[Aplikacji mobilnych dla wielu platform dodatkowe przykłady dla języka C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

##  <a name="Unity"></a>Tworzenie gier i platform dla systemu Android, iOS i Windows za pomocą narzędzi Visual Studio tools for Unity
 Visual Studio Tools for Unity jest bezpłatne rozszerzenia dla programu Visual Studio, która integruje się programu Visual Studio edycji kodu zaawansowanych, wydajności i debugowania narzędzi z *Unity*, aparat popularnych i platform gier grafiki i Środowisko deweloperskie do aplikacji bez ramek, które odnoszą się do systemu Windows, iOS, Android i innych platform, w tym sieci web.

 ![Środowisko projektowe pomocą rozszerzenia VSTU](../cross-platform/media/vstu_overview.png "VSTU_Overview")

 Program Visual Studio Tools dla Unity (pomocą rozszerzenia VSTU) programu Visual Studio służy również do zapisu gry i Edytor skryptów w języku C#, a następnie znajdź i napraw błędy za pomocą jego doskonałego debugera. Najnowszą wersję pomocą rozszerzenia VSTU zapewnia obsługę Unity 5 i zawiera kolorowanie składni dla języka programu do cieniowania ShaderLab dla Unity, lepiej synchronizacji z Unity, bardziej zaawansowane funkcje debugowania i generowanie kodu ulepszone kreatora MonoBehavior. Pomocą rozszerzenia VSTU oferuje również plików projektu Unity, komunikaty konsoli i możliwość uruchamiania gry w programie Visual Studio, aby móc poświęcić mniej czasu przełączanie z edytora Unity podczas pisania kodu.

 Gry środowiska Unity i narzędzia Visual Studio Tools for Unity już dziś zacznij tworzyć.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu Unity gry z programem Visual Studio](https://www.visualstudio.com/en-us/features/unitytools-vs.aspx)|
|[Dowiedz się więcej o programie Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (Biblioteka MSDN)|
|[Uruchom przy użyciu programu Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (Biblioteka MSDN)|
|[Przeczytaj o najnowsze ulepszenia do programu Visual Studio Tools dla Unity 2.0 w wersji zapoznawczej](http://blogs.msdn.com/b/visualstudio/archive/2014/12/03/visual-studio-tools-for-unity-2-0-preview.aspx) (blog Visual Studio)|
|[Obejrzyj film wideo zawierający wprowadzenie do programu Visual Studio Tools dla Unity 2.0 w wersji zapoznawczej](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (klip wideo)|
|[Dowiedz się więcej o Unity](http://unity3d.com/) (Unity witryny sieci Web)|

## <a name="see-also"></a>Zobacz też
 - [Dodaj do projektu programu Visual Studio Office 365 API](http://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
 - [Usługi aplikacji Azure — aplikacje mobilne](https://azure.microsoft.com/en-us/services/app-service/mobile/)
 - [HockeyApp dla urządzeń przenośnych](https://azure.microsoft.com/en-us/services/hockeyapp/)