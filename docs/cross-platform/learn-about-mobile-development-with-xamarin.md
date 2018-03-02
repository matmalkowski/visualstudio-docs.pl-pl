---
title: "Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: 6dcfd6be29d8ba978605301412f7ee918deda8f2
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin

Ten temat kieruje do materiałów Przegląd, która pomaga w zrozumieniu tworzenie wieloplatformowych aplikacji mobilnych za pomocą platformy Xamarin. Jeśli użytkownik nie został jeszcze zainstalowany program Visual Studio i Xamarin, uruchom [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) procesu należy następnie wróć tutaj do pracy przy użyciu tych zasobów, gdy pliki instalacyjne są uruchomione.  
  
> [!NOTE]
> Jeśli nie podano inaczej, zalecamy początkowo odczytywania tylko te strony połączone bezpośrednio w tym miejscu i nie przedstawicielstwach strony. Jeśli proces instalacji jest nadal uruchomiony po zakończeniu tej listy, możesz przejść wstecz i Poznaj dodatkowe tematy.  
>   
> Ponadto się zapoznaj się z tematami oznaczone "Podstawowe" i powracanie do tematów "Bardziej Zgłębić temat".  
  
## <a name="essentials-introduction-to-xamarin"></a>Essentials: Wprowadzenie do platformy Xamarin  

*10-20 minut*  
  
1.  [Aplikacje mobilne w programie Visual Studio z platformą Xamarin](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) zapewnia bardzo krótki uwalniania podstawowego właściwości Xamarin.  
  
