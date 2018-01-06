---
title: Tworzenie aplikacji OpenGL ES w systemach Android i iOS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: xplat-cplusplus
ms.openlocfilehash: 6378826a090b05a681a4808573eefd95899b9f6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Tworzenie aplikacji OpenGL ES w systemach Android i iOS
Po zainstalowaniu programu Visual C++ for Cross Platform Mobile Development — opcja, można utworzyć rozwiązań programu Visual Studio i projektów dla aplikacji systemu iOS i Android aplikacje, które mają wspólny kod. Ten temat przeprowadzi Cię przez szablon rozwiązania, który tworzy zarówno aplikację iOS proste, jak i aplikacji systemu Android działania natywnego. Aplikacje mają kod w języku C++ wspólną używane przez interfejsy OpenGL ES do wyświetlenia tego samego modułu obracania animowany na każdej z platform. Interfejsy OpenGL ES (OpenGL dla osadzonych systemów lub GLES) jest 2W i 3W grafiki interfejsu API, który jest obsługiwany na wielu urządzeniach przenośnych.  
  
 [Wymagania](#req)   
 [Utwórz nowy projekt aplikacji OpenGLES](#Create)   
 [Tworzenie i uruchamianie aplikacji systemu Android](#BuildAndroid)   
 [Tworzenie i uruchamianie aplikacji systemu iOS](#BuildIOS)   
 [Dostosowywanie aplikacji](#Customize)  
  
##  <a name="req"></a>Wymagania  
 Przed utworzeniem aplikacji OpenGL ES dla systemów iOS i Android, należy się upewnić, że zostały spełnione wszystkie wymagania systemowe. Należy zainstalować Visual C++ for Cross Platform Mobile Development — opcja programu Visual Studio 2015. Upewnij się, że wymagane narzędzia innych firm i zestawy SDK znajdują się w instalacji i że jest zainstalowany program Visual Studio Emulator for Android. Aby uzyskać więcej informacji oraz szczegółowe instrukcje, zobacz [zainstalować Visual C++ for Cross Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Do tworzenia i testowania aplikacji systemu iOS, będziesz potrzebować Mac komputer, skonfigurowany zgodnie z instrukcjami instalacji. Aby uzyskać więcej informacji dotyczących sposobu konfigurowania dla opracowywania aplikacji systemu iOS, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
##  <a name="Create"></a>Utwórz nowy projekt aplikacji OpenGLES  
 W tym samouczku najpierw utwórz nowy projekt OpenGL ES aplikacji i późniejszego kompilowania i uruchamianie aplikacji domyślnej w Visual Studio Emulator for Android. Następnie tworzenie aplikacji dla systemu iOS i uruchomić aplikację w symulatorze systemu iOS.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Otwórz program Visual Studio. Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **szablony**, wybierz **Visual C++**, **Cross Platform**, a następnie wybierz pozycję  **OpenGLES aplikacji (Android, iOS)** szablonu.  
  
3.  Nadaj nazwę, takie jak aplikacja `MyOpenGLESApp`, a następnie wybierz pozycję **OK**.  
  
     ![Nowy projekt aplikacji OpenGLES](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
     Visual Studio tworzy nowe rozwiązanie i otworzy w Eksploratorze rozwiązań.  
  
     ![MyOpenGLESApp w Eksploratorze rozwiązań](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
 Nowe rozwiązanie OpenGL ES aplikacja obejmuje trzy projekty bibliotek i dwa projekty aplikacji. Folder biblioteki obejmuje projektu udostępnionego kodu i dwa projekty specyficzne dla platformy, które odwołują się do udostępnionego kodu:  
  
-   **MyOpenGLESApp.Android.NativeActivity** zawiera odwołań i kodu pośredniczącego, który implementuje aplikacji jako działania natywnego w systemie Android. Implementacja punktów wejścia z kodu pośredniczącego znajdują się w main.cpp, w tym typowy kod udostępnionych w MyOpenGLESApp.Shared. Prekompilowane nagłówki są pch.h. Ten projekt aplikacji natywnej działania jest kompilowany do pliku biblioteki udostępnionej (.so), który zostaje pobrana przez projekt MyOpenGLESApp.Android.Packaging.  
  
-   **MyOpenGLESApp.iOS.StaticLibrary** tworzy plik biblioteki statycznej (tj.) z systemem iOS, który zawiera kod udostępnionych w MyOpenGLESApp.Shared. Jest on powiązany aplikacji utworzonych przez MyOpenGLESApp.iOS.Application projektu.  
  
-   **MyOpenGLESApp.Shared** zawiera kod udostępnionego, który działa na różnych platformach. Makra preprocesora używa do kompilacji warunkowej kodu specyficzne dla platformy. Udostępniony kod zostaje pobrana przez odwołanie do projektu w MyOpenGLESApp.Android.NativeActivity i MyOpenGLESApp.iOS.StaticLibrary.  
  
 Rozwiązania zawiera dwa projekty do tworzenia aplikacji dla systemu Android i iOS platform:  
  
-   **MyOpenGLESApp.Android.Packaging** tworzy plik apk dla wdrożenia na urządzeniu z systemem Android lub w emulatorze. Zawiera zasoby i których wartość właściwości manifestu pliku AndroidManifest.xml. Zawiera ona także pliku build.xml, która kontroluje proces kompilacji narzędzia Ant. Ustawiono go jako projekt startowy domyślnie, dzięki czemu można go wdrożyć i uruchomić bezpośrednio z programu Visual Studio.  
  
-   **MyOpenGLESApp.iOS.Application** zawiera zasoby i kodu pośredniczącego Objective-C do tworzenia aplikacji systemu iOS prowadzący do kodu biblioteki statycznej C++ w MyOpenGLESApp.iOS.StaticLibrary. Ten projekt tworzy pakiet kompilacji, który jest przekazywany do komputera Mac przez program Visual Studio i zdalnego agenta. Podczas kompilowania projektu programu Visual Studio wysyła pliki i polecenia do tworzenia i wdrażania aplikacji na komputerach Mac.  
  
##  <a name="BuildAndroid"></a>Tworzenie i uruchamianie aplikacji systemu Android  
 Rozwiązanie utworzonej przez szablon ustawia aplikacji systemu Android jako projekt domyślny.  Możesz skompilować i uruchomić tę aplikację, aby zweryfikować instalacji i konfiguracji. Dla testu początkowej, uruchom aplikację na jeden z profilów urządzeń instalowane przez Visual Studio Emulator for Android. Jeśli wolisz testowanie aplikacji na inny element docelowy można załadować emulatora docelowego lub podłącz urządzenie do komputera.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Tworzenie i uruchamianie aplikacji natywnej działanie systemu Android  
  
1.  Jeśli nie została jeszcze wybrana, wybierz **x86** z **platformy rozwiązania** listy rozwijanej.  
  
     ![Ustaw platforma rozwiązania x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
     Użyj x86 pod kątem Android Emulator dla systemu Windows. Jeśli ma być przeznaczona dla urządzenia, wybierz platforma rozwiązania oparte na procesorze urządzenia. Jeśli **platformy rozwiązania** lista nie jest wyświetlana, wybierz **platformy rozwiązania** z **Dodaj lub usuń przyciski** listy, a następnie wybierz platformy.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu MyOpenGLESApp.Android.Packaging, a następnie wybierz pozycję **kompilacji**.  
  
     ![Kompilacji projektu systemu Android pakowania](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
     W oknie danych wyjściowych wyświetla dane wyjściowe z procesu tworzenia Android współużytkowanych biblioteki i aplikacji systemu Android.  
  
     ![Dane wyjściowe kompilacji dla projektów w systemie Android](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3.  Wybierz jedną z emulatora VS profile telefonów z systemem Android (x86) jako urządzenie docelowe wdrożenia.  
  
     ![Wybierz cel wdrożenia](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
     Jeśli masz zainstalowany innych emulatory lub podłączone urządzenie z systemem Android, możesz je na liście rozwijanej cel wdrożenia. Aby uruchomić aplikację, wbudowanego platforma rozwiązania musi być zgodna platformy urządzenia docelowego.  
  
4.  Naciśnij klawisz F5, aby rozpocząć debugowanie lub Shift + F5, aby uruchomić bez debugowania.  
  
     Visual Studio rozpoczyna emulatora, który przyjmuje kilka sekund, aby załadować i wdrażanie kodu. Poniżej przedstawiono sposób wyświetlania aplikacji w emulatorze Visual Studio dla systemu Android.  
  
     ![Aplikacja działa w emulatorze systemu Android](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
     Po uruchomieniu aplikacji, można ustawić punktów przerwania i Debuggera krokowo kodu, Sprawdź zmienne lokalne i obejrzyj wartości.  
  
5.  Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
     Emulator jest oddzielny proces, który jest nadal uruchomiona. Można edytować, kompilowanie i wdrażanie kodu wielokrotnie do tego samego emulatora. Aplikacja pojawia się w kolekcji aplikacji na emulatorze i można było go uruchomić z niego bezpośrednio.  
  
 Wygenerowany Android Native działania aplikacji i biblioteki projektów języka C++ udostępniony kod w dynamicznej biblioteki, która zawiera kod "sklejki" do interfejsu z platformy systemu Android. Oznacza to, większość kodu aplikacji znajduje się w bibliotece, a w projekcie pakowania ma manifestu, zasobów i instrukcje kompilacji. Udostępniony kod jest wywoływana z main.cpp w projekcie działania NativeActivity. Aby uzyskać więcej informacji na temat programu Android działania natywnego, zobacz zestawu NDK systemu Android Developer [pojęcia](https://developer.android.com/ndk/guides/concepts.html) strony.  
  
 Visual Studio kompiluje projekty natywnego działanie systemu Android przy użyciu zestawu Android NDK, który używa jako zestaw narzędzi platformy Clang. Visual Studio mapuje właściwości w projekcie działania NativeActivity przełączniki wiersza polecenia i opcje, które są używane do kompilowania, łączenie i debugowania na platformie docelowej. Aby uzyskać więcej informacji, otwórz **strony właściwości** okna dialogowego MyOpenGLESApp.Android.NativeActivity projektu. Aby uzyskać więcej informacji na temat przełączników wiersza polecenia, zobacz [Clang kompilatora obsługi](http://clang.llvm.org/docs/UsersManual.html).  
  
##  <a name="BuildIOS"></a>Tworzenie i uruchamianie aplikacji systemu iOS  
 Projekt aplikacji systemu iOS jest utworzone i edytowane w programie Visual Studio, ale z powodu ograniczeń licencji musi być skompilowany i wdrożone z komputerów Mac. Visual Studio komunikuje się z agentem zdalnym systemem Mac do transferu plików projektu i wykonać kompilację, wdrażania i debugowania poleceń. Należy skonfigurować i konfigurowania komputerów Mac i Visual Studio do komunikowania się przed utworzeniem aplikacji dla systemu iOS. Aby uzyskać szczegółowe instrukcje, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Po zdalnego agent jest uruchomiony i Visual Studio jest łączyć się z komputera Mac, należy skompilować i uruchomić aplikacji dla systemu iOS, aby zweryfikować instalacji i konfiguracji.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Aby skompilować i uruchomić aplikację systemu iOS  
  
1.  Sprawdź, czy zdalny agent jest uruchomiony na komputerze Mac i że Visual Studio jest łączyć się z agentem zdalnym. Aby uruchomić agenta zdalnego, Otwórz okno terminala aplikacji, a następnie wprowadź `vcremote`. Aby uzyskać więcej informacji, zobacz [konfiguracji agenta zdalnego w programie Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
     ![Okno terminalu Mac systemem vcremote](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")  
  
2.  Jeśli nie została jeszcze wybrana, wybierz **x86** z **platformy rozwiązania** listy rozwijanej.  
  
     ![Ustaw platforma rozwiązania x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
     Użyj x86 pod kątem symulatora systemu iOS. Jeśli ma być przeznaczona dla urządzenia z systemem iOS, wybierz platforma rozwiązania oparte na procesorze urządzenia (zazwyczaj procesor ARM). Jeśli **platformy rozwiązania** lista nie jest wyświetlana, wybierz **platformy rozwiązania** z **Dodaj lub usuń przyciski** listy, a następnie wybierz platformy.  
  
3.  W Eksploratorze rozwiązań Otwórz menu skrótów projektu MyOpenGLESApp.iOS.Application i wybierz polecenie **kompilacji**.  
  
     ![Tworzenie projektu aplikacji systemu iOS](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
     W oknie danych wyjściowych wyświetla dane wyjściowe z procesu tworzenia biblioteki statycznej systemu iOS i aplikacji dla systemu iOS. Dla komputerów Mac uruchamiania agenta zdalnego Pokazuje okno polecenia i plik transfer działania.  
  
     Na komputerze Mac może zostać wyświetlony monit na akceptować żądania podpisywania kodu. Wybierz opcję Zezwalaj, aby kontynuować.  
  
4.  Wybierz **symulatora systemu iOS** na pasku narzędzi, aby uruchomić aplikację w symulatorze systemu iOS opartym na systemie Może upłynąć kilka minut, aby uruchomić symulatora. Masz symulator się na pierwszym planie przełączenie na komputerze Mac, aby wyświetlić dane wyjściowe.  
  
     ![Aplikacja uruchomiona w systemie iOS Simulator](../cross-platform/media/cppmdd_opengles_iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
     Po uruchomieniu aplikacji, można ustawić punktów przerwania i użyj debuger programu Visual Studio, aby zbadać zmiennych lokalnych, zobacz stosu wywołań i obejrzyj wartości.  
  
     ![Debuger na punkt przerwania w aplikacji dla systemu iOS](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5.  Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
     IOS Simulator jest procesem oddzielne kontynuuje działanie opartym na systemie Można edytować, kompilowanie i wdrażanie kodu wiele razy w tym samym wystąpieniu symulatora systemu iOS. Można również uruchomić kod bezpośrednio w symulatorze po jej wdrożeniu.  
  
 Projekty aplikacji i biblioteki wygenerowanego iOS umieść kod C++ w bibliotece statycznej implementujący udostępnionego kodu. Większość kodu aplikacji znajduje się w projekcie aplikacji. Kod biblioteki udostępnionej w tym projekcie szablonu wywołań w pliku GameViewController.m. Tworzenie aplikacji systemu iOS, Visual Studio korzysta z narzędzi platformy Xcode, który wymaga komunikacji z klientem zdalnym, który działa na komputerach Mac.  
  
 Visual Studio przesyłanie plików projektu i wysyła polecenia do zdalnego klienta do kompilowania aplikacji za pomocą środowiska Xcode. Klient zdalny wysyła kompilacji informacje o stanie do programu Visual Studio. W przypadku aplikacji został pomyślnie utworzony, można użyć programu Visual Studio należy wysyłać polecenia do uruchomienia i debugowania aplikacji. W debugerze programu Visual Studio określa uruchomiona w działaniu symulatora systemu iOS na komputerze Mac lub na urządzeniu z systemem iOS dołączone aplikacja. Visual Studio mapuje właściwości w projekcie StaticLibrary przełączniki wiersza polecenia i opcje, które są używane do tworzenia, łączenie i debugowania na platformie iOS docelowej. Dla opcji wiersza polecenia kompilatora uzyskać szczegółowe informacje, otwórz **strony właściwości** okna dialogowego MyOpenGLESApp.iOS.StaticLibrary projektu.  
  
##  <a name="Customize"></a>Dostosowywanie aplikacji  
 Można zmodyfikować udostępnionym kodem C++, aby dodać lub zmienić często używane funkcje. Należy zmienić wywołania do udostępnionego kodu w projektach MyOpenGLESApp.Android.NativeActivity i MyOpenGLESApp.iOS.Application do dopasowania. Makra preprocesora służy do określenia sekcji specyficzne dla platformy w kodzie wspólnej. Makro preprocesora `__ANDROID__` jest wstępnie zdefiniowane podczas budowania dla systemu Android. Makro preprocesora `__APPLE__` jest wstępnie zdefiniowane podczas budowania dla systemu iOS.  
  
 Aby wyświetlić IntelliSense dla konkretnego projektu platformy, wybierz projekt, na liście rozwijanej przełącznik kontekstu na pasku nawigacyjnym w górnej części okna edytora.  
  
 ![Projekt z listy rozwijanej przełącznik kontekstu w edytorze](../cross-platform/media/cppmdd_opengles_contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 Problemów IntelliSense w bieżącym projekcie są oznaczone ikoną z czerwonym wiersza faliste. Problemy z innych projektów są oznaczone linii faliste purpurowy. Domyślnie program Visual Studio nie obsługuje kod kolorowania i technologii IntelliSense dla plików języka Java lub Objective-C. Można nadal modyfikować pliki źródłowe i zmieniać zasoby, aby ustawić nazwę aplikacji, ikony i inne szczegóły implementacji.