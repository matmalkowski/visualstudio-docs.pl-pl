---
title: Wprowadzenie do korzystania z C++ w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: "18"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 48f2bb4e61ca6a4f9a9464a6b67a3218b418c8ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-c-in-visual-studio"></a>Wprowadzenie do korzystania z C++ w programie Visual Studio
Wykonując tego przewodnika, użytkownik będzie zapoznanie się z wielu narzędzi i oknach dialogowych, których można używać podczas opracowywania aplikacji za pomocą programu Visual Studio. Utworzysz prosty tekst "Hello, World" — styl aplikacji, podczas gdy Dowiedz się więcej o pracy w zintegrowane środowisko programistyczne (IDE).  
  
 Ten temat zawiera następujące sekcje:  
  
 [Zaloguj się do programu Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)  
  
 [Utworzyć prostą aplikację](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)  
  
 [Dodawanie kodu do aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)  
  
 [Debugowanie i testowanie aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)  
  
 [Tworzenie wersji aplikacji](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)  
  
##  <a name="BKMK_Configure"></a>Zaloguj się do programu Visual Studio  
 Po uruchomieniu programu Visual Studio po raz pierwszy, są podane można logować się za pomocą konta Microsoft, takich jak Live lub Outlook. Logowanie umożliwia ustawienia mają być synchronizowane na Twoich urządzeniach. Aby uzyskać więcej informacji, zobacz [rejestrowanie w programie Visual Studio](../ide/signing-in-to-visual-studio.md)  
  
 Rysunek 1: Program Visual Studio IDE  
  
 ![IDE z Visual C &43; &#43; ustawienia stosowane](../ide/media/c--ide_defaultenvironmentlayout.png "IDE_DefaultEnvironmentLayout C ++")  
  
 Po otwarciu programu Visual Studio można wyświetlić trzy podstawowe części IDE: narzędzia systemu windows, menu i pasków narzędzi oraz obszaru głównego okna. Narzędzia systemu windows są zadokowane po lewej i prawej stronie okna aplikacji **Szybkie uruchamianie**, paska menu i standardowym pasku narzędzi u góry. Zawiera środek okna aplikacji **— strona początkowa**. Po otwarciu rozwiązania lub projektu, w tym miejscu są wyświetlane edytory oraz projektantów. Podczas opracowywania aplikacji poświęcany większość czasu w tym obszarze centralnej.  
  
##  <a name="BKMK_CreateApp"></a>Utworzyć prostą aplikację  
 Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projektu i rozwiązania. W tym przykładzie utworzysz aplikacji konsoli systemu Windows.  
  
#### <a name="to-create-a-console-app"></a>Aby utworzyć aplikację konsoli  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     ![Na pasku menu, wybierz plik, nowy, projektu](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")  
  
2.  W **Visual C++** kategorii, wybierz **aplikacji konsoli Win32** szablonu, a następnie nazwę projektu `GreetingsConsoleApp`.  
  
     ![Szablon aplikacji konsoli Win32](../ide/media/c--ide_newprojectdlg.png "IDE_NewProjectDlg C ++")  
     Twoje okno dialogowe może mieć różne opcje, w zależności od tego, czy zostały zainstalowane. Jeśli nie widzisz szablony projektów Visual C++, należy wrócić do poprzedniej strony Instalatora i zainstaluj obciążenia C++.
  
3.  Gdy pojawi się Kreator aplikacji Win32, wybierz **Zakończ** przycisku.  
  
     ![Kreator aplikacji konsoli Win32](../ide/media/c--ide_win32consoleappwizard.png "IDE_Win32ConsoleAppWizard C ++")  
  
 GreetingsConsoleApp projektu i rozwiązania z podstawowych plików w przypadku aplikacji konsoli Win32 są tworzone i ładowane automatycznie do **Eksploratora rozwiązań**. Plik GreetingsConsoleApp.cpp jest otwarty w edytorze kodu. Następujące elementy są wyświetlane w **Eksploratora rozwiązań**:  
  
 Rysunek 4: Elementy projektu  
  
 ![Pliki rozwiązania w Eksploratorze rozwiązań](../ide/media/c--ide_solutioncontents.png "IDE_SolutionContents C ++")  
  
##  <a name="BKMK_AddCode"></a>Dodawanie kodu do aplikacji  
 Następnie można będzie Dodaj kod, aby wyświetlić wyraz "Hello" w oknie konsoli.  
  
#### <a name="to-display-hello-in-the-console-window"></a>Aby wyświetlić "tekst Hello" w oknie konsoli  
  
1.  W pliku GreetingsConsoleApp.cpp wprowadzić pusty wiersz przed wierszem `return 0;` , a następnie wprowadź poniższy kod:  
  
    ```  
    cout << "Hello\n";  
    ```  
  
     Linii o dowolnym kształcie red jest wyświetlany w obszarze `cout`. Komunikat o błędzie pojawia się po wskazaniu go.  
  
     ![Tekst błędu dla cout](../ide/media/c--ide_couterror.png "IDE_CoutError C ++")  
  
     Komunikat o błędzie pojawia się również w **listy błędów** okna. Okno można wyświetlić, wybierając **widoku**, **listy błędów** na pasku menu.  
  
     [Cout](/cpp/standard-library/iostream) znajduje się w \<iostream > pliku nagłówka.  
  
2.  Aby uwzględnić iostream — nagłówek, wprowadź poniższy kod po `#include "stdafx.h"`:  
  
    ```  
    #include <iostream>  
    using namespace std;  
    ```  
  
     Należy zauważyć, jak został wprowadzony kod, zapewniając sugestie dotyczące znaków, które zostały wprowadzone pojawił się pole. To pole jest częścią IntelliSense dla C++, co zapewnia kodowania monitów, w tym listę elementów członkowskich klasy lub interfejsu i informacje o parametrach. Umożliwia także wstawki kodu, które są wstępnie zdefiniowane bloków kodu. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md) i [wstawki kodu](../ide/code-snippets.md).  
  
     Czerwony dowolnym kształcie linii pod `cout` zniknie po naprawieniu błędu.  
  
