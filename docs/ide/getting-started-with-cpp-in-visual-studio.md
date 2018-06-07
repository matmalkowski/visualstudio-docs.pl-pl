---
title: Wprowadzenie do języka C++ w programie Visual Studio
description: ''
ms.custom: mvc
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
author: corob-msft
ms.author: tglee
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: b49f83813bc5acd64de74a27a025bc78503902c5
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747355"
---
# <a name="get-started-with-c-in-visual-studio"></a>Wprowadzenie do języka C++ w programie Visual Studio

Ukończenie tego przewodnika Szybki Start zapoznać się z wielu narzędzi i oknach dialogowych, których można używać podczas opracowywania aplikacji w języku C++ w programie Visual Studio. Tworzenie "Hello, World" — styl aplikacji konsoli, gdy Dowiedz się więcej o pracy w zintegrowane środowisko programistyczne (IDE).

## <a name="prerequisites"></a>Wymagania wstępne

Nie trzeba znać C++ do ukończenia tego przewodnika Szybki Start, ale należy się zapoznać z programowanie ogólne i debugowanie pojęcia. Dokumentacji programu Visual Studio nie pokazuje, jak program w języku C++. Jest dobrym przewodnik dotyczący C++ materiałów szkoleniowych [wprowadzenie](https://isocpp.org/get-started) strony w witrynie sieci Web ISO C++.

Aby z niego skorzystać, potrzebujesz kopię programu Visual Studio 2017 wersji 15.3 lub nowszy z **tworzenia klasycznych aplikacji w języku C++** obciążenia zainstalowane. Przewodnik szybkiego do instalacji, zobacz [zainstalować obsługi języka C++ w programie Visual Studio](/cpp/build/vscpp-step-0-installation).

## <a name="create-a-console-app"></a>Tworzenie aplikacji konsoli

Jeśli nie jest jeszcze uruchomiona, uruchom program Visual Studio.

![IDE z Visual C&#43; &#43; zastosowane ustawienia](../ide/media/get-started-cpp-ide-layout.png)

Po otwarciu programu Visual Studio można wyświetlić trzy podstawowe części IDE: narzędzia systemu windows, menu i pasków narzędzi oraz obszaru głównego okna. Narzędzia systemu windows są zadokowane po lewej i prawej stronie okna aplikacji. **Szybkie uruchamianie** okno, na pasku menu i narzędzi Standardowy znajdują się u góry. Zawiera środek okna **— strona początkowa**. Po otwarciu rozwiązania lub projektu, w tym miejscu są wyświetlane edytory oraz projektantów. Podczas opracowywania aplikacji, większość czasu jest spędzana w tym obszarze centralnej.

Visual Studio będzie korzystać *projekty* organizowania kodu dla aplikacji i *rozwiązań* do organizowania projektów. Projekt zawiera wszystkie opcje, konfiguracji i reguły służące do tworzenia aplikacji. Umożliwia także zarządzanie relacji między plików wszystkich projektów i pliki zewnętrzne. Aby utworzyć aplikację, najpierw należy utworzyć nowy projekt i rozwiązanie.

### <a name="to-create-a-console-app-project"></a>Aby utworzyć projekt aplikacji konsoli

1. Na pasku menu wybierz **Plik > Nowy > Projekt** otworzyć **nowy projekt** okno dialogowe.

   ![Na pasku menu, wybierz Plik > Nowy > Projekt](../ide/media/get-started-cpp-file-new-project-menu.png)

1. W **nowy projekt** okno dialogowe, wybierz opcję **zainstalowana > Visual C++** Jeśli nie została już wybrana. W środkowym okienku wybierz **aplikacji konsoli systemu Windows** szablonu. W **nazwa** pole edycji, wprowadź *HelloApp*.

   ![Utwórz projekt aplikacji przy użyciu okna dialogowego Nowy projekt](../ide/media/get-started-cpp-new-project-dialog.png)

   Twoje okno dialogowe może mieć różne opcje, w zależności od obciążeń programu Visual Studio i składników, które zostały zainstalowane. Jeśli nie widzisz szablony projektów Visual C++, musisz ponownie uruchomić Instalatora programu Visual Studio i zainstaluj **tworzenia klasycznych aplikacji w języku C++** obciążenia. Można to zrobić bezpośrednio z **nowy projekt** okna dialogowego. Aby uruchomić Instalatora, wybierz **Otwórz Instalator programu Visual Studio** łącze w oknie dialogowym.

1. Wybierz **OK** przycisk, aby utworzyć projekt aplikacji i rozwiązań.

   HelloApp projektu i rozwiązania z podstawowych plików aplikacji konsoli systemu Windows są tworzone i ładowane automatycznie do **Eksploratora rozwiązań**. *HelloApp.cpp* plik jest otwarty w edytorze kodu. Te elementy są wyświetlane w **Eksploratora rozwiązań**:

   ![Pliki rozwiązania w Eksploratorze rozwiązań](../ide/media/get-started-cpp-solution-explorer.png)

## <a name="add-code-to-the-app"></a>Dodawanie kodu do aplikacji

Następnie dodaj kod, aby wyświetlić wyraz "Hello" w oknie konsoli.

### <a name="to-edit-code-in-the-editor"></a>Aby edytować kodu w edytorze

1. W *HelloApp.cpp* plików, należy wprowadzić pusty wiersz przed wierszem `return 0;` , a następnie wprowadź ten kod:

   ```cpp
   cout << "Hello\n";
   ```

   Linii o dowolnym kształcie red jest wyświetlany w obszarze `cout`. Jeśli wskaźnik znajduje się nad nim, zostanie wyświetlony komunikat o błędzie.

   ![Tekst błędu dla cout](../ide/media/get-started-cpp-intellisense-error.png)

   Komunikat o błędzie pojawia się również w **listy błędów** okna. To okno można wyświetlić, wybierając **Widok > listy błędów** na pasku menu.

   ![Błąd w oknie Lista błędów](../ide/media/get-started-cpp-error-list.png)

   Brak deklaracji dla kodu [std::cout](/cpp/standard-library/iostream), który znajduje się w  *\<iostream >* pliku nagłówka.

1. Aby uwzględnić *iostream* nagłówka, wprowadź ten kod po `#include "stdafx.h"`:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Należy zauważyć, jak został wprowadzony kod pojawił się pole. To pole zawiera automatycznego uzupełniania sugestie dotyczące znaków, które należy wprowadzić. Tego część IntelliSense dla C++, która zapewnia kodowania monitów, w tym elementów członkowskich klasy lub interfejsu i informacje o parametrach. Umożliwia także wstawki kodu, które są wstępnie zdefiniowane bloków kodu. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md) i [wstawki kodu](../ide/code-snippets.md).

   ![Stałe kodu w edytorze](../ide/media/get-started-cpp-cout-fix.png)

   Czerwony dowolnym kształcie linii pod `cout` zniknie po naprawieniu błędu.

1. Aby zapisać zmiany w pliku, naciśnij klawisz **Ctrl + S**.

## <a name="build-the-app"></a>Tworzenie aplikacji

Jest łatwy do kompilacji kodu. Na pasku menu wybierz **kompilacji > Kompiluj rozwiązanie**. Visual Studio tworzy rozwiązanie HelloApp, a raporty postępu w **dane wyjściowe** okna.

   ![Skompiluj rozwiązanie HelloApp](../ide/media/get-started-cpp-build-solution.gif)

## <a name="debug-and-test-the-app"></a>Debugowanie i testowanie aplikacji

Można debugować HelloApp, aby zobaczyć, czy słowo "Hello" jest wyświetlany w oknie konsoli.

### <a name="to-debug-the-app"></a>Do debugowania aplikacji

Można uruchomić debugera, wybierz **Debuguj > Rozpocznij debugowanie** na pasku menu.

![Rozpocznij debugowanie polecenia menu debugowania](../ide/media/get-started-cpp-start-debugging-menu.png)

Debuger uruchamia i uruchamia kod. W oknie konsoli (osobnym oknie przypominającą wiersza polecenia) pojawia się na kilka sekund, ale zamyka szybkie, gdy debuger przestanie działać. Aby wyświetlić tekst, należy ustawić punkt przerwania, aby zatrzymać wykonanie programu.

### <a name="to-add-a-breakpoint"></a>Aby dodać punkt przerwania

1. W edytorze, umieść kursor w wierszu `return 0;`. Na pasku menu wybierz **Debuguj > Przełącz punkt przerwania**. Możesz również kliknąć na lewym marginesie, aby ustawić punkt przerwania.

     ![Przełącz punkt przerwania — polecenie menu debugowania](../ide/media/get-started-cpp-toggle-breakpoint-menu.png)

     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

     ![Wskazane okno margines punktu przerwania](../ide/media/get-started-cpp-breakpoint-set.png)

1. Aby rozpocząć debugowanie, naciśnij klawisz **F5**.

   Po uruchomieniu debugera i zostanie wyświetlone okno konsoli przedstawiający wyraz **Hello**.

   ![Witaj tekst w oknie konsoli](../ide/media/get-started-cpp-helloapp-window.png)

1. Aby zatrzymać debugowanie, naciśnij klawisz **Shift + F5**.

Aby uzyskać więcej informacji na temat debugowania projektu konsoli, zobacz [konsoli projekty](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Tworzenie wersji aplikacji

Teraz, gdy upewnieniu się, że wszystko działa, można przygotować kompilację wersji aplikacji. Wersja kompilacji pozostaw informacji o debugowaniu i opcje optymalizacji kompilatora używany do tworzenia mniejszy, szybszy kodu.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Aby wyczyścić pliki rozwiązań i zbudować wersję przeznaczoną do publikacji

1. Na pasku menu wybierz **kompilacji > Wyczyść rozwiązanie** do usuwania plików pośrednich i pliki wyjściowe, które zostały utworzone w poprzednich wersjach.

   ![Polecenie Wyczyść rozwiązanie w menu kompilacji](../ide/media/get-started-cpp-clean-solution-menu.png)

1. Aby zmienić konfigurację rozwiązania HelloApp z **debugowania** do **wersji**, na pasku narzędzi wybierz z listy rozwijanej w formancie konfiguracje rozwiązania, a następnie wybierz pozycję **wersji**.

   ![Tworzenie dystrybucyjnej wersji tej aplikacji](../ide/media/get-started-cpp-set-release-configuration.png)

1. Skompiluj rozwiązanie. Na pasku menu wybierz **kompilacji > Kompiluj rozwiązanie**.

Po zakończeniu tej kompilacji, po utworzeniu aplikacji, które mogą kopiować i uruchamiać w dowolnym oknie wiersza polecenia. Nie może wykonać znacznie, ale jest bramy do elementów większa.

Gratulujemy Kończenie pracy tego przewodnika Szybki Start! Jeśli chcesz poznać więcej przykładów, zobacz [przykłady programu Visual Studio](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Zobacz także

- [Do tworzenia klasycznych aplikacji C++ za pomocą środowiska IDE programu Visual Studio](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)
- [Wskazówki: Tworzenie prostej aplikacji w języku C# lub Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)
- [Wskazówki dotyczące produktywności dla programu Visual Studio](../ide/productivity-tips-for-visual-studio.md)
