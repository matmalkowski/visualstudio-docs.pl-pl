---
title: "Przy użyciu wirtualnego wykres aktywności użytkownika dla testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: f7063775f093b08b859343fbc314399d0cc9fdd4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Wskazówki: korzystanie z wykresu działań użytkownika wirtualnego do izolowania problemów

W tym przewodniku dowiesz się, jak za pomocą wirtualnej wykres aktywności użytkownika wykrywać błędy, które wystąpiły dla poszczególnych wirtualnych użytkowników, którzy uruchomili testu obciążenia.

 Wykres aktywności wirtualnego użytkownika umożliwia wizualizacja aktywności wirtualnego użytkownika, który jest skojarzony z testu obciążenia. Każdy wiersz na wykresie reprezentuje wirtualnych użytkownika. Wirtualne wykres aktywności użytkownika zawiera dokładnie co każdego wirtualnego użytkownika było wykonywane podczas testu. Dzięki temu można wyizolować problemy z wydajnością sprawdzając wzorców aktywności użytkownika, wzorce obciążenia skorelowania testy zakończone niepowodzeniem lub wolne i wyświetlania żądań z innych działań wirtualnego użytkownika. Wirtualne wykres aktywności użytkownika jest dostępna tylko po załadowaniu po zakończeniu wykonywania.

 W tym przewodniku będzie wykonać następujące zadania:

-   Dowiedz się, jak za pomocą następujących narzędzi, skojarzone z wirtualnych wykres aktywności użytkownika:

    -   Użyj **Powiększ do okresu czasu** narzędzie do określania na wykresie, które mają być analizowane w określonym przedziale czasu.

    -   Użyj **legendy szczegóły** panelu i **filtrowanie wyników** panelu, aby zastosować filtrowanie do wykresu, aby wyizolować problemy.