2.  [Tworzenie wieloplatformowych Mobile aplikacji przy użyciu języka C# i Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9 15m16s) z i Propagator systemu Xamarin, James Montemagno. Pierwsze trzy minuty są zawiera przegląd Xamarin, następuje pokazów kodu.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Essentials: Omówienie programu Visual Studio i Xamarin środowiska  

*5 – 15 minut*  
  
-   Komputer z systemem Windows z Visual Studio i Xamarin jest, gdzie należy wykonać większość pracy. Na tym komputerze należy bezpośrednio tworzenia aplikacji systemu Android i Windows, uruchomić i debugowania je na urządzeniu lub emulatorze. Możesz również zdalnie kompilacji, uruchamiania i debugowania aplikacji systemu iOS za pomocą komputerów Mac. Visual Studio na komputerze z systemem Windows można również nawiązać designer scenorysu z systemem iOS i symulatora systemu iOS.  
  
-   Mac z Xcode i Xamarin służy jako kompilacji/podpisania środowisko hosta i środowiska uruchomieniowego dla aplikacji systemu iOS. Kompilacje dla systemu iOS w programie Visual Studio na komputerze z systemem Windows mają delegowane do tego komputera Mac; podczas debugowania aplikacji systemu iOS w programie Visual Studio, działa w symulatorze systemu iOS w Mac lub bezpośrednio na urządzenia powiązanego podłączone do komputerów Mac. W takim przypadku zostanie interakcji z aplikacją lub w jego pobliżu Mac oraz mieć środowiska debugowania w programie Visual Studio.  
  
Poniżej przedstawiono te relacje i możesz przeczytać dodatkowe informacje o pracy z aplikacjami systemu iOS na [wprowadzenie do platformy Xamarin.iOS dla programu Visual Studio](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/) (xamarin.com).  
  
![Relacja między komputerami deweloperów systemu Windows i Mac w środowisku Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin informacje 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Essentials: Projekty są struktury  

*10-30 minut*  
  
1.  [Udostępnianie kodu opcje](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (xamarin.com). Zaleca się przy użyciu opcji bibliotek klas przenośnych, ponieważ najlepiej obsługuje przy użyciu tylko tych interfejsów API architektury .NET, które są obsługiwane na wszystkich platformach docelowych. Większość kodu logiki biznesowej będą znajdować się w PCL, łącznie z dostępem do bazy danych, wywołania interfejsów API REST i wywołania przenośne składników Xamarin (zobacz [bardziej Zgłębić temat: składników Xamarin](#components) na końcu tego tematu). Typowy kod interfejsu użytkownika napisany za pomocą platformy Xamarin.Forms również mogą znajdować się w PCL.  
  
2.  (Opcjonalnie) [— Analiza przypadków: Tasky](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/case_study-tasky/) (xamarin.com), w tym artykule opisano niektóre najważniejsze wskazówki dotyczące projektowania i struktury aplikacji oferujący wszystkie funkcje, takie jak tworzenie struktury projektu z PCL dla udostępnionego kodu, która oddziela danych, dostęp do danych i warstwy biznesowej.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Essentials: natywne i warstwy interfejsu użytkownika platformy Xamarin.Forms  

*10 40 minut*  
  
Xamarin udostępnia dwa sposoby tworzenia niezwykłych aplikacji natywnych: Xamarin Native i platformy Xamarin.Forms.  
  
Z macierzystego Xamarin zapisu oddzielny kod interfejsu użytkownika dla każdej platformy docelowej: iOS, Android i Windows.  Z tej metody można mieć bezpośredni dostęp do interfejsów API specyficzne dla platformy, dzięki czemu dostosowanego środowiska interfejsu użytkownika dla każdej platformy.  Masz również pełny dostęp do natywnych projektanta i formantów dla poszczególnych platform ułatwiające tworzenie odpowiedniego interfejsu użytkownika.  
  
Platformy Xamarin.Forms obejmują uogólniony zestaw interfejsów API, która umożliwia zapisanie udostępnionej warstwy interfejsu użytkownika dla wszystkich platform w bibliotece klas przenośnych.  Renderuje platformy Xamarin.Forms natywnych kontrolek w każdej platformy docelowej, aby zapewnić natywnego wyglądu i działania.  Zamiast z platformy Xamarin.Forms przy użyciu projektanta, należy utworzyć interfejsu użytkownika przy użyciu języka C# i języka XAML.  
  
Nie musisz zdecydować, które rozwiązanie do wykonania na początku; aplikacje można zaimplementować przy użyciu kombinacji Xamarin Native i platformy Xamarin.Forms:  
  
-   Platformy Xamarin.Forms używany do tworzenia ekrany ogólnego przeznaczenia, które zapewniają podobne interfejsu użytkownika i możliwości na platformach, takich jak nazwy logowania, skontaktuj się z formularzy i wyników wyszukiwania.  
  
-   Użyj różnych możliwości dostosowywania w platformy Xamarin.Forms dostosowanie interfejsu użytkownika na podstawie poszczególnych platform. Obejmują one OnPlatform interfejsu API, które mogą być używane zarówno kod i języka XAML, tworzenie widok niestandardowy, rozszerzanie istniejących renderowania i tworzenie niestandardowego modułu renderowania.  
  
-   W razie potrzeby użyj natywnego Xamarin do tworzenia ekrany używających unikatowe funkcje interfejsu użytkownika dla każdej z platform, na przykład, ekran, który używa manipulowania przechwytywania i obrazu natywnego aparatu.  
  
Firma Microsoft zaleca zawsze począwszy od platformy Xamarin.Forms rozwiązania do skonfigurowania kodu interfejsu użytkownika do udostępniania różnych platform i przy użyciu możliwości dostosowywania wprowadzanie korekt specyficzne dla platformy. Jeśli potrzebujesz ekrany całkowicie specyficzne dla platformy, można dodać te oddzielnie za pomocą natywnego Xamarin.  
  
Aby dowiedzieć się więcej:  
  
1.  [Platformy Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/) (xamarin.com) zawiera krótki przegląd i zalet i wad platformy Xamarin.Forms a natywnego warstwy interfejsu użytkownika (czyli Xamarin.iOS i Xamarin.Android).  
  
2.  Pierwsze trzy minuty wideo Kuba Montemagno [platformy Xamarin.Forms: natywnego iOS, Android i Windows aplikacji przy użyciu języka C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9 13m3s) zapewnia przegląd innego i można kontynuować wyszukiwanie pokazy.  
  
3.  (Opcjonalnie) [Wprowadzenie do platformy Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/introduction-to-xamarin-forms/) (xamarin.com)  
  
4.  (Opcjonalnie) Zobacz przykłady użycia OnPlatform do dostosowania w [klasę urządzeń](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) dokumentacji (xamarin.com)  
  
5.  (Opcjonalnie) [Wieloplatformowych - udziału interfejsu użytkownika kod między platform Mobile z platformy Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) przez Jason Smith (MSDN Magazine) zawiera opcje różne dostosowania w ramach platformy Xamarin.Forms, dla których szczegóły są przedstawione na [ Dostosowywanie formantów na każdej platformie](http://developer.xamarin.com/guides/xamarin-forms/custom-renderer/) (xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Bardziej zgłębić temat: Debugowanie za pomocą emulatory  

*10 – 15 minut*  
  
Aby debugować i platform aplikacji bez konieczności używania urządzenia fizycznego, konieczne będzie Użyj następującego polecenia:  
  
1.  **Emulatorze systemu Android.** W zależności od wersji systemu Windows są używane zaleca się albo programu Microsoft Visual Studio Emulator dla systemu Android lub Xamarin Player, które oferują duża wydajność i obsługuje szeroką gamę możliwości urządzenia:  
  
    -   **Komputery z systemem Windows 8 +:** zdecydowanie zaleca się przy użyciu firmy Microsoft [programu Visual Studio Emulator for Android](https://www.visualstudio.com/en-us/features/msft-android-emulator-vs.aspx), który został zainstalowany program Visual Studio.  [Programu Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) wideo (Channel9, 5m55s) zawiera omówienie i demonstracji.  
  
    -   **Windows 7 lub wcześniejszej/systemu Windows w systemie Mac OS X**: Użyj [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player) (xamarin.com).  
  
2.  **IOS firmy Apple symulatora.** Aby dowiedzieć się więcej, przeczytaj [wprowadzenie symulatora systemu iOS](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
3.  **Emulator Windows Phone firmy Microsoft.** Aby dowiedzieć się więcej, przeczytaj [Windows Phone Emulator for Windows Phone 8](../debugger/run-windows-phone-apps-in-the-emulator.md).  
  
##  <a name="components"></a> Bardziej zgłębić temat: Składniki platformy Xamarin  

*10 minut*  
  
Wiele funkcji rozszerzonej są dostępne za pośrednictwem składników Xamarin przy użyciu aplikacji Xamarin. Możesz znaleźć pełnym wykazie dostępne do pobrania na [http://components.xamarin.com/](http://components.xamarin.com/), która obejmuje składniki dodatkowe kontrolek interfejsu użytkownika, uwierzytelniania, szerokiej gamy usług chmury, takich jak Microsoft Azure i wiele innych.