3.  Zapisz zmiany w pliku.  
  
     ![Kod, który umożliwia naprawienie błędu cout](../ide/media/c--ide_coutfix.png "IDE_CoutFix C ++")  
  
##  <a name="BKMK_DebugTest"></a>Debugowanie i testowanie aplikacji  
 Można debugować GreetingsConsoleApp, aby zobaczyć, czy słowo "Hello" jest wyświetlany w oknie konsoli.  
  
#### <a name="to-debug-the-application"></a>Aby debugować aplikację  
  
-   Uruchom debuger.  
  
     ![Rozpocznij debugowanie polecenia menu debugowania](../ide/media/exploreide-startdebugging.png "ExploreIDE StartDebugging")  
  
     Debuger uruchamia i uruchamia kod. W oknie konsoli (osobnym oknie przypominającą wiersza polecenia) pojawia się na kilka sekund, ale zamyka szybkie, gdy debuger przestanie działać. Aby wyświetlić tekst, należy ustawić punkt przerwania, aby zatrzymać wykonanie programu.  
  
#### <a name="to-add-a-breakpoint"></a>Aby dodać punkt przerwania  
  
1.  Dodaj punkt przerwania z paska menu, w wierszu `return 0;`. Możesz także po prostu kliknąć na lewym marginesie, aby ustawić punkt przerwania.  
  
     ![Przełącz punkt przerwania — polecenie menu debugowania](../ide/media/exploreide-togglebreakpoint.png "togglebreakpoint — ExploreIDE")  
  
     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.  
  
2.  Wybierz klawisz F5, aby rozpocząć debugowania.  
  
     Po uruchomieniu debugera i zostanie wyświetlone okno konsoli przedstawiający wyraz **Hello**.  
  
     ![Tekst w oknie wiersza polecenia systemu Windows Hello](../ide/media/c--ide_hellocommandwindow.png "IDE_HelloCommandWindow C ++")  
  
3.  Naciśnij klawisze SHIFT + F5, aby zatrzymać debugowanie.  
  
 Aby uzyskać więcej informacji, zobacz [projekty startowe](../debugger/debugging-preparation-console-projects.md).  
  
##  <a name="BKMK_BuildRelease"></a>Tworzenie wersji aplikacji  
 Teraz, gdy upewnieniu się, że wszystko działa, można przygotować kompilację wersji aplikacji.  
  
#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Aby wyczyścić pliki rozwiązań i zbudować wersję przeznaczoną do publikacji  
  
1.  Na pasku menu Usuń plików pośrednich i pliki wyjściowe, które zostały utworzone w poprzednich wersjach.  
  
     ![Polecenie Wyczyść rozwiązanie w menu kompilacji](../ide/media/exploreide-cleansolution.png "ExploreIDE CleanSolution")  
  
2.  Zmień konfigurację kompilacji dla GreetingsConsoleApp z **debugowania** do **wersji**.  
  
     ![Tworzenie wersji aplikacji](../ide/media/c--ide_changingbuildtorelease.png "IDE_ChangingBuildtoRelease C ++")  
  
3.  Skompiluj rozwiązanie.  
  
     ![Kompiluj rozwiązanie, polecenie menu kompilacji](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
 Gratulujemy zakończenia instruktażu! Jeśli chcesz poznać więcej przykładów, zobacz [przykłady dotyczące programu Visual Studio](../ide/visual-studio-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą programu Visual Studio IDE dla projektowania aplikacji C++](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)   
 [Wskazówki: Tworzenie prostej aplikacji z Visual C# lub Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)   
 [Wskazówki dotyczące produktywności dla programu Visual Studio](../ide/productivity-tips-for-visual-studio.md)   
 [Przykłady programu Visual Studio](../ide/visual-studio-samples.md)   
 [Wprowadzenie do programowania z użyciem programu Visual Studio](../ide/get-started-developing-with-visual-studio.md)