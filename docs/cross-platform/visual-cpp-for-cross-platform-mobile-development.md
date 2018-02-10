---
title: Visual C++ for Cross Platform Mobile Development | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 2ae49bb09d30122297efc66779f808e0c39dd0d7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Visual C++ for Cross Platform Mobile Development
Można tworzyć natywne aplikacje C++ dla systemu iOS, Android i Windows i udziału typowy kod w bibliotekach przeznaczony dla systemu iOS, Android i Windows za pomocą programu Visual C++ dla aplikacji mobilnych dla wielu Platform. Ta opcja jest dostępna w programie Visual Studio 2015, który instaluje zestawy SDK i narzędzia potrzebne do aplikacji dla wielu platform bibliotek udostępnionych i aplikacje natywne. Po jej zainstalowaniu może umożliwiają utworzenie kodu uruchamianego w systemach iOS i urządzeniach z systemem Android i platform, oprócz Windows, Windows Phone lub Xbox Visual C++.  
  
 Pisanie kodu dla wielu platform może być irytujące. Języki programowania podstawowego i narzędzia dla systemów iOS, Android i Windows są różne na każdej z platform. Jednak wszystkie platformy obsługują pisanie kodu w języku C++. Jest to wspólnego mianownika używanej umożliwiające ponowne użycie kodu rdzeni na platformach. Natywny kod napisany w języku C++ może być zarówno jeden wydajność i odporność do odtwarzania. Ponowne użycie kodu można zapisać zarówno ilość czasu, podczas tworzenia aplikacji dla wielu platform.  
  
 Programowanie za pomocą języka Visual C++ dla wielu Platform Mobile Development ma kilka zalet:  
  
1.  **Łatwe instalacji.** Instalator programu Visual Studio pobiera i instaluje wymagane narzędzia innych firm i zestawy SDK jest potrzebne do tworzenia aplikacji oraz bibliotek dla systemów Android i iOS. Konfiguracja i ustawienia jest proste i przede wszystkim automatycznego.  
  
2.  **Środowisko wydajny i znanych kompilacji.** Zabezpieczać wieloplatformowych rozwiązania i projekty łatwo utworzyć szablony programu Visual Studio. Zarządzanie właściwościami we wszystkich projektach przy użyciu jednego wspólnego interfejsu. Edytowanie kodu w edytorze programu Visual Studio i skorzystać z wbudowanych funkcji IntelliSense i platform uzupełnianie kodu i błąd podświetlania.  
  
3.  **Ujednolicone obsługi debugowania.** Narzędzia światowej klasy debugowania w programie Visual Studio można oglądać i kroków kod w języku C++ na wszystkich platformach, w tym urządzeń z systemem Android emulatorów, symulatorów iOS i urządzeń i urządzeń z systemem Windows lub Windows Phone i emulatory.  
  
