---
title: "Dowiedz się, jak do testowania kodu z aktywnego testu jednostkowego w Visual Studio 2017 | Dokumentacja firmy Microsoft | Dokumentacja firmy Microsoft"
ms.date: 08/31/2017
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 2f2c8ba68419b23d2e74b82e23640c68a6f534aa
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Rozpoczynanie pracy z Live testów jednostkowych programu Visual Studio

Po włączeniu opcji Live testów jednostkowych w rozwiązaniu Visual Studio na żywo testów jednostkowych wizualnie przedstawia Twojej pokrycie testu oraz stan testów. Wykonuje również dynamicznie testów, gdy modyfikowania kodu. Zawiera natychmiastowego wysłania powiadomienia, gdy zmiany przerwane kodu i wskazuje obszary, dla których wymagane są dodatkowe testy. 

Testowanie jednostkowe na żywo może służyć do testowania rozwiązania, które odnoszą się do .NET Framework lub .NET Core. Z tego samouczka dowiesz się, za pomocą testów jednostkowych Live tworzenia biblioteki klas proste, którego element docelowy .NET Standard, a utworzysz projekt MSTest którego element docelowy .NET Core, aby przetestować go.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
Kompletne rozwiązanie C# można pobrać z [MicrosoftDocs/Visual Studio — dokumentacja](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) repozytorium w witrynie GitHub.
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
Kompletne rozwiązanie Visual Basic można pobrać z [MicrosoftDocs/Visual Studio — dokumentacja](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) repozytorium w witrynie GitHub.

---

## <a name="prerequisites"></a>Wymagania wstępne

Ten samouczek wymaga, aby po zainstalowaniu programu Visual Studio 2017 Enterprise Edition w wersji 15 ustęp 3 z obciążeniem, .NET Core 2.0.

## <a name="create-the-solution-and-the-class-library-project"></a>Tworzenie rozwiązania i projektu biblioteki klas

Rozpocznij od utworzenia rozwiązania Visual Studio o nazwie `UtilityLibraries` składający się z jednego .NET Standard projektu biblioteki klas, `StringLibrary`. Można napisać `StringLibrary` w języku C# lub Visual Basic. 

Rozwiązanie to po prostu kontener dla jednego lub więcej projektów. Aby utworzyć rozwiązanie, Otwórz program Visual Studio 2017 i wykonaj następujące czynności:

1. Wybierz **pliku**, **nowy**, **projektu** z menu najwyższego poziomu programu Visual Studio.

1. W **nowy projekt** okna dialogowego, rozwiń węzeł **inne typy projektów** a następnie wybierz węzeł **rozwiązań programu Visual Studio**. Wybierz **puste rozwiązanie** szablonu w okienku po prawej stronie, a następnie wprowadź `UtilityLibraries` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Okno dialogowe nowego projektu **](./media/lut-start/new-solution.png)

1. Wybierz **OK** do utworzenia rozwiązania.
 
Teraz, po utworzeniu rozwiązania, utworzysz biblioteki klas o nazwie `StringLibrary` zawiera szereg metody rozszerzenia dla pracy z ciągami znaków.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `UtilityLibraries` rozwiązania i wybierz **Dodaj**, **nowy projekt**.

1. W **Dodawanie nowego projektu** okna dialogowego, węzeł wybierz C#, następnie wybierz **.NET Standard**. 

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczony dla platformy .NET Standard zamiast konkretnej implementacji .NET, może zostać wywołana z implementacji .NET obsługującej danej wersji programu .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

1. Wybierz **biblioteki klas (.NET Standard)** szablonu w okienku po prawej stronie, a następnie wprowadź `StringLibrary` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Oknie dialogowym Dodawanie nowego projektu **](./media/lut-start/add-project-cs.png)

1. Wybierz **OK** Aby utworzyć projekt.

