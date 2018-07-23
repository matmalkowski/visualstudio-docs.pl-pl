---
title: Analizowanie aktywności wirtualnego użytkownika testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 20367c2632e62d53199ee7bc1a522b81b570070e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178508"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Porady: analizowanie, co robią użytkownicy wirtualni podczas testu obciążenia za pomocą wykresu aktywności wirtualnego użytkownika

Wyświetl aktywność wirtualnego użytkownika, która jest skojarzona z testu obciążenia za pomocą wykresu wirtualnego aktywności użytkownika. Każdy wiersz na wykresie reprezentuje poszczególnych użytkowników wirtualnych. Wykres aktywności wirtualnych użytkowników zawiera dokładnie co każdy użytkownik wirtualny był wykonywany podczas testu. Można widać wzorce aktywności użytkowników, wzorce obciążenia, korelowanie testy zakończone niepowodzeniem lub wolne i zobacz żądań z innych działań wirtualnego użytkownika. Wykres aktywności wirtualnych użytkowników jest dostępna tylko wtedy, gdy test obciążenia zakończył działanie.

Poniższe procedury pokazują, jak wyświetlać wykres aktywności wirtualnych użytkowników, jak Zbadaj działania konkretnego użytkownika oraz sposobu korzystania z filtrowania.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby wyświetlić wykres aktywności wirtualnych użytkowników w wyniki testu obciążenia

1.  Aby wyświetlić dane użytkowników wirtualnych, należy najpierw skonfigurować **wszystkie szczegółowe dane** ustawienie **przechowywanie informacji** właściwość, która jest skojarzona z testu obciążenia. Następnie uruchom test obciążenia. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie zbierania szczegółowych informacji umożliwiających Włączanie wykres aktywności wirtualnych użytkowników](../test/how-to-configure-load-tests-to-collect-full-details.md).

2.  Po załadowaniu usługi przebiegów testów, zostanie wyświetlona strona podsumowania wyników testu. Wybierz **szczegółów użytkownika** przycisk na pasku narzędzi.

     —lub—

     Otwórz widok wykresów, wybierając **wykresów** przycisk na pasku narzędzi. Kliknij prawym przyciskiem myszy wykres, a następnie wybierz pozycję **przejdź do szczegółów użytkownika**.

     Jeśli używasz tej opcji, wykres aktywności wirtualnych użytkowników będzie automatycznego powiększania części testu, który kliknięcia. Na przykład, jeśli wskaźnik myszy znajduje się na około 30 drugim znaku, widok szczegółów wyświetli około na 30 drugim znaku w **Powiększ do okresu czasu** narzędzie u dołu wykresu wirtualnego aktywności użytkownika.

     Następnie można zbadać szczegóły działań określonych użytkowników, w wykres aktywności wirtualnych użytkowników.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Aby zbadać określonych użytkowników w wykres aktywności wirtualnych użytkowników

1.  Użyj powiększenia do narzędzia okresu czasu w dolnej części wykres aktywności wirtualnych użytkowników, aby wybrać obszar na wykresie, w którym chcesz zbadać szczegółowe informacje na temat określonego użytkownika.

2.  Umieść kursor myszy szczegółów na wykresie. Zwróć uwagę, że w etykietce narzędzia są wyświetlane następujące informacje:

    -   **Identyfikator użytkownika**

    -   **Scenariusz**

    -   **Test**

    -   **Adres URL** (nie jest wyświetlane w testowej lub transakcji)

    -   **Wynik**

    -   **Przeglądarka** (nie jest wyświetlane w testowej lub transakcji)

    -   **Sieci**

    -   **Godzina rozpoczęcia**

    -   **Czas trwania**

    -   **Agent**

    -   **Dziennik testu** (łącze do dziennika testu)

        > [!NOTE]
        > Aby pomóc w debugowaniu aplikacji, jeśli wybierzesz łącze dziennika testu, otworzy się wynik testu sieci web lub wyniku testu jednostkowego skojarzone z dziennika.

     Następnie można użyć operacje filtrowania i wyróżniania, które muszą być dostępne w wykres aktywności wirtualnych użytkowników.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Aby użyć opcji filtrowania w wykres aktywności wirtualnych użytkowników

1.  W legendzie szczegółowe informacje, użyj listy rozwijanej, aby wybrać albo **testu**, **strony**, lub **transakcji**.

     **Legenda szczegółów — panel**

     ![Legenda szczegółów — panel](../test/media/ltest_detailslegend.png)

2.  Zaznacz lub wyczyść pola wyboru dla błędów, dzienniki, testy, wyszukiwania i stron aspx, które są skojarzone z testu obciążenia.

     Wykres aktywności wirtualnych użytkowników odpowiednio aktualizowany.

     Wykres aktywności wirtualnych użytkowników umożliwia filtrowanie testy, strony i transakcje na podstawie kilku różnych kryteriów. Można usunąć niektórych testów w widoku lub Usuń wszystkie testy zakończone powodzeniem i usuwać testy, które nie powiodło się z pewnych błędów. Można również usunąć wszystkie testy, które nie mają dzienniki.

     Na przykład, możesz wybrać **(Podświetl błędy)** opcja, która wyświetla wszystkie błędy na koszyka pokolorowane w kolorze czerwonym. Możesz również wybrać **(Podświetl wyniki z dziennikami)** opcja, która wyświetla wszystkie wyniki testów, które mają dzienniki pokolorowane w kolorze zielonym na wykresie.

     **Panel wyników filtrowania**

     ![Panel wyników filtrowania](../test/media/ltest_filterresults.png)

3.  W wynikach filtrowania zaznacz lub wyczyść pola wyboru dla następujących opcji filtrowania:

    -   **Pokaż tylko wyniki z dziennikami** wyświetla tylko wyniki, które mają dzienniki testów skojarzonych z nimi.

    -   **Pokaż pomyślne wyniki** Wyświetla pomyślne wyniki.

    -   **Pokaż wyniki z błędami** wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

        > [!NOTE]
        > Lista typów błędów, które są wyświetlane w obszarze **Pokaż wyniki z błędami** węzła może dalszego zbadania, wybierając przycisk tabele w **podglądu wyników testu wydajności sieci Web** paska narzędzi. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     Wykres aktywności wirtualnych użytkowników odpowiednio aktualizowany.

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Przewodnik: Używanie wykresu aktywności wirtualnego użytkownika umożliwiającego Wyizolowanie problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)