---
title: Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.prod: xamarin
ms.technology: xamarin-tools
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: abeac53d6907603d6158c483095152d0f4ab2c5e
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin

W tym artykule wymieniono kilka omówienie, które mogą ułatwić zrozumienie tworzenie wieloplatformowych aplikacji mobilnych za pomocą platformy Xamarin. Jeśli użytkownik nie został jeszcze zainstalowany program Visual Studio i Xamarin, uruchom [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) procesu należy następnie wróć tutaj do pracy przy użyciu tych zasobów, gdy pliki instalacyjne są uruchomione.  
  
> [!NOTE]
> Jeśli nie podano inaczej, początkowo można odczytać tylko tych stron, które są połączone bezpośrednio z tutaj i nie przedstawicielstwach strony. Jeśli proces instalacji jest nadal uruchomiony po zakończeniu tej listy, możesz przejść wstecz i Poznaj dodatkowe tematy.  
>   
> Ponadto się zapoznaj się z tematami oznaczone "Podstawowe" i powracanie do tematów "Bardziej Zgłębić temat".  
  
## <a name="essentials-introduction-to-xamarin"></a>Essentials: Wprowadzenie do platformy Xamarin  

*10-20 minut*  
  
1.  [Aplikacje mobilne w programie Visual Studio z platformą Xamarin](https://www.visualstudio.com/xamarin/) (visualstudio.com) zawiera krótki uwalniania podstawowego właściwości Xamarin.  
  
2.  [Tworzenie wieloplatformowych Mobile aplikacji przy użyciu języka C# i Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9 15m16s) z i Propagator systemu Xamarin, James Montemagno. Pierwsze trzy minuty są zawiera przegląd Xamarin, następuje pokazów kodu.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Essentials: Omówienie programu Visual Studio i Xamarin środowiska  

*5 – 15 minut*  
  
-   Należy to zrobić większość pracy na komputerze z systemem Windows zainstalowanego z programu Visual Studio i Xamarin. Na tym komputerze możesz bezpośrednio tworzenia aplikacji systemu Android i Windows, uruchomić i debugowania je na pulpicie, urządzenia lub emulatory. Zdalnie kompilacji, uruchamiania i debugowania aplikacji systemu iOS za pomocą komputerów Mac. Visual Studio na komputerze z systemem Windows można również nawiązać designer scenorysu z systemem iOS i symulatora systemu iOS.  
  
-   Mac z Xcode i Visual Studio for Mac zainstalowanych służy jako host kompilacji, host podpisywania i środowiska uruchomieniowego dla aplikacji systemu iOS. Tworzy iOS delegatów komputera z systemem Windows do tego Mac. Aplikacja zostanie uruchomiona w symulatorze iOS, Mac lub bezpośrednio powiązane urządzenie podłączone do komputerów Mac. Możesz interakcji z aplikacją dla komputerów Mac, ale należy przeprowadzić proces debugowania w programie Visual Studio.
  
Te relacje są przedstawione poniżej.  
  
![Relacja między komputerami deweloperów systemu Windows i Mac w środowisku Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin informacje 1")  

> [!NOTE]
> Windows Phone jest wyświetlany na tym diagramie, do celów informacje były kompletne. Podczas korzystania z platformy Xamarin, to zalecana opcja udostępniania kodu jest biblioteki .NET 2.0 standardowego, co jest niezgodne z urządzenia Windows Phone lub Windows 10 Mobile. 

Możesz przeczytać dodatkowe informacje o pracy z aplikacjami systemu iOS na [wprowadzenie do platformy Xamarin.iOS dla programu Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio/).
  
## <a name="essentials-how-projects-are-structured"></a>Essentials: Projekty są struktury  

*10-30 minut*  
  
1.  [Udostępnianie kodu opcje](/xamarin/cross-platform/app-fundamentals/code-sharing/). Dla nowych aplikacji należy używać biblioteki .NET Standard udostępnianie kodu. Większość kodu logiki biznesowej będą znajdować się w bibliotece .NET Standard, łącznie z dostępem do bazy danych, wywołania interfejsów API REST i wywołania przenośne składników Xamarin. (Zobacz [bardziej Zgłębić temat: składników Xamarin](#components) na końcu tego artykułu). Typowy kod interfejsu użytkownika napisany za pomocą platformy Xamarin.Forms również znajduje się w bibliotece .NET Standard.  
  
2.  (Opcjonalnie) [— Analiza przypadków: Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky/) Opisuje najlepsze rozwiązania dotyczące projektowania i struktury aplikacji oferujący wszystkie funkcje, takie jak tworzenie struktury projektu z udostępnionego kodu, która oddziela danych, dostęp do danych i warstwy biznesowej.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Essentials: natywne i warstwy interfejsu użytkownika platformy Xamarin.Forms  

*10 40 minut*  
  
Xamarin udostępnia dwa sposoby tworzenia niezwykłych aplikacji: Xamarin Native i platformy Xamarin.Forms.  
  
Z macierzystego Xamarin zapisu oddzielny kod interfejsu użytkownika dla każdej platformy docelowej: iOS, Android i Windows.  Z tej metody należy mieć bezpośredni dostęp do interfejsów API specyficzne dla platformy do projektowania dostosowanego środowiska interfejsu użytkownika dla każdej platformy.  Masz również pełny dostęp do natywnych projektanta i formantów dla poszczególnych platform ułatwiające tworzenie odpowiedniego interfejsu użytkownika.  
  
Platformy Xamarin.Forms zawiera zestaw ogólnych interfejsów API, która umożliwia zapisanie udostępnionej warstwy interfejsu użytkownika dla wszystkich platform z biblioteki .NET Standard.  Renderuje platformy Xamarin.Forms natywnych kontrolek w każdej platformy docelowej, aby zapewnić natywnego wyglądu i działania.  Zamiast przy użyciu projektanta, należy utworzyć interfejsu użytkownika przy użyciu języka C# i języka XAML.  

Większość deweloperzy za pomocą platformy Xamarin.Forms. Jest to zalecane trasy dla deweloperów nowego na platformie Xamarin. Podejście Xamarin Native trudniej jest i wymaga więcej szczegółowych informacji dotyczących platformy docelowej.
  
Nie musisz zdecydować, które rozwiązanie do wykonania na początku; aplikacje można zaimplementować przy użyciu kombinacji Xamarin Native i platformy Xamarin.Forms:  
  
-   Umożliwia tworzenie ekranów ogólnego przeznaczenia platformy Xamarin.Forms. Określają one podobne interfejsy użytkownika i możliwości na różnych platformach, takich jak nazwy logowania, skontaktuj się z formularzy i wyniki wyszukiwania.  
  
-   Użyj różnych możliwości dostosowywania w platformy Xamarin.Forms dostosowanie interfejsu użytkownika na podstawie poszczególnych platform. Obejmuje to najprostsza opcja dostosowania `OnPlatform` interfejsu API. Można również tworzyć widoki niestandardowe, Rozszerz istniejącą renderowania i tworzyć niestandardowe moduły renderowania.  
  
-   W razie potrzeby użyj natywnego Xamarin, aby skompilować ekrany korzystających z interfejsu użytkownika funkcji poszczególnych platform. Przykładem jest ekran, który używa manipulowania przechwytywania i obrazu natywnego aparatu.  
  
Ogólnie należy zacząć z rozwiązaniem platformy Xamarin.Forms, aby zdefiniować kod interfejsu użytkownika do udostępniania różnych platform. Wykorzystanie możliwości dostosowania można następnie dostosować specyficzne dla platformy. Jeśli potrzebujesz ekrany całkowicie specyficzne dla platformy, można dodać te oddzielnie za pomocą natywnego Xamarin.  
  
Aby dowiedzieć się więcej:  
  
1.  [Platformy Xamarin.Forms](/xamarin/xamarin-forms/) zawiera krótki przegląd i zalet i wad platformy Xamarin.Forms a natywnego warstwy interfejsu użytkownika (czyli Xamarin.iOS i Xamarin.Android).  
  
2.  Pierwsze trzy minuty wideo Kuba Montemagno [platformy Xamarin.Forms: natywnego iOS, Android i Windows aplikacji przy użyciu języka C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9 13m3s) zapewnia przegląd innego i można kontynuować wyszukiwanie pokazy.  
  
3.  (Opcjonalnie) [Wprowadzenie do platformy Xamarin.Forms](/xamarin/xamarin-forms/get-started/introduction-to-xamarin-forms/)  
  
4.  (Opcjonalnie) Zobacz przykłady użycia `OnPlatform` do dostosowania w [klasę urządzeń](/xamarin/xamarin-forms/platform/device/) dokumentacji
  
5.  (Opcjonalnie) [Wieloplatformowych - udziału interfejsu użytkownika kod między platform Mobile z platformy Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) przez Jason Smith (MSDN Magazine) zawiera opcje różne dostosowania w ramach platformy Xamarin.Forms, dla których szczegóły są przedstawione na [ Niestandardowe moduły renderowania](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Bardziej zgłębić temat: Debugowanie za pomocą emulatory  

*10 – 15 minut*  
  
Do debugowania aplikacji i platform, bez konieczności używania urządzenia fizycznego, należy użyć emulatory omówione w tym miejscu:  
  
### <a name="microsofts-android-emulator"></a>Emulator systemu Android firmy Microsoft 

Zaleca się, że używasz firmy Microsoft [programu Visual Studio Emulator for Android](~/cross-platform/visual-studio-emulator-for-android.md), który został zainstalowany program Visual Studio.  [Programu Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) wideo (Channel9, 5m55s) zawiera omówienie i demonstracji.  
  
### <a name="apples-ios-simulator"></a>Symulatora systemu iOS firmy Apple

Aby dowiedzieć się więcej, przeczytaj [wprowadzenie symulatora systemu iOS](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
### <a name="microsofts-windows-phone-emulator"></a>Emulator Windows Phone firmy Microsoft.

Aby dowiedzieć się więcej, przeczytaj [testu w emulatorze firmy Microsoft dla systemu Windows 10 Mobile](/windows-uwp/windows-apps-src/debug-test-perf/test-with-the-emulator/).  
  
<a name="components" /> 

## <a name="deeper-dive-xamarin-components"></a>Bardziej zgłębić temat: Składniki platformy Xamarin  

*10 minut*  
  
Wiele funkcji rozszerzonej są dostępne za pośrednictwem składników Xamarin przy użyciu aplikacji Xamarin. Możesz znaleźć pełnym wykazie dostępne do pobrania na [ http://components.xamarin.com/ ](http://components.xamarin.com/), która obejmuje składniki dodatkowe kontrolek interfejsu użytkownika, uwierzytelniania, szerokiej gamy usług chmury, takich jak Microsoft Azure i wiele innych.