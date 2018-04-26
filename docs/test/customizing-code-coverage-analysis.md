---
title: Dostosowywanie analizy pokrycia kodu w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c9b51137c6b66fe2895bcc0e70e3ffab8ebd637e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="customize-code-coverage-analysis"></a>Dostosowywanie analizy pokrycia kodu

Domyślnie narzędzie Visual Studio Code Coverage analizuje wszystkie zestawy rozwiązania, które są ładowane podczas testów jednostkowych. Zaleca się zachować to ustawienie domyślne, ponieważ w większości przypadków działa ono prawidłowo. Aby uzyskać więcej informacji, zobacz [przy użyciu pokrycia kodu do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Przed rozpoczęciem dostosowywania zachowania pokrycia kodu należy wziąć pod uwagę kilka alternatyw:

- *Chcę wyłączyć kod testu z wyników pokrycia kodu i zawiera tylko kod aplikacji.*

     Dodaj `ExcludeFromCodeCoverage Attribute` do własnej klasy testu.

- *Chcę dołączyć zestawy, które nie są częścią Moje rozwiązanie.*

     Uzyskaj pliki .pdb dla tych zestawów i skopiuj je do tego samego folderu, co pliki .dll zestawu.

Aby dostosować zachowanie pokrycia kodu, skopiuj [przykładowa na końcu tego tematu](#sample) i dodaj go do rozwiązania, przy użyciu rozszerzenia pliku *runsettings*. Edytowanie jej do własnych potrzeb, a następnie na **testu** menu, wybierz **ustawień testu**, **wybierz ustawienia testu** pliku. W dalszej części tego artykułu opisano tej procedury bardziej szczegółowo.

## <a name="the-run-settings-file"></a>Plik parametrów uruchomieniowych

Ustawienia pokrycia kodu zaawansowane są określone w *runsettings* pliku. Plik parametrów uruchomieniowych jest pliku konfiguracji używanego przez narzędzia do testowania jednostki. Firma Microsoft zaleca, należy skopiować [przykładowa na końcu tego tematu](#sample) i edytować go do własnych potrzeb.

Aby dostosować pokrycie kodu, Dodaj plik parametrów uruchomieniowych do rozwiązania:

1. Dodaj plik XML jako element rozwiązania z rozszerzeniem *runsettings*:

     W Eksploratorze rozwiązań, w menu skrótów rozwiązania, wybierz **Dodaj** > **nowy element**i wybierz **pliku XML**. Zapisz plik z nazwą zakończenia, takich jak *CodeCoverage.runsettings*.

2. Dodaj zawartość w przykładzie na końcu tego artykułu, a następnie dostosować go do potrzeb zgodnie z opisem w poniższych sekcjach.

3. Na **testu** menu, wybierz **ustawień testu** > **wybierz plik ustawień testu** i wybierz plik.

4. Teraz po uruchomieniu **Analizuj pokrycie kodu**, plik parametrów uruchomieniowych będzie kontrolowanie swojego zachowania. Pamiętaj, że należy ponownie uruchomić pokrycia kodu. Poprzednie wyniki pokrycia i kolorowanie kodu nie są automatycznie ukrywane podczas uruchamiania testów lub zaktualizuj kod.

5. Wyłącz i Włącz ustawienia niestandardowe, Anuluj wybór lub wybierz plik w **testu** > **ustawień testu** menu.

 ![Menu Ustawienia testu z plikiem ustawień niestandardowych](../test/media/codecoverage-settingsfile.png)

Innych aspektów testy jednostkowe można skonfigurować w tym samym pliku ustawień uruchamiania. Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md).

### <a name="specifying-symbol-search-paths"></a>Określanie ścieżek wyszukiwania symbolu

Pokrycie kodu wymaga symboli (pliki .pdb), aby były obecne zestawy. Zestawy wbudowanych w tym rozwiązaniu pliki symboli są zazwyczaj obecny obok pliki binarne i pokrycie kodu działa automatycznie. Jednak w niektórych przypadkach można chcieć dołączyć odwołania do zestawów do analizy pokrycia kodu. W takich przypadkach pliki .pdb mogą nie być przylegającymi do plików binarnych, ale ścieżkę wyszukiwania symbolu można określić w pliku .runsettings.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!WARNING]
> Rozpoznawanie symboli może potrwać, zwłaszcza w przypadku korzystania z wielu zestawów lokalizację pliku zdalnego. W związku z tym należy wziąć pod uwagę kopiowanie zdalnych plików .pdb do tej samej lokalizacji lokalnej co pliki binarne (.dll i .exe).

### <a name="excluding-and-including"></a>Uwzględnianie i wykluczanie

Określone zestawy można wykluczyć z analizy pokrycia kodu. Na przykład:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Alternatywnie można określić zestawy, które powinny być włączone. Takie podejście ma tę wadę, że po dodaniu większej liczby zestawów do rozwiązania trzeba pamiętać, aby dodać je do listy:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Jeśli `<Include>` jest pusta, a następnie przetwarzania pokrycia kodu obejmuje wszystkie zestawy, które są ładowane i dla którego można znaleźć .pdb, pliki. Pokrycie kodu nie ma elementów, które odpowiadają klauzuli `<Exclude>` listy.

`Include` jest przetwarzana przed `Exclude`.

### <a name="regular-expressions"></a>Wyrażenia regularne

Uwzględnij lub wyklucz węzły, używając wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Wyrażenia regularne nie są tym samym, co symbole wieloznaczne. W szczególności:

- **. \***  ciąg znaków

- **\\.** Dopasowuje pojedynczego znaku kropki ".")

- **\\( \\)** odpowiada nawiasów ()"

- **\\\\** Dopasowuje ogranicznika ścieżki pliku "\\"

- **^** Dopasowuje początek ciągu

- **$** Dopasowuje koniec ciągu

We wszystkich dopasowaniach rozróżniana jest wielkość liter.

Na przykład:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> Jeśli występuje błąd w wyrażeniu regularnym, taki jak nawiasy niedopasowane lub o niezmienionym znaczeniu, analiza pokrycia kodu nie będzie działać.

### <a name="other-ways-to-include-or-exclude-elements"></a>Inne sposoby, aby dołączyć lub wykluczyć elementy

Zobacz [przykładowa na końcu tego tematu](#sample) przykłady.

- `ModulePath` -Zestawy określonego w ścieżce pliku zestawu.

- `CompanyName` -odpowiada zestawy za pomocą atrybutu firmy.

- `PublicKeyToken` -dopasowań zestawy podpisane przez token klucza publicznego. Na przykład dopasować wszystkich składników programu Visual Studio i rozszerzenia, należy użyć `<PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>`.

- `Source` -odpowiada elementów przez nazwę ścieżki pliku źródłowego, w którym jest zdefiniowany.

- `Attribute` -odpowiada elementów, do których jest dołączony określonego atrybutu. Podaj pełną nazwę atrybutu, łącznie z wyrazem „Atrybut” na końcu nazwy.

- `Function` -odpowiada procedury, funkcji lub metody przez w pełni kwalifikowanej nazwy.

**Pasujących do nazwy funkcji**

Wyrażenie regularne musi odpowiadać w pełni kwalifikowanej nazwy funkcji, łącznie z przestrzeni nazw, nazwę klasy, nazwy metody i listy parametrów. Na przykład

- C# lub Visual Basic: `Fabrikam.Math.LocalMath.SquareRoot(double)`

- C++:  `Fabrikam::Math::LocalMath::SquareRoot(double)`

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>
```

## <a name="how-to-specify-run-settings-files-while-running-tests"></a>Sposób określania ustawień uruchamiania plików podczas testów

### <a name="to-customize-run-settings-in-visual-studio-tests"></a>Aby dostosować ustawienia wykonywania w testów programu Visual Studio

Wybierz **testu** > **ustawień testu** > **wybierz plik ustawień testu** i wybierz *runsettings* plik. Plik pojawi się w menu Ustawienia testu, gdzie można zaznaczyć go lub usunąć. Gdy zaznaczone, przy każdym użyciu stosuje się plik parametrów uruchomieniowych **Analizuj pokrycie kodu**.

### <a name="to-customize-run-settings-in-a-command-line-test"></a>Aby dostosować ustawienia wykonywania w teście wiersza polecenia

Aby uruchomić testy z wiersza polecenia, użyj *vstest.console.exe*. Plik ustawień jest parametrem tego narzędzia.

1. Uruchom wiersz polecenia programisty dla programu Visual Studio:

    W systemie Windows **Start** menu, wybierz **programu Visual Studio 2017** > **wiersz polecenia dla programu VS 2017 deweloperów**.

2. Uruchom następujące polecenie:

    `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings`

### <a name="to-customize-run-settings-in-a-build-definition"></a>Dostosowywanie ustawień wykonywania w definicji kompilacji

Dane pokrycia kodu można uzyskać z kompilacji zespołu.

![Określanie runsettings w definicji kompilacji](../test/media/codecoverage-buildrunsettings.png)

1. Upewnij się, że zaznaczone jest pole pliku ustawień uruchamiania.

2. W programie Team Explorer Otwórz **kompilacje**, a następnie dodaj lub Edytuj definicję kompilacji.

3. Na **procesu** rozwiń pozycję **testów automatycznych** > **źródła testu** > **parametrów uruchomieniowych**. Wybierz *runsettings* pliku.

   > [!TIP]
   > Jeśli **zestawu testowego** pojawia się zamiast **źródła testu**, i można wybrać tylko *.testsettings* pliki, ustaw **Test Runner** właściwości w następujący sposób. W obszarze **testów automatycznych**, wybierz pozycję **zestawu testowego**, a następnie wybierz pozycję **[...]**  na końcu linii. W **Dodawanie/edytowanie testu** okno dialogowe, zestaw **Test Runner** do **Visual Studio Test Runner**.

Wyniki są widoczne w sekcji podsumowania raportu kompilacji.

##  <a name="sample"></a> Przykładowy plik runsettings

Skopiuj ten kod i dostosuj go do swoich potrzeb.

(Do innych celów plik parametrów uruchomieniowych, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku ustawień uruchamiania](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).)

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See http://msdn.microsoft.com/library/2k3te2cs.aspx.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Zobacz także

- [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Testowanie jednostek kodu](../test/unit-test-your-code.md)