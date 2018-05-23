---
title: Tworzenie i Uruchamianie testów jednostkowych zarządzanego kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 9cfcfab850d4d56589688eea0d5833400df9cb9d
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla zarządzanego kodu

Ten przewodnik zawiera kroki tworzenia, uruchomione, i dostosowywanie serii jednostki testów za pomocą frameworka testów jednostkowych Microsoft dla kodu zarządzanego i Visual Studio **Eksploratora testów**. Rozpoczynać się od projektu C#, który jest w fazie projektowania, Utwórz testy, które wykonuje jego kod, uruchom testy i przejrzeć wyniki. Następnie możesz zmienić kod projektu i ponownie uruchom testy.

> [!NOTE]
> W tym przewodniku zastosowano frameworka testów jednostkowych Microsoft dla kodu zarządzanego. **Testowanie Explorer** również uruchomić testy z innej jednostki platform testów, kartami dla **Eksploratora testów**. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

> [!NOTE]
> Aby uzyskać informacje o sposobie uruchamiania testów z wiersza polecenia, zobacz [wskazówki: Użyj narzędzia wiersza polecenia testowego](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867).

## <a name="prerequisites"></a>Wymagania wstępne

- Projekt Bank. Zobacz [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Tworzenie projektu do testowania

1. Otwórz program Visual Studio.

2. Na **pliku** menu, wybierz opcję **nowy** > **projektu**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

3. W obszarze **zainstalowane szablony**, kliknij przycisk **Visual C#**.

4. Na liście typów aplikacji, kliknij **biblioteki klas**.

5. W **nazwa** wpisz `Bank` , a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli nazwa "Bank" jest już używana, wybierz inną nazwę dla projektu.

     Nowy projekt Bank jest tworzone i wyświetlane w **Eksploratora rozwiązań** z *Class1.cs* plik otwarty w edytorze kodu.

    > [!NOTE]
    > Jeśli *Class1.cs* plik nie jest otwarty w edytorze kodu, kliknij dwukrotnie plik *Class1.cs* w Eksploratorze rozwiązań, aby go otworzyć.

6. Kopiowanie kodu źródłowego z [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md)i Zastąp zawartość oryginalnego *Class1.cs* ze skopiowanego kodu.

7. Zapisz plik jako *BankAccount.cs*.

8. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

Masz teraz projektu o nazwie Bank. Zawiera kod źródłowy do testowania i narzędzia do testowania go przy użyciu. Obszar nazw dla banku, BankAccountNS, zawiera klasa publiczna waluty, której metody przetestujesz, w poniższych procedurach.

W tym artykule testy skupić się na metodzie debetowa. Metoda debetowa jest wywoływane, gdy pieniężnego zostanie wycofany z konta. W tym miejscu znajduje się definicja metody:

```csharp
// Method to be tested.
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

## <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

1. Na **pliku** menu, wybierz opcję **Dodaj** > **nowy projekt**.

2. W oknie dialogowym Nowy projekt, rozwiń węzeł **zainstalowana**, rozwiń węzeł **Visual C#**, a następnie wybierz pozycję **testu**.

3. Wybierz z listy szablonów **jednostkowy projekt testowy**.

4. W **nazwa** wprowadź `BankTests`, a następnie wybierz **OK**.

     **BankTests** projekt zostanie dodany do **Bank** rozwiązania.

5. W **BankTests** projekt, Dodaj odwołanie do **Bank** projektu.

     W Eksploratorze rozwiązań wybierz **odwołania** w **BankTests** projektu, a następnie wybierz pozycję **Dodaj odwołanie** z menu kontekstowego.

6. W oknie dialogowym Menedżera odwołań, rozwiń węzeł **rozwiązania** , a następnie sprawdź **Bank** elementu.

## <a name="create-the-test-class"></a>Tworzenie klasy testowej

Utwórz klasę testu Aby sprawdzić `BankAccount` klasy. Można użyć *UnitTest1.cs* pliku, który został wygenerowany przez szablon projektu, ale nadaj plikowi i nazwy opisowej klasy. Możesz to zrobić w jednym kroku przez zmianę nazwy pliku w **Eksploratora rozwiązań**.

### <a name="rename-a-class-file"></a>Zmień nazwę pliku — klasa

W **Eksploratora rozwiązań**, wybierz pozycję *UnitTest1.cs* plik w projekcie BankTests. Z menu kontekstowego wybierz **zmienić**, a następnie zmień nazwę pliku do *BankAccountTests.cs*. Wybierz **tak** w oknie dialogowym z pytaniem, jeśli chcesz zmienić wszystkie odwołania do elementu kodu `UnitTest1` w projekcie.

Ten krok zmienia nazwę klasy, która ma `BankAccountTests`. *BankAccountTests.cs* plik zawiera teraz następujący kod:

```csharp
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

### <a name="add-a-using-statement-to-the-project-under-test"></a>Dodawanie przy użyciu instrukcji w projekcie w ramach testu

Można również dodać `using` instrukcji do klasy, aby można było wywołać w projekcie w ramach testu bez używające w pełni kwalifikowanych nazw. W górnej części pliku klasy należy dodać:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Wymagania dotyczące klasy testowej

Dostępne są następujące minimalne wymagania dla klasy testowej:

- `[TestClass]` Atrybut jest wymagany w jednostce Microsoft testowania framework do zarządzanego kodu dla dowolnej klasy, która zawiera metody testowe jednostki, które mają być uruchamiane w Eksploratorze testów.

- Każda metoda ma Eksploratora testów do uruchomienia testu musi mieć `[TestMethod]`atrybutu.

Może mieć inne klasy jednostkowy projekt testowy, które nie mają `[TestClass]` atrybutu, a może mieć inne metody w klasie testu, które nie mają `[TestMethod]` atrybutu. Te klasy i metody można użyć w metody testu.

## <a name="create-the-first-test-method"></a>Tworzenie pierwszej metody testowej

W tej procedurze przedstawiono tworzenie metody, aby sprawdzić działanie testu jednostkowego `Debit` metody `BankAccount` klasy. `Debit` Metody przedstawiono wcześniej w tym artykule.

Istnieją co najmniej trzy zachowania, które muszą zostać sprawdzone:

- Metoda zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli kwota debetowa jest większa niż równowagi.

- Metoda zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli kwota debetowa jest mniejsza od zera.

- Jeśli kwota debetowa jest prawidłowa, metoda odejmuje kwoty debetowa z danym koncie.

> [!TIP]
> Można usunąć domyślnego `TestMethod1` metody, ponieważ nie będzie go używać w tym przewodniku.

### <a name="to-create-a-test-method"></a>Aby utworzyć metody testowej

Pierwszy test sprawdza, czy prawidłową kwotę (czyli taki, który jest mniejsza niż saldo konta i większa od zera) wycofuje poprawną ilość z konta. Dodaj następującą metodę do tego `BankAccountTests` klasy:

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Metoda jest prosta: Konfiguruje nowy `BankAccount` obiekt z saldo początkowe, a następnie wycofuje prawidłową kwotę. Używa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> metodę, aby sprawdzić, czy saldo końcowe jest zgodnie z oczekiwaniami.

### <a name="test-method-requirements"></a>Wymagania dotyczące metody testowej

Metoda testowa musi spełniać następujące wymagania:

- Ma ona `[TestMethod]` atrybutu.

- Zwraca `void`.

- Nie może on mieć parametrów.

## <a name="build-and-run-the-test"></a>Tworzenie i uruchamianie testu

1. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

   Jeśli nie ma żadnych błędów **Eksploratora testów** występuje z **Debit_WithValidAmount_UpdatesBalance** na liście **nie Uruchom testy** grupy.

   > [!TIP]
   > Jeśli **Eksploratora testów** nie jest wyświetlana po pomyślnej kompilacji, wybierz **testu** menu, wybierz **systemu Windows**, a następnie wybierz pozycję **Eksploratora testów**.

2. Wybierz **Uruchom wszystkie** do uruchomienia testu. Po uruchomieniu testu jest animowany paska stanu w górnej części okna. Po zakończeniu uruchomienia testu pasku włącza zielony przekazania wszystkich metod lub czerwony, jeśli którykolwiek z testów nie powiedzie się.

3. W takim przypadku test zakończy się niepowodzeniem. Metoda testowa została przeniesiona do **testy nie powiodło się** grupy. Wybierz metodę w **Eksploratora testów** Aby wyświetlić szczegóły w dolnej części okna.

## <a name="fix-your-code-and-rerun-your-tests"></a>Usuń kod i ponownie uruchomić testy

**Analizuj wyniki testów**

Wynik testu zawiera komunikat zawierający opis błędu. Dla `AreEquals` metoda, komunikat wyświetla oczekiwanym ( **Oczekiwano\<*wartość* >**  parametru) i co faktycznie otrzymano ( **Rzeczywiste\<*wartość* >** parametru). Oczekiwano saldo zmniejszyć, ale zamiast tego go faktycznie zwiększyć ilość wycofanie.

Test jednostkowy ma niewykrytych usterki: ilość wycofanie *dodane* na koncie, lecz powinna być *odejmować*.

**Popraw błąd**

Aby naprawić błąd, należy zastąpić wiersz:

```csharp
m_balance += amount;
```

Z:

```csharp
m_balance -= amount;
```

**Ponowne uruchomienie testu**

W Eksploratorze testów, wybierz **Uruchom wszystkie** ponowne uruchomienie testu. Pasek czerwony/zielony włącza zielony, wskazujący przekazany testu i test zostanie przeniesiony do **przekazany testy** grupy.

## <a name="use-unit-tests-to-improve-your-code"></a>Użyj testów jednostkowych, aby poprawić kod

W tej sekcji opisano, jak procesem iteracyjnym analizy, programowanie testów jednostkowych i refaktoryzacji może pomóc zwiększyć kodu produkcyjnego bardziej niezawodny i efektywny.

**Analiza problemów**

Po utworzeniu metody testowej, aby potwierdzić poprawnie odliczona prawidłową kwotę przy `Debit` metody. Teraz, sprawdź, czy metoda zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli kwota debetowa:

- większa niż saldo, lub
- mniejsze niż zero.

**Tworzenie metody testowe**

Utwórz metody testowej, aby zweryfikować poprawne zachowanie w sytuacji, gdy ilość debetowa jest mniejsza od zera:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atrybut do potwierdzenia, że zgłosił wyjątek poprawne. Atrybut powoduje, że test, aby zakończyć się niepowodzeniem, chyba że <xref:System.ArgumentOutOfRangeException> jest generowany. Metody w ramach testu ma zostać zgłoszony więcej ogólny zmodyfikowanie tymczasowo <xref:System.ApplicationException> gdy wielkość debetowa jest mniejsza od zera, test poprawne działanie&mdash;oznacza to, że nie powiedzie się.

Aby przetestować w przypadku, gdy ilość wycofane jest większy niż saldo, wykonaj następujące czynności:

1. Utworzenie nowej metody testu o nazwie `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Skopiuj treści metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nowej metody.

3. Ustaw `debitAmount` na większą niż równowagi.

**Uruchom testy**

Uruchomiona dwie metody testowe pokazuje testy działać poprawnie.

**Kontynuować analizę**

Jednak również niepokojące są ostatnich dwóch metod. Nie można mieć niektórych warunek, który w testowana metoda zgłasza wyjątek, po uruchomieniu tych testów. Niektóre sposób pozwalających dwa warunki kwota debetowa ujemny lub kwotę większą niż saldo, zwiększy z zaufania w testach.

Obejrzyj testowana metoda ponownie i zwróć uwagę, że oba warunkowe instrukcje używać `ArgumentOutOfRangeException` Konstruktor, który po prostu przyjmuje nazwę argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Brak Konstruktora służy raport znacznie bardziej rozbudowane informacje: <xref:System.ArgumentOutOfRangeException.%23ctor%2A> `(String, Object, String)` zawiera nazwę argumentu, wartość argumentu i wiadomości zdefiniowane przez użytkownika. Można zrefaktoryzuj metody w ramach testu do używania tego konstruktora. Lepszy można użyć typu publicznie dostępnych elementów członkowskich określenie błędów.

**Zrefaktoryzuj kod w ramach testu**

Najpierw należy zdefiniować dwa stałe komunikaty o błędach w zakresie klasy. Umieścić w klasie w ramach testu (`Bank`):

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Następnie należy zmodyfikować dwóch warunkowe instrukcje w `Debit` metody:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

**Zrefaktoryzuj metody testowe**

Usuń `ExpectedException` testowanie atrybutu metody i zamiast tego catch zwrócony wyjątek i weryfikowanie jego skojarzony wiadomości. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Metoda pozwala, aby porównać dwa ciągi.

Teraz `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` może wyglądać następująco:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

**Sprawdź jeszcze raz, Nadpisz i Analizuj ponownie**

Załóżmy, jest to błąd w metodzie w ramach testu i `Debit` — metoda nie nawet *throw* <xref:System.ArgumentOutOfRangeException>, nevermind output poprawne komunikat o wyjątku. Obecnie metoda testowa nie obsługuje tego przypadku. Jeśli `debitAmount` wartość jest prawidłowa (to znaczy mniejsza niż saldo, ale większa od zera), nie jest wyjątek, więc assert nigdy nie uruchamia się. Przekazuje jeszcze metody testowej. To nie jest dobra, ponieważ ma metody testowej niepowodzenie, jeśli nie jest wyjątek.

Jest to błąd w metodzie testowej. Aby rozwiązać ten problem, Dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> assert na końcu metody testowej do obsługi w przypadku, gdy nie wyjątku.

Jednak uruchomienie testu wskazuje, że test teraz *nie powiedzie się* Jeśli poprawne wyjątek. `catch` Bloku przechwytuje wyjątek, ale metoda kontynuuje wykonywanie nie powiedzie się na nowy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> potwierdzenia. Aby rozwiązać ten problem, Dodaj `return` instrukcji po `StringAssert` w `catch` bloku. Ponowne uruchomienie testu potwierdza, że problem został rozwiązany problem. Z ostateczną wersją `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wygląda podobnie do następującej:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

Ulepszenia kod testu doprowadziło do bardziej niezawodny i informacyjny metody testowe. Ale co ważniejsze, ich ulepszono również testowanego kodu.
