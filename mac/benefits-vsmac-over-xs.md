---
title: Zalety programu Visual Studio dla komputerów Mac w programie Xamarin Studio
description: ''
ms.topic: overview
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.openlocfilehash: db4a328bceb79c1b99fdea95da89cc6cc7451523
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>Zalety programu Visual Studio dla komputerów Mac w programie Xamarin Studio 

Visual Studio for Mac została zastąpiona Xamarin Studio jako w pełni funkcjonalnego środowiska IDE na komputerach Mac. Zapewnia funkcje, które umożliwiają opracowywanie aplikacji sieci web i usług, i platform mobilnych i klasycznych aplikacji i gier. Ponadto ułatwia integrowanie z Azure błyskawicznie, czy oznacza to publikowanie na platformie Azure lub tworzenie usługi Azure Functions. Ma ona wszystko, czego można oczekiwać od nowoczesnych IDE, w tym edytorze źródła kompletne, zaawansowany debuger obszaru roboczego można dostosowywać, integracja z usługą git i sformatowanego rozszerzenia systemu, wszystkie zaprojektowane w sposób macierzysty dla komputerów Mac. 

Oto niektóre inne funkcje: 

* Na podstawie Roslyn C# IntelliSense, refaktoryzacji analizatory i poprawki kodu 
* Pakiet NuGet zarządzania 
* Format zgodnego projektu usługi Visual Studio 
* Aparat kompilacji MSBuild 
* Zintegrowane testy jednostkowe 
* Obsługa języka F # out-of--box 

