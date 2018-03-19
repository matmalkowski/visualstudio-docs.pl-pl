---
title: "Tworzenie i uruchamianie testu obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/01/2016
ms.topic: article
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 53bde20393f5acd55295bf106cb35f6f09e68bf3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Wskazówki: Tworzenie i uruchamianie testu obciążenia zawierającego testy jednostkowe

W tym przewodniku tworzenia testu obciążenia zawierającego testy jednostkowe.

W tym przewodniku opisano proces tworzenia i uruchomienie testu obciążenia za pomocą programu Visual Studio Enterprise. Test obciążenia jest kontenerem testów wydajności sieci Web i testów jednostkowych. Nowy Kreator testu obciążenia utworzysz testy obciążenia.

Test obciążenia udostępnia również wiele właściwości środowiska wykonawczego, które można zmodyfikować, aby wygenerować symulacji żądaną obciążenia. W tym przewodniku umożliwia załadować Test Kreator nowego Dodawanie testów jednostkowych do testu obciążenia.

W tym przewodniku będzie wykonać następujące zadania:

-   Tworzenie testu obciążenia, która używa testów jednostkowych.

-   Zmiana niektórych ustawień testu obciążenia.

-   Uruchamianie testu obciążenia.

-   Wykonaj kroki opisane w [wskazówki: tworzenie i uruchomionych testów jednostkowych dla zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) utworzyć prosty biblioteki klas C# zawierającą sieci Web wydajności i obciążenia projekt testowy z niektórych testów jednostkowych w nim.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Tworzenie testu obciążenia zawierającego testy jednostkowe przy użyciu Kreatora nowego testu obciążenia

### <a name="to-start-the-new-load-test-wizard"></a>Aby uruchomić Kreatora nowego testu obciążenia

