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
ms.openlocfilehash: 9cdf1b9051f409571989073692cf38906d26b85b
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815954"
---
# <a name="customize-code-coverage-analysis"></a>Dostosowywanie analizy pokrycia kodu

Domyślnie pokrycie kodu analizuje wszystkie zestawy rozwiązania, które są ładowane podczas testów jednostkowych. Zalecane jest użycie to zachowanie domyślne, ponieważ działa dobrze w większości przypadków. Aby uzyskać więcej informacji, zobacz [Użyj pokrycie kodu, aby określić, ile kodu jest testowana](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Aby wykluczyć z wyników pokrycia kodu kod testu i zawierać tylko kod aplikacji, Dodaj <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atrybutu do własnej klasy testu.

Aby uwzględnić zestawy, które nie są częścią rozwiązania, należy uzyskać *.pdb* plików dla tych zestawów i skopiuj je do folderu zestawu *.dll* plików.

## <a name="run-settings-file"></a>Plik parametrów uruchomieniowych

[Plik parametrów uruchomieniowych uruchomienia](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) jest używana przez narzędzia do testowania jednostkowego pliku konfiguracji. Ustawienia pokrycia kodu zaawansowane są określone w *runsettings* pliku.

Aby dostosować pokrycie kodu, wykonaj następujące kroki:

1. Dodaj plik parametrów uruchomieniowych do rozwiązania. W **Eksploratora rozwiązań**, w menu skrótów rozwiązania wybierz **Dodaj** > **nowy element**i wybierz **pliku XML**. Zapisz plik z nazwą, takich jak *CodeCoverage.runsettings*.

1. Dodaj zawartość z przykładowy plik na końcu tego artykułu, a następnie dostosować go do potrzeb zgodnie z opisem w poniższych sekcjach.

1. Wybierz plik parametrów uruchomieniowych na **testu** menu, wybierz **ustawień testu** > **wybierz plik ustawień testu**. Aby określić plik parametrów uruchomieniowych dla uruchamiania testów z wiersza polecenia lub w przepływie pracy kompilacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file).

   Po wybraniu **Analizuj pokrycie kodu**, informacje o konfiguracji zostanie odczytany z pliku ustawień uruchamiania.

   > [!TIP]
   > Poprzednie wyniki pokrycia kodu i kolorowanie kodu nie są automatycznie ukrywane podczas uruchamiania testów lub zaktualizuj kod.

Wyłącz i Włącz ustawienia niestandardowe, Anuluj wybór lub wybierz plik w **testu** > **ustawień testu** menu.

![Menu Ustawienia testu z plikiem ustawień niestandardowych](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Określ ścieżki wyszukiwania symboli

Pokrycie kodu wymaga plików symboli (*.pdb* plików) dla zestawów. Dla zestawów utworzony przez rozwiązanie pliki symboli są zazwyczaj obecny obok pliki binarne i pokrycie kodu działa automatycznie. Jednak w niektórych przypadkach można chcieć dołączyć odwołania do zestawów do analizy pokrycia kodu. W takich przypadkach *.pdb* plików może nie być sąsiadujących ze sobą, aby pliki binarne, ale można określić ścieżki wyszukiwania symboli w *runsettings* pliku.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Rozpoznawanie symboli może potrwać, zwłaszcza w przypadku korzystania z wielu zestawów lokalizację pliku zdalnego. W związku z tym należy rozważyć kopiowanie *.pdb* pliki w tej samej lokalizacji lokalnego jako dane binarne (*.dll* i *.exe*) plików.

### <a name="exclude-and-include"></a>Dołączanie i wykluczanie

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

Jeśli **Include** jest pusta, a następnie przetwarzania pokrycia kodu zawiera wszystkie zestawy, które są załadowane i dla którego *.pdb* znajdują się pliki. Pokrycie kodu nie ma elementów, które odpowiadają klauzuli **wykluczyć** listy.

**Obejmują** jest przetwarzana przed **wykluczyć**.

### <a name="regular-expressions"></a>Wyrażenia regularne

Uwzględnij lub wyklucz węzły, używając wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz [używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Wyrażenia regularne nie są tym samym, co symbole wieloznaczne. W szczególności:

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
> Jeśli w wyrażeniu regularnym, takich jak niezmienionym znaczeniu lub niedopasowane nawiasy, występuje błąd analizy pokrycia kodu nie będą uruchamiane.

### <a name="other-ways-to-include-or-exclude-elements"></a>Inne sposoby, aby dołączyć lub wykluczyć elementy

- **ModulePath** -odpowiada zestawy określonego w ścieżce pliku zestawu.

- **Nazwa firmy** -odpowiada zestawy przez **firmy** atrybutu.

- **PublicKeyToken** -dopasowań zestawy podpisane przez token klucza publicznego.

- **Źródło** -odpowiada elementów przez nazwę ścieżki pliku źródłowego, w którym jest zdefiniowany.

- **Atrybut** -odpowiada elementów, do których jest dołączony określonego atrybutu. Określ pełną nazwę atrybutu, a inclue "Atrybutu" na końcu nazwy.

- **Funkcja** -odpowiada procedury, funkcji lub metody przez w pełni kwalifikowanej nazwy. Aby dopasować nazwę funkcji, wyrażenie regularne musi odpowiadać w pełni kwalifikowanej nazwy funkcji, łącznie z przestrzeni nazw, nazwę klasy, nazwy metody i listy parametrów. Na przykład:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

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

## <a name="sample-runsettings-file"></a>Przykładowy plik .runsettings

Skopiuj ten kod i edytowanie go w zależności od potrzeb.

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

- [Konfigurowanie testów jednostkowych przy użyciu pliku ustawień uruchamiania](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Umożliwia określenie, ile kodu jest testowana przez pokrycie kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Kod testu jednostkowego](../test/unit-test-your-code.md)