Korzyści wymienione w tym przewodniku, które są oznaczone jako **Podgląd** są dostępne tylko w [kanał alfa](https://docs.microsoft.com/visualstudio/mac/update#Changing_the_Updater_channel). 

## <a name="language-support"></a>Obsługa języków 

Pisanie kodu C# 7 na komputerze Mac jest oferowana tylko w programie Visual Studio dla komputerów Mac.

## <a name="net-core"></a>.NET Core  

[.NET core](https://www.microsoft.com/net/core#macos) to platforma do tworzenia aplikacji dla systemów Windows i Linux oraz dla komputerów Mac. Program Visual Studio for Mac obsługuje ładowanie, tworzenie, uruchamianie i debugowanie projektów platformy .NET Core. 

.NET core są zainstalowane z programem Visual Studio dla komputerów Mac i działa bez.

Obsługa platformy .NET Core obejmuje poniższe elementy: 

* Funkcja IntelliSense języków C# i F#. 
* Szablony projektów platformy .NET Core dla aplikacji konsoli, biblioteki i sieci Web. 
* Pełna obsługa debugowania, w tym punkty przerwania, stos wywołań i okno wyrażeń kontrolnych. 
* Odwołania do pakietu NuGet i przywracanie na podstawie programu MSBuild. 
* Jednostka zintegrowane testowania pomocy technicznej do uruchamiania i debugowanie testów z dołączoną do programu .NET Core SDK platformy testowej Visual Studio. 
* Migracja z formatu starego pliku project.json. 
* Obsługa standardowych projektu platformy .NET.

## <a name="web-development"></a>Projektowanie witryn sieci Web  

### <a name="aspnet-core"></a>ASP.NET Core 

Visual Studio for Mac zawiera szablony platformy ASP.NET Core dla projektów MVC i interfejsu API sieci Web poza pole.
 
![HTML Intellisense](media/benefits-vsmac-over-xs-image3.png)

Visual Studio for Mac dodaje również nowe narzędzia obsługi plików HTML, CSS i JSON sieci web. 

### <a name="html"></a>HTML 

* Nowy szablon HTML. 
* Ulepszone inteligentne wcięcia i formatowanie. 
* Lepsze kolorowanie. 
* Ulepszona funkcja IntelliSense. 
* Funkcja zwijania kodu (musi być włączona). 
* Polecenie Odwróć minimalizację. 
* Ulepszone szablony kodu (fragmenty). 
* Polecenie Otocz zaznaczenie za pomocą `<div>`. 
* Opcja w górę/w dół przenosi zaznaczony tekst w górę/w dół. 

### <a name="css"></a>CSS 

* Ulepszone inteligentne wcięcia i formatowanie. 
* Lepsze kolorowanie. 
* Ulepszona funkcja IntelliSense. 
* Zwijanie kodu. 
* Wiele szablonów kodu (fragmentów). 
* Opcja w górę/w dół przenosi zaznaczony tekst w górę/w dół. 

### <a name="json"></a>JSON 
* Selektor schematów z dostępem do kolekcji schemastore.org. 
* Walidacja z poziomu schematu. 
* Funkcja IntelliSense dostępna z poziomu schematu. 
* Ulepszone inteligentne wcięcia i formatowanie. 
* Lepsze kolorowanie. 
* Funkcja dodawania/usuwania komentarzy. 
* Iniekcja cytatów i parowanie nawiasów klamrowych. 
* Opcja w górę/w dół przenosi zaznaczony tekst w górę/w dół. 

## <a name="publishing-to-azure"></a>Publikowanie na platformie Azure

Program Visual Studio for Mac jest możliwe do publikowania usług i aplikacji sieci web platformy ASP.NET Core w usłudze Azure App Service. 

![Publikowanie na platformie Azure](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions-preview"></a>Środowisko Azure Functions (**Podgląd**)

Azure Functions to rozwiązanie umożliwiające łatwe uruchamianie małych fragmentów kodu lub funkcje, w chmurze. Visual Studio for Mac umożliwia kodu i lokalnie debugowania funkcji platformy Azure. Aby rozpocząć korzystanie wygląd dla usługi Azure Functions do chmury w oknie dialogowym Nowy projekt. 

### <a name="docker-support-preview"></a>Obsługa docker (**Podgląd**)

Możesz teraz publikowanie aplikacji platformy ASP.NET Core dla kontenerów Docker i uruchamiać je w usłudze Azure App Service. 

Aby włączyć obsługę Docker w projekcie, kliknij prawym przyciskiem myszy na aplikację sieci web platformy ASP.NET Core, a następnie wybierz **Dodaj > Dodaj obsługuje Docker**. 

Aby opublikować aplikację sieci web w kontenerze Docker, użyj **publikowania > Publikowanie na platformie Azure** przepływu pracy, wprowadzone w programie Visual Studio dla komputerów Mac.

## <a name="source-editor-improvements"></a>Ulepszenia edytora źródła 

Oprócz na podstawie Roslyn C# IntelliSense, refaktoryzacji, analizatory i poprawki kodu programu Visual Studio for Mac Edytor źródła oferują następujące udoskonalenia w programie Xamarin Studio: 

### <a name="language-bundles"></a>Pakiety języka 

Visual Studio for Mac ma obsługę TextMate (`.tmBundle`) i sublime 3 (`.sublime`) pakietów językowych, które służy do dodania: 

* Motywy kolorów edytora 
* Wstawki kodu 
* Gramatyki dla nowych języków, włączanie funkcji IntelliSense wyróżnienia i podstawowych 

Można dodać te pakiety w **Preferencje > Edytor tekstu > pakietów językowych**. 

### <a name="color-theme-support"></a>Obsługa motywu kolorów 

Następujące formaty motywu kolorów są obsługiwane w programie Visual Studio dla komputerów Mac: 

* Visual Studio (`.vssettings`) 
* Program Xamarin studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) jest narzędziem do tworzenia gier służy do tworzenia wysokiej jakości gier 2W i 3W i platform dla wszystkich głównych platform: przenośne, komputerów, konsol, AR i VR urządzenia i nawet sieci web. 

Począwszy od platformy Unity 5.6.1, można użyć programu Visual Studio dla komputerów Mac do zapisu i debugowania gry środowiska Unity. Aby rozpocząć pracę, należy ustawić Visual Studio, aby 5.6.1 Unity przez Edytor skryptów. 

Tools for Unity obejmują: 

* Obsługa skryptów napisanych w języku C#. 
* Konsola rozwiązania Unity. 
* Jednym kliknięciem debugowania Edytor platformy Unity. 
* IntelliSense dla Unity wiadomości. 
* Kod zabarwienie dla Unity dla programów do cieniowania. 
* Dostęp do dokumentacji Unity. 

## <a name="xamarin"></a>Xamarin 

Gdy funkcji i platform Xamarin były zawsze najwyższej jakości funkcji programu Xamarin Studio, są funkcje Xamarin, które są dostępne tylko w programie Visual Studio dla komputerów Mac 

### <a name="android"></a>Android 

* [Android SDK manager](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* Android O będą tylko obsługiwane w programie Visual Studio dla komputerów Mac, nie Xamarin Studio 

### <a name="ios-and-mac"></a>iOS i Mac 

* [iOS podpisywania aktualizacji przepływu pracy ](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * Tworzenie tożsamości podpisywania i zainstaluj je do lokalnej łańcucha kluczy. 
    * Utwórz profile aprowizacji. 
    * Dodaj tożsamości podpisywania do istniejącego profilu.
    *  Dostarczyć urządzeniom: zarejestrowanie urządzenia w portalu dla deweloperów firmy Apple i dodaj je do profilu inicjowania obsługi administracyjnej.
* iOS 11, watchOS 4 i systemu tvOS 2 będą tylko obsługiwane w programie Visual Studio dla komputerów Mac, nie Xamarin Studio 
* System MacOS wysokiej Sierra będą tylko obsługiwane w programie Visual Studio dla komputerów Mac, nie Xamarin Studio 

### <a name="cross-platform"></a>Wiele platform 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/) (**Podgląd**) 
* [Xamarin IoT](https://developer.xamarin.com/guides/cross-platform/iot/) (**Podgląd**) 
 