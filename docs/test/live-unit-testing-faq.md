---
title: "Często zadawane pytania dotyczące testowania jednostek na żywo | Dokumentacja firmy Microsoft"
ms.date: 2017-10-03
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload: dotnet
ms.openlocfilehash: e2e219dae6d7e99f6c5e6ef394a31bbeb436c573
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Aktywne testy jednostkowe często zadawane pytania

## <a name="live-unit-testing-is-improved-and-enhanced-regularly-how-can-i-find-information-about-the-latest-new-features-and-enhancements"></a>Testowanie jednostkowe na żywo ulepszone i rozszerzone regularnie. Jak można znaleźć informacje o najnowszych nowe funkcje i ulepszenia?

**Odpowiedź:**

Aby dowiedzieć się więcej na temat nowych funkcji i ulepszeń, które zostały wprowadzone do testowania jednostki na żywo w programie Visual Studio 2017 wersji 15 ustęp 3, zobacz [What's New in Live testów jednostkowych](live-unit-testing-whats-new.md).


## <a name="what-test-frameworks-does-live-unit-testing-support-and-what-are-the-minimum-supported-versions"></a>Jakie platform testów jest obsługa Live testów jednostkowych i jakie są minimalne obsługiwane wersje?  

**Odpowiedź:**

Testowanie jednostkowe na żywo współpracuje z trzech platform testowych popularnych jednostki wymienione w poniższej tabeli. Minimalna obsługiwana wersja ich kart i struktur również znajduje się w tabeli. Platformy testowania jednostki są wszystkie dostępne z NuGet.org.
 
<table> 
<tr>
   <th>Struktury testowej</th>
   <th>Minimalna wersja programu Visual Studio karty</th>
   <th>Minimalna wersja Framework</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> 2.2.0-beta3-build1187 wersji xunit.Runner.VisualStudio</td>
   <td>xunit 1.9.2</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter wersji 3.5.1</td>  
   <td>NUnit wersji 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Jeśli masz starszą testu MSTest na podstawie projektów tego odwołania `Microsoft.VisualStudio.QualityTools.UnitTestFramework` i nie chcesz przejść do nowszej pakietów MSTest NuGet, przeprowadź uaktualnienie do programu Visual Studio 2017 wersji 15.4. 

W niektórych przypadkach może być konieczne jawnie przywracania pakietów NuGet, odwołuje się projektów w rozwiązaniu Aby pracować na żywo testów jednostkowych. Można to zrobić za pomocą jawnego kompilacji rozwiązania (wybierz **kompilacji**, **Kompiluj ponownie rozwiązanie** z menu najwyższego poziomu programu Visual Studio) lub przez Przywracanie pakietów w rozwiązaniu (kliknij prawym przyciskiem myszy rozwiązanie i wybierz **przywracania pakietów NuGet**) przed włączeniem testów jednostkowych życia. 


## <a name="does-live-unit-testing-work-with-net-core"></a>Działa na żywo testów jednostkowych z platformą .NET Core?  

**Odpowiedź:**

Tak. Testowanie jednostkowe na żywo współpracuje z platformy .NET Core i .NET Framework. Obsługa .NET Core została ostatnio dodane w programie Visual Studio 2017 wersji 15 ustęp 3. Przeprowadź uaktualnienie do tej wersji programu Visual Studio, jeśli chcesz, aby na żywo testów jednostkowych obsługę .NET Core. 

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>Dlaczego nie testów jednostkowych na żywo działa po jej włączeniu? 

**Odpowiedź:** 

**Okno danych wyjściowych** (gdy na żywo testów jednostkowych listy rozwijanej jest zaznaczone) należy sprawdzić, dlaczego Live testów jednostkowych nie działa. Testy jednostkowe na żywo może nie działać dla jednego z następujących powodów: 

- Jeśli pakiety NuGet odwołuje się projektów w rozwiązaniu nie zostały przywrócone, Live testów jednostkowych nie będzie działać. Podczas jawnego kompilacji rozwiązania lub przywracanie pakietów NuGet w rozwiązaniu przed włączeniem Live testów jednostkowych powinno rozwiązać ten problem. 

- Jeśli używasz testów na podstawie przełącznika MSTest w projektach, upewnij się, że Usuń odwołanie do `Microsoft.VisualStudio.QualityTools.UnitTestFramework`i dodaj odwołania do najnowszych pakietów MSTest NuGet `MSTest.TestAdapter` (wymagana jest minimalna wersja 1.1.11) i `MSTest.TestFramework` (minimalna wersja 1.1.11 jest wymagane). Aby uzyskać więcej informacji, zobacz sekcję "Struktur testu obsługiwane" [Użyj Live testów jednostkowych w Visual Studio 2017 Enterprise Edition](live-unit-testing.md#supported-test-frameworks) tematu.
 
- Co najmniej jeden projekt w rozwiązaniu powinien mieć odwołanie NuGet albo bezpośrednie odwołanie do xUnit, NUnit lub MSTest struktury testowej. Ten projekt powinien odwoływać się również odpowiedniego pakietu NuGet kart testu Visual Studio. Adapter testowy programu Visual Studio można także odwoływać się za pośrednictwem `.runsettings` pliku. `.runsettings` Plik musi istnieć wpis podobny do poniższego: 

   ```xml
    <RunSettings> 
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration> 
    </RunSettings> 
   ``` 

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>Dlaczego jest Live testów jednostkowych wyświetlany niepoprawny pokrycia po uaktualnieniu adapter testowy występujący w odwołaniu w projektach Visual Studio do obsługiwanej wersji?

**Odpowiedź:**

- Jeśli wielu projektów w odwołaniu do rozwiązania NuGet test pakietu karty, każde z nich należy uaktualnić do obsługiwanej wersji.

- Upewnij się, ponieważ plik .props MSBuild zaimportowane z pakiet adapter testowy jest poprawnie aktualizowany również. Sprawdź NuGet pakietu wersji/ścieżkę importu, które zwykle znajdują się w górnej części pliku projektu, takie jak następujące:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>Czy mogę dostosować mój kompilacji na żywo testów jednostkowych 

**Odpowiedź:**

Jeśli rozwiązanie wymaga niestandardowych kroki, aby kompilacji dla Instrumentacji (Live testów jednostkowych), które nie są wymagane dla kompilacji nieinstrumentowanego "regularne", a następnie można dodać kod do plików projektu lub .targets, które sprawdza, czy `BuildingForLiveUnitTesting` właściwości i wykonuje niestandardowe poprzedzającego utworzenie kopii zapasowej lub używanego po kroki procesu kompilacji. Możesz również usunąć niektóre kroki procesu kompilacji (na przykład publikowania lub generowania pakietów) lub aby dodać kroki procesu kompilacji (takich jak kopiowanie wymagania wstępne) do kompilacji testów jednostkowych na żywo na podstawie tej właściwości projektu. To nie ma wpływu na regularne kompilację w jakikolwiek sposób i tylko będzie miało wpływ na żywo testów jednostkowych kompilacji. 

Na przykład może być elementem docelowym, tworzącego pakietów NuGet podczas kompilacji regularne. Prawdopodobnie nie ma pakietów NuGet, które ma być generowany po każdej modyfikacji wprowadzone. Dlatego można wyłączyć obiektu docelowego w kompilacji na żywo testów jednostkowych, wykonując postać zbliżoną do następującej:   

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'"> 
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/> 
</Target> 
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Komunikaty o błędach z &lt;OutputPath&gt; lub &lt;OutDir&gt;

**Dlaczego jest zgłaszany następujący błąd, gdy na żywo testów jednostkowych spróbuje kompilacji Moje rozwiązanie: ".. .pojawia bezwarunkowo ustawić `<OutputPath>` lub `<OutDir>`. Testowanie jednostkowe na żywo nie będzie wykonywał testy z zestawu wyjściowego"?**

**Odpowiedź:**

Może się to zdarzyć, jeśli proces kompilacji dla rozwiązania bezwarunkowo zastępuje `<OutputPath>` lub `<OutDir>` tak, aby nie jest podkatalogiem katalogu `<BaseOutputPath>`. W takich przypadkach Live testów jednostkowych nie będzie działać, ponieważ zastępuje również tych zasobów w celu zapewnienia porzucenia artefaktów kompilacji do folderu, w obszarze `<BaseOutputPath>`. Jeśli konieczne jest przesłonięcie lokalizację użytkownika artefaktów kompilacji na usunięte w regularnych kompilacji, Zastąp `<OutputPath>` warunkowo na podstawie `<BaseOutputPath>`. 

Na przykład, jeśli kompilacji overrides `<OutputPath>` w sposób przedstawiony poniżej: 

```xml 
<Project> 
  <PropertyGroup> 
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath> 
  </PropertyGroup> 
</Project> 
```

następnie można zastąpić go z następujących czynności: 

```xml 
<Project> 
  <PropertyGroup> 
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath> 
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath> 
  </PropertyGroup> 
</Project> 
```
 
Gwarantuje to, że `<OutputPath>` znajduje się w obrębie `<BaseOutputPath>` folderu. 
 
Nie zastępuj `<OutDir>` bezpośrednio w procesie kompilacji; zastąpić `<OutputPath>` zamiast tego można porzucić artefaktów kompilacji do określonej lokalizacji.
  
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>Ustawianie lokalizacji na żywo testów jednostkowych artefaktów kompilacji

**Chcę artefaktów kompilacji testów jednostkowych na żywo można przejść do określonej lokalizacji, zamiast domyślnej lokalizacji, w obszarze `.vs` folderu. Jak zmienić który?**
 
**Odpowiedź:**

Ustaw `LiveUnitTesting_BuildRoot` zmiennej środowiskowej na poziomie użytkownika do ścieżki, miejsce na żywo testów jednostkowych kompilacji artefakty porzucanie.  

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>Jak działa testy z okna narzędzia Eksplorator testów inny niż uruchamiania testów w Live testów jednostkowych? 

**Odpowiedź:**

Istnieje kilka różnic: 

- Uruchomiona lub debugowanie testów z okna narzędzia Eksplorator testów uruchamia regularne plików binarnych, natomiast na żywo testów jednostkowych uruchamia instrumentowanych danych binarnych. Jeśli chcesz debugować instrumentowanych danych binarnych, dodawanie [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) wywołania metody w metodę testu powoduje, że debuger można uruchomić zawsze, gdy metoda jest wykonywana (w tym gdy jest wykonywana przez testów jednostkowych Live), czy użytkownik może następnie Dołączanie i debugowania instrumentowanego pliku binarnego. Mamy nadzieję, że nasze jest jednak Instrumentacji jest niewidoczna dla większości scenariuszy użytkownika, czy konieczne do debugowania instrumentowane pliki binarne. 

- Testowanie jednostkowe na żywo nie powoduje utworzenia nowej domeny aplikacji do uruchamiania testów, ale testów uruchamianych w oknie Eksploratora testów tworzenia nowej domeny aplikacji. 

- Testowanie jednostkowe na żywo uruchamia testy w każdym zestawu testowego sekwencyjnie, po uruchomieniu wielu testów z okna Eksploratora testów i wybrania **Uruchom testy równolegle** przycisku one będą uruchamiane równolegle. 

- Odnajdywania i uruchamiania testów w Live testów jednostkowych jest używana wersja 2 `TestPlatform`, podczas gdy okno Eksploratora testów używa wersji 1. Różnica w większości przypadków, nie należy jednak zauważyć.  

- Eksplorator testów aktualnie uruchamia testy w jednowątkowego apartamentu (STA) domyślnie, natomiast na żywo testów jednostkowych uruchamia testy w apartamencie wielowątkowe (MTA). Aby uruchomić testy MSTest w STA przy testowaniu jednostki na żywo, dekoracji metody testowej lub klasa zawierająca z `<STATestMethod>` lub `<STATestClass>` atrybut, który znajduje się w `MSTest.STAExtensions 1.0.3-beta` pakietu NuGet. Dla NUnit, dekoracji metody testowej z `<RequiresThread(ApartmentState.STA)>` atrybutu oraz xUnit, z `<STAFact>` atrybutu.
 
## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>Jak wykluczyć testy z uczestnictwa w Live testów jednostkowych?

**Odpowiedź:**

Zobacz sekcję "Włączanie i wyłączanie projekty testowe i metod testowych" [Użyj Live testów jednostkowych w Visual Studio 2017 Enterprise Edition](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods) tematu dla ustawienia specyficzne dla użytkownika. Jest to bardzo przydatne, gdy chcesz uruchomić określonego zestawu testów dla sesji edytowania określonego lub utrwalić osobistych preferencji.
  
W przypadku ustawienia specyficzne dla danego rozwiązania, można zastosować <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> atrybutu programowo, aby wykluczyć metod, właściwości, klasy lub struktury z są instrumentowane przez funkcję Live testów jednostkowych. Ponadto można również ustawić `<ExcludeFromCodeCoverage>` właściwości `true` w pliku projektu, aby wykluczyć całego projektu z jest instrumentowany. Testowanie jednostkowe na żywo ciągle będą uruchamiać testy, które nie zostały zinstrumentowane, ale nie będzie można zwizualizować ich pokrycia.

Można również sprawdzić, czy `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` jest ładowany w bieżącej domenie aplikacji i Wyłącz testy oparta na. Można na przykład czy przypominać następujące — z xUnit:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name == 
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>Nagłówki Win32 PE są różne w zestawów instrumentowanych kompilacja za pomocą testów jednostkowych na żywo 

**Odpowiedź:**

Ten problem zostanie rozwiązany i nie istnieje w w programie Visual Studio 2017 wersji 15 ustęp 3. Przeprowadź uaktualnienie do tej wersji programu Visual Studio.

Dla starszych wersji programu Visual Studio 2017 jest znaną usterką, które mogą skutkować kompilacji na żywo testów jednostkowych awarie do osadzenia następujące dane nagłówek PE Win32: 

- Wersja pliku (określonego przez @System.Reflection.AssemblyFileVersionAttribute w kodzie). 

- Ikona Win32 (określonego przez `/win32icon:` w wierszu polecenia). 

- Win32 Manifest (określonego przez `/win32manifest:` w wierszu polecenia). 

Testy, które zależą od tych wartości może zakończyć się niepowodzeniem, gdy wykonywane przez testów jednostkowych na żywo.

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>Dlaczego na żywo jednostki badań keep tworzenia Moje rozwiązanie zawsze, nawet jeśli nie mam I wprowadzaniem zmian w? 

**Odpowiedź:**

Może się to zdarzyć, jeśli proces kompilacji rozwiązania generuje kod źródłowy, który jest częścią rozwiązania, sama i pliki docelowy kompilacji ma odpowiednie wejściami i wyjściami określony. Obiekty docelowe należy podać listę wejściami i wyjściami tak, aby MSBuild można wykonać odpowiednie sprawdzenie aktualności i określić, czy wymagane jest nowa kompilacja. 

Testowanie jednostkowe na żywo rozpoczyna się kompilacja zawsze, gdy wykryje, że zostały zmienione pliki źródłowe. Ponieważ kompilacji rozwiązania generuje pliki źródłowe, otrzyma Live testów jednostkowych w pętli nieskończonej kompilacji. Jeśli jednak wejściami i wyjściami docelowej są zaznaczone uruchomienia testów jednostkowych Live drugi kompilacji (po wykryciu nowo wygenerowanych plików źródłowych z poprzedniej kompilacji), spowoduje przerwanie poza pętli ponieważ wskaże kontroli danych wejściowych i wyjściowych ustawienia są aktualne.   

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>Jak testowania pracy z funkcją ładowania rozwiązania Lightweight jednostek na żywo? 

**Odpowiedź:**

Testowanie jednostkowe na żywo aktualnie nie działają prawidłowo w funkcji obciążenia lekkie rozwiązanie. Działa tylko wtedy, gdy co najmniej jeden z projektów testów jest załadowany. Do tego czasu nie będzie działać, ponieważ na żywo testów jednostkowych jest zależny od co najmniej jeden z projektów testów odwołujące się do adaptera testowego (MSTest, xUnit lub NUnit) ładowany.

Uwaga: Obciążenia lekkie rozwiązanie nie jest już dostępna w wersji Visual Studio 2017 15,5 cala lub nowszy. W programie Visual Studio wersji 15.5 i nowszych dużych rozwiązaniach, które zawierają zarządzany kod obciążenia znacznie szybsze niż wcześniej, nawet bez obciążenia lekkie rozwiązanie.
 
## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>Dlaczego na żywo testów jednostkowych nie przechwytywania pokrycia z nowego procesu utworzone za pomocą testu?
 
**Odpowiedź:**

Jest to znany problem i powinny być ustalone w kolejnych aktualizacji programu Visual Studio 2017 r. 

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>Dlaczego nothing stanie po dołączyć lub wykluczyć testów z zestawu testowego na żywo? 

**Odpowiedź:**

Ten problem zostanie rozwiązany i nie istnieje w programie Visual Studio 2017 wersji 15 ustęp 3. Uaktualnienie do tej wersji programu Visual Studio. 

Dla wcześniejszych wersji programu Visual Studio 2017 jest to znany problem. Aby obejść ten problem, należy dokonać edycji dowolnego pliku po uwzględnione lub wykluczone testy.  

## <a name="live-unit-testing-and-editor-icons"></a>Ikony testów jednostkowych i edytor na żywo 

**Dlaczego nie widzę żadnych ikon w edytorze nawet na żywo testów jednostkowych wydaje się działać testów oparte na komunikaty w oknie danych wyjściowych?** 

**Odpowiedź:**

Dzieje się tak, jeśli z jakiegoś powodu nie są instrumentowane zestawy, które na żywo testów jednostkowych jest zasilany. Na przykład testów jednostkowych na żywo nie jest zgodny z projektów, które ustawić `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. W takim przypadku procesu kompilacji musi zostać zaktualizowany, albo usuń to ustawienie lub zmień, aby `true` dla pracy na żywo testów jednostkowych.  

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>Jak zebrać bardziej szczegółowe Dzienniki raportów usterki plików? 

**Odpowiedź:**

Możesz wykonać kilka czynności w celu zbierania bardziej szczegółowych dzienników: 

- Przejdź do **narzędzia**, **opcje**, **Live testów jednostkowych** i zmień opcję rejestrowania **pełne**. Powoduje to bardziej szczegółowe dzienniki, który będzie wyświetlany w oknie danych wyjściowych. 

- Ustaw `LiveUnitTesting_BuildLog` zmiennej środowiskowej użytkownika na nazwę pliku do przechwycenia dziennika programu MSBuild. Następnie można pobrać szczegółowe komunikaty dziennika program MSBuild z kompilacji na żywo testów jednostkowych z tego pliku.

- Ustaw `LiveUnitTesting_TestPlatformLog` zmienną środowiskową użytkownika `1` do przechwycenia dziennika platformy testowej. Następnie można pobrać szczegółowe komunikaty dziennika platformy testowej z uruchomień testów jednostkowych na żywo z `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Utwórz zmienną środowiska użytkownika o nazwie `VS_UTE_DIAGNOSTICS` i wartości 1 (lub dowolna wartość) i uruchom ponownie program Visual Studio. Teraz powinny pojawić się wiele rejestrowania w **dane wyjściowe — testy** kartę w programie Visual Studio. 
  
## <a name="see-also"></a>Zobacz także

[Testy jednostkowe na żywo](live-unit-testing.md)
 