-   Użyj wirtualnych wykres aktywności użytkownika do analizowania błąd wystąpił z określonym użytkownikiem wirtualnego i wyświetlić szczegóły typu błędu powodować problemy.

 Aby uzyskać więcej informacji, zobacz [analizowanie wirtualnego działań użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

## <a name="prerequisites"></a>Wymagania wstępne

-   Visual Studio Enterprise

-   Wykonaj następujące procedury:

    -   [Rejestruj i uruchamianie testu wydajności sieci web](http://msdn.microsoft.com/en-us/bd0a82fd-cec0-4861-bc09-e1b0b2d258ef).

    -   [Tworzenie i uruchamianie testu obciążenia](http://msdn.microsoft.com/en-us/7041cbcf-9ab1-4579-98ff-8f296aeaded4)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Otwórz rozwiązanie ColorWebApp utworzony w poprzedniej — wskazówki

### <a name="open-the-solution"></a>Otwórz rozwiązanie

1.  Uruchom program Visual Studio.

2.  Otwórz rozwiązanie ColorWebApp, który zawiera LoadTest1.loadtest. Ta operacja ładowania testów wyników z przeprowadzenie czynności opisane w trzech wskazówki, które są wymienione na początku tego tematu w sekcji wymagania wstępne.

     Pozostałe kroki w tym przewodniku założono aplikacji sieci Web o nazwie ColorWebApp, testów wydajności sieci Web o nazwie ColorWebAppTest.webtest i testu obciążenia o nazwie LoadTest1.loadtest.

## <a name="run-the-load-test"></a>Uruchamianie testu obciążenia
 Uruchom test obciążenia, aby zbierać dane o aktywności wirtualnego użytkownika.

### <a name="run-the-load-test-to-collect-virtual-user-activity-data"></a>Uruchom test obciążenia, aby zbierać dane o aktywności użytkownika wirtualnego

-   W edytorze testu obciążenia, wybierz **Uruchom** przycisk na pasku narzędzi. LoadTest1 zaczyna działać.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Wyizolować problemy z wykres aktywności użytkownika wirtualnego

Po testu obciążenia i zebrane dane o aktywności wirtualnego użytkownika, dane można wyświetlić w wynikach testów obciążenia przy użyciu obciążenia widok szczegółów testu analizatora wykresu aktywności wirtualnego użytkownika. Ponadto można użyć wirtualnych wykres aktywności użytkownika, aby wyizolować problemy z wydajnością w teście obciążenia sieci.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby użyć wirtualnego wykres aktywności użytkownika w wynikach testów obciążenia

1.  Po załadowaniu zakończeniu testu uruchomiony, stronie podsumowania wyników testu obciążenia jest wyświetlana w analizatorze testu obciążenia. Wybierz **wykresy** przycisk na pasku narzędzi.

     Zostanie wyświetlony widok wykresów.

2.  Na **czas odpowiedzi strony** programu graph, kliknij prawym przyciskiem myszy w pobliżu jedną z ikon naruszenie progu i wybierz **przejdź do szczegółów użytkownika**.

    > [!NOTE]
    > Można użyć **szczegóły** przycisk paska narzędzi edytora testu obciążenia do zbyt Otwórz wykres aktywności użytkownika. Jednak jeśli używasz **przejdź do szczegółów użytkownika** opcji wirtualnego wykres aktywności użytkownika będą automatycznie powiększyć część testu, która została kliknięta prawym przyciskiem myszy na wykresie.

     Widok szczegółów zostanie wyświetlony z **wykres aktywności użytkownika wirtualnego** fokus w danym okresie czasu wystąpienia naruszenia progu.

     Na osi y poziomy powierzchni reprezentują poszczególnych wirtualnych użytkowników. Osi x zawiera oś czasu dla uruchomienia testu obciążenia.

3.  W **Powiększ do okresu czasu** narzędzie poniżej **wykres aktywności użytkownika wirtualnego**, dostosować po lewej i prawej suwaki, dopóki oba są blisko ikona naruszenie progu. Spowoduje to zmianę skali czasu w **wykres aktywności użytkownika wirtualnego**

4.  W **legendy szczegóły**, zaznacz pole wyboru dla **(Podświetl błędy)**. Zwróć uwagę, że zostanie wyróżniona wirtualnego użytkownika, który spowodował naruszenie progu.

5.  W **filtrowanie wyników** panelu, usuń zaznaczenie pól wyboru dla **Pokaż wyniki pomyślnie** i **HttpError** , ale pozostawić **ValidationRuleError**zaznaczone pole wyboru.

     **Wykres aktywności użytkownika wirtualnego** wyświetla tylko wirtualnych użytkowników, które poświęciły więcej niż 3 sekundy na stronie Red.aspx określony przez naruszenie progu skonfigurowana w poprzednim przewodniku.

6.  Wskaźnik myszy nad linia pozioma reprezentujący wirtualnego użytkownika z błąd reguły sprawdzania poprawności dla naruszenie progu.

7.  Etykietka narzędzia, która jest wyświetlana z następującymi informacjami:

    -   **Identyfikator użytkownika**

    -   **Scenariusz**

    -   **Test**

    -   **Wynik**

    -   **Sieci**

    -   **Godzina rozpoczęcia**

    -   **Czas trwania**

    -   **Agent**

    -   **Dziennik testu**

8.  Zwróć uwagę, że **Dziennik testu** jest łącze. Wybierz **Dziennik testu** łącza.

9. Otwiera testu wydajności sieci ColorWebTest Web, który jest skojarzony z dziennika w wydajności sieci Web testów Podgląd wyników. Dzięki temu można odizolować, w którym wystąpił naruszenia progu.

     Za pomocą różnych ustawień w obu **legendy szczegóły** i **filtrowanie wyników** panele ułatwiające wyizolowanie wyników problemy z wydajnością i błędy w testów obciążenia. Eksperymentów przy użyciu tych ustawień i **Powiększ do okresu czasu** narzędzia, aby zobaczyć, jak dane użytkownika wirtualnego jest podana w **wykres aktywności użytkownika wirtualnego**.

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md)
- [Porady: Tworzenie ustawień testu dla rozproszonego testu obciążenia](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)