1. Zastąp wszystkie istniejący kod w oknie Kod następujący kod:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` ma trzy metody statycznej:

      - `StartsWithUpper` Zwraca `true` Jeśli ciąg rozpoczyna się wielką literę; w przeciwnym razie zwraca `false`.
      
      - `StartsWithLower`Zwraca `true` Jeśli ciąg rozpoczyna się małą literę; w przeciwnym razie zwraca `false`.
     
      - `HasEmbeddedSpaces` Zwraca `true` Jeśli ciąg zawiera znak spacji osadzonych; w przeciwnym razie zwraca `false`.
    
1.  Wybierz **kompilacji**, **Kompiluj rozwiązanie** z menu najwyższego poziomu programu Visual Studio. Visual Studio pomyślnie należy utworzyć bibliotekę.
 
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `UtilityLibraries` rozwiązania i wybierz **Dodaj**, **nowy projekt**.

1. W **Dodawanie nowego projektu** okno dialogowe, wybierz węzeł języka Visual Basic, a następnie wybierz **.NET Standard**. 

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczony dla platformy .NET Standard zamiast konkretnej implementacji .NET, może zostać wywołana z implementacji .NET obsługującej danej wersji programu .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

1. Wybierz **biblioteki klas (.NET Standard)** szablonu w okienku po prawej stronie, a następnie wprowadź `StringLibrary` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Oknie dialogowym Dodawanie nowego projektu **](./media/lut-start/add-project-vb.png)

1. Wybierz **OK** Aby utworzyć projekt.

1. Zastąp wszystkie istniejący kod w oknie Kod następujący kod:

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` ma trzy metody statycznej:

      - `StartsWithUpper` Zwraca `true` Jeśli ciąg rozpoczyna się wielką literę; w przeciwnym razie zwraca `false`.
      
      - `StartsWithLower`Zwraca `true` Jeśli ciąg rozpoczyna się małą literę; w przeciwnym razie zwraca `false`.
     
      - `HasEmbeddedSpaces` Zwraca `true` Jeśli ciąg zawiera znak spacji osadzonych; w przeciwnym razie zwraca `false`.
    
1. Kliknij prawym przyciskiem myszy na projekt StringLibrary w **Eksploratora rozwiązań** i wybierz **właściwości**. W **aplikacji** karcie, usuń tekst w **głównej przestrzeni nazw** pola tekstowego, jak przedstawiono na poniższym rysunku. Główna przestrzeń nazw jest definiowana za pomocą [instrukcji Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement) w kodzie źródłowym.

   ![Okno dialogowe właściwości projektu dla projektu Visual Basic](./media/lut-start/vb-properties.png)
 
1.  Wybierz **kompilacji**, **Kompiluj rozwiązanie** z menu najwyższego poziomu programu Visual Studio. Visual Studio pomyślnie należy utworzyć bibliotekę.

---

## <a name="create-the-test-project"></a>Tworzenie projektu testu

Następnym krokiem jest utworzenie jednostkowy projekt testowy do testowania `StringLibrary` biblioteki. Tworzenie testów jednostkowych, wykonując następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `UtilityLibraries` rozwiązania i wybierz **Dodaj**, **nowy projekt**.

1. W **Dodawanie nowego projektu** okna dialogowego, węzeł wybierz C#, następnie wybierz **.NET Core**. 

   > [!NOTE]
   > Nie masz pisania testów jednostkowych w tym samym języku co biblioteki klas.

1. Wybierz **jednostkowy projekt testowy (.NET Core)** szablonu w okienku po prawej stronie, a następnie wprowadź `StringLibraryTests` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Oknie dialogowym Dodawanie nowego projektu ** jednostkowy projekt testowy](./media/lut-start/add-unit-test-cs.png)

1. Wybierz **OK** Aby utworzyć projekt.

   > [!NOTE]
   > W tym samouczku korzysta z struktury testowej MSTest Live testów jednostkowych. Można również użyć xUnit i platform testów NUnit. 