## <a name="get-the-tools"></a>Pobierz narzędzia  
 Visual C++ dla wielu Platform Mobile Development to opcja zainstalowania dołączoną do programu Visual Studio 2015. Wymagania wstępne i instrukcje dotyczące instalacji, zobacz [zainstalować Visual C++ for Cross Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Aby utworzyć kodu dla systemu iOS, należy również komputera Mac i Apple iOS konta dewelopera. Aby uzyskać więcej informacji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Pochodzić się wszystkiego  
 Jeśli jest pochodzące programowanie Android lub iOS, mamy niektórych materiałów dużą jak rozpocząć pracę. Visual Studio to środowisko programistyczne obszerne i stanie. Aby dowiedzieć się, jak z niego korzystać, spróbuj [wprowadzenie dla deweloperów systemu Android](https://msdn.microsoft.com/en-us/library/windows/apps/dn275875.aspx) lub [wprowadzenie dla deweloperów systemu iOS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/jj657966.aspx). W tych tematach przedstawiono Visual Studio i koncepcje potrzebne do tworzenie wieloplatformowych aplikacji dla systemu Windows i Windows Phone. Aby rozpocząć pisanie pierwszej aplikacji i platform dla systemu iOS i Android, zobacz [kompilacji aplikacji OpenGL ES w systemach Android i iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C++ dla wielu Platform Mobile Development zawiera kilka szablonów, aby pomóc Ci rozpocząć w aplikacjach:  
  
-   OpenGLES 2 aplikacji (Android, iOS, uniwersalnych systemu Windows)  
  
     Tworzy rozwiązania, które zawiera zestaw projektów do kompilacji aplikacji systemu Android działania natywnego, aplikację systemu iOS i aplikacji uniwersalnej systemu Windows, wraz z biblioteki współużytkowanej kodu C++. Te aplikacje użyj biblioteki specyficzne dla platformy utworzone przy użyciu wspólnej kodu C++ OpenGL ES do rysowania tego samego wirujący sześcian w każdej aplikacji. Należy dołączyć opcję Narzędzia do programowania aplikacji uniwersalnych systemu Windows po zainstalowaniu programu Visual Studio, aby użyć tego szablonu.  
  
-   Aplikacji klasy Nativeactivity (Android)  
  
     Tworzy pełnej aplikacji C++ OpenGL jako projekt Android działania natywnego.  
  
-   OpenGLES aplikacji (Android, iOS)  
  
     Tworzy rozwiązanie z zestawem projektów do kompilacji zarówno aplikacji natywnej działanie systemu Android, jak i aplikacji systemu iOS. Te aplikacje użyj biblioteki specyficzne dla platformy utworzone przy użyciu wspólnej kodu C++ OpenGL ES do rysowania tego samego wirujący sześcian w każdej aplikacji.  
  
-   Biblioteka udostępniona (Android, iOS)  
  
     Tworzy rozwiązanie z projektami do utworzenia pliku dynamicznej biblioteki systemu Android (.so) i pliku biblioteki statycznej (tj.) z systemem iOS przy użyciu wspólnej kodu C++ w projekcie udostępnionym.  
  
-   Aplikacji w warstwie podstawowa (Android, Ant)  
  
     Tworzy Android projektu aplikacji "Hello, World", który używa tylko kod źródłowy Java i Ant systemu kompilacji.  
  
-   Aplikacji w warstwie podstawowa (Android, Gradle)  
  
     Tworzy Android projektu aplikacji "Hello, World", który używa tylko do kodu źródłowego języka Java i Gradle systemu kompilacji.  
  
-   Podstawowa biblioteka (Android, Ant)  
  
     Tworzy Android projektu biblioteki "Hello, World", który używa tylko kod źródłowy Java i Ant systemu kompilacji.  
  
-   Podstawowa biblioteka (Android, Gradle)  
  
     Tworzy Android projektu biblioteki "Hello, World", który używa tylko do kodu źródłowego języka Java i Gradle systemu kompilacji.  
  
-   Dynamiczna Biblioteka (Android) udostępniona  
  
     Tworzy plik dynamicznej biblioteki systemu Android (.so) przy użyciu kodu C++.  
  
-   OpenGLES 2 aplikacji (iOS)  
  
     Tworzy rozwiązanie z zestawem projektów do kompilacji aplikacji systemu iOS OpenGL ES 2. Aplikacja używa biblioteki kodu C++ OpenGL ES do rysowania wirujący sześcian w aplikacji systemu iOS. Ta aplikacja może być dobry punkt wyjścia przy przeglądaniu jak zaimportować biblioteki języka C++ do aplikacji systemu iOS.  
  
-   Biblioteka statyczna (Android)  
  
     Tworzy projekt do tworzenia biblioteki statycznej dla systemu Android. Można tylko jeden dynamicznej biblioteki w aplikacji systemu Android, ale możesz połączyć dowolną liczbę bibliotek statycznych.  
  
-   Biblioteka statyczna (iOS)  
  
     Tworzy projekt do tworzenia biblioteki statycznej dla systemu iOS.  
  
-   Projektu pliku reguł programu make (Android)  
  
     Tworzy otokę projektu dla projektów makefile systemu Android.  
  
## <a name="try-out-sample-code"></a>Wypróbuj przykładowy kod  
 Pobierz przykłady pokazujące, jak utworzyć biblioteki udostępnionej kodu, używanego w systemie Windows, Android i aplikacje dla systemu iOS oraz sposobu tworzenia zakończenie działania natywnego aplikacje dla systemu Android. Aby rozpocząć, zobacz [i Platform Mobile Development przykłady](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
1.  [Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [Instalowanie i konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [Tworzenie aplikacji systemu Android działania natywnego](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Tworzenie aplikacji OpenGL ES w systemach Android i iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Przykłady programowania międzyplatformowych aplikacji mobilnych](../cross-platform/cross-platform-mobile-development-examples.md)