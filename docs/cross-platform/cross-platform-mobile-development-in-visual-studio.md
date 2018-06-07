---
title: Obsługujący wiele Platform Mobile Development w Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/24/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: asb3993
ms.author: amburns
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: 26edc3f48c72fb81bd60396ad8a3047dafa7f48e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572381"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Aplikacji mobilnych dla wielu Platform w programie Visual Studio

Można tworzyć aplikacje dla urządzeń z systemem Android, iOS i Windows za pomocą programu Visual Studio.  Podczas projektowania aplikacji, użyj narzędzia w programie Visual Studio ułatwia dodawanie podłączonych usług takich jak Office 365, Azure App Service i usługi Application Insights.

Tworzenie aplikacji przy użyciu języka C# i .NET Framework, HTML i JavaScript lub C++. Udostępnianie kodu, ciągi, obrazy, a w niektórych przypadkach nawet interfejsu użytkownika.

Jeśli chcesz utworzyć graficzny aplikacji gry lub bez ramek, instalowanie narzędzi Visual Studio tools for Unity i korzysta z pełni najnowsze funkcje programu Visual Studio z Unity, popularnych i platform gry grafiki środowiska aparatu i rozwoju aplikacji który Uruchom w systemach iOS, Android, Windows i innych platform.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Tworzenie aplikacji dla systemu Android, iOS i Windows (.NET Framework)

