---
title: Utwórz wydajności sieci web i projektu testu obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: dbd89b92ec3ca5059fbbf91680db660825cdec8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-create-a-load-test-project"></a>Szybki Start: Tworzenie projektu testu obciążenia

W tym szybkiego startu 10 minut dowiesz się, jak do tworzenia i uruchamiania wydajności sieci Web i projektu testu obciążenia w programie Visual Studio. Wydajności sieci Web lub testów jednostkowych, aby symulować wielu użytkowników, dostęp do serwera w tym samym czasie uruchamiać testów obciążenia.

> [!IMPORTANT]
> Projekty testowe wydajności i obciążenia sieci Web są dostępne tylko w wersji Enterprise programu Visual Studio 2017 r.

## <a name="install-the-load-testing-component"></a>Zainstaluj składnik testowania obciążenia

Jeśli jeszcze nie masz wydajności sieci Web i obciążenia zainstalowany składnik narzędzia do testowania, musisz zainstalować go za pośrednictwem Instalator programu Visual Studio.

1. Otwórz Instalator programu Visual Studio z menu Start systemu Windows. Można także używać go w programie Visual Studio z **nowy projekt** okno dialogowe, lub wybierając **narzędzia** > **Pobierz narzędzia i funkcje...**  na pasku menu.

1. Instalator programu Visual Studio, wybierz **pojedynczych składników** karcie, a następnie przewiń w dół do **debugowania i testowania** sekcji. Wybierz **wydajności sieci Web i narzędzia do testowania obciążenia**.

   ![Wydajności sieci Web i składnika narzędzia do testowania obciążenia](media/web-perf-load-testing-tools-component.png)

1. Wybierz **Modyfikuj** przycisku.

   Zainstalowano wydajności sieci Web i składnika narzędzia do testowania obciążenia.

## <a name="create-a-load-test-project"></a>Tworzenie projektu testu obciążenia

W tej sekcji utworzymy projektu testu obciążenia C#. Można również tworzenie projektu testu obciążenia Visual Basic, jeśli wolisz.

1. Otwórz program Visual Studio i wybierz polecenie **pliku** > **nowy** > **projektu...**  na pasku menu.

   **Nowy projekt** zostanie otwarte okno dialogowe.

1. W **nowy projekt** okna dialogowego rozwiń **zainstalowana** i **Visual C#**, a następnie wybierz **testu** kategorii. Wybierz **wydajności sieci Web i projektu testu obciążenia** szablonu.

   ![Wydajności sieci Web i testów obciążenia szablonu projektu](media/web-perf-load-test-project-template.png)

1. Wprowadź nazwę projektu, jeśli nie chcesz użyć nazwy domyślnej, a następnie wybierz **OK**.

   Visual Studio tworzy projekt i wyświetla pliki w **Eksploratora rozwiązań**. Projekt zawiera początkowo jeden plik testu sieci Web o nazwie *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Dodaj do projektu testu obciążenia

1. Po kliknięciu prawym przyciskiem lub menu kontekstowego węzła projektu w **Eksploratora rozwiązań**, wybierz **Dodaj** > **testu obciążenia...** .

   **Nowy Kreator testu obciążenia** otwiera.

1. Wybierz **testu obciążenia lokalnej** opcji, a następnie wybierz pozycję **dalej**. Dowiedz się więcej na temat testowania obciążenia opartego na chmurze [tutaj](/vsts/load-test/get-started-simple-cloud-load-test).

   ![Nowy Kreator testu obciążenia — pierwsza strona](media/load-test-wizard-page-1.png)

1. Wybierz **dalej** kroków kreatora aż **Dodaj testy do scenariusza testu obciążenia i Edytuj zestaw testów** strony. Wybierz **Dodaj** przycisku.

   **Dodaj testy** zostanie otwarte okno dialogowe.

1. W obszarze **dostępne testy**, wybierz pozycję **WebTest1**, a następnie wybierz przycisk strzałki w prawo, aby przenieść ją do **wybrane testy** pole. Wybierz **OK** przycisku.

   ![Dodawanie testów, okno dialogowe](media/add-tests-dialog-box.png)

1. W **nowy Kreator testu obciążenia**, wybierz **Zakończ** przycisku.

   Test obciążenia jest dodawane do projektu i otwiera plik testu obciążenia w oknie edytora.

## <a name="run-the-load-test"></a>Uruchamianie testu obciążenia

Utworzyliśmy testu obciążenia nie są bardzo podobne, ale umożliwia uruchamianie mimo to.

Kliknij prawym przyciskiem myszy menu lub menu kontekstowego, który jest otwarty w edytorze testu obciążenia wybierz **uruchomienia testu obciążenia**.

![Uruchom menu Test obciążenia](media/run-load-test.png)

Test obciążenia zacznie działać. **Wyników testu** Pokazuje okno testu jest w toku, czy analizatora testu obciążenia jest wyświetlany w oknie edytora. Po zakończeniu testu, który powinien być pięć minut, jeśli zaakceptować wartości domyślne, podsumowanie jest pokazywane w edytorze. Możesz wybrać **wykresy**, **tabel**, lub **szczegółów** uzyskać różne informacje o wynikach testu obciążenia.

![Okna analizatora testu obciążenia](media/load-test-analyzer.png)

## <a name="next-steps"></a>Następne kroki

Teraz, po utworzeniu projektu testu obciążenia proste, następnym krokiem jest konfigurowanie scenariuszach zbiorów liczników i parametrów uruchomieniowych.

> [!div class="nextstepaction"]
> [Edytuj ustawienia testu](edit-load-tests.md)