1. Jednostkowy projekt testowy automatycznie nie może uzyskać dostępu do biblioteki klas, który testuje ją. Należy zapewnić dostęp biblioteki testu przez dodanie odwołania do projektu biblioteki klas. Aby to zrobić, kliknij prawym przyciskiem myszy `StringLibraryTests` projekt i wybierz **Dodaj**, **odwołania**. W **Menedżera odwołań** okna dialogowego, upewnij się, że **rozwiązania** karta jest zaznaczone i wybierz `StringLibrary` projektu, jak pokazano na poniższej ilustracji. 

   ![** Okna dialogowego odwołania Menedżera **](./media/lut-start/add-reference.png)
 
1. Zastąp schematyczny kod testu jednostkowego, dostarczone przez szablon z następującym kodem:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. Zapisz projekt, wybierając **zapisać** ikonę na pasku narzędzi. 

1. Ponieważ testu jednostkowego kod zawiera znaki spoza zestawu ASCII, Visual Studio wyświetla to okno dialogowe ostrzec niektóre znaki zostaną utracone jeśli możemy zapisać plik w formacie ASCII domyślne. Wybierz **Zapisz z kodowaniem inne** przycisku. 
 
   ![Wybierz kodowanie pliku](media/lut-start/ascii-encoding.png) 

1. W **kodowanie** listy rozwijanej **opcji Zapisz zaawansowanych** okno dialogowe, wybierz **Unicode (UTF-8 bez podpisu) - strona kodowa 65001**, jak pokazano na poniższej ilustracji:

   ![Wybieranie kodowania UTF-8](media/lut-start/utf8-encoding.png) 

1. Kompiluj jednostkowy projekt testowy przez **kompilacji**, **Kompiluj ponownie rozwiązanie** z menu najwyższego poziomu programu Visual Studio.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `UtilityLibraries` rozwiązania i wybierz **Dodaj**, **nowy projekt**.

1. W **Dodawanie nowego projektu** okno dialogowe, wybierz węzeł języka Visual Basic, a następnie wybierz **.NET Core**. 

   > [!NOTE]
   > Nie masz pisania testów jednostkowych w tym samym języku co biblioteki klas.

1. Wybierz **jednostkowy projekt testowy (.NET Core)** szablonu w okienku po prawej stronie, a następnie wprowadź `StringLibraryTests` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Oknie dialogowym Dodawanie nowego projektu ** dla testu jednostkowego](./media/lut-start/add-unit-test-vb.png)

1. Wybierz **OK** Aby utworzyć projekt.

   > [!NOTE]
   > W tym samouczku korzysta z struktury testowej MSTest Live testów jednostkowych. Można również użyć xUnit i platform testów NUnit. 

1. Jednostkowy projekt testowy automatycznie nie może uzyskać dostępu do biblioteki klas, który testuje ją. Należy zapewnić dostęp biblioteki testu przez dodanie odwołania do projektu biblioteki klas. Aby to zrobić, kliknij prawym przyciskiem myszy `StringLibraryTests` projekt i wybierz **Dodaj**, **odwołania**. W **Menedżera odwołań** okna dialogowego, upewnij się, że **rozwiązania** karta jest zaznaczone i wybierz `StringLibrary` projektu, jak pokazano na poniższej ilustracji. 

   ![** Okna dialogowego odwołania Menedżera **](./media/lut-start/add-reference.png)
 
1. Zastąp schematyczny kod testu jednostkowego, dostarczone przez szablon z następującym kodem:

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. Zapisz projekt, wybierając **zapisać** ikonę na pasku narzędzi. 

1. Ponieważ testu jednostkowego kod zawiera znaki spoza zestawu ASCII, Visual Studio wyświetla to okno dialogowe ostrzec niektóre znaki zostaną utracone jeśli możemy zapisać plik w formacie ASCII domyślne. Wybierz **Zapisz z kodowaniem inne** przycisku. 
 
   ![Wybierz kodowanie pliku](media/lut-start/ascii-encoding.png) 

1. W **kodowanie** listy rozwijanej **opcji Zapisz zaawansowanych** okno dialogowe, wybierz **Unicode (UTF-8 bez podpisu) - strona kodowa 65001**, jak pokazano na poniższej ilustracji:

   ![Wybieranie kodowania UTF-8](media/lut-start/utf8-encoding.png)

1. Kompiluj jednostkowy projekt testowy przez **kompilacji**, **Kompiluj ponownie rozwiązanie** z menu najwyższego poziomu programu Visual Studio.

---

Zostanie utworzona biblioteki klas, jak również niektórych testów jednostkowych dla niego. Teraz po zakończeniu czynności wstępne, potrzebne do użycia na żywo testów jednostkowych.

## <a name="enable-live-unit-testing"></a>Włącz testy jednostkowe na żywo

Tak daleko, mimo że napisanych testów dla `StringLibrary` biblioteki klas, możesz nie zostało to jeszcze wykonane je. Testowanie jednostkowe na żywo wykonuje je automatycznie po jej włączeniu. Aby to zrobić, wykonaj następujące czynności:

1. Opcjonalnie wybierz okno kodu, który zawiera kod `StringLibrary`. Jest to class1.cs dla projektu C# lub Class1.vb dla projektu Visual Basic. (Ten krok pozwala wizualnie sprawdzić wyniki z testów i zakresu z pokrycia kodu po włączeniu na żywo testów jednostkowych.)

1. Wybierz **testu**, **Live testów jednostkowych**, **Start** z menu najwyższego poziomu programu Visual Studio.
 
1. Visual Studio rozpoczyna się na żywo testu jednostkowego, który automatycznie uruchamia wszystkie testy. 
 
Po zakończeniu uruchamiania testów, **Eksploratora testów** wyświetlania ogólne wyniki i wyniki poszczególnych testów. Ponadto okno kodu graficznie wyświetla zarówno pokrycie kodu użytkownika testowego i wynik dla testów. Jak pokazano na poniższej ilustracji, wszystkie trzy testy zostały wykonane pomyślnie. Zawiera także że nasze testy zostały objęte wszystkie ścieżki kodu `StartsWithUpper` metody, a te wszystkie testy wykonane pomyślnie (co jest określane przez zielony znacznik wyboru "✓"). Na koniec go wskazuje, że żadna z innych metod w `StringLibrary` ma pokrycie kodu, (co jest określane przez linię "➖"). 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Okno Eksploratora testów i kod po uruchomieniu testów jednostkowych na żywo](media/lut-start/lut-results-cs.png) 

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Okno Eksploratora testów i kod po uruchomieniu testów jednostkowych na żywo](media/lut-start/lut-results-vb.png) 

---  

Również uzyskania bardziej szczegółowe informacje na temat test wyniki pokrycia i testowania, wybierając ikonę pokrycia kodu określonego w oknie kodu. Badanie tych szczegółów, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Kliknij zielony znacznik wyboru w wierszu `if (String.IsNullOrWhiteSpace(s))` w `StartsWithUpper` metody. Jak pokazano na poniższej ilustracji, Live testów jednostkowych wskazuje, że trzy testy obejmują wiersza kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji warunkowej "if"](media/lut-start/code-coverage-cs1.png) 

1. Kliknij zielony znacznik wyboru w wierszu `return Char.IsUpper(s[0])` w `StartsWithUpper` metody. Jak pokazano na poniższej ilustracji, Live testów jednostkowych wskazuje, że tylko dwa testy obejmują wiersza kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji return](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Kliknij zielony znacznik wyboru w wierszu `If (String.IsNullOrWhiteSpace(s)) Then` w `StartsWithUpper` metody. Jak pokazano na poniższej ilustracji, Live testów jednostkowych wskazuje, że trzy testy obejmują wiersza kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji warunkowej "If"](media/lut-start/code-coverage-vb1.png) 

1. Kliknij zielony znacznik wyboru w wierszu `Return Char.IsUpper(s(0))` w `StartsWithUpper` metody. Jak pokazano na poniższej ilustracji, Live testów jednostkowych wskazuje, że tylko dwa testy obejmują wiersza kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji return](media/lut-start/code-coverage-vb2.png)

---

Główne problem, który identyfikuje Live testów jednostkowych jest pokrycie kodu niekompletne. Będzie ona adresów w następnej sekcji. 

## <a name="expand-test-coverage"></a>Rozwiń węzeł pokrycie testu

W tej sekcji można rozszerzyć testy jednostkowe do `StartsWithLower` metody. Podczas gdy można to zrobić, na żywo testów jednostkowych dynamicznie będzie do testowania kodu.

Aby rozszerzyć pokrycia kodu do `StartsWithLower` metody, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Dodaj następujące `TestStartsWithLower` i `TestDoesNotStartWithLower` metody do pliku projektu testowego źródła kodu:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modyfikowanie `DirectCallWithNullOrEmpty` metody, dodając następujący kod bezpośrednio po wywołaniu [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Automatycznie na żywo testów jednostkowych wykonuje testy nowych i zmodyfikowanych podczas modyfikowania kodu źródłowego. Jako wartość następujące **Eksploratora testów** pokazuje, wszystkie testy w tym dodano dwa i jeden zmodyfikowano, zakończyło się pomyślnie.

   ![Eksplorator testów po rozwinięciu pokrycie testu.](media/lut-start/test-dynamic.png) 

1. Przełącz do okna zawierającego kod źródłowy `StringLibrary` klasy. Na żywo testów jednostkowych teraz wskazuje, że nasze pokrycie kodu jest rozszerzony do `StartsWithLower` metody.

    ![Pokrycie kodu dla metody StartsWithLower](media/lut-start/lut-extended-cs.png) 

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Dodaj następujące `TestStartsWithLower` i `TestDoesNotStartWithLower` metody do pliku projektu testowego źródła kodu:

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. Modyfikowanie `DirectCallWithNullOrEmpty` metody, dodając następujący kod bezpośrednio po wywołaniu [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Automatycznie na żywo testów jednostkowych wykonuje testy nowych i zmodyfikowanych podczas modyfikowania kodu źródłowego. Jako wartość następujące **Eksploratora testów** pokazuje, wszystkie testy w tym dodano dwa i jeden zmodyfikowano, zakończyło się pomyślnie.

   ![Eksplorator testów po rozwinięciu pokrycie testu.](media/lut-start/test-dynamic.png) 

1. Przełącz do okna zawierającego kod źródłowy `StringLibrary` klasy. Na żywo testów jednostkowych teraz wskazuje, że nasze pokrycie kodu jest rozszerzony do `StartsWithLower` metody.

    ![Pokrycie kodu dla StartsWithLower](media/lut-start/lut-extended-vb.png)

---
 
W niektórych przypadkach pomyślnie testy w **Eksploratora testów** może być aktywna. Wskazująca, czy test jest aktualnie wykonywany, lub czy test nie został uruchomiony ponownie, ponieważ było zmiany żaden kod, który może mieć wpływ testu od czasu ostatniego zostało wykonane.

Do tej pory wszystkie nasze testy mają powiodło się. W następnej sekcji zajmiemy się, jak może obsłużyć niepowodzenia testu.

## <a name="handling-a-test-failure"></a>Obsługa niepowodzenia testu

W tej sekcji można odkryć sposób korzystania na żywo testów jednostkowych zidentyfikować, rozwiązywanie problemów i rozwiązania niepowodzenia testu. Będzie to zrobić po rozwinięciu pokrycia testu do `HasEmbeddedSpaces` metody.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Dodaj następującą metodę do pliku testowego:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Podczas testu, testów jednostkowych na żywo oznacza to, że `TestHasEmbeddedSpaces` metody nie powiodło się, jak przedstawiono na poniższym rysunku: ![Eksploratora testów raportowania testu nie powiodło się.](media/lut-start/test-failure.png) 
 
1. Wybierz okno, który zawiera kod biblioteki. Należy pamiętać, że na żywo testów jednostkowych rozwinął pokrycia kodu do `HasEmbeddedSpaces` metody. Również raporty niepowodzenia testu, dodając czerwony "🞩" do wierszy objętych testy zakończone niepowodzeniem. 

1. Umieść kursor nad wiersz z `HasEmbeddedSpaces` podpis metody. Testowanie jednostkowe na żywo Wyświetla etykietki narzędzia, który zgłasza, że metoda jest objęty przez jeden test, jak przedstawiono na poniższym rysunku:

   ![Na żywo testów jednostkowych informacji na temat testu nie powiodło się.](media/lut-start/test-failure-info-cs.png) 

1. Wybierz nieudane **TestHasEmbeddedSpaces** testu. Należy pamiętać, że testów jednostkowych na żywo zapewnia szereg opcje, takie jak uruchamianie wszystkich testów, wybierz testów debugowania wszystkie testy i debugowanie wybrane testy, jako następujący rysunek przedstawia:

   ![Na żywo opcje testów jednostkowych dla testu nie powiodło się.](media/lut-start/test-failure-options.png) 
    
1. Wybierz **debugowania wybrane** można debugować testu nie powiodło się. 
 
1. Visual Studio wykonuje testu w trybie debugowania. Naszym teście przypisuje każdy ciąg w tablicy zmiennej o nazwie `phrase` i przekazuje je do `HasEmbeddedSpaces` metody. Wykonanie programu wstrzymuje i wywołuje czasu debugera pierwsze wyrażenie assert jest `false`. Okno dialogowe wyjątku, będącą wynikiem nieoczekiwaną wartość w [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) wywołanie metody przedstawiono na poniższej ilustracji.  

   ![Na żywo testów jednostkowych okno dialogowe wyjątku.](media/lut-start/exception-dialog-cs.png) 
 
   Ponadto wszystkie narzędzia debugowania programu Visual Studio są dostępne w celu ułatwienia rozwiązywania naszym teście nie powiodło się, jak przedstawiono na poniższym rysunku:
 
   ![Narzędzia debugowania programu Visual Studio.](media/lut-start/debugging-tools-cs.png) 

   Należy zwrócić uwagę w **automatycznych** okna który wartość `phrase` zmiennej jest "Name\tDescription", która jest drugi element tablicy. Metoda testowa oczekuje `HasEmbeddedSpaces` do zwrócenia `true` przekazanej tego ciągu; zamiast tego zwraca `false`. Oczywiście nie rozpoznaje "\t" znak tabulacji osadzonych miejsca.

1. Wybierz **debugowania**, **Kontynuuj**, a następnie naciśnij klawisz F5 lub kliknij przycisk **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie test program. Ponieważ wystąpił nieobsługiwany wyjątek, kończy testu.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Dodaj następującą metodę do pliku testowego:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. Podczas testu, testów jednostkowych na żywo oznacza to, że `TestHasEmbeddedSpaces` metody nie powiodło się, jak przedstawiono na poniższym rysunku:
 
   ![Eksplorator testów raportowania testu nie powiodło się.](media/lut-start/test-failure.png) 
 
1. Wybierz okno, który zawiera kod biblioteki. Należy pamiętać, że na żywo testów jednostkowych rozwinął pokrycia kodu do `HasEmbeddedSpaces` metody. Również raporty niepowodzenia testu, dodając czerwony "🞩" do wierszy objętych testy zakończone niepowodzeniem. 

1. Umieść kursor nad wiersz z `HasEmbeddedSpaces` podpis metody. Testowanie jednostkowe na żywo Wyświetla etykietki narzędzia, który zgłasza, że metoda jest objęty przez jeden test, jak przedstawiono na poniższym rysunku:

   ![Na żywo testów jednostkowych informacji na temat testu nie powiodło się.](media/lut-start/test-failure-info-vb.png) 

1. Wybierz nieudane **TestHasEmbeddedSpaces** testu. Należy pamiętać, że testów jednostkowych na żywo zapewnia szereg opcje, takie jak uruchamianie wszystkich testów, wybierz testów debugowania wszystkie testy i debugowanie wybrane testy, jako następujący rysunek przedstawia:

   ![Na żywo opcje testów jednostkowych dla testu nie powiodło się.](media/lut-start/test-failure-options.png) 
    
1. Wybierz **debugowania wybrane** można debugować testu nie powiodło się. 
 
1. Visual Studio wykonuje testu w trybie debugowania. Naszym teście przypisuje każdy ciąg w tablicy zmiennej o nazwie `phrase` i przekazuje je do `HasEmbeddedSpaces` metody. Wykonanie programu wstrzymuje i wywołuje czasu debugera pierwsze wyrażenie assert jest `false`. Okno dialogowe wyjątku, będącą wynikiem nieoczekiwaną wartość w [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) wywołanie metody przedstawiono na poniższej ilustracji.  

   ![Na żywo testów jednostkowych okno dialogowe wyjątku.](media/lut-start/exception-dialog-vb.png) 
 
   Ponadto wszystkie narzędzia debugowania programu Visual Studio są dostępne w celu ułatwienia rozwiązywania naszym teście nie powiodło się, jak przedstawiono na poniższym rysunku:
 
   ![Narzędzia debugowania programu Visual Studio.](media/lut-start/debugging-tools-vb.png) 

   Należy zwrócić uwagę w **automatycznych** okna który wartość `phrase` zmiennej jest "Name" + vbTab "Opis", który jest drugi element tablicy. Metoda testowa oczekuje `HasEmbeddedSpaces` do zwrócenia `true` przekazanej tego ciągu; zamiast tego zwraca `false`. Oczywiście nie rozpoznaje znak tabulacji osadzonych miejsca.

1. Wybierz **debugowania**, **Kontynuuj**, a następnie naciśnij klawisz F5 lub kliknij przycisk **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie test program. Ponieważ wystąpił nieobsługiwany wyjątek, kończy testu.

--- 

Zapewnia to wystarczających informacji do wstępne badanie usterki. Albo `TestHasEmbeddedSpaces`, procedura testu, wprowadzone nieprawidłowe założenie, lub `HasEmbeddedSpaces` poprawnie nie rozpoznaje wszystkie spacje. Aby zdiagnozować i rozwiązać problem, uruchom przy użyciu `StringLibrary.HasEmbeddedSpaces` metody:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Przyjrzyj się porównanie w `HasEmbeddedSpaces` metody. Traktuje osadzonych miejsca, U + 0020. Jednak w standardzie Unicode zawiera wiele innych znaków spacji. Sugeruje to, że kod biblioteki niepoprawnie został przetestowany pod kątem znak odstępu.
 
1. Zamień porównania równości wywołanie <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Testowanie jednostkowe na żywo automatycznie zwracające metoda testowa nie powiodło się i aktualizuje wyniki w oknie kodu i w **Eksploratora testów**, jak pokazano na poniższej ilustracji:

    ![Pomyślnie testu HasEmbeddedSpaces.](media/lut-start/test-success-cs.png) 

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Przyjrzyj się porównanie w `HasEmbeddedSpaces` metody. Traktuje osadzonych miejsca, U + 0020. Jednak w standardzie Unicode zawiera wiele innych znaków spacji. Sugeruje to, że kod biblioteki niepoprawnie został przetestowany pod kątem znak odstępu.
 
1. Zamień porównania równości wywołanie <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Testowanie jednostkowe na żywo automatycznie ponownie uruchamia metoda testowa nie powiodło się i aktualizuje wyniki w oknie kodu i w **Eksploratora testów**, jak pokazano na poniższej ilustracji:

    ![Pomyślnie testu HasEmbeddedSpaces.](media/lut-start/test-success-vb.png) 

---

## <a name="see-also"></a>Zobacz także
[Jednostki na żywo testowania w programie Visual Studio](live-unit-testing.md)   
[Aktywne testy jednostkowe często zadawane pytania](live-unit-testing-faq.md)   
