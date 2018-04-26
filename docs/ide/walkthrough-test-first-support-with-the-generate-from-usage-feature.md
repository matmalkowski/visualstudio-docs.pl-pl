---
title: 'Wskazówki: Wcześniejsze testowanie Programowanie przy użyciu funkcji generowania z użycia'
ms.date: 10/09/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd970f9de33b3fffa542360c7f866de1c836a1d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Wskazówki: Wcześniejsze testowanie Programowanie przy użyciu funkcji generowania z użycia

W tym temacie przedstawiono sposób użycia [Generowanie z użycia](../ide/visual-csharp-intellisense.md#generate-from-usage) funkcji, która obsługuje programowanie pierwszego testu.

 *Wcześniejsze testowanie programowanie* jest podejście do projektowania oprogramowania, w którym najpierw zapisać testy jednostkowe oparte na specyfikacje produktów, a następnie wpisz kod źródłowy, który jest wymagana do udostępnienia testów powiodło się. Program Visual Studio obsługuje programowanie pierwszego testu przez generowanie nowych typów i członków w kodzie źródłowym, gdy najpierw odwołuje się je z przypadków testowych, zanim nie zostaną zdefiniowane.

 Program Visual Studio generuje nowych typów i członków z minimalnym przerwania do przepływu pracy. Możesz utworzyć klas zastępczych dla typów, metody, właściwości, pola lub konstruktory bez opuszczania bieżącej lokalizacji w kodzie. Po otwarciu okno dialogowe umożliwia określenie opcji typu generacji fokus natychmiast zwraca do bieżącego otwartego pliku, po zamknięciu okna dialogowego.

 Funkcja generowania z użycia może być używana z platform testów, które integrują się z programem Visual Studio. W tym temacie przedstawiono Framework testów jednostkowych firmy Microsoft.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Tworzenie projektu biblioteki klas systemu Windows i Projekt testowy

1.  W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], Utwórz nową **biblioteki klas Windows** projektu. Nadaj mu nazwę `GFUDemo_VB` lub `GFUDemo_CS`, w zależności od języka, w którym są używane.

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy ikonę rozwiązania u góry, wybierz **Dodaj**, a następnie wybierz pozycję **nowy projekt**. W lewym okienku **nowy projekt** oknie dialogowym wybierz **testu**.

3.  W środkowym okienku wybierz **jednostkowy projekt testowy** i zaakceptuj domyślną nazwę UnitTestProject1. Na poniższej ilustracji przedstawiono okno dialogowe, gdy pojawi się on w [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], okno dialogowe wygląda podobnie.

     ![Okno dialogowe nowego projektu testowego](../ide/media/newproject_test.png "NewProject_Test")

4.  Wybierz **OK** zamknąć **nowy projekt** okno dialogowe.

### <a name="to-add-a-reference-to-the-class-library-project"></a>Aby dodać odwołanie do projektu biblioteki klas

1.  W **Eksploratora rozwiązań**, w obszarze urządzenia projekt testowy, kliknij prawym przyciskiem myszy **odwołania** wejścia i wybierz polecenie **Dodaj odwołanie**.

2.  W **Menedżera odwołań** okno dialogowe, wybierz opcję **projektów** , a następnie wybierz projektu biblioteki klas.

3.  Wybierz **OK** zamknąć **Menedżera odwołań** okno dialogowe.

4.  Zapisz swoje rozwiązanie. Teraz można przystąpić do rozpoczęcia pisania testów.

### <a name="to-generate-a-new-class-from-a-unit-test"></a>Aby wygenerować nową klasę z testu jednostkowego

1.  Projekt testowy zawiera plik o nazwie UnitTest1. Kliknij dwukrotnie ten plik w **Eksploratora rozwiązań** aby otworzyć go w edytorze kodu. Wygenerowano testu klasy i metody testowej.

2.  Znajdź w deklaracji klasy `UnitTest1` i zmienić jego nazwę na `AutomobileTest`.

 > [!NOTE]
 >  IntelliSense zapewnia teraz dwie alternatywne dla instrukcji IntelliSense: *tryb uzupełniania* i *tryb sugestii*. Tryb sugestii w sytuacjach, w których klas i członków są używane zanim nie zostaną zdefiniowane. Po otwarciu okna IntelliSense, możesz nacisnąć przycisk **Ctrl + Alt + spacja** można przełączać tryb uzupełniania i tryb sugestii. Zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md) Aby uzyskać więcej informacji. Tryb sugestii zawierają informacje pomocne podczas wpisywania `Automobile` w następnym kroku.

