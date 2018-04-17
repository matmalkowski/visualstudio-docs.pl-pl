---
title: Teście jednostkowym w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 2016-01-07
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e6bfbd65a7f242a14f1aebf2c554d481aa570ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="unit-test-basics"></a>Teście jednostkowym

Sprawdź, czy kod działa zgodnie z oczekiwaniami, tworzenie i Uruchamianie testów jednostkowych. Jest to testowania, ponieważ można podzielić funkcji programu do odrębny testować zachowania, które można sprawdzić w poszczególnych jednostek *jednostki*. Narzędzia Eksplorator testów programu Visual Studio zapewnia elastyczne i wydajne sposób uruchamiania testów jednostkowych i wyświetlać ich wyniki w programie Visual Studio. Visual Studio instaluje testowania struktur dla kodu zarządzanego i natywnego jednostek firmy Microsoft. Użyj *framework testy jednostkowe* do tworzenia testów jednostkowych, uruchom je i raportuje o wynikach tych testów. Testów jednostkowych Uruchom ponownie podczas wprowadzania zmian, aby przetestować czy kodzie nadal działa poprawnie. Visual Studio Enterprise można to zrobić automatycznie [Live testów jednostkowych](live-unit-testing-intro.md), która wykrywa testów, których dotyczą przez kod zmiany i ich działa w tle podczas pisania.

Testy jednostkowe ma największy wpływ na jakości kodu, gdy jest integralną częścią przepływu pracy rozwoju oprogramowania. Jak pisania funkcji lub innych bloku kodu aplikacji, należy utworzyć testy jednostek, który Sprawdź zachowania kodu w odpowiedzi na standardowy, granic lub niepoprawne przypadków w danych wejściowych, a który żadnym założeniu jawnych ani niejawnych wprowadzone przez kod. Z *programowanie sterowane testami*, przed przystąpieniem do napisania kodu, aby używać testów jednostkowych jako dokumentacja i specyfikacje funkcjonalności tworzenia testów jednostkowych.

Możesz szybko generować projekty testowe i metod testowych w kodzie lub ręcznie utworzyć testy w miarę potrzeby. Korzystając z programu IntelliTest do eksplorowania kodu platformy .NET, można wygenerować danych testowych i zestaw testów jednostkowych. Dla każdej instrukcji w kodzie, jest generowany wprowadzania testu który wykona tej instrukcji. Dowiedz się, jak [Generowanie testów jednostek dla kodu](http://msdn.microsoft.com/library/dn823749.aspx).

Eksplorator testów można również uruchomić innych firm i otwórz źródła platform testów jednostkowych, które zostały zaimplementowane interfejsy dodatek Eksploratora testów. Można dodać wiele z tych platform za pomocą Menedżera rozszerzenia programu Visual Studio i galerii Visual Studio. Zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

## <a name="getting-started"></a>Wprowadzenie

Aby obejrzeć wprowadzenie do testowania jednostek, które umożliwia przejście bezpośrednio do kodowania Zobacz jedną z poniższych tematów:

- [Przewodnik: tworzenie i uruchamianie testów jednostkowych zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Szybki Start: Test programowanie sterowane za pomocą narzędzia Eksplorator testów](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Pisanie testów jednostkowych dla C/C++ w programie Visual Studio](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>Przykład rozwiązania MyBank

W tym artykule używamy programowanie fikcyjnej aplikacji o nazwie `MyBank` jako przykład. Nie jest potrzebny rzeczywisty kod do wykonania wyjaśnienia, w tym temacie. Metody testowe są napisane w języku C# i przedstawione za pomocą Framework testów jednostkowych Microsoft dla kodu zarządzanego, jednak pojęć można łatwo przenosić do innych języków i struktur.

 ![MyBank Solution](../test/media/ute_mybanksolution.png "UTE_MyBankSolution")

 Nasze pierwsza próba projektu dla `MyBank` aplikacja zawiera składnik kont, który reprezentuje indywidualne konto i jego transakcji w banku i składnika bazy danych, który zapewnia funkcje do agregacji i zarządzanie indywidualne konta.

 Utworzymy `MyBank` rozwiązania, która zawiera dwa projekty:

-   `Accounts`

-   `BankDb`

 Nasze pierwsza próba projektowanie `Accounts` projekt zawiera klasę do przechowywania podstawowe informacje o koncie, interfejs, który określa typowe funkcje dowolnego typu konta, takich jak zdeponowanie i wycofania zasobów z konta i klasy pochodzące z interfejsu, który reprezentuje konta bankowego. Zaczniemy projektów kont przez utworzenie następujących plików źródłowych:

-   `AccountInfo.cs` Definiuje podstawowe informacje dotyczące konta.

-   `IAccount.cs` Określa standard `IAccount` interfejs dla konta, w tym metod do złożenia i wycofać zasoby z konta oraz do pobierania saldo konta.

-   `CheckingAccount.cs` zawiera `CheckingAccount` klasa implementująca `IAccounts` interfejs dla konta bankowego.

Wiemy z doświadczenia tego jedyną operacją, której należy wykonać wycofania z konta bankowego jest upewnij się, że wielkość wycofane jest mniejsza niż saldo konta. Dlatego firma Microsoft zastąpienie `IAccount.Withdaw` metody w `CheckingAccount` za pomocą metody, która sprawdza tego warunku. Metoda może wyglądać następująco:

```csharp
public void Withdraw(double amount)
{
    if(m_balance >= amount)
    {
        m_balance -= amount;
    }
    else
    {
        throw new ArgumentException(amount, "Withdrawal exceeds balance!")
    }
}
```

Teraz, gdy mamy kodu jest czasu testowania.

## <a name="create-unit-test-projects-and-test-methods"></a>Tworzenie projektów testów jednostkowych i metod testowych

Często jest szybsze do generowania jednostkowy projekt testowy i klas zastępczych testów jednostkowych w kodzie. Można też utworzyć jednostkowy projekt testowy i testy ręczne w zależności od wymagań.

 **Generowanie jednostkowy projekt testowy i klas zastępczych testu jednostkowego**

1.  W oknie edytora kodu, kliknij prawym przyciskiem myszy i wybierz polecenie **tworzenia testów jednostkowych** z menu kontekstowego.

     ![W oknie edytora wyświetlić menu kontekstowe](../test/media/createunittestsrightclick.png "CreateUnitTestsRightClick")

2.  Kliknij przycisk OK, aby zaakceptować wartości domyślne tworzenia testów jednostkowych lub zmiany wartości używane do tworzenia i nazwę jednostki Testowanie projektu i testów jednostkowych. Można wybrać kod, który jest domyślnie dodawany do metody testowe jednostki.

     ![Prawo&#45;kliknij w edytorze i wybierz polecenie Utwórz testy jednostkowe](../test/media/createunittestsdialog.png "CreateUnitTestsDialog")

3.  Klas zastępczych testów jednostkowych są tworzone w nowym projekcie testowym jednostki dla wszystkich metod w klasie.

     ![Testy jednostkowe są tworzone](../test/media/createunittestsstubs.png "CreateUnitTestsStubs")

4.  Teraz przejść do Dowiedz się, jak [Dodaj kod do metody testowe jednostki](#BKMK_Writing_your_tests) z testu jednostkowego łatwy do rozpoznania i wszelkie dodatkowe testów, które warto dodać do dokładnego przetestowania kodu.

 **Test jednostki projektu i jednostki testy ręczne tworzenie**

 Jednostkowy projekt testowy zazwyczaj odzwierciedla strukturę pojedynczy kod projektu. W tym przykładzie MyBank dodaniu dwóch projektów testów jednostkowych o nazwie `AccountsTests` i `BankDbTests` do `MyBanks` rozwiązania. Nazwy projektu testowego są dowolne, ale przyjęcie standardowej konwencji nazewnictwa jest dobrym rozwiązaniem.

 **Aby dodać jednostkowy projekt testowy do rozwiązania:**

1.  Na **pliku** menu, wybierz **nowy** , a następnie wybierz **projektu** (klawiatury Ctrl + Shift + N).

2.  W oknie dialogowym Nowy projekt, rozwiń węzeł **zainstalowana** węzła, wybierz język, którego chcesz użyć dla projektu testowego, a następnie wybierz **testu**.

3.  Aby użyć jednego z platform testów jednostkowych firmy Microsoft, wybierz **projektu testu jednostki** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu jednostki struktury testowej, która ma być używany. Aby przetestować `Accounts` projektu z naszym przykładzie, czy nazwa projektu `AccountsTests`.

    > [!WARNING]
    > Nie wszystkie platform testów jednostkowych innych firm i otwórz źródła Podaj szablon projektu Visual Studio. Zapoznaj się z dokumentem framework informacje na temat tworzenia projektu.

4.  W jednostkowy projekt testowy Dodaj odwołanie do projektu kodu, w ramach testu, w tym przykładzie do projektu kont.

     Aby utworzyć odwołanie do projektu kodu:

    1.  Wybierz projekt w Eksploratorze rozwiązań.

    2.  Na **projektu** menu, wybierz **Dodaj odwołanie**.

    3.  W oknie dialogowym Menedżera odwołań Otwórz **rozwiązania** węzeł i wybierz polecenie **projekty**. Wybierz nazwę projektu kodu, a następnie zamknij okno dialogowe.

 Każdy jednostkowy projekt testowy zawiera klasy, które duplikatów nazw klas w projekcie kodu. W naszym przykładzie `AccountsTests` projekt będzie zawierał następujące klasy:

-   `AccountInfoTests` Klasa zawiera metody testów jednostkowych dla `AccountInfo` klasy w `BankAccount` projektu

-   `CheckingAccountTests` Klasa zawiera metody testów jednostkowych dla `CheckingAccount` klasy.

## <a name="write-your-tests"></a>Pisania testów

Testu jednostkowego framework, którego używasz, i Visual Studio IntelliSense poprowadzi Cię przez pisanie kodu dla testów jednostkowych dla projektu kodu. Aby uruchomić Eksploratora testów, większość struktur wymagają, aby dodać określone atrybuty, które identyfikują jednostkę metody testowe. Struktury umożliwiają także — zwykle za pośrednictwem assert instrukcji lub atrybuty metody — aby wskazać, czy metoda testowa został przekazany lub niepowodzenie. Inne atrybuty zidentyfikować metody Instalacja opcjonalna, które są podczas inicjowania klasy i przed każdym metody testowej i metody usuwania, które są uruchamiane po każdej metody i przed klasy.

Wzorzec AAA (Rozmieść Act, Assert) jest to często stosowana metoda pisania testów jednostkowych dla metody w ramach testu.

- **Rozmieść** sekcji metody testowej jednostki inicjuje obiekty i ustawia wartość danych, który jest przekazywany do metody w ramach testu.

- **Act** sekcji wywołuje metodę w obszarze test uszeregowanych parametrów.

- **Assert** sekcji sprawdza, czy akcja metody w ramach testu działa zgodnie z oczekiwaniami.

Aby przetestować `CheckingAccount.Withdraw` metody w naszym przykładzie, firma Microsoft może zapisywać dwóch testów: jedną, która sprawdza standardowe zachowanie metody i jedną, która sprawdza, czy wycofanie więcej niż saldo zakończy się niepowodzeniem. W `CheckingAccountTests` klasy, możemy Dodaj następujące metody:

```csharp
[TestMethod]
public void Withdraw_ValidAmount_ChangesBalance()
{
    // arrange
    double currentBalance = 10.0;
    double withdrawal = 1.0;
    double expected = 9.0;
    var account = new CheckingAccount("JohnDoe", currentBalance);
    // act
    account.Withdraw(withdrawal);
    double actual = account.Balance;
    // assert
    Assert.AreEqual(expected, actual);
}

[TestMethod]
[ExpectedException(typeof(ArgumentException))]
public void Withdraw_AmountMoreThanBalance_Throws()
{
    // arrange
    var account = new CheckingAccount("John Doe", 10.0);
    // act
    account.Withdraw(20.0);
    // assert is handled by the ExpectedException
}
```

Należy pamiętać, że `Withdraw_ValidAmount_ChangesBalance` używa jawnego `Assert` instrukcję w celu sprawdzenia, czy metoda testowa przekazuje nie powiedzie się, gdy `Withdraw_AmountMoreThanBalance_Throws` używa `ExpectedException` atrybutu, aby określić Powodzenie metody testowej. W obszarze obejmuje frameworka testów jednostkowych otacza metody testowe instrukcji try/catch. W większości przypadków Jeśli wystąpił wyjątek metody testowej nie powiedzie się i wyjątek jest ignorowany. `ExpectedException` Atrybut powoduje metody testowej do przekazania, jeśli określony wyjątek.

Aby uzyskać więcej informacji o jednostce Microsoft struktur testowania, zobacz jedną z następujących tematów:

-   [Pisanie testów jednostkowych dla .NET Framework za pomocą struktury testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

-   [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)

## <a name="set-timeouts-for-unit-tests"></a>Ustawianie limitów czasu dla testów jednostkowych

Aby ustawić limit czasu dla metody testowej poszczególnych:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Aby ustawić maksymalną dozwoloną wartość Limit czasu:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Uruchom testy w narzędzia Eksplorator testów

Podczas kompilowania projektu testowego, testy są wyświetlane w Eksploratorze testów. Eksploratora testów nie jest widoczny, jeśli **testu** w menu programu Visual Studio, wybierz **systemu Windows**, a następnie wybierz pozycję **Eksploratora testów**.

 ![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Jak uruchamiać, zapisu i ponownie uruchomić testy domyślny widok Eksploratora testów wyświetla wyniki w grupach **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i  **Nie uruchamiać testów**. Można wybrać nagłówek grupy, aby otworzyć widok, który wyświetla wszystkie testy w tej grupie.

 Można również filtrować testy w dowolnym widoku szukanego tekstu w polu wyszukiwania na poziomie globalnym lub wybierając jedną z wstępnie zdefiniowanych filtrów. Wszystkie wybrane testy można uruchomić w dowolnym momencie. Wyniki uruchomienia testu są od razu widoczne na pasku przebiegu/Niepowodzenie w górnej części okna Eksploratora. Po wybraniu testu, wyświetlane są szczegóły wyniku testu metody.

### <a name="run-and-view-tests"></a>Uruchom i wyświetlić testy

Pasek narzędzi Eksploratora testów ułatwia odnajdywanie, organizować i uruchamiać testy, które planuje się.

 ![Uruchamianie testów za pomocą narzędzi Eksploratora testów](../test/media/ute_toolbar.png "UTE_ToolBar")

 Możesz wybrać **Uruchom wszystkie** do uruchomienia wszystkich testów, lub wybierz **Uruchom** wybranie podzestawu testów do uruchomienia. Po uruchomieniu zestawu testów w dolnej części okna Eksploratora testów zostanie wyświetlone podsumowanie uruchomienia testu. Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku. Wybierz **Otwórz Test** z menu kontekstowego (klawiatury: F12) do wyświetlenia kodu źródłowego dla wybranego testu.

 Jeśli poszczególne testy nie ma żadnych zależności, które uniemożliwiają uruchomione w dowolnej kolejności, włącz wykonywanie równoległe testu z ![UTE&#95;parallelicon&#45;małych](../test/media/ute_parallelicon-small.png "małych UTE_parallelicon") przycisk przełączania na pasku narzędzi. To znacznie ograniczyć czas potrzebny na uruchamianie wszystkich testów.

### <a name="run-tests-after-every-build"></a>Uruchom testy po każdej kompilacji

> [!WARNING]
> Jednostka uruchomionych testów po każdej kompilacji jest obsługiwany tylko w programie Visual Studio Enterprise.

|||
|-|-|
|![Uruchom po kompilacji](../test/media/ute_runafterbuild_btn.png "UTE_RunAfterBuild_btn")|Aby uruchomić testy jednostkowe po każdym lokalnej kompilacji, wybierz pozycję **testu** w standardowe menu, wybierz **Uruchom testy po kompilacji** na pasku narzędzi Eksplorator testów.|

### <a name="filter-and-group-the-test-list"></a>Filtr i Grupa listy testów

Jeśli masz dużą liczbę testów, można wpisać w polu wyszukiwania Eksploratora testów, aby filtrować listę według określonego ciągu. Można ograniczyć zdarzenie filtru więcej wybierając z listy filtrów.

 ![Wyszukaj filtr kategorii](../test/media/ute_searchfilter.png "UTE_SearchFilter")

|||
|-|-|
|![Przycisk Eksploratora testów](../test/media/ute_groupby_btn.png "UTE_GroupBy_btn")|Do grupowania testów według kategorii, wybierz **Group By** przycisku.|

 Aby uzyskać więcej informacji, zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)

## <a name="qa"></a>FUNKCJA PYTANIA I ODPOWIEDZI

**Pytanie: jak debugować testy jednostkowe?**

**Odpowiedź:** Użyj Eksploratora testów, aby rozpocząć sesję debugowania dla testów. Krokowe wykonywanie kodu z debuger programu Visual Studio bezproblemowe przejście i z powrotem między testów jednostkowych i projektu w ramach testu. Można rozpocząć debugowania:

1.  W edytorze programu Visual Studio należy ustawić punkt przerwania w metody testowe, które chcesz debugować.

    > [!NOTE]
    > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkie metody testowe, które chcesz debugować.

2.  W Eksploratorze testów, wybierz metody testowe, a następnie wybierz **Debuguj zaznaczone testy** z menu skrótów.

Dowiedz się więcej informacji o [profilowanie testów jednostkowych](../debugger/debugging-in-visual-studio.md).

 **Pytanie: jeśli używam TDD, jak I generowanie kodu na podstawie moich testów?**

 **Odpowiedź:** Użyj IntelliSense do generowania klasy i metody w kodzie projektu. Pisanie instrukcji w metody testowej, która wywołuje klasy lub metody, która ma zostać wygenerowany, a następnie otwórz menu IntelliSense w wywołaniu. W przypadku wywołania konstruktora nowej klasy, wybierz **wygenerować nowy typ** z menu i wykonaj polecenia kreatora, aby wstawić klasę w projekcie kodu. W przypadku wywołania metody, wybierz **wygenerować nową metodę** z IntelliSense menu.

 ![Generowanie Menu IntelliSense szkieletu metody](../test/media/ute_generatemethodstubintellisense.png "UTE_GenerateMethodStubIntellisense")

 **Pytanie: czy można utworzyć testów, które przyjmują wiele zestawów danych jako dane wejściowe, aby uruchomić test?**

 **Odpowiedź:** tak. *Metody oparte na danych* umożliwiają testowanie zakres wartości z metody testowej pojedynczą jednostką. Użyj `DataSource` atrybutu dla metody testowej, który określa źródło danych i tabeli, która zawiera wartości zmiennych, które mają zostać przetestowane.  W treści metody, przypisz wartości wierszy do zmiennych przy użyciu `TestContext.DataRow[` *ColumnName* `]` indeksatora.

> [!NOTE]
> Te procedury dotyczą tylko przetestować metody modyfikujące za pomocą frameworka testów jednostkowych Microsoft dla kodu zarządzanego. Jeśli używasz różnych framework, zajrzyj do dokumentacji framework równoważne funkcje.

 Załóżmy na przykład, dodamy niepotrzebnych sposób `CheckingAccount` klasy o nazwie `AddIntegerHelper`. `AddIntegerHelper` dodaje dwie liczb całkowitych.

 Aby utworzyć testu opartego na danych dla `AddIntegerHelper` metody, najpierw utworzymy bazy danych programu Access o nazwie `AccountsTest.accdb` i tabela o nazwie `AddIntegerHelperData`. `AddIntegerHelperData` Definiuje tabeli, kolumny, aby określić argumenty operacji dodawania pierwszego i drugiego i kolumny, aby określić oczekiwany wynik. Liczba wierszy możemy wprowadzić odpowiednie wartości.

```csharp
[DataSource(
    @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Projects\MyBank\TestData\AccountsTest.accdb",
    "AddIntegerHelperData"
)]
[TestMethod()]
public void AddIntegerHelper_DataDrivenValues_AllShouldPass()
{
    var target = new CheckingAccount();
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.AddIntegerHelper(x, y);
    Assert.AreEqual(expected, actual);
}
```

Metody oparte na atrybutach jest uruchamiane jeden raz dla każdego wiersza w tabeli. Eksplorator testów zgłasza błąd testu dla metody, jeśli dowolne iteracji nie powiedzie się. W okienku szczegółów wyników testów dla metody zawiera metodę stan przebiegu/błędów dla każdego wiersza danych.

 Dowiedz się więcej o [testów jednostkowych opartych na danych](../test/how-to-create-a-data-driven-unit-test.md).

 **Pytanie: czy można wyświetlać ile mojego kodu jest testowana przez mój testy jednostkowe?**

 **Odpowiedź:** tak. Można określić ilość swój kod, który jest rzeczywiście testowane przez testy jednostkowe za pomocą narzędzia pokrycia kodu programu Visual Studio. Są obsługiwane języki natywnych i zarządzanych i wszystkich platform testów jednostkowych, które mogą być uruchamiane przez Framework testów jednostkowych.

 Pokrycie kodu można uruchomić wybranych testów lub wszystkie testy w rozwiązaniu. Okno wyników pokrycia kodu przedstawia wartość procentową bloków kodu produktu, które były wykonywane przez wiersz, funkcji, klasy, przestrzeń nazw i moduł.

 Aby uruchomić pokrycie kodu dla metody testowe w rozwiązaniu, wybierz pozycję **testy** w menu programu Visual Studio, a następnie wybierz **Analizuj pokrycie kodu**.

 W oknie wyników pokrycia kodu zostaną wyświetlone wyniki pokrycia.

 ![Wyniki pokrycia kodu](../test/media/ute_codecoverageresults.png "UTE_CodeCoverageResults")

 Dowiedz się więcej o [pokrycie kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

 **Pytanie: jak przetestować metody w kodzie mające zależności zewnętrzne**

 **Odpowiedź:** tak. Jeśli masz program Visual Studio Enterprise Microsoft Fakes może służyć metody testowe, które zapisu przy użyciu platform testów jednostkowych dla kodu zarządzanego.

 Microsoft Fakes wykorzystuje dwa podejścia do tworzenia klas zastępczych dla zależności zewnętrznych:

1.  *Klas zastępczych* wygenerować klas zastępczych pochodną interfejsu nadrzędnej klasy docelowej zależności. Klasy zastępczej metody mogą zastąpić publicznego metody wirtualne klasy docelowej.

2.  *Podkładek* umożliwia kierowanie wywołań metody docelowej dla metody podkładki zastępczej dla metody niewirtualnej środowiska uruchomieniowego instrumentacji.

W obu podejść użyjesz wygenerowanego delegatów wywołań metod w zależności do określania zachowania, które mają w metodzie testowej.

Dowiedz się więcej o [izolowanie metody testowe jednostki z Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

 **Pytanie: czy do tworzenia testów jednostkowych można używać innych platform testów jednostkowych?**

 **Odpowiedź:** tak, wykonaj następujące kroki, aby [znajdować i instalować innych platform,](../test/install-third-party-unit-test-frameworks.md). Po ponownym uruchomieniu programu Visual Studio ponownie otwórz rozwiązanie, aby utworzyć testy jednostkowe, a następnie wybierz zainstalowanych platform tutaj:

 ![Wybierz inne frameworka testów jednostkowych zainstalowanych](../test/media/createunittestsdialogextensions.png "CreateUnitTestsDialogExtensions")

 Z klas zastępczych testu jednostki zostanie utworzona przy użyciu wybranej platformy.
