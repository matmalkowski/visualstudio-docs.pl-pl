---
title: Wprowadzenie do programu Visual Studio dla komputerów Mac
description: W tym artykule przedstawiono funkcje programu Visual Studio dla komputerów Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 738964deed9aa1e51d5a6e4788879bc3165284a7
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37889888"
---
# <a name="introducing-visual-studio-for-mac"></a>Wprowadzenie do programu Visual Studio dla komputerów Mac

Program Visual Studio for Mac to nowoczesnych, rozbudowanych środowisko IDE z wieloma funkcjami do tworzenia, mobilnych, klasycznych i aplikacji sieci web. Obsługuje następujące typy tworzenia:

* Telefon komórkowy przy użyciu platformy .NET: Android, iOS, tvOS i watchOS
* Aplikacji klasycznej dla komputerów Mac
* Aplikacje .NET core
* Aplikacje sieci web platformy ASP.NET Core
* Gry Unity dla wielu platform

Zawiera funkcje, takie jak Zaawansowany edytor, debugowanie, platformy natywnej integracji z systemem iOS, Mac i Android i zintegrowane z kontroli źródła.

W tym artykule badań różnych części programu Visual Studio dla komputerów Mac i zawiera funkcje, które ułatwiają zaawansowane narzędzie do tworzenia aplikacji dla wielu platform.

## <a name="installation"></a>Instalacja

Postępuj zgodnie z instrukcjami w [instalacji](installation.md) przewodnika, aby pobrać i zainstalować program Visual Studio dla komputerów Mac.

## <a name="language-support"></a>Obsługa języków

Domyślnie program Visual Studio for Mac obsługuje programowanie w języku C# i F #.

### <a name="c"></a>C#

C# jest językiem najczęściej używane do tworzenia aplikacji dla wielu platform w programie Visual Studio dla komputerów Mac. IDE ma pełną pomoc techniczną dla wszystkich funkcji w języku C# 7.

### <a name="f"></a>F#

F # to silnie typizowane funkcjonalny język programowania przeznaczony do działania na platformie .NET. Jest ona dostępna jako języka programowania do programu Visual Studio dla użytkowników komputerów Mac w systemach Android, Mac i iOS. Aby uzyskać więcej informacji na temat korzystania z F # i wyświetlić przykłady utworzone w języku, odwiedź stronę [F #](https://developer.xamarin.com/guides/cross-platform/fsharp/) przewodników.

## <a name="platform-support"></a>Obsługa różnych platform

## <a name="net-core"></a>.NET Core

[.NET core](https://www.microsoft.com/net/core#macos) to platforma do tworzenia aplikacji działających w Windows, Linux i Mac. Program Visual Studio for Mac obsługuje ładowanie, tworzenie, uruchamianie i debugowanie projektów platformy .NET Core. 

W celu uruchamiania projektów .NET Core, .NET Core SDK powinno zostać pobrana i zainstalowana.

Obsługa platformy .NET Core obejmuje poniższe elementy:

* Funkcja IntelliSense języków C# i F#.
* Szablony projektów platformy .NET Core dla aplikacji konsoli, biblioteki i internetowych.
* Pełna obsługa debugowania, w tym punkty przerwania, stos wywołań i okno wyrażeń kontrolnych.
* Odwołania PackageReference do pakietów NuGet i przywracanie oparte na aparacie kompilacji MSBuild.
* Zintegrowana obsługa umożliwiająca uruchamianie i debugowanie testów jednostkowych testów za pomocą platforma testowa Visual Studio, który jest dołączony do zestawu .NET Core SDK.
* Migracja ze starego formatu project.json.

Aby rozpocząć, zapoznaj się z aplikacji sieci web platformy ASP.NET Core [laboratorium praktycznego](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="xamarin"></a>Xamarin

Najwyższej jakości pomoc techniczna dla platformy [Xamarin](https://developer.xamarin.com/) umożliwia tworzenie rozbudowanych natywnych środowisk dla systemów Android, macOS, iOS, tvOS i watchOS. Aplikacje dla wielu platform oparte na platformie Xamarin.Forms ułatwiają współużytkowanie kodu interfejsu użytkownika opartego na języku XAML między systemami Android, iOS i macOS bez ograniczania dostępu do funkcji natywnych.

Aby rozpocząć, zapoznaj się z aplikacji mobilnych [laboratorium praktycznego](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started).

### <a name="android"></a>Android

Visual Studio ma swój własny zintegrowane Menedżer zestawu Android SDK.

Dla aplikacji systemu Android program Visual Studio dla komputerów Mac zawiera swój własny projektanta, który współdziała z programem Android `.axml` pliki do konstruowania wizualnie interfejsów użytkownika. Program Visual Studio for Mac zostanie otwarty tych plików w jego projektanta systemu Android, jak pokazano na poniższej ilustracji:

![Projektant interfejsu użytkownika dla systemu android](media/intro-image31.png)

Aby uzyskać więcej informacji na temat narzędzia Android Designer, zobacz [Przegląd projektanta](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview) dokumentu.

### <a name="ios"></a>iOS

IOS Designer jest w pełni zintegrowana z programem Visual Studio dla komputerów Mac i umożliwia wizualne edytowanie .pliki i pliki scenorysu, aby utworzyć dla systemu iOS, tvOS i UI systemu WatchOS i przejścia. Cały interfejs użytkownika może być skompilowana przy użyciu funkcji przeciągania i upuszczania między przybornik i powierzchni projektowej podczas korzystania z intuicyjnym sposobem obsługi zdarzeń. System iOS obsługuje również projektanta [niestandardowe formanty](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/) jednocześnie ma dodatkową zaletę renderowania w czasie projektowania.

![Projektant scenorysu z systemem iOS](media/intro-image30.png)

Aby uzyskać więcej informacji na temat korzystania z narzędzia iOS Designer, zobacz [projektanta](https://developer.xamarin.com/guides/ios/user_interface/designer) dokumentów.

### <a name="mac"></a>Mac

Środowisko Xamarin zapewnia natywne powiązań interfejsów API komputera Mac, które umożliwiają tworzenie atrakcyjnych aplikacji dla komputerów Mac.

Aby uzyskać więcej informacji na temat pisania aplikacji dla komputerów Mac z programem Visual Studio dla komputerów Mac, zobacz [Xamarin.Mac](https://developer.xamarin.com/guides/#mac) dokumentacji.

## <a name="gaming"></a>Gry

Program Visual Studio for Mac zapewnia obsługę tworzenia gier dla wielu platform przy użyciu aparatu Unity 5.6.1.

Aby rozpocząć, zapoznaj się z aparatu Unity [laboratorium praktycznego](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started).

## <a name="enterprise-features"></a>Funkcje wersji Enterprise

> [!Note]
> Te produkty należy używać tylko z subskrypcją programu Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Profiler Xamarin ma trzy instrumenty dostępny do profilowania. [Wprowadzenie do platformy Xamarin Profiler](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/) przewodnik przedstawiono te dokumenty pomiaru i sposób ich analizowania aplikacji i wyjaśnia znaczenie danych prezentowanych na każdym ekranie.

### <a name="inspector"></a>Inspektor

Narzędzia Xamarin Inspector udostępnia interaktywną konsolę C# za pomocą narzędzi użytkownika. Może służyć jako pomoc w debugowaniu lub diagnostyce podczas inspekcji aplikacji na żywo, jako narzędzie nauczania, jako narzędzie dokumentacji lub eksperymentowanie w usłudze.

![Xamarin Inspector](media/intro-inspector.png)

Składa się z aplikacją samodzielną dostarcza zaawansowane C# konsolę, która może różnych platformach programowania (Android, iOS, Mac i Windows) oraz integrowanie Twojego środowiska IDE debugowanie przepływu pracy. 

Aby uzyskać więcej informacji, zobacz [narzędzia Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/) przewodnik.

## <a name="next-steps"></a>Następne kroki

* **Pobierz Przewodnik** — aby omówienie wielu funkcji głównych w programie Visual Studio dla komputerów Mac, zobacz Visual Studio dla komputerów Mac [samouczek środowiska IDE](ide-tour.md).
* **Konfigurowanie** — Aby dowiedzieć się więcej o tym, jak pobrać i zainstalować program Visual Studio, zobacz [instalacji](installation.md) przewodnik.
* **Samouczki platformy Xamarin** — Aby dowiedzieć się więcej o tym, jak tworzyć kod za pomocą platformy Xamarin, przejdź do Xamarin [Centrum deweloperów](https://developer.xamarin.com).
* **Filmy wideo** — Aby dowiedzieć się więcej o innych funkcjach i aspekty Visual Studio dla komputerów Mac, Obejrzyj wideo w witrynie [Xamarin University](https://university.xamarin.com) witryny sieci Web.
* **Laboratoria tematyczne** — aby rozpocząć pracę z różnych obciążeń zawarte w Visual Studio dla komputerów Mac, zapoznaj się z [warsztaty](https://github.com/Microsoft/vs4mac-labs).