3.  Zlokalizuj `TestMethod1()` — metoda i zmienić jego nazwę na `DefaultAutomobileIsInitializedCorrectly()`. Wewnątrz tej metody, Utwórz nowe wystąpienie klasy o nazwie `Automobile`, jak pokazano na poniższych zrzutach ekranu. Faliste podkreślenie pojawia się, co oznacza to błąd kompilacji i [szybkie akcje](../ide/quick-actions.md) żarówki jest wyświetlana na lewym marginesie (C# tylko) lub bezpośrednio pod wężyk w przypadku Aktywuj ją.

     ![Szybkie akcje w języku Visual Basic](../ide/media/genclass_underlinevb.png "GenClass_UnderlineVB")

     ![Szybkie akcje w języku C&#35;](../ide/media/genclass_underline.png "GenClass_Underline")

4.  Wybierz lub kliknij żarówkę szybkie akcje. Zostanie wyświetlony komunikat o błędzie stwierdzający, że typ `Automobile` nie jest zdefiniowany. Jest również wyświetlana rozwiązania.

5. Kliknij przycisk **wygenerować nowy typ...**  otworzyć **Generowanie typu** okno dialogowe. To okno dialogowe zawiera opcje, które obejmują generowania typu w innym projekcie.

6. W **projektu** kliknij **GFUDemo\_VB** lub **GFUDemo_CS** nakazać programowi Visual Studio, aby dodać plik do projektu biblioteki klas zamiast testu Projekt. Jeśli jeszcze nie jest wybrana, wybierz **Utwórz nowy plik** i nadaj mu nazwę **Automobile.cs** lub **Automobile.vb**.

     ![Okno dialogowe Nowy typ Generowanie](../ide/media/genotherdialog.png "GenOtherDialog")

6.  Kliknij przycisk **OK** aby zamknąć okno dialogowe i utworzyć nowy plik.

7.  W **Eksploratora rozwiązań**, sprawdź w obszarze węzła projektu GFUDemo_VB lub GFUDemo_CS, aby sprawdzić, czy nowy Automobile.vb lub istnieje już plik Automobile.cs. W edytorze kodu fokus jest nadal w `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`, co umożliwia nadal zapisywać testu z co najmniej przerwania.

### <a name="to-generate-a-property-stub"></a>Do generowania szkieletu właściwości
Załóżmy specyfikacji stwierdza, że `Automobile` klasa ma dwie właściwości publicznej o nazwie `Model` i `TopSpeed`. Te właściwości musi być zainicjowany z wartościami domyślnymi `"Not specified"` i `-1` przez konstruktora domyślnego. Następujące testu jednostkowego sprawdzi, czy domyślny konstruktor ustawia właściwości do wartości domyślnych poprawne.

1. Dodaj następujący wiersz kodu w celu `DefaultAutomobileIsInitializedCorrectly` metoda testowa.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Ponieważ kod odwołuje się do dwóch niezdefiniowanymi właściwościami na `Automobile`, faliste podkreślenie jest wyświetlany w obszarze `Model` i `TopSpeed`. Umieść kursor nad `Model` i wybierz żarówkę szybkie akcje, a następnie wybierz **wygenerować właściwości "Automobile.Model"**.

3. Generowania szkieletu właściwości dla `TopSpeed` właściwości w taki sam sposób.

     W `Automobile` klasy, jakiego rodzaju nowe właściwości są poprawnie wywnioskować z kontekstu.

### <a name="to-generate-a-stub-for-a-new-constructor"></a>Aby wygenerować klasy zastępczej dla nowego Konstruktora
Teraz utworzymy metody testowej, który zostanie wygenerowany przez konstruktora szkielet zainicjować `Model` i `TopSpeed` właściwości. Później dodasz więcej kod w celu zakończenia testu.

1. Dodaj następującą metodę dodatkowy test do Twojej `AutomobileTest` klasy.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2.  Kliknij żarówkę szybkie akcje w obszarze czerwona falista, a następnie kliknij przycisk **Generuj Konstruktor w "Samochodów"**.

     W `Automobile` klasy pliku, zwróć uwagę, że nowy konstruktor ma zbadać nazwy zmiennych lokalnych, które są używane w wywołaniu konstruktora, podczas gdy znaleziono właściwości, które mają takie same nazwy w `Automobile` klasy i podany kod treść konstruktora, aby przechowywanie wartości argumentu w `Model` i `TopSpeed` właściwości.


3.  Po wygenerowaniu nowego Konstruktora faliste podkreślenie jest wyświetlany w obszarze wywołanie konstruktora domyślnego w `DefaultAutomobileIsInitializedCorrectly`. Komunikat o błędzie stanów `Automobile` klasa nie ma konstruktora, który nie przyjmuje argumentów zero. Aby wygenerować jawny Konstruktor domyślny, który nie ma parametrów, kliknij żarówkę szybkie akcje, a następnie kliknij przycisk **Generuj Konstruktor w "Samochodów"**.

### <a name="to-generate-a-stub-for-a-method"></a>Aby wygenerować klasy zastępczej dla metody
Załóżmy specyfikację stwierdza, że nowy `Automobile` mogą być przełączane do stanu działania, jeśli jego `Model` i `TopSpeed` właściwości są ustawione na inną niż wartości domyślne.

1. Dodaj następujące wiersze do `AutomobileWithModelNameCanStart` metody.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2.  Kliknij żarówkę szybkie akcje dla `myAuto.Start` wywołania metody, a następnie kliknij przycisk **wygenerować metody "Automobile.Start"**.

3.  Kliknij żarówkę szybkie akcje dla `IsRunning` właściwości, a następnie kliknij przycisk **wygenerować właściwości "Automobile.IsRunning"**.

     `Automobile` Klasa teraz zawiera metodę o nazwie `Start()` i właściwość o nazwie `IsRunning`.

### <a name="to-run-the-tests"></a>Aby uruchomić testy

1.  Na **testu** menu, wybierz **Uruchom**, **wszystkie testy**.

     **Uruchom**, **wszystkie testy** polecenie uruchamia wszystkie testy w żadnych platform testów, które są przeznaczone dla bieżącego rozwiązania. W takim przypadku istnieją dwa testy, a nie ich obu, zgodnie z oczekiwaniami. `DefaultAutomobileIsInitializedCorrectly` Test zakończy się niepowodzeniem, ponieważ `Assert.IsTrue` warunku zwraca `False`. `AutomobileWithModelNameCanStart` Test zakończy się niepowodzeniem, ponieważ `Start` metoda `Automobile` klasy zgłasza wyjątek.

     **Wyników testu** okno jest wyświetlane na poniższej ilustracji.

     ![Wyników testu, który uległ awarii](../ide/media/testsfailed.png "TestsFailed")

2.  W **wyników testu** okna, kliknij dwukrotnie pozycję w każdym wierszu wynik testu, aby przejść do lokalizacji każdego z testów.

### <a name="to-implement-the-source-code"></a>Aby zaimplementować kodu źródłowego

1.  Dodaj poniższy kod do konstruktora domyślnego tak że `Model`, `TopSpeed` i `IsRunning` właściwości są inicjowane z wartościami domyślnymi poprawne z `"Not specified"`, `-1`, i `False` (lub `false` język C#).

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2.  Gdy `Start` metoda jest wywoływana, należy ją ustawić `IsRunning` flagi na wartość true tylko wtedy, gdy `Model` lub `TopSpeed` właściwości są ustawione na inną niż ich wartość domyślną. Usuń `NotImplementedException` z metody treści i Dodaj następujący kod.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="to-run-the-tests-again"></a>Aby ponownie uruchomić testy

- Na **testu** menu wskaż **Uruchom**, a następnie kliknij przycisk **wszystkie testy**.

     Teraz testy zostały zaliczone pomyślnie. **Wyników testu** okno jest wyświetlane na poniższej ilustracji.

     ![Wyników testu, który przekazał](../ide/media/testspassed.png "TestsPassed")

## <a name="see-also"></a>Zobacz także

- [Generowanie na podstawie użycia](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Pisanie kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Testowanie jednostek kodu](../test/unit-test-your-code.md)
- [Szybkie akcje](../ide/quick-actions.md)