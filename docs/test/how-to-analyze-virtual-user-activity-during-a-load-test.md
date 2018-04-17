---
title: Analizowanie aktywności wirtualnego użytkownika testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 3688b49a5e16d52ee569afe94569a705ead7f99c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Porady: analizowanie, co robią użytkownicy wirtualni podczas testu obciążenia za pomocą wykresu aktywności wirtualnego użytkownika

Wyświetl aktywności wirtualnego użytkownika, który został skojarzony z testu obciążenia za pomocą wirtualnej wykres aktywności użytkownika. Każdy wiersz na wykresie reprezentuje wirtualnych użytkownika. Wirtualne wykres aktywności użytkownika zawiera dokładnie co każdego wirtualnego użytkownika było wykonywane podczas testu. Można wyświetlić wzorców aktywności użytkownika, wzorce obciążenia, skorelowania testy zakończone niepowodzeniem lub wolne i zobacz żądań z innych działań wirtualnego użytkownika. Wykres aktywności wirtualnego użytkownika jest dostępna tylko po zakończeniu testu obciążenia.

Poniższe procedury pokazują sposób wyświetlania wirtualnego wykres aktywności użytkownika, jak Zbadaj działania konkretnego użytkownika i sposobu korzystania z filtrowania.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby wyświetlić wirtualnego wykres aktywności użytkownika w wynikach testów obciążenia

1.  Aby wyświetlić dane wirtualnego użytkownika, należy najpierw skonfigurować **wszystkie szczegóły poszczególnych** ustawienie **magazynowania szczegółów chronometrażu** właściwość, która jest skojarzona z testu obciążenia. Następnie uruchom test obciążenia. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie zbierania szczegółowych informacji umożliwiających włączyć wirtualnego wykres aktywności użytkownika](../test/how-to-configure-load-tests-to-collect-full-details.md).

2.  Po obciążenia uruchomień testów, zostanie wyświetlona strona podsumowania wyników testu. Wybierz **szczegółów użytkownika** przycisk na pasku narzędzi.

     —lub—

     Otwórz widok wykresy, wybierając **wykresy** przycisk na pasku narzędzi. Kliknij prawym przyciskiem myszy wykres, a następnie wybierz **przejdź do szczegółów użytkownika**.

     Użycie tej opcji, wirtualnych wykres aktywności użytkownika zostanie automatycznie powiększenia do części klikniętej testu. Na przykład, gdy wskaźnik myszy znajduje się na około 30 drugi znacznik, szczegółów zostaną wyświetlone około na 30 drugi znacznik w **Powiększ do okresu czasu** narzędzia w dolnej części wykresu aktywności wirtualnego użytkownika.

     Następnie można zbadać szczegóły aktywności określonych użytkowników, w wirtualnej wykres aktywności użytkownika.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Do sprawdzania, czy działanie określonych użytkowników, na wykresie działań wirtualnego użytkownika

1.  Użyj powiększenia do narzędzia okresu czasu w dolnej części wirtualnego wykres aktywności użytkownika, aby wybrać obszar wykresu, w którym chcesz zbadać szczegóły dotyczące określonego użytkownika.

2.  Umieść kursor myszy nad szczegółów na wykresie. Zwróć uwagę, że w etykietce narzędzia są wyświetlane następujące informacje:

    -   **Identyfikator użytkownika**

    -   **Scenariusz**

    -   **Test**

    -   **Adres URL** (nie wyświetla na liście testu lub transakcji)

    -   **Wynik**

    -   **Przeglądarka** (nie wyświetla na liście testu lub transakcji)

    -   **Sieci**

    -   **Godzina rozpoczęcia**

    -   **Czas trwania**

    -   **Agent**

    -   **Dziennik testu** (łącze do Dziennik testu)

        > [!NOTE]
        > Aby pomóc w debugowaniu aplikacji, po wybraniu łącza Dziennik testu, zostanie otwarte wyniku testu sieci Web lub wyniku testu jednostkowego skojarzone z dziennika.

     Następnie można użyć dostępne operacje filtrowania i wyróżnienia na wykresie działań wirtualnego użytkownika.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Aby użyć opcji filtrowania na wykresie działań wirtualnego użytkownika

1.  W legendzie szczegółowe informacje, należy użyć listy rozwijanej możesz wybrać opcję **testu**, **strony**, lub **transakcji**.

     **Panel szczegółów legendy**

     ![Panel szczegółów legendy](../test/media/ltest_detailslegend.png "LTest_DetailsLegend")

2.  Zaznacz lub usuń zaznaczenie pól wyboru dla błędów, dzienniki, testy, wyszukiwanie i strony aspx, które są skojarzone z testu obciążenia.

     Wykres aktywności wirtualnego użytkownika odpowiednio aktualizowany.

     Wirtualne wykres aktywności użytkownika umożliwia filtrowanie testów, strony i transakcji dla kilku różnych kryteriów. Można usunąć niektórych testów z widoku, lub Usuń wszystkie testy pomyślne lub usunąć testy, których nie powiodła się z niektórych błędów. Można również usunąć wszystkie testy, które nie mają dzienników.

     Na przykład można wybrać **(Podświetl błędy)** opcja, która wyświetla wszystkie błędy na koszyka pokolorowane kolorem czerwonym. Możesz też wybrać **(Podświetl wyniki z dziennikami)** opcja, która wyświetla wszystkie wyniki testów, które mają dzienniki pokolorowane na zielono na wykresie.

     **Panel wyników filtru**

     ![Filtrowanie wyników panel](../test/media/ltest_filterresults.png "LTest_FilterResults")

3.  W wynikach filtrowania wybierz lub wyczyść pola wyboru dla następujących opcji filtrowania:

    -   **Pokaż tylko wyniki z dziennikami** wyświetla tylko wyniki mających dzienników testu skojarzonych z nimi.

    -   **Pokaż wyniki pomyślnie** wyświetla wyniki powiodło się.

    -   **Pokaż wyniki z błędami** wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

        > [!NOTE]
        > Lista typów błędów, które są wymienione w obszarze **Pokaż wyniki z błędami** węzła można dalszego zbadania, wybierając przycisk tabele w pasku narzędzi przeglądarki wyników testu wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     Wykres aktywności wirtualnego użytkownika odpowiednio aktualizowany.

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Wskazówki: Używanie wykres aktywności użytkownika wirtualnego do izolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)