![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

Program Visual Studio Tools dla platformy Xamarin można kierować systemu Android, iOS i Windows w tym samym rozwiązaniu, udostępnianie kodu i nawet interfejsu użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Więcej informacji na temat platformy Xamarin w programie Visual Studio](http://www.visualstudio.com/explore/xamarin-vs) (VisualStudio.com)|
|[Dokumentacji dla deweloperów aplikacji mobilnych Xamarin](/xamarin/) |
|[Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) |
|[Więcej informacji na temat aplikacji uniwersalnych systemu Windows w programie Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Dowiedz się więcej o podobieństwa między Swift i C#](http://aka.ms/scposter) (witrynie download.microsoft.com)|

###  <a name="AndroidHTML"></a> Z jednej bazy kodu docelową systemu Android, iOS i Windows

 Można tworzyć natywne aplikacje dla systemu Android, iOS i Windows za pomocą języka C# lub języka F # (Visual Basic nie jest obsługiwana w tej chwili).  Aby rozpocząć, zainstaluj program Visual Studio 2017, wybierz **programowania aplikacji mobilnych z platformą .NET** opcji w Instalatorze.

 Jeśli masz już Visual Studio 2017 r zainstalowane, uruchom ponownie **Instalator programu Visual Studio** i wybierz taki sam **programowania aplikacji mobilnych z platformą .NET** opcji xamarin (jak powyżej).

 Gdy wszystko będzie gotowe, szablony projektu są wyświetlane w **nowy projekt** okno dialogowe. Najprostszym sposobem Xamarin szablonów jest po prostu wyszukaj "Xamarin."

 Xamarin dostęp do natywnych funkcji systemu Android, iOS i Windows jako .NET klasy i metody. Oznacza to, aplikacje mają pełny dostęp do natywnych interfejsów API i kontrolki natywne i są one tylko jako reakcji jako aplikacji napisanych w języku macierzystym platformy.

 Po utworzeniu projektu będzie wykorzystać wszystkie funkcje produktywności programu Visual Studio. Na przykład zostanie tworzenie stron za pomocą projektanta i użyj IntelliSense do eksplorowania natywnych interfejsów API platform przenośnych. Gdy wszystko jest gotowe do uruchamiania aplikacji i zobacz, jak wygląda, możesz użyć emulatora Android SDK i działania aplikacji systemu Windows. Powiązane urządzeń z systemami Android i Windows można również korzystać bezpośrednio. Dla projektów dla systemu iOS nawiązać połączenie sieciowe Mac i uruchom emulator systemu iOS w programie Visual Studio lub Połącz z urządzenia powiązanego.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projekt jeden zestaw stron, które renderują dla wszystkich urządzeń za pomocą platformy Xamarin.Forms

 W zależności od złożoności projektu aplikacji, należy rozważyć skompilowanie go za pomocą *platformy Xamarin.Forms* szablonów w **Mobile Apps** grupy szablonów projektu. Platformy Xamarin.Forms jest zestaw narzędzi interfejsu użytkownika, które pozwala utworzyć jeden interfejs, który można udostępniać między Android, iOS i Windows.  Podczas kompilowania rozwiązania platformy Xamarin.Forms uzyskasz aplikacji systemu Android, aplikację systemu iOS i aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) i [dokumentacji platformy Xamarin.Forms](/xamarin/xamarin-forms/).

####  <a name="ShareHTML"></a> Współużytkowanie kodu dla systemu Android, iOS i aplikacji systemu Windows

 Jeśli nie używasz platformy Xamarin.Forms i projektować osobno dla każdej platformy można udostępniać większość kodu bez interfejsu użytkownika między projektami platform (Android, iOS i Windows). W tym wszelka logika biznesowa, integracja chmury, dostęp do bazy danych lub inny kod, przeznaczonego dla programu .NET Framework. Nie można udostępniać tylko kod jest kodu przeznaczonego dla określonej platformy.

 ![Współużytkowanie kodu systemu Windows, iOs i Android interfejsu użytkownika](../cross-platform/media/sharecode.png "ShareCode")

 Możesz udostępniać kodu za pomocą udostępnionego projektu i projektu biblioteki klas przenośnych. Może się okazać, że niektóre kodu mieści się przez więcej najlepiej w projekcie udostępnionym i kodu znaczeniu wewnątrz projektu biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|[Udostępnianie kodu opcje](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Kod opcje udostępniania z platformą .NET](/dotnet/standard/cross-platform/) |

###  <a name="WindowsHTML"></a> Docelowych urządzeń z systemem Windows 10

 ![Urządzenia z systemem Windows](../cross-platform/media/windowsdevices.png "urządzeń z systemem Windows")

 Jeśli chcesz utworzyć tylko jednej aplikacji, którego celem jest rozmaitych urządzeń z systemem Windows 10, należy utworzyć uniwersalną aplikację systemu Windows. Będzie projektowania aplikacji przy użyciu jednego projektu i będą wyświetlane prawidłowo niezależnie od tego, jakiego urządzenia można je wyświetlić.

 Uruchom z szablonem projektu aplikacji systemu Windows platformy Uniwersalnej. Wizualnego projektowania stron, a następnie otwórz je w oknie Podgląd, aby sprawdzić, jak są wyświetlane dla różnych typów urządzeń. Jeśli nie lubisz, jak zostanie wyświetlona strona na urządzeniu, aby zoptymalizować strony w celu lepszego dopasowania rozmiaru ekranu, rozwiązania lub różnych orientacji, takim jak tryb pozioma lub pionowa. Można wykonywać wszystkie na tym, za pomocą menu łatwo dostępne opcje i intuicyjne narzędzia systemu windows w programie Visual Studio. Gdy wszystko jest gotowe do uruchamiania aplikacji i krok za pomocą kodu, można znaleźć wszystkie urządzenia emulatorów i symulatorów dla różnych typów urządzeń razem na jednej liście rozwijanej, który znajduje się na **standardowe** paska narzędzi.

|**Dowiedz się więcej**|
|--------------------|
|[Wprowadzenie do platformy uniwersalnej systemu Windows](/windows/uwp/get-started/universal-application-platform-guide)|
|[Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrowanie aplikacji platformy uniwersalnej systemu Windows (UWP)](https://msdn.microsoft.com/en-us/library/mt148501.aspx)|

##  <a name="HTML"></a> Tworzenie aplikacji dla systemu Android, iOS i Windows (HTML/JavaScript)

 ![Windows, iOS i urządzeniach z systemem Android](../cross-platform/media/homedevices.png "systemu Windows, iOS i urządzeniach z systemem Android")

 Jeśli jesteś deweloperem sieci web i znasz kodu HTML i JavaScript, można kierować systemu Windows, Android i iOS za pomocą narzędzi Visual Studio Tools for Apache Cordova. Te aplikacje można wskazać wszystkie trzy platformy i można je utworzyć za pomocą umiejętności i procesy, które znasz najbardziej.

 Apache Cordova to platforma, która zawiera model dodatku plug-in. Ten model wtyczek udostępnia jeden interfejs API JavaScript, która umożliwia dostęp do możliwości urządzenie z natywnym wszystkich trzech platform (Android, iOS i Windows).

 Ponieważ te interfejsy API są międzyplatformowa, można udostępniać większość zapisu między wszystkich trzech platform. Pozwala to ograniczyć koszty rozwoju i konserwacji. Ponadto jest niepotrzebna od samego początku. Jeśli po utworzeniu innych typów aplikacji sieci web, można udostępniać te pliki aplikacji platformy Cordova bez konieczności modyfikowania lub zmodyfikowanie je w dowolny sposób.

 ![Aplikacji hybrydowych dla wielu urządzeń przy użyciu języka Javascript](../cross-platform/media/multidevicehybridapps.png "aplikacji hybrydowych dla wielu urządzeń przy użyciu języka Javascript")

 Aby rozpocząć, zainstaluj program Visual Studio 2017 r, a następnie wybierz pozycję **programowania aplikacji mobilnych w języku Javascript** funkcji podczas instalacji. Narzędzia Cordova automatycznie zainstalować wszystkie oprogramowania innych firm, które są wymagane do utworzenia aplikacji w wielu platform.

 Po zainstalowaniu rozszerzenia, Otwórz program Visual Studio i utworzyć **pusta aplikacja (Apache Cordova)** projektu. Następnie możesz utworzyć aplikację przy użyciu języka JavaScript i Typescript. Możesz także dodać wtyczki, aby rozszerzyć funkcjonalność aplikacji i interfejsów API z dodatków plug-in są wyświetlane w IntelliSense podczas pisania kodu.

 Gdy wszystko jest gotowe do uruchamiania aplikacji i krok za pomocą kodu, należy wybrać emulator, takich jak emulatorze Apache Ripple lub emulatora systemu Android, przeglądarki lub urządzeń, które zostały podłączone bezpośrednio do komputera. Następnie uruchom aplikację. Jeśli projektujesz aplikacji na komputerach z systemem Windows, możesz nawet uruchamiać go na tym. Wszystkie te opcje są wbudowane w program Visual Studio jako część programu Visual Studio Tools for Apache Cordova.

 Szablony projektu do tworzenia aplikacji systemu Windows platformy Uniwersalnej są nadal dostępne w programie Visual Studio tak najbliższym z nich korzystać, jeśli planujesz pod kątem tylko urządzeń z systemem Windows. Jeśli zechcesz później target Android i iOS, należy zawsze portu swój kod projektu oprogramowania Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Wprowadzenie do programu Visual Studio Tools for Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/) (docs.microsoft.com)|
|[Dowiedz się więcej o programie Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

<a name="CPP"></a>

## <a name="build-an-app-for-android-and-windows-c"></a>Tworzenie aplikacji dla systemu Android i Windows (C++)
 ![Użyj C&#43; &#43; do kompilacji dla systemu Android, iOS i Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw należy zainstalować program Visual Studio 2017 i **programowania aplikacji mobilnych w języku C++** obciążenia. Następnie można utworzyć aplikacji działania natywnego dla systemu Android lub aplikacji, która jest przeznaczony dla systemu Windows. Szablonów języka C++, które są przeznaczone dla systemu iOS nie są jeszcze dostępne. Android i Windows można kierować w tym samym rozwiązaniu Jeśli, a następnie udostępnić kod między nimi przy użyciu wielu platform statyczne lub dynamiczne biblioteki współużytkowanej.

 Jeśli potrzebujesz do tworzenia aplikacji dla systemu Android, które wymaga dowolny rodzaj manipulowanie grafiki zaawansowanych, takich jak gier, można użyć C++ aby wykonać to zadanie. Rozpoczynać **aplikacji klasy Nativeactivity (Android)** projektu. Ten projekt zawiera pełną obsługę łańcuch narzędzi Clang.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat_cpp_native.png "działania natywnego projektu szablonu")

 Gdy wszystko jest gotowe do uruchamiania aplikacji i zobacz, jak wygląda, należy użyć emulatora systemu Android. Jest szybkie, niezawodne i łatwe do instalowania i konfigurowania.

 Można także utworzyć aplikację, która dotyczy rozmaitych urządzeń z systemem Windows 10 za pomocą języka C++ i szablonu projektu aplikacji Uiversal platformy systemu Windows (UWP). Dowiedz się więcej o tym w [urządzeń docelowych systemu Windows 10](#WindowsHTML) sekcji, która występuje wcześniej w tym temacie.

 Kod w języku C++ między systemami Android i Windows można udostępniać tworząc statyczne lub dynamiczne biblioteki udostępnionej.

 ![Współużytkowanych bibliotekach statycznych i dynamicznych](../cross-platform/media/cross_plat_cpp_libraries.png "współużytkowanych bibliotekach statycznych i dynamicznych")

 Będzie można korzystać z tej biblioteki w systemie Windows lub projekt systemu Android, jak firma opisana wcześniej w tej sekcji. Można również korzystać go w aplikacji, podczas tworzenia za pomocą platformy Xamarin, Java lub dowolnego języka, który pozwala wywoływać funkcje w niezarządzanej bibliotece DLL.

 Podczas pisania kodu w tych bibliotek, można użyć IntelliSense do eksplorowania macierzystych interfejsów API platformy systemu Android i Windows. Te projekty biblioteki są w pełni zintegrowane z debuger programu Visual Studio, można ustawić punktów przerwania, kroki do kodu i znajdowanie i rozwiązywanie problemów przy użyciu wszystkich zaawansowanych funkcji debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobierz program Visual Studio.](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Zainstaluj Visual C++ for Cross Platform Mobile Development tools.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o języku C++ do wielu platform docelowych.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj co i następnie tworzenie aplikacji natywnych działania dla systemu Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o udostępnianiu kod w języku C++ aplikacji systemu Android i Windows](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Wiele platform przenośnych przykłady dla języka C++](https://msdn.microsoft.com/library/dn707596.aspx) (Biblioteka MSDN)|
|[Aplikacji mobilnych dla wielu platform dodatkowe przykłady dla języka C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Tworzenie gier i platform dla systemu Android, iOS i Windows za pomocą narzędzi Visual Studio tools for Unity

 Visual Studio Tools for Unity jest bezpłatne rozszerzenia dla programu Visual Studio, która integruje się programu Visual Studio edycji kodu zaawansowanych, wydajności i debugowania narzędzi z *Unity*, aparat popularnych i platform gier grafiki i Środowisko deweloperskie do aplikacji bez ramek, które odnoszą się do systemu Windows, iOS, Android i innych platform, w tym sieci web.

 ![Środowisko projektowe pomocą rozszerzenia VSTU](../cross-platform/media/vstu_overview.png "Visual Studio Tools for Unity — omówienie")

 Program Visual Studio Tools dla Unity (pomocą rozszerzenia VSTU) programu Visual Studio służy również do zapisu gry i Edytor skryptów w języku C#, a następnie znajdź i napraw błędy za pomocą jego doskonałego debugera. Najnowszą wersję pomocą rozszerzenia VSTU zapewnia obsługę Unity 2018.1 i zawiera kolorowanie składni dla języka programu do cieniowania ShaderLab dla Unity, lepiej synchronizacji z Unity, bardziej zaawansowane funkcje debugowania i generowanie kodu ulepszone kreatora MonoBehavior. Pomocą rozszerzenia VSTU oferuje również plików projektu Unity, komunikaty konsoli i możliwość uruchamiania gry w programie Visual Studio, aby móc poświęcić mniej czasu przełączanie z edytora Unity podczas pisania kodu.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu Unity gry z programem Visual Studio](https://www.visualstudio.com/en-us/features/unitytools-vs.aspx)|
|[Więcej informacji na temat programu Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) |
|[Uruchom przy użyciu programu Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Przeczytaj o najnowsze ulepszenia do programu Visual Studio Tools dla Unity 2.0 w wersji zapoznawczej](http://blogs.msdn.com/b/visualstudio/archive/2014/12/03/visual-studio-tools-for-unity-2-0-preview.aspx) (blog Visual Studio)|
|[Obejrzyj film wideo zawierający wprowadzenie do programu Visual Studio Tools dla Unity 2.0 w wersji zapoznawczej](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (klip wideo)|
|[Dowiedz się więcej o Unity](http://unity3d.com/) (Unity witryny sieci Web)|

## <a name="see-also"></a>Zobacz też

- [Dodaj do projektu programu Visual Studio Office 365 API](http://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Usługi aplikacji Azure — aplikacje mobilne](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](https://docs.microsoft.com/appcenter)