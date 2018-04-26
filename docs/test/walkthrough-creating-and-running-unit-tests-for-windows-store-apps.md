---
title: Tworzenie i Uruchamianie testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 4de04bcd612c11f2b739fbdb1521008a45a3aead
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows

Visual Studio obsługuje testowania aplikacji systemu Windows platformy Uniwersalnej jednostek. Zawiera szablony projektów testów jednostkowych dla języka Visual C#, Visual Basic i Visual C++.

> [!TIP]
> Aby uzyskać więcej informacji dotyczących tworzenia aplikacji platformy uniwersalnej systemu Windows, zobacz [wprowadzenie do aplikacji platformy UWP](/windows/uwp/get-started/).

W poniższych procedurach opisano kroki tworzenia, uruchamiania i debugowania testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Tworzenie projektu testu jednostkowego dla aplikacji platformy uniwersalnej systemu Windows

1.  Z **pliku** menu, wybierz **nowy projekt**.

     Wyświetla okno dialogowe Nowy projekt.

2.  W obszarze Szablony wybierz język programowania do tworzenia testów jednostkowych w, a następnie wybierz, czy biblioteki testowej, która skojarzona jednostka uniwersalnych systemu Windows. Na przykład wybrać **Visual C#** , a następnie wybierz **uniwersalnych systemu Windows**, a następnie wybierz pozycję **Biblioteka testów jednostkowych (uniwersalna systemu Windows)**.

3.  (Opcjonalnie) W **nazwa** pole tekstowe, wprowadź nazwę, którego chcesz użyć dla projektu.

4.  (Opcjonalnie) Zmodyfikuj ścieżkę, w której chcesz utworzyć projekt, wprowadzając go w **lokalizacji** pole tekstowe, lub wybierając **Przeglądaj** przycisku.

5.  (Opcjonalnie) W **rozwiązania** Nazwa pola tekstowego, wprowadź nazwę, że chcesz użyć dla rozwiązania.

6.  Pozostaw **Utwórz katalog rozwiązania** opcja wybrana i wybierz **OK** przycisku.

     ![Biblioteka testów jednostkowych dostosowane](../test/media/unit_test_win8_1.png "Unit_Test_Win8_1")

     Eksplorator rozwiązań jest wypełniana jednostkowy projekt testowy platformy uniwersalnej systemu Windows i edytora kodu wyświetla zatytułowany UnitTest1 testu jednostkowego domyślne.

     ![Nowe dopasowane jednostkowy projekt testowy](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Edytowanie pliku manifestu aplikacji platformy uniwersalnej systemu Windows jednostkowy projekt testowy

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *Package.appxmanifest* plik i wybierz polecenie **Otwórz**.

     Projektant manifestu Wyświetla do edycji.

2.  W Projektancie manifestu wybierz **możliwości** kartę.

3.  Na liście w obszarze **możliwości**, wybierz możliwości należy z testu jednostkowego i kod ten test, aby mieć. Na przykład wybierz **Internet** pole wyboru, jeśli wymaga testu jednostkowego i kod jest testowania muszą mieć możliwość uzyskania dostępu do Internetu.

    > [!NOTE]
    > Możliwości wybranej powinien zawierać możliwości, które są niezbędne dla testu jednostkowego do poprawnego działania.

     ![Manifest testów jednostkowych](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Kod testu jednostkowego dla aplikacji platformy uniwersalnej systemu Windows

W edytorze kodu edytowanie testu jednostkowego i Dodaj potwierdzeń i logiki wymagane dla testu.

## <a name="run-unit-tests"></a>Uruchom testy jednostkowe

### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Aby skompilować rozwiązanie i uruchamianie testu jednostkowego za pomocą Eksploratora testów

1.  Na **testu** menu, wybierz **Windows**, a następnie wybierz pozycję **Eksploratora testów**.

     Testowanie Explorer wyświetla bez testu są wymienione.

2.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

     Znajduje się teraz z testu jednostkowego.

    > [!NOTE]
    > Należy utworzyć rozwiązanie, aby zaktualizować listę testów jednostkowych w Eksploratorze testów.

3.  W Eksploratorze testów wybierz testu jednostkowego, który został utworzony.

    > [!TIP]
    > Eksplorator testów Link do kodu źródłowego obok **źródła:**.

4.  Wybierz **uruchomić wszystkie**.

     ![Eksplorator testów jednostkowych &#45; Uruchamianie testu jednostkowego](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

    > [!TIP]
    > Możesz wybrać jeden lub więcej testów jednostkowych wymienionych w Eksploratorze i kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom wybrane testy**.
    >
    > Ponadto istnieje możliwość **Debuguj zaznaczone testy**, **Otwórz testu**i użyj **właściwości** opcji.
    >
    > ![Unit Test Explorer &#45; uni test context menu](../test/media/unit_test_win8_unittestexplorer_contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

    Jednostka uruchomień testów. Po zakończeniu Eksploratora testów Wyświetla stan testów, czas, który upłynął oraz link do źródła.

    ![Eksplorator testów jednostkowych &#45; test ukończony](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Zobacz także

- [Testowanie aplikacji platformy UWP za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)
- [Tworzenie i testowanie aplikacji platformy uniwersalnej systemu Windows](/vsts/build-release/apps/windows/universal?tabs=vsts)