1.  Otwórz rozwiązanie Bank, który został utworzony w [wskazówki: tworzenie i uruchomionych testów jednostkowych dla zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

2.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązania Bank, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.

     Wyświetla okno dialogowe Dodawanie nowego projektu.

3.  W oknie dialogowym Dodawanie nowego projektu, rozwiń węzeł **Visual C#** i wybierz polecenie **testu**. Z listy szablonów wybierz **wydajności sieci Web i projektu testu obciążenia** i **nazwa** wpisz `BankLoadTest`. Wybierz **OK**.

     BankLoadTest web wydajności i obciążenia projektu testowego jest dodany do rozwiązania.

4.  Otwórz menu skrótów dla BankLoadTest wydajności sieci web i testów obciążenia projektu, wybierz **Dodaj**, a następnie wybierz pozycję **testów obciążenia**.

5.  **Nowy Kreator testu obciążenia** uruchamia.

6.  **Powitalnej** strony **nowy Kreator testu obciążenia** jest pierwszą stroną.

7.  Wybierz **dalej**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Aby edytować ustawienia scenariusza testu obciążenia

1.  W **wprowadź nazwę scenariusza testu obciążenia** polu tekstowym **ScenarioSample**.

     A *scenariusza* mechanizm grupowania. Zawiera zestaw testów i właściwości dla testów pod obciążeniem.

2.  Ustaw **czasu Pomyśl profilu** do `Use normal distribution centered on recorded think times`. Czasów reakcji odpowiadają za czas, który użytkownik może ponder strony sieci Web przed przejściem do następnej strony.

1.  Wybierz **dalej** po zakończeniu.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Aby edytować ustawienia wzorca obciążenia dla scenariusza testu

1.  Wybierz **obciążenia krok**.

    > [!NOTE]
    > Są dostępne dwa typy wzorców obciążenia: stała i kroku. Każdy typ ma swoje funkcje w testów obciążenia, ale na potrzeby tego przewodnika, wybierz **obciążenia krok**.

2.  Ustaw **Start liczba użytkowników** do 10 użytkowników.

3.  Ustaw **czas trwania kroku** do 10 sekund.

4.  Ustaw **krok liczba użytkowników** do 10 użytkowników/kroku.

5.  Ustaw **maksymalna liczba użytkowników** do 100 użytkowników.

6.  Wybierz **dalej**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Wybierz model testu mieszanego dla scenariusza

1.  W obszarze jak należy modelować test mieszany, wybierz **na podstawie całkowitej liczby testów**.

2.  Wybierz **dalej**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Aby dodać do scenariusza testów jednostkowych

1.  Następnym krokiem jest **Dodaj testów obciążenia scenariusza testu i Edytuj test mieszany**.

2.  Wybierz **Dodaj** do wyboru testów.

3.  Testy jednostkowe CreditTest na liście wybierz **dostępne testy** okienko, w której znajduje się lista wszystkich testów wydajności sieci Web i testów jednostkowych w wydajności sieci Web i projektu testu obciążenia.

4.  Wybierz strzałkę, aby dodać CreditTest testu jednostkowego do **wybrane testy** okienka.

5.  Powtórz kroki 3 i 4 dla DebitTest i FreezeAccountTest testów jednostkowych.

6.  Po zakończeniu dodawania testów jednostkowych trzy wybierz **OK**.

     Dostępne są testu mieszanego.

7.  Przesuń suwak w obszarze dystrybucji dla CreditTest nieco z prawej strony, aby dopasować dystrybucji testu. Należy zauważyć, że inne suwaki automatycznie przemieszczać się po lewej stronie, aby dystrybucji pozostaje w skali 100%.

8.  Wybierz **dalej**.

### <a name="to-select-network-mix-for-test-scenario"></a>Aby wybrać mieszany profil sieciowy w scenariuszu testu

1.  Wybierz typ połączenia sieci LAN do dodania do różnych przepustowości sieci.

     Można dodać więcej typów sieci. Za pomocą suwaków Dostosuj dystrybucji testu i wagi.

2.  Wybierz **dalej**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Aby określić komputery, aby monitorować zbiorem liczników podczas testu obciążenia

1.  Wybierz **dalej**.

     Aby uzyskać więcej informacji na temat zestawów liczników, zobacz [Określanie ustawia liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Aby edytować ustawienia uruchamiania dla testu obciążenia

1.  Wybierz **czas trwania testu obciążenia** , a następnie ustaw **Uruchom czas trwania** do 2 minuty w celu *dymu testu* testów obciążenia.

     Podczas tworzenia testów obciążenia jest dobrym rozwiązaniem, aby sprawdzić, czy wszystko jest poprawnie skonfigurowany i uruchomiony, zgodnie z oczekiwaniami, uruchamiając testu obciążenia krótkie, światła. Ten proces jest nazywany *test*.

2.  Wybierz **Zakończ**. Test obciążenia zostanie otwarty w **edytora testu obciążenia**.

## <a name="running-the-load-test"></a>Uruchamianie testu obciążenia
 Po utworzeniu testu obciążenia, uruchom go, aby wyświetlić sposób aplikacji bank odpowiadania na symulacyjnych obciążenia. Podczas testu obciążenia, zobacz **analizatora testu obciążenia** okna.

### <a name="to-run-the-load-test"></a>Aby uruchomić test obciążenia

1.  Z otwartych w teście obciążenia **edytora testu obciążenia**, wybierz zielonego **Uruchom Test** przycisku w pasku narzędzi. Test obciążenia zaczyna działać.

2.  Jeśli symulacji testu przekracza wszelkie progi, ikony wyświetlane w węzłach drzewa sterowania wskazująca na naruszenie progu. Czerwone koło nakładki mieć błędy, ostrzeżenia żółtego trójkąta nakładki. Można znaleźć licznika, który przekroczył próg i wykres go przeciągając ikony na wykresie. Można to zrobić, gdy test jest uruchomiony.

## <a name="see-also"></a>Zobacz także

- [Edytowanie mieszanki testów, aby określić, które testy do scenariusza testów obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Edytowanie wzorców obciążenia w celu modelowania aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa uruchamiania testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)