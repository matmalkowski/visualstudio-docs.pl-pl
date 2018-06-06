---
title: Ostrzeżenia wytyczne Core C++
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- cplusplus
ms.openlocfilehash: ef0b06be65322dc6a15f92b1d808d585960f0331
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746069"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Przy użyciu programy wytyczne Core C++
Wskazówki Core C++ są przenośny zestaw wskazówki, reguł i najlepsze rozwiązania dotyczące pisania kodu w języku C++ utworzone przez ekspertów C++ i projektantów. Program Visual Studio obsługuje obecnie podzbiór tych reguł jako część jej narzędzi analizy kodu dla języka C++. Podstawowe wytyczne są instalowane domyślnie w programie Visual Studio 2017 oraz są [dostępne jako pakietu NuGet dla programu Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Projekt wytycznych C++ Core
 Utworzone przez Bjarne Stroustrup i inne osoby, wskazówki Core C++ są przewodnik przy użyciu nowoczesnych wersji języka C++, bezpieczne i efektywnie. Wytyczne wyróżnianie statycznego typu bezpieczeństwa i bezpieczeństwa zasobów. Zidentyfikować sposobów, aby wyeliminować lub minimalizowanie najbardziej podatnych części języka i zasugerować jak kod był prostszy i wydajności więcej w niezawodny sposób. Wskazówki te są obsługiwane przez standardowe Foundation C++. Aby dowiedzieć się więcej, zajrzyj do dokumentacji [C++ podstawowe wskazówki](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)i uzyskać dostęp do plików projektu dokumentacji C++ podstawowe wskazówki na [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Włącz C++ podstawowe sprawdzanie wskazówki zawarte w analizy kodu
 Można włączyć analizy kodu w projekcie, wybierając **Włącz analizę kodu podczas kompilacji** checkbox w **analizy kodu** sekcji **strony właściwości** okno dialogowe projektu.

 ![Strony właściwości dla ustawienia ogólne analizy kodu](../code-quality/media/cppcorecheck_codeanalysis_general.png)

 Sprawdź Core C++ reguły są rozszerzenia do zestawów reguł domyślne uruchamianych podczas analizy kodu jest włączone. Ponieważ zasady Sprawdź Core C++ są opracowywane, niektóre reguły są utrwalonego, a niektóre może nie być gotowy do użycia na cały kod, ale nadal mogą służyć jako źródło informacji. Reguły są podzielone na dwie grupy: zwolniono i eksperymentalne. Możesz wybrać, czy do uruchamiania zasady zwolniony lub eksperymentalne we właściwościach projektu.

 ![Strony właściwości dla ustawień rozszerzenia analizy kodu](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

 Aby włączyć lub wyłączyć zestawy reguł sprawdzania Core C++, otwórz **strony właściwości** okna dialogowego dla projektu. W obszarze **właściwości konfiguracji**, rozwiń węzeł **analizy kodu**, **rozszerzenia**. W menu rozwijanym obok pozycji kontroli **włączyć sprawdzanie Core C++ (zwolnione)** lub **włączyć sprawdzanie Core C++ (eksperymentalne)**, wybierz **tak** lub **nr**. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

## <a name="examples"></a>Przykłady
 Oto przykład niektórych problemów, które można znaleźć reguły Sprawdź Core C++:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

 W tym przykładzie pokazano kilka ostrzeżeń, które można znaleźć reguły Sprawdź Core C++:

-   C26494 jest reguła Type.5: zawsze zainicjować obiektu.

-   C26485 jest reguła Bounds.3: nie zanikania tablicy na wskaźnik.

-   C26481 jest reguła Bounds.1: nie używaj arytmetyki wskaźnika. Zamiast nich należy używać słów kluczowych `span`.

 Jeśli zestawów reguł C++ Core Sprawdź analizy kodu nie zostaną zainstalowane i włączone podczas kompilowania tego kodu, pierwsze dwa ostrzeżenia są dane wyjściowe, ale trzeci jest pomijane. Oto przykładowy kod dane wyjściowe kompilacji:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Wytyczne Core C++ istnieją ułatwia pisanie kodu lepsze i bezpieczniejsze. Jednak jeśli masz wystąpienie, w którym nie można zastosować reguły lub profilu jest łatwy do pomijania go bezpośrednio w kodzie. Można użyć `gsl::suppress` atrybutu, aby sprawdzić Core C++ wykrywanie i zgłoszenie naruszenia reguły w następujący blok kodu. Możesz oznaczyć poszczególne instrukcje, aby pominąć określone zasady. Można nawet pominąć wszystkie profile granice pisząc `[[gsl::suppress(bounds)]]` bez uwzględniania określonej reguły.

## <a name="supported-rule-sets"></a>Obsługiwane zestawy reguł
Jak nowe zasady zostaną dodane do sprawdzania wytyczne Core C++, może zwiększyć liczbę ostrzeżeń, które są tworzone dla istniejącego kodu. Zestawy wstępnie zdefiniowanych reguł służy do filtrowania rodzajów reguły, aby włączyć. Począwszy od programu Visual Studio 2017 wersji 15 ustęp 3 zestawy reguł obsługiwane są:
  - **Reguły wskaźnika właściciela** wymusić [zarządzanie zasobami sprawdza powiązany właściciel<T> z wytycznymi Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Reguły Const** wymusić [powiązane const kontroli z wytycznymi Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Wskaźnik reguł** wymusić [zarządzanie zasobami sprawdza wskaźniki związanych z pierwotnych z wytycznymi Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Unikatowe zasady wskaźnika** wymusić [zarządzanie zasobami sprawdza związanych z typami z semantyki unikatowy wskaźnika z wytycznymi Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Zakresem reguły** wymusić [zakresem profilu wytycznych Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Typ reguły** wymusić [typu profilu wytycznych Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).


 Można ograniczyć ostrzeżenia do tylko jednej lub kilku grup. **Native Minimum** i **natywnego zalecane** Sprawdź Core C++ reguł oprócz innych PREfast kontroli dołączania zestawów reguł. Aby wyświetlić dostępne zestawów reguł, Otwórz okno dialogowe właściwości projektu, zaznacz **Analysis\General kod**, otwórz menu rozwijanego w **zestawów reguł** pole kombi i pobrania **Wybierz wiele zestawów reguł** . Aby uzyskać więcej informacji o korzystaniu z zestawów reguł w programie Visual Studio, zobacz [przy użyciu zestawów reguł do grupowania reguł analizy kodu](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makra
 Sprawdzanie wskazówki Core C++ jest dostarczany z pliku nagłówka, który definiuje makra, które ułatwiają Pomiń całych kategorii ostrzeżeń w kodzie:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Te makra odpowiadają zestawów reguł i rozszerzyć do rozdzielonej spacjami listy numerów ostrzeżeń. Przy użyciu konstrukcji odpowiednie pragma można skonfigurować skuteczne zestaw reguł jest interesujące dla projektu lub sekcji kodu. W poniższym przykładzie analizę kodu tylko ostrzegać brak modyfikatorów stałe:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atrybuty
 Kompilator Microsoft Visual C++ ma ograniczoną obsługę GSL Pomiń atrybutu.
Może służyć do Pomijaj ostrzeżenia w przypadku wyrażenia i instrukcje bloku wewnątrz funkcji.

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>Pomijanie analizy przy użyciu opcji wiersza polecenia
 Zamiast #pragmas możesz użyć opcji wiersza polecenia na stronie właściwości pliku do pomijanie ostrzeżeń dla projektu lub pojedynczym plikiem. Na przykład, aby wyłączyć ostrzeżenia 26400 dla pliku:

 1) Kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań**

 2) Wybierz **właściwości | C C ++ / | Wiersz polecenia**

 3) W **dodatkowe opcje** okna, Dodaj `/wd26400`.

 Opcja wiersza polecenia można tymczasowo wyłączyć, określając analizę kodu dla pliku `/analyze-`. Spowoduje to utworzenie ostrzeżenie *D9025 zastępowanie "/ analyze" z "/ analyze-"*, który przypomina ponownie później włączyć analizy kodu.

 ## <a name="corecheck_per_file"></a> Włączenie sprawdzania C++ podstawowe wskazówki dotyczące plików określonego projektu
Czasami mogą być przydatne do analizy kodu fokus i nadal korzystaj środowiska IDE programu Visual Studio. Poniżej znajduje się przykładowy scenariusz, który może służyć do dużych projektów, aby zapisać czas kompilacji i łatwiejsze do wyników filtrowania.
1.  W powłoce poleceń programu ustawić `esp.extension` i `esp.annotationbuildlevel` zmiennych środowiskowych.
2.  Uruchom program Visual Studio z powłoki poleceń umożliwiającej dziedziczą tych zmiennych.
3.  Załadowanie projektu i otwórz jej właściwości.
4.  Włącz analizę kodu, wybierz odpowiednią regułę zestawów, ale nie należy włączać rozszerzenia analizy kodu.
5.  Przejdź do pliku, który ma być analizowane za pomocą sprawdzanie wskazówki Core C++ i otwórz jej właściwości.
6.  Wybierz **C / C ++ \Command opcji wiersza** i Dodaj `/analyze:plugin EspXEngine.dll`
7.  Wyłącz użycie prekompilowanego nagłówka (**C / C ++ \Precompiled nagłówki**). Jest to konieczne, ponieważ aparat rozszerzenia może próbować odczytywać wewnętrznych informacji prekompilowanego nagłówka, a jeśli jego został skompilowany z domyślne opcje projektu, nie będzie zgodny.
8.  Skompiluj ponownie projekt. Typowe kontroli PREFast należy uruchomić we wszystkich plikach. Ponieważ sprawdzanie wskazówki Core C++ nie jest domyślnie włączona, należy wykonać tylko w pliku, który jest skonfigurowany do używania go.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Jak używać sprawdzania C++ podstawowe wskazówki dotyczące poza Visual Studio
Umożliwia sprawdzanie wskazówki Core C++ w kompilacjach zautomatyzowanych.

### <a name="msbuild"></a>MSBuild
 Narzędzie sprawdzania analizy kodu natywnego (PREfast) jest zintegrowany środowiska MSBuild przez pliki niestandardowych obiektów docelowych. Możesz ją włączyć za pomocą właściwości projektu i dodać sprawdzanie wskazówki Core C++, (która jest oparta na PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Upewnij się, że te właściwości, przed zaimportowaniem plików Microsoft.Cpp.targets dodawane. Można pobranie zestawów reguł określone lub utworzyć niestandardowego zestawu reguł lub użyj domyślnego zestawu reguł, który zawiera inne kontrole PREfast.

Sprawdzania Core C++ można uruchomić tylko na określonych plików, przy użyciu tej samej metody jako [opisanych wcześniej](#coreckeck_per_file), ale przy użyciu programu MSBuild plików. Zmienne środowiskowe można ustawić przy użyciu `BuildMacro` elementu:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Jeśli nie chcesz zmodyfikować plik projektu, można przekazać właściwości w wierszu polecenia:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Inne niż MSBuild projektów
Jeśli używasz systemu kompilacji, które nie korzystają z programu MSBuild nadal można uruchomić narzędzie sprawdzania, ale należy zapoznać się z niektóre funkcje wewnętrzne Konfiguracja aparatu analizy kodu (który nie jest gwarantowana w przyszłości obsługiwane).

Należy ustawić kilka zmienne środowiskowe i użyć opcji wiersza polecenia właściwe dla kompilatora. Najlepiej do pracy w środowisku "natywny wiersz polecenia narzędzi", dzięki czemu nie trzeba wyszukiwać określone ścieżki dla kompilatora, Dołącz katalogi itp.

1.  **Zmienne środowiskowe**
  - `set esp.extensions=cppcorecheck.dll` Ta wartość informuje aparat można załadować modułu C++ podstawowe wskazówki.
  - `set esp.annotationbuildlevel=ignore` Powoduje wyłączenie logikę, która przetwarza adnotacji SAL. Adnotacje nie wpływają na analizy kodu w module sprawdzania C++ podstawowe wskazówki dotyczące, ale ich zajmuje przetwarzanie czasu (czasami mnóstwo czasu). To ustawienie jest opcjonalne, lecz zdecydowanie zalecane.
  - `set caexcludepath=%include%` Zdecydowanie zaleca się wyłączenie ostrzeżenia, które wyzwalać na standardowych nagłówków. Możesz dodać więcej ścieżek, na przykład ścieżki do wspólnych nagłówków w projekcie.
2.  **Opcje wiersza polecenia**
  - `/analyze`  Analiza kodu umożliwia (Rozważ też użycie / analyze: tylko i / analyze: quiet).
  - `/analyze:plugin EspXEngine.dll` Ta opcja ładuje aparat rozszerzenia analizy kodu do PREfast. Ten aparat ładuje z kolei sprawdzanie wskazówki Core C++.



## <a name="use-the-guideline-support-library"></a>Korzystanie z biblioteki obsługi wytyczne
 Podstawowa biblioteka obsługi zaprojektowano w celu ułatwienia postępuj zgodnie z wytycznymi Core. GSL zawiera definicje, które umożliwiają Zamień podatnych konstrukcje bezpieczniejszych alternatyw. Na przykład można zastąpić `T*, length` para parametrów z `span<T>` typu. GSL znajduje się w temacie [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Biblioteka jest typu open source, aby wyświetlić źródła, wprowadzania komentarzy lub współtworzenia. Projekt można znaleźć w folderze [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a> Użyj wytycznych Sprawdź Core C++ w projektach Visual Studio 2015
  Jeśli używasz programu Visual Studio 2015 zestawów reguł analizy kodu C++ Core Sprawdź nie są instalowane domyślnie. Należy wykonać dodatkowe kroki, aby można było włączyć sprawdzanie Core C++ narzędzi analizy kodu programu Visual Studio 2015. Firma Microsoft zapewnia obsługę projektów programu Visual Studio 2015 przy użyciu pakietu Nuget. Pakiet nosi nazwę Microsoft.CppCoreCheck i jest dostępny w [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Ten pakiet wymaga się, że co najmniej zainstalowanego programu Visual Studio 2015 Update 1.

 Pakiet instaluje inny pakiet jako zależność, tylko nagłówek wskazówek dotyczących pomocy technicznej biblioteki (GSL). GSL jest również dostępna w witrynie GitHub pod [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 Ze względu na sposób, w jaki są ładowane reguł analizy kodu należy zainstalować pakiet Microsoft.CppCoreCheck NuGet do każdego projektu C++, który chcesz sprawdzić w programie Visual Studio 2015.

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Aby dodać pakiet Microsoft.CppCoreCheck do projektu programu Visual Studio 2015

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe projektu w rozwiązaniu, które mają zostać dodane do pakietu. Wybierz **Zarządzaj pakietami NuGet** otworzyć **Menedżera pakietów NuGet**.

2.  W **Menedżera pakietów NuGet** okna, wyszukiwanie Microsoft.CppCoreCheck.

     ![Pakiet CppCoreCheck Pokazuje okno Menedżera pakietów Nuget](../code-quality/media/cppcorecheck_nuget_window.png)

3.  Wybierz pakiet Microsoft.CppCoreCheck, a następnie wybierz pozycję **zainstalować** przycisk, aby dodać reguły do projektu.

 Pakiet NuGet dodaje dodatkowe pliki .targets MSBuild do projektu, które jest wywoływane, gdy Włącz analizę kodu w projekcie. Ten plik .targets dodaje reguł C++ podstawowej — sprawdź jako dodatkowe rozszerzenia do narzędzie do analizy kodu programu Visual Studio. Po zainstalowaniu pakietu służy okna dialogowego strony właściwości do włączania lub wyłączania reguł zwolnione i eksperymentalne.

