---
title: Wprowadzenie do programu Visual Studio for Mac | Dokumentacja firmy Microsoft
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: bc836806e1acf33b35604419ac1d6aad41a2d795
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="introducing-visual-studio-for-mac"></a>Wprowadzenie do programu Visual Studio dla komputerów Mac

Visual Studio for Mac jest nowoczesnych, rozbudowanych IDE z wiele funkcji umożliwiających tworzenie mobile, pulpitu i aplikacji sieci web. Obsługuje programowanie z następujących czynności:

* Telefon komórkowy z platformą .NET: Android, iOS, systemu tvOS, watchOS
* Aplikacje komputerowe Mac
* Aplikacje .NET core
* Aplikacje ASP.NET Core sieci Web
* Gry środowiska Unity i platform

Go zawiera zaawansowany edytor, debugowanie, natywnego platformy integracji z systemem iOS, Mac i Android i zintegrowanej kontroli źródła tylko kilka z wielu funkcji.

W tym temacie ankiety różnych części programu Visual Studio dla komputerów Mac, podając informacje o niektórych funkcji, które ułatwiają zaawansowane narzędzie do tworzenia aplikacji dla wielu platform.

## <a name="installation"></a>Instalacja

Postępuj zgodnie z instrukcjami [instalacji](~/installation.md) przewodnika do pobrania i zainstalowania programu Visual Studio dla komputerów Mac.

## <a name="language-support"></a>Obsługa języków

Domyślnie programu Visual Studio for Mac obsługuje programowanie w języku C# i F #.

### <a name="c"></a>C#

C# jest najczęściej używane język do tworzenia aplikacji dla wielu platform w programie Visual Studio dla komputerów Mac. To zapewnia pełną obsługę wszystkich funkcji języka C# 7.

### <a name="f"></a>F#

F # to silnie typizowane funkcjonalny język programowania przeznaczonych do uruchamiania na platformie .NET. Jest ona dostępna jako język programowania Visual Studio dla użytkowników komputerów Mac w systemach Android, Mac i z systemem iOS. Więcej informacji na temat używania F # i aby wyświetlić przykłady utworzonych w języku, można znaleźć [F #](https://developer.xamarin.com/guides/cross-platform/fsharp/) przewodników.

## <a name="platform-support"></a>Obsługa platform

## <a name="net-core"></a>.NET Core

[.NET core](https://www.microsoft.com/net/core#macos) to platforma do tworzenia aplikacji dla systemów Windows i Linux oraz dla komputerów Mac. Program Visual Studio for Mac obsługuje ładowanie, tworzenie, uruchamianie i debugowanie projektów platformy .NET Core.

Do uruchomienia projektów .NET Core, .NET Core SDK powinien zostać pobrana i zainstalowana.

Obsługa platformy .NET Core obejmuje poniższe elementy:

* Funkcja IntelliSense języków C# i F#.
* Szablony projektów platformy .NET Core dla aplikacji konsoli, biblioteki i sieci Web.
* Pełna obsługa debugowania, w tym punkty przerwania, stos wywołań i okno wyrażeń kontrolnych.
* Odwołania PackageReference do pakietów NuGet i przywracanie oparte na aparacie kompilacji MSBuild.
* Jednostka zintegrowane testowania pomocy technicznej do uruchamiania i debugowanie testów z dołączoną do programu .NET Core SDK platformy testowej Visual Studio.
* Migracja z formatu starego pliku project.json.

Aby rozpocząć, zapoznaj się aplikacji sieci web platformy ASP.NET Core [laboratorium praktycznego](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="xamarin"></a>Xamarin

Najwyższej jakości pomoc techniczna dla platformy [Xamarin](https://developer.xamarin.com/) umożliwia tworzenie rozbudowanych natywnych środowisk dla systemów Android, macOS, iOS, tvOS i watchOS. Aplikacje dla wielu platform oparte na platformie Xamarin.Forms ułatwiają współużytkowanie kodu interfejsu użytkownika opartego na języku XAML między systemami Android, iOS i macOS bez ograniczania dostępu do funkcji natywnych.

Aby rozpocząć, zapoznaj się aplikacji mobilnych [laboratorium praktycznego](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started).

### <a name="android"></a>Android

Visual Studio ma własną zintegrowane menedżera zestawu SDK systemu Android.

W przypadku aplikacji systemu Android, programu Visual Studio for Mac obejmuje własną designer, który współpracuje z systemem Android `.axml` plików do wizualnego tworzenia interfejsów użytkownika. Visual Studio for Mac Otwórz tych plików w jego projektanta dla systemu Android, jak pokazano poniżej:

![](media/intro-image31.png)

Aby uzyskać więcej informacji o Android Zobacz projektanta [Omówienie projektanta](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview) dokumentu.

### <a name="ios"></a>iOS

IOS Projektant jest w pełni zintegrowana z programem Visual Studio dla komputerów Mac i umożliwia edycja wizualna .xib i pliki scenorysu, aby utworzyć dla systemu iOS, systemu tvOS i UI WatchOS i przejścia. Cały interfejs użytkownika mogą być tworzone za pomocą funkcji przeciągania i upuszczania między przybornika i powierzchni projektowej, używając intuicyjne rozwiązanie do obsługi zdarzeń. IOS projektanta obsługuje również [Kontrolki niestandardowe](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/) tę zaletę renderowania w czasie projektowania.

![](media/intro-image30.png)

Aby uzyskać więcej informacji na temat używania systemu iOS projektanta dotyczą [projektanta](https://developer.xamarin.com/guides/ios/user_interface/designer) dokumentów.

### <a name="mac"></a>Mac

Xamarin zawiera natywny powiązania Mac API umożliwiające tworzenie doskonałych aplikacji dla komputerów Mac.

Aby uzyskać więcej informacji na temat pisania aplikacji dla komputerów Mac z programem Visual Studio dla komputerów Mac, zapoznaj się [Xamarin.Mac](https://developer.xamarin.com/guides/#mac) dokumentacji.

## <a name="gaming"></a>Gry

Visual Studio for Mac obsługuje programowanie wieloplatformowych gry z Unity 5.6.1.

Aby rozpocząć, zapoznaj się jednolitości [laboratorium praktycznego](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started).

## <a name="enterprise-features"></a>Funkcje organizacji

> [!Note]
> Te produkty można używać tylko z subskrypcji programu Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Xamarin Profiler ma trzy instrumentów dostępnych do profilowania. [Wprowadzenie do platformy Xamarin profilera](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/) przewodnik Eksploruje pomiaru tych dokumentów i sposób ich analizowania aplikacji i wyjaśnia, w rozumieniu dane wyświetlane na poszczególnych ekranach.

### <a name="inspector"></a>Inspektor

Inspektor Xamarin zapewnia interaktywne C# konsolę narzędzia do użytkowników. Może służyć jako pomoc debugowania lub diagnostyki podczas sprawdzania aplikacji na żywo w ramach nauczania jako narzędzie dokumentacji lub eksperymenty.

![](media/intro-inspector.png)

Składa się z aplikacja autonomiczna, która udostępnia bogate C# konsolę, która może kierować różnych platform programowania (Android, iOS, Mac i z systemem Windows) oraz integrowanie debugowania przepływ pracy programu IDE.

Więcej informacji można znaleźć w [inspektora Xamarin](https://developer.xamarin.com/guides/cross-platform/inspector/) przewodnik.

## <a name="next-steps"></a>Następne kroki

* **Duży obraz** — Aby uzyskać przegląd wielu najważniejszych funkcji w programie Visual Studio dla komputerów Mac, zobacz Visual Studio dla komputerów Mac [samouczek IDE](~/ide-tour.md).
* **Instalator** — Aby dowiedzieć się więcej o tym, jak pobrać i zainstalować program Visual Studio, zobacz [instalacji](~/installation.md) przewodnik.
* **Samouczki platformy Xamarin** — Aby dowiedzieć się więcej na temat opracowywania kodu za pomocą platformy Xamarin, przejdź do Xamarin [Centrum deweloperów](https://developer.xamarin.com).
* **Filmy wideo** — Aby dowiedzieć się więcej o innych funkcjach i aspektów programu Visual Studio dla komputerów Mac, zapoznaj się wideo na [Xamarin University](https://university.xamarin.com) witryny sieci Web.
* **Laboratoria praktyczne** — aby rozpocząć pracę z różnych obciążeń uwzględnione w programie Visual Studio dla komputerów Mac, zapoznaj się z [praktyczne labs](https://github.com/Microsoft/vs4mac-labs).