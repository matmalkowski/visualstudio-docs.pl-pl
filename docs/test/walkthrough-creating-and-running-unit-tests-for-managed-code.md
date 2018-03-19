---
title: "Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla zarządzanego kodu w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 74e364b9ea3660c8daa58b75bb6ba74f9af26c69
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla zarządzanego kodu

W tym przewodniku będzie kroku użytkownika przez proces tworzenia, uruchamiania i dostosowywania serii testów jednostkowych za pomocą frameworka testów jednostkowych Microsoft dla kodu zarządzanego i programu Visual Studio Explorer testu. Rozpoczynać się od projektu C#, który jest w fazie projektowania, Utwórz testy, które wykonuje jego kod, uruchom testy i przejrzeć wyniki. Następnie możesz zmienić kod projektu i ponownie uruchom testy.

 Ten temat zawiera następujące sekcje:

 [Przygotowanie przewodnika](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)

 [Tworzenie projektu testu jednostkowego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)

 [Tworzenie klasy testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)

-   [Wymagania dotyczące klasy testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)

 [Tworzenie pierwszej metody testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)

-   [Wymagania dotyczące metody testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)

 [Tworzenie i uruchamianie testu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)

 [Usuń kod i ponownie uruchomić testy](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)

 [Użyj testów jednostkowych, aby poprawić kod](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)

> [!NOTE]
>  W tym przewodniku zastosowano frameworka testów jednostkowych Microsoft dla kodu zarządzanego. Eksplorator testów również można uruchomić testy z innej jednostki testu struktur, co ma kart sieciowych w Eksploratorze testów. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

> [!NOTE]
>  Aby uzyskać informacje o sposobie uruchamiania testów z wiersza polecenia, zobacz [wskazówki: za pomocą narzędzia wiersza polecenia testowego](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867).

## <a name="prerequisites"></a>Wymagania wstępne

-   Projekt Bank. Zobacz [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md).

##  <a name="BKMK_Prepare_the_walkthrough"></a> Przygotowanie przewodnika

1.  Otwórz program Visual Studio.

2.  Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

3.  W obszarze **zainstalowane szablony**, kliknij przycisk **Visual C#**.

4.  Na liście typów aplikacji, kliknij **biblioteki klas**.

5.  W **nazwa** wpisz `Bank` , a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli nazwa "Bank" jest już używana, wybierz inną nazwę dla projektu.

     Nowy projekt Bank jest tworzone i wyświetlane w Eksploratorze rozwiązań plik Class1.cs otwarty w edytorze kodu.

    > [!NOTE]
    > Jeśli plik Class1.cs nie jest otwarty w edytorze kodu, kliknij dwukrotnie plik Class1.cs w Eksploratorze rozwiązań, aby go otworzyć.

6.  Kopiowanie kodu źródłowego z [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md).

7.  Zastąp kod z oryginalnej zawartości Class1.cs [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md).

8.  Zapisz plik jako BankAccount.cs

9. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

 Masz teraz projektu o nazwie Bank. Zawiera kod źródłowy do testowania i narzędzia do testowania go przy użyciu. Przestrzeń nazw dla banku **BankAccountNS**, zawiera publicznej klasy **waluty**, metody, której będzie testowane w poniższych procedurach.

 W tym szybki start, możemy skupić się na `Debit` metody. Metoda debetowa jest wywoływane, gdy wycofania pieniędzy konta i zawiera następujący kod:

```csharp
// method under test
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}
```

##  <a name="BKMK_Create_a_unit_test_project"></a> Tworzenie projektu testu jednostki
 **Wymagań wstępnych**: wykonaj kroki opisane w procedurze [przygotowanie przewodnika](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).

### <a name="to-create-a-unit-test-project"></a>Aby utworzyć jednostkowy projekt testowy

1.  Na **pliku** menu, wybierz **Dodaj**, a następnie wybierz pozycję **nowy projekt...** .

2.  W oknie dialogowym Nowy projekt, rozwiń węzeł **zainstalowana**, rozwiń węzeł **Visual C#**, a następnie wybierz pozycję **testu**.

3.  Wybierz z listy szablonów **jednostkowy projekt testowy**.

4.  W **nazwa** wprowadź BankTest, a następnie wybierz pozycję **OK**.

     **BankTests** projekt zostanie dodany do **Bank** rozwiązania.

5.  W **BankTests** projekt, Dodaj odwołanie do **Bank** rozwiązania.

     W Eksploratorze rozwiązań wybierz **odwołania** w **BankTests** projektu, a następnie wybierz pozycję **Dodawanie odwołania...**  z menu kontekstowego.

6.  W oknie dialogowym Menedżera odwołań, rozwiń węzeł **rozwiązania** , a następnie sprawdź **Bank** elementu.

##  <a name="BKMK_Create_the_test_class"></a> Tworzenie klasy testowej
 Potrzebujemy klasy testowej sprawdzania `BankAccount` klasy. Możemy użyć UnitTest1.cs, który został wygenerowany przez szablon projektu, ale możemy należy nadać i klasy nazwy opisowej. Firma Microsoft może zrobić w jednym kroku, zmiana nazwy pliku w Eksploratorze rozwiązań.

 **Zmiana nazwy pliku — klasa**

 W Eksploratorze rozwiązań wybierz plik UnitTest1.cs w projekcie BankTests. Z menu kontekstowego wybierz **zmienić**, a następnie zmień nazwę pliku na BankAccountTests.cs. Wybierz **tak** w oknie dialogowym z pytaniem, jeśli chcesz zmienić wszystkie odwołania do projektu do elementu kodu "UnitTest1". Ten krok zmienia nazwę klasy, która ma `BankAccountTest`.

 Plik BankAccountTests.cs zawiera teraz następujący kod:

```csharp
// unit test code
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

 **Dodawanie przy użyciu instrukcji w projekcie w ramach testu**

 Można także dodać przy użyciu instrukcji do klasy, aby poinformować nas, wywołują projektu w ramach testu bez przy użyciu w pełni kwalifikowanej nazwy. W górnej części pliku klasy należy dodać:

```csharp
using BankAccountNS;
```

###  <a name="BKMK_Test_class_requirements"></a> Wymagania dotyczące klasy testowej
 Minimalne wymagania dla klasy testowej są następujące:

-   `[TestClass]` Atrybut jest wymagany w jednostce Microsoft testowania framework do zarządzanego kodu dla dowolnej klasy, która zawiera metody testowe jednostki, które mają być uruchamiane w Eksploratorze testów.

-   Każda metoda ma Eksploratora testów do uruchomienia testu musi mieć `[TestMethod]`atrybutu.

 Może mieć inne klasy jednostkowy projekt testowy, które nie mają `[TestClass]` atrybutu, a może mieć inne metody w klasie testu, które nie mają `[TestMethod]` atrybutu. Te klasy i metody można użyć w metody testu.

##  <a name="BKMK_Create_the_first_test_method"></a> Tworzenie pierwszej metody testowej
 W tej procedurze, firma Microsoft będzie zapisywać, metody, aby sprawdzić działanie testu jednostkowego `Debit` metody `BankAccount` klasy. Metoda to wymienione powyżej.

 Analizując metody w ramach testu, możemy ustalić, czy co najmniej trzy zachowania, które muszą zostać sprawdzone:

1.  Metoda zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli kwota debetowa jest większa niż równowagi.

2.  Również zgłasza `ArgumentOutOfRangeException` Jeśli kwota debetowa jest mniejsza od zera.

3.  Jeśli kontroli w 1.) i 2.) są spełnione, metoda odejmuje kwoty z danym koncie.

 W naszym pierwszego testu możemy zweryfikować, że prawidłową kwotę (po jednym jest mniejsza niż saldo konta i jest większa od zera) wycofuje poprawną ilość z konta.

### <a name="to-create-a-test-method"></a>Aby utworzyć metody testowej

1.  Dodaj using `BankAccountNS;` instrukcji do pliku BankAccountTests.cs.

2.  Dodaj następującą metodę do tego `BankAccountTests` klasy:

    ```csharp
    // unit test code
    [TestMethod]
    public void Debit_WithValidAmount_UpdatesBalance()
    {
        // arrange
        double beginningBalance = 11.99;
        double debitAmount = 4.55;
        double expected = 7.44;
        BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

        // act
        account.Debit(debitAmount);

        // assert
        double actual = account.Balance;
        Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
    }
    ```

 Ta metoda jest raczej prosta. Skonfigurowanie nowego `BankAccount` obiekt z saldo początkowe, a następnie cofnąć prawidłową kwotę. Używamy frameworka testów jednostkowych Microsoft dla kodu zarządzanego <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> metody, aby potwierdzić, że saldo końcowe oczekujemy.

###  <a name="BKMK_Test_method_requirements"></a> Wymagania dotyczące metody testowej
 Metoda testowa musi spełniać następujące wymagania:

-   Metoda musi być dekorowane za `[TestMethod]` atrybutu.

-   Metoda musi zwracać `void`.

-   Metoda nie może mieć parametrów.

##  <a name="BKMK_Build_and_run_the_test"></a> Tworzenie i uruchamianie testu

### <a name="to-build-and-run-the-test"></a>Aby skompilować i uruchomić test

1.  Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

     Jeśli nie ma żadnych błędów, z zostanie wyświetlone okno UnitTestExplorer **Debit_WithValidAmount_UpdatesBalance** na liście **nie Uruchom testy** grupy. Eksplorator testów nie jest wyświetlany po pomyślnej kompilacji, jeśli **testu** menu, wybierz **Windows**, a następnie wybierz **Eksploratora testów**.

2.  Wybierz **Uruchom wszystkie** do uruchomienia testu. Ponieważ test jest uruchomiony na pasku stanu w górnej części okna jest animowany. Po zakończeniu uruchomienia testu pasku włącza zielony przekazania wszystkich metod lub czerwony, jeśli którykolwiek z testów nie powiedzie się.

3.  W takim przypadku testu zakończyć się niepowodzeniem. Metoda testowa została przeniesiona do **testy nie powiodło się**. Grupa. Wybierz metodę w Eksploratorze testów, aby wyświetlić szczegóły w dolnej części okna.

##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Usuń kod i ponownie uruchomić testy
 **Analizuj wyniki testów**

 Wynik testu zawiera komunikat zawierający opis błędu. Dla `AreEquals` metody komunikat wyświetlany przez możesz oczekiwanym ((**Oczekiwano\<*XXX*>**parametru) i co faktycznie otrzymano (  **Rzeczywiste\<*YYY* >**  parametru). Oczekiwaną saldo zrezygnować z saldo początkowe, ale zamiast tego wzrosła o ilość wycofanie.

 Ponowne testy kodu debetowa pokazuje, że test jednostkowy zakończyła się pomyślnie, w poszukiwaniu błędów. Ilość wycofanie jest dodawany do saldo konta, gdy powinna być odjęta.

 **Popraw błąd**

 Aby naprawić błąd, po prostu zastąpić wiersza

```csharp
m_balance += amount;
```

 with

```csharp
m_balance -= amount;
```

 **Ponowne uruchomienie testu**

 W Eksploratorze testów, wybierz **Uruchom wszystkie** ponowne uruchomienie testu. Pasek czerwony/zielony włącza zielony i test zostanie przeniesiony do **przekazany testy** grupy.

##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Użyj testów jednostkowych, aby poprawić kod
 W tej sekcji opisano, jak procesem iteracyjnym analizy, programowanie testów jednostkowych i refaktoryzacji może pomóc zwiększyć kodu produkcyjnego bardziej niezawodny i efektywny.

 **Analiza problemów**

 Po utworzeniu metody testowej, aby upewnić się, że prawidłową kwotę jest prawidłowo odjąć `Debit` metody, możemy włączyć w pozostałych przypadkach w naszym oryginalnego analizy:

1.  Metoda zgłasza `ArgumentOutOfRangeException` Jeśli kwota debetowa jest większa niż równowagi.

2.  Również zgłasza `ArgumentOutOfRangeException` Jeśli kwota debetowa jest mniejsza od zera.

 **Tworzenie metody testowe**

 Jest to pierwsza próba utworzenia metody testowej do rozwiązania tych problemów prawdopodobnie obietnicy:

```csharp
//unit test method
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    account.Debit(debitAmount);

    // assert is handled by ExpectedException
}
```

 Używamy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atrybut do potwierdzenia, że zgłosił wyjątek prawo. Atrybut powoduje, że test, aby zakończyć się niepowodzeniem, chyba że `ArgumentOutOfRangeException` jest generowany. Wykonywania testu z obu dodatnie i ujemne `debitAmount` wartości i tymczasowo modyfikacja metody w ramach testu ma zostać zgłoszony ogólnego <xref:System.ApplicationException> gdy wartość jest mniejsza od zera pokazuje test działa prawidłowo. Do testowania w przypadku gdy ilość wycofane jest większy niż saldo, konieczne jest:

1.  Utworzenie nowej metody testu o nazwie `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2.  Skopiuj treści metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nowej metody.

3.  Ustaw `debitAmount` na większą niż równowagi.

 **Uruchom testy**

 Uruchomione z różnymi wartościami dla dwóch metod `debitAmount` pokazuje, że testy odpowiednio obsługiwać naszych pozostałych przypadkach. Uruchamianie wszystkich trzech testach upewnij się, czy opisano wszystkich przypadków naszych oryginalnego analizy.

 **Kontynuować analizę**

 Nieco niepokojące są również jednak ostatnich dwóch metod. Firma Microsoft nie może być niektórych warunek, który w kodzie w ramach testu zgłasza wyjątek, gdy albo uruchomień testów. Sposób rozróżnienie dwóch warunków będą przydatne. Jak możemy Pomyśl o problemie więcej, okaże się że wiedząc warunek, który zostało naruszone wzrośnie naszych zaufania w testach. Te informacje również najprawdopodobniej będzie przydatne do mechanizmu produkcji, który obsługuje wyjątek, gdy jest generowany przez metodę w ramach testu. Generowanie więcej informacji, gdy metoda zgłasza umożliwi wszystkie dane, ale `ExpectedException` atrybutu nie może dostarczyć te informacje.

 Ponownie patrzeć testowana metoda widzimy zarówno warunkowe instrukcje użyj `ArgumentOutOfRangeException` Konstruktor, który przyjmuje nazwę argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

 Wyszukiwanie biblioteki MSDN odnajdywania konstruktora istnieje, która raportuje znacznie bardziej rozbudowane informacje. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` zawiera nazwę argumentu, wartość argumentu i wiadomości zdefiniowane przez użytkownika. Firma Microsoft może zrefaktoryzuj metody w ramach testu do używania tego konstruktora. Lepszy możemy użyć typów publicznie dostępnych elementów członkowskich określenie błędów.

 **Zrefaktoryzuj kod w ramach testu**

 Definiujemy najpierw dwie stałe komunikaty o błędach w zakresie klasy:

```csharp
// class under test
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";
```

 Firma Microsoft następnie zmodyfikować dwóch warunkowe instrukcje w `Debit` metody:

```csharp
// method under test
// ...
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
// ...
```

 **Zrefaktoryzuj metody testowe**

 W naszym metody testowej najpierw usuwamy `ExpectedException` atrybutu. W tym miejscu możemy catch zwrócony wyjątek i sprawdź, został zgłoszony w instrukcji poprawne warunku. Jednak firma Microsoft musi teraz zdecyduj, jedną z dwóch opcji, aby sprawdzić naszych pozostałe postanowienia. Na przykład w `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` metody, firma Microsoft można wykonać jedną z następujących czynności:

-   Potwierdzenia, że `ActualValue` właściwość wyjątku (drugi parametr funkcji `ArgumentOutOfRangeException` Konstruktor) jest większa niż saldo początkowe. Ta opcja wymaga, aby firma Microsoft testuje `ActualValue` właściwość wyjątku przed `beginningBalance` zmiennej metody testowej i wymaga także a następnie sprawdź, czy `ActualValue` jest większa od zera.

-   Potwierdzenia, że komunikat (trzeci parametr konstruktora) zawiera `DebitAmountExceedsBalanceMessage` zdefiniowane w `BankAccount` klasy.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Metoda framework testów jednostkowych firmy Microsoft umożliwia nam zweryfikować druga opcja bez obliczeń, które są wymagane w pierwszej opcji.

 Druga próba wprowadzenia zmian `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` może wyglądać tak:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
    }
}
```

 **Sprawdź jeszcze raz, Nadpisz i Analizuj ponownie**

 Gdy firma Microsoft sprawdź jeszcze raz metody testowe o różnych wartościach możemy występują następujące fakty:

1.  Firma Microsoft catch Napraw błąd przy użyciu assert gdzie `debitAmount` większą od pozostałej `Contains` assert przekazuje wyjątek jest ignorowany i dlatego przekazuje metody testowej. Jest to zachowanie, którą chcemy udostępnić.

2.  Jeśli używamy `debitAmount` jest mniejszy niż 0, assert kończy się niepowodzeniem, ponieważ zwracany jest niewłaściwy komunikat o błędzie. Assert nie powiedzie się także jeśli wprowadzeniu tymczasowej `ArgumentOutOfRange` wyjątek w momencie innej metody w ścieżce kodu testu. Zbyt jest dobra.

3.  Jeśli `debitAmount` wartość jest prawidłowa, (tj. mniej niż saldo jednak większa niż zero, nie jest wyjątek, więc assert nigdy nie zostanie przechwycony. Przekazuje metody testowej. To nie jest dobra, ponieważ chcemy metody testowej niepowodzenie, jeśli nie jest wyjątek.

 Trzeci fakt jest na usterkę w naszym metody testowej. Aby spróbować rozwiązać ten problem, dodamy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> assert na końcu metody testowej do obsługi w przypadku, gdy nie wyjątku.

 Jednak ponowne pokazuje, że test teraz wynik negatywny, jeśli poprawne wyjątek. Instrukcji catch resetuje wyjątek i metody kontynuuje wykonywanie, niepowodzeniem na nowe potwierdzenia. Aby rozwiązać problem nowe, dodamy `return` instrukcji po `StringAssert`. Ponowne potwierdza Naprawiono naszych problemów. Naszym ostateczna wersja `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wygląda podobnie do następującego:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
        return;
    }
    Assert.Fail("No exception was thrown.");
}
```

W tej sekcji końcowego pracy robiliśmy poprawy naszych kod testu doprowadziło do bardziej niezawodny i informacyjny metody testowe. Ale co ważniejsze, dodatkowe analizy również doprowadziło do lepszego kodu w naszym projektu w ramach testu.
