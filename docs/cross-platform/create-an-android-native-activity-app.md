---
title: "Tworzenie aplikacji systemu Android działania natywnego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: e03fb8fd62e7f9b2e37dfc2efe8f02580c7b32f5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="create-an-android-native-activity-app"></a>Tworzenie aplikacji systemu Android działania natywnego
Po zainstalowaniu Visual C++ for Cross Platform Mobile Development — opcja programu Visual Studio 2015 może służyć do tworzenia funkcjonalnej aplikacji natywnej działanie systemu Android. Native Development Kit (zestawu NDK systemu Android) to zestaw narzędzi, która pozwala na wdrożenie większość aplikacji systemu Android przy użyciu czystym kodzie C/C++. Kod języka Java JNI działa jako sklejki, aby umożliwić kodu C/C++ do interakcji z systemem Android. Zestaw Android NDK wprowadzono możliwość tworzenia działania natywnego aplikacje z systemem Android 9 poziom interfejsu API. Kod natywny działania jest popularnych do tworzenia gier i graficzne znacznym aplikacji, które używają aparatu Unreal Engine lub OpenGL. W tym temacie przedstawiono tworzenie prostej aplikacji działania natywnego, który używa OpenGL. Dodatkowe tematy przeprowadzenie cyklu życia developer edycji, kompilowanie, debugowanie i wdrażanie działania natywnego kodu.  
  
 [Wymagania](#req)   
 [Utwórz nowy projekt działania natywnego](#Create)   
 [Tworzenie i uruchamianie aplikacji systemu Android działania natywnego domyślne](#BuildHello)  
  
##  <a name="req"></a>Wymagania  
 Przed utworzeniem aplikacji systemu Android działania natywnego musi upewnij się, że zostały spełnione wszystkie wymagania systemowe i zainstalowane opcję Visual C++ Mobile Development w Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [zainstalować Visual C++ for Cross Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Upewnij się, że wymagane narzędzia innych firm i zestawy SDK znajdują się w instalacji, oraz że zainstalowano programu Microsoft Visual Studio Emulator for Android.  
  
##  <a name="Create"></a>Utwórz nowy projekt działania natywnego  
 W tym samouczku zostanie najpierw utwórz nowy projekt Android działania natywnego, a następnie skompilować i uruchomić domyślna aplikacja w Visual Studio Emulator dla systemu Android.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Otwórz program Visual Studio. Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **szablony**, wybierz **Visual C++**, **Cross Platform**, a następnie wybierz pozycję  **Aplikacji klasy Nativeactivity (Android)** szablonu.  
  
3.  Nadaj nazwę, takie jak aplikacja `MyAndroidApp`, a następnie wybierz pozycję **OK**.  
  
     ![Tworzenie projektu działania natywnego](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")  
  
     Visual Studio tworzy nowe rozwiązanie i otworzy w Eksploratorze rozwiązań.  
  
     ![Natywnego projektu działania w Eksploratorze rozwiązań](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
 Nowe rozwiązanie aplikacji systemu Android działania natywnego zawiera dwa projekty:  
  
-   **MyAndroidApp.NativeActivity** zawiera odwołań i kodu pośredniczącego aplikacji do uruchamiania jako działania natywnego w systemie Android. Implementacja punktów wejścia z kodu pośredniczącego znajdują się w main.cpp. Prekompilowane nagłówki są pch.h. Ten projekt aplikacji natywnej działania jest kompilowany do pliku .so biblioteki udostępnionej, który zostaje pobrana przez projekt opakowania.  
  
-   **MyAndroidApp.Packaging** tworzy plik apk dla wdrożenia na urządzeniu z systemem Android lub w emulatorze. Zawiera zasoby i których wartość właściwości manifestu pliku AndroidManifest.xml. Zawiera ona także pliku build.xml, która kontroluje proces kompilacji narzędzia Ant. Ustawiono go jako projekt startowy domyślnie, dzięki czemu można go wdrożyć i uruchomić bezpośrednio z programu Visual Studio.  
  
##  <a name="BuildHello"></a>Tworzenie i uruchamianie aplikacji systemu Android działania natywnego domyślne  
 Tworzenie i uruchamianie aplikacji wygenerowane przez szablonu, aby zweryfikować instalacji i konfiguracji. Dla tego testu początkowej, uruchom aplikację na jeden z profilów urządzeń instalowane przez Visual Studio Emulator for Android. Jeśli wolisz testowanie aplikacji na inny element docelowy można załadować emulatora docelowego lub podłącz urządzenie do komputera.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>Tworzenie i uruchamianie aplikacji natywnej działania domyślne  
  
1.  Jeśli nie została jeszcze wybrana, wybierz **x86** z **platformy rozwiązania** listy rozwijanej.  
  
     ![Wybór listy rozwijanej x86 platformy rozwiązania](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     Jeśli **platformy rozwiązania** listy nie jest wyświetlany, wybierz **platformy rozwiązania** z **Dodaj lub usuń przyciski** listy, a następnie wybierz platformy.  
  
2.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
     W oknie danych wyjściowych wyświetla dane wyjściowe procesu kompilacji dwa projekty w rozwiązaniu.  
  
3.  Wybierz jedną z emulatora VS profile telefonów z systemem Android (x86) jako urządzenie docelowe wdrożenia.  
  
     Jeśli masz zainstalowany innych emulatory lub podłączone urządzenie z systemem Android, możesz je na liście rozwijanej cel wdrożenia.  
  
4.  Naciśnij klawisz F5, aby rozpocząć debugowanie lub Shift + F5, aby uruchomić bez debugowania.  
  
     Oto, co domyślna aplikacja wygląda w emulatora programu Visual Studio dla systemu Android.  
  
     ![Emulator z tą aplikacją](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")  
  
     Visual Studio rozpoczyna emulatora, który zajmuje kilka sekund do ładowania i wdrażanie kodu. Po uruchomieniu aplikacji, można ustawić punktów przerwania i Debuggera krokowo kodu, Sprawdź zmienne lokalne i obejrzyj wartości.  
  
5.  Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
     Emulator jest oddzielny proces, który jest nadal uruchomiona. Można edytować, kompilowanie i wdrażanie kodu wielokrotnie do tego samego emulatora.