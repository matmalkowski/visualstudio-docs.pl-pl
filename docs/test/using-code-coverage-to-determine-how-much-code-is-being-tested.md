---
title: Pokrycie kodu w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ec694fc904df2fd15ada008d9cb9f64f1df8492e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Użyj pokrycie kodu, aby określić, ile kodu jest poddawana testom

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny obejmować lub pokrywać znaczną część kodu.

Analizy pokrycia kodu mogą dotyczyć zarówno kodów zarządzanych (CLI), jak i niezarządzanych (natywnych).

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

![Wyniki pokrycia kodu z kolorowanie](../test/media/codecoverage1.png)

 **Wymagania**

-   Visual Studio Enterprise

## <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Analizowanie pokrycia kodu w ramach testów jednostkowych w Eksploratorze testów

1.  Na **testu** menu, wybierz **Analizuj pokrycie kodu**.

2.  Aby wyświetlić wierszy, które zostały uruchomione, wybierz pozycję ![Pokaż ikonę kolorowanie pokrycia kodu](../test/media/codecoverage-showcoloringicon.png)**Pokaż kolorowanie pokrycia kodu**.

     Aby zmienić kolory lub użyj czcionką pogrubioną, wybierz **narzędzia** > **opcje** > **środowiska** > **czcionek i Kolory** > **Pokaż ustawienia dla: Edytor tekstu**. W obszarze **wyświetlania elementów**, Dostosuj zakres elementów.

3.  Jeśli wyniki wykażą niewielkie pokrycie, zbadaj części kodu, które nie są wykonywane, i napisz więcej testów, aby je pokryć. Zespoły deweloperów zazwyczaj dążą do około 80% pokrycia kodu. W niektórych sytuacjach dopuszczalne jest niższe zapotrzebowanie. Niższe zapotrzebowanie jest dopuszczalne np. tam, gdzie dany kod jest generowany na podstawie standardowego szablonu.

> [!TIP]
> - Upewnij się, że tej optymalizacji kompilatora jest wyłączona.
> - Jeśli pracujesz z kodem niezarządzanym (natywna), korzystanie z kompilacji debugowania
> - Upewnij się, że generowania plików PDB (symbol) dla każdego zestawu.

Jeśli nie otrzymasz wyniki spodziewasz się, zobacz [Rozwiązywanie problemów z pokrycia kodu](../test/troubleshooting-code-coverage.md). . Nie zapomnij Uruchom ponownie po zakończeniu aktualizacji kodu pokrycia kodu. Wyniki pokrycia i kolorowanie kodu nie są automatycznie aktualizowane po zmodyfikowaniu kodu ani po uruchomieniu testów.

## <a name="report-in-blocks-or-lines"></a>Raport w blokach lub wierszy

Pokrycie kodu jest liczony w *bloków*. Blok jest fragmentem kodu z dokładnie jednym punktem wejścia i wyjścia.  Jeżeli przepływu sterowania programu przechodzi przez blok podczas uruchomienia testu, tym bloku jest traktowane jako objęte. To, ile razy użyto danego bloku, nie ma wpływu na wynik.

Może także zawierać wyniki wyświetlane w postaci liczby wierszy, wybierając **Dodaj/Usuń kolumny** w nagłówku tabeli. Jeżeli przebieg testu sprawdził wszystkie bloki kodu w każdym jego wierszu, liczy się to jako jeden wiersz. W przypadku gdy wiersz zawiera bloki kodu, które były sprawdzane, oraz takie, które nie były, jest liczony jako wiersz częściowy.

Niektórzy użytkownicy preferują liczbę wierszy, ponieważ wartości procentowe ściślej odpowiadają rozmiarowi fragmentów, które widać w kodzie źródłowym. Duży blok obliczeń jest traktowany jako pojedynczy, nawet jeśli zajmuje wiele wierszy.

## <a name="manage-code-coverage-results"></a>Zarządzanie wyników pokrycia kodu

Okno Wyniki pokrycia kodu zwykle przedstawia najnowszy wynik uruchomionych testów. Wyniki będą się różnić, jeśli zmienisz ich dane lub za każdym razem uruchomisz tylko niektóre z testów.

Okno pokrycia kodu może służyć również do wyświetlania poprzednich wyników lub wyników uzyskanych na innych komputerach.

Można scalać wyniki kilku uruchomień, na przykład tych, które używają różnych danych testowych.

-   **Aby wyświetlić poprzedniego zestawu wyników**, wybierz ją z menu rozwijanego. W menu pojawia się tymczasowa lista, która jest czyszczona po otwarciu nowego rozwiązania.

-   **Aby wyświetlić wyniki z poprzedniej sesji**, wybierz **importowanie wyników pokrycia kodu**, przejdź do folderu TestResults w rozwiązaniu i zaimportować plik .coverage.

    Kolorowanie pokrycia może być niepoprawne, jeśli kod źródłowy zmienił się od czasu wygenerowania pliku .coverage.

-   **Aby odczytywać wyników jako tekst**, wybierz **eksportowanie wyników pokrycia kodu**. Spowoduje to wygenerowanie pliku .coveragexml, który można odczytać. Można go też przetwarzać z innymi narzędziami lub łatwo wysłać pocztą.

-   **Aby wysyłać wyniki do kogoś innego**, Wyślij plik .coverage lub .coveragexml eksportowanego pliku. Następnie można zaimportować plik. Jeśli mają one tę samą wersję kodu źródłowego, mogą odczytać kolorowanie pokrycia.

## <a name="merge-results-from-different-runs"></a>Wyniki z różnych uruchomień scalania

W niektórych sytuacjach, w zależności od danych testowych, używane będą różne bloki w kodzie. W związku z tym można wykorzystać wyniki z różnych przebiegów testów.

 Można na przykład założyć, że po uruchomieniu testu z wpisem „2” okaże się, że pokryto 50% określonej funkcji. Po uruchomieniu testu po raz drugi z wpisem „-2” widoczne kolorowanie pokrycia obejmie pozostałe 50% funkcji. Teraz należy scalić wyniki z dwóch przebiegów testów, a raport i widok kolorowania pokrycia pokaże 100% pokrycia funkcji.

 Użyj ![ikony dla przycisku scalania w oknie pokrycie kodu](../test/media/codecoverage-mergeicon.png "CodeCoverage MergeIcon")**scalania wyników pokrycia kodu** w tym celu. Można wybrać dowolną kombinację ostatnich uruchomień lub zaimportowanych wyników. Aby połączyć wyeksportowane wyniki, należy je najpierw zaimportować.

 Użyj **eksportowanie wyników pokrycia kodu** być zapisane wyniki w operacji scalania.

### <a name="limitations-in-merging"></a>Ograniczenia w scalaniu

-   W przypadku scalania danych pokrycia z różnych wersji kodu wyniki są wyświetlane oddzielnie i nie są połączone. Aby uzyskać w pełni połączone wyniki, należy zastosować tę samą kompilację kodu, zmieniając tylko dane testowe.

-   W przypadku scalania pliku wyników, które zostały wyeksportowane, a następnie zaimportowane, wyniki można przeglądać tylko według wierszy, a nie bloków. Użyj **Dodaj/Usuń kolumny** polecenie w celu wyświetlenia danych wiersza.

-   W przypadku scalania wyników z testów programu ASP.NET wyniki dla oddzielnych testów są wyświetlane, ale nie są połączone. Dotyczy to tylko samych artefaktów ASP.NET: wyniki dla innych zestawów zostaną połączone.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Wykluczanie elementów z wyników pokrycia kodu

Można chcieć wykluczyć określone elementy w kodzie z oceny pokrycia, jeśli np. kod jest generowany na podstawie szablonu tekstu. Dodaj atrybut `System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverage` do żadnej z następujących elementów kodu: klasy, struktury, metodę, właściwość, metody ustawiającej lub metody pobierającej, zdarzenia. Należy zauważyć, że wykluczenie klasy nie wyklucza jej klas pochodnych.

 Na przykład:

```csharp

using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }

```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Wyklucz elementy w kodzie natywnym kodzie C++

Aby wykluczyć niezarządzane (natywne) elementy kodu C++:

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Użyj następujących makr:

 `ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

 `ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

-   *ExclusionName* jest dowolną unikatową nazwę.

-   *FunctionName* jest nazwą FQDN funkcji. Może ona zawierać symbole wieloznaczne. Na przykład aby wykluczyć wszystkie funkcje klasy, należy napisać `MyNamespace::MyClass::*`

-   *SourceFilePath* jest lokalną lub ścieżkę UNC pliku .cpp. Może ona zawierać symbole wieloznaczne. Poniższy przykład wyklucza wszystkie pliki w określonym katalogu: `\\MyComputer\Source\UnitTests\*.cpp`

-   `#include <CodeCoverage\CodeCoverage.h>`

-   Miejsce wywołuje wyłączenie makr w globalnej przestrzeni nazw, nie w dowolnym obszarze nazw lub klasie.

-   Można umieścić wyłączenia w pliku kodu testu jednostkowego lub w pliku kodu aplikacji.

-   Wykluczenia muszą być skompilowane jako kodu niezarządzanego (natywna), przez ustawienie opcji kompilatora lub za pomocą `#pragma managed(off)`.

> [!NOTE]
> Aby wykluczyć funkcji w języku C + +/ CLI kodu, zastosuj atrybut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` funkcji. To jest tak samo jak w języku C#.

### <a name="include-or-exclude-additional-elements"></a>Dołącz lub Wyklucz dodatkowe elementy

Analizy pokrycia kodu są wykonywane tylko na zestawach, które są ładowane i dla których plik .pdb jest dostępny w tym samym katalogu co plik .exe lub .dll. Dlatego w pewnych okolicznościach można rozszerzyć zbiór zestawów, włączony przez uzyskanie kopii odpowiednich plików .pdb.

Można zwiększyć kontrolę nad tym, które zespoły i elementy są zaznaczone dla analizy pokrycia kodu przez napisanie pliku .runsettings. Można np. wykluczyć zestawy określonego typu bez konieczności dodawania atrybutów do ich klas. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-the-build-service"></a>Analizuj pokrycie kodu w usłudze kompilacji

Podczas sprawdzania kodu testy będą uruchamiane na serwerze kompilacji, razem z innymi testami pozostałych członków zespołu. (Jeśli nie zostało już skonfigurować tę funkcjonalność, zobacz [Uruchom testy w procesie budowy](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) Jest on przydatny do analizy pokrycia kodu w usłudze kompilacji, ponieważ zapewniającą najbardziej aktualnych i kompleksowy obraz pokrycia w całego projektu. Zawiera również automatycznych testów systemowych i innych kodowane testy, które zwykle nie uruchamiane na komputerach programowanie.

1. W programie Team Explorer Otwórz **kompilacje**, a następnie dodaj lub Edytuj definicję kompilacji.

2. Na **procesu** rozwiń pozycję **testów automatycznych**, **źródła testu**, **parametrów uruchomieniowych**. Ustaw **typu pliku ustawień uruchamiania** do **włączonym pokryciem kodu**.

   Jeśli masz więcej niż jedną definicję źródła testów, powtórz ten krok dla każdej z nich.

   ![Ustawienie definicji kompilacji dla pokrycia kodu](../test/media/codecoverage-plaincc.png "CodeCoverage plainCC")

> [!TIP]
> Jeśli nie istnieje żadne pole o nazwie **typu z Uruchom plik ustawień**, zmień **Test Runner** właściwości. W obszarze **testów automatycznych**, wybierz pozycję **zestawu testowego** i kliknij przycisk wielokropka **[...]**  na końcu linii. W **Dodawanie/edytowanie testu** okna dialogowego, w obszarze **Test Runner**, wybierz **Visual Studio Test Runner**.

Po uruchomieniu kompilacji wyniki pokrycia kodu są dołączane do przebiegu testowego i pojawiają się w podsumowaniu kompilacji.

## <a name="analyze-code-coverage-in-a-command-line"></a>Analizuj pokrycie kodu w wierszu polecenia

Aby uruchomić testy z wiersza polecenia, należy użyć narzędzia vstest.console.exe. Pokrycie kodu jest opcją narzędzia vstest.console.exe.

1.  Uruchom wiersz polecenia programisty dla programu Visual Studio:

    W systemie Windows **Start** menu, wybierz **programu Visual Studio 2017** > **wiersz polecenia dla programu VS 2017 deweloperów**.

2.  Uruchom następujące polecenie:

    `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage`

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli nie widzisz wyników pokrycia kodu, [Rozwiązywanie problemów z pokrycia kodu](../test/troubleshooting-code-coverage.md) temacie mogą pomóc.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Pokrycie kodu — wyszukiwanie błędów](../test/troubleshooting-code-coverage.md)
- [Testowanie jednostek kodu](../test/unit-test-your-code.md)
