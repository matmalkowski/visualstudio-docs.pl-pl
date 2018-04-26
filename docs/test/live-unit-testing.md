---
title: Jednostki na żywo testowania w programie Visual Studio
ms.date: 2017-03-07
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 577ebebec7de0599675f60d764dec52d0d8babd6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="live-unit-testing-with-visual-studio-2017"></a>Testy jednostkowe za pomocą programu Visual Studio 2017 na żywo

Jako tworzysz aplikację na żywo testów jednostkowych automatycznie uruchamia wszystkie testy jednostkowe ryzyko w tle i przedstawia wyniki i pokrycie kodu na żywo w programie Visual Studio IDE w czasie rzeczywistym. Podczas modyfikowania kodu na żywo testów jednostkowych Wyświetla informacje o wpływ zmian na istniejące testy i określa, czy nowy kod dodano jest objęte co najmniej jeden z istniejących testów. To spowoduje ostrożnie Przypomnij do pisania testów jednostkowych podczas wprowadzania poprawki lub dodawanie nowych funkcji.

> [!NOTE]
> Testowanie jednostkowe na żywo jest dostępna dla projektów C# i Visual Basic, przeznaczonych dla platformy .NET Core lub .NET Framework w Enterprise Edition dla programu Visual Studio 2017 r.

Używając Live testów jednostkowych dla testów, Live testów jednostkowych utrzymuje dane o stanie testów. Możliwość użycia danych pozwala na żywo testów jednostkowych oferują lepszą wydajność podczas uruchamiania testów dynamicznie w odpowiedzi na zmiany kodu.
 
## <a name="supported-test-frameworks"></a>Platform obsługiwanych badania
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

Jeśli masz starszą MSTest na podstawie projekty testowe, które odwołują się `Microsoft.VisualStudio.QualityTools.UnitTestFramework` i nie chcesz przejść do nowszej pakietów MSTest NuGet, przeprowadź uaktualnienie do programu Visual Studio 2017 wersji 15.4. 

W niektórych przypadkach może być konieczne jawnie przywracania pakietów NuGet, odwołuje się projektów w rozwiązaniu Aby pracować na żywo testów jednostkowych. Można to zrobić za pomocą jawnego kompilacji rozwiązania (wybierz **kompilacji**, **Kompiluj ponownie rozwiązanie** z menu najwyższego poziomu programu Visual Studio) lub przez Przywracanie pakietów w rozwiązaniu (kliknij prawym przyciskiem myszy rozwiązanie i wybierz **przywracania pakietów NuGet**) przed włączeniem testów jednostkowych życia. 

#   <a name="configuring-live-unit-testing"></a>Konfigurowanie testy jednostkowe na żywo

Testowanie jednostkowe na żywo można skonfigurować, wybierając **narzędzia**, **opcje** z menu najwyższego poziomu programu Visual Studio, a następnie wybierając **Live testów jednostkowych** w okienku po lewej stronie **Opcje** okna dialogowego. Na poniższej ilustracji przedstawiono opcje konfiguracji na żywo testów jednostkowych dostępne w oknie dialogowym.

  ![Obraz](./media/lut-options.png)

Można skonfigurować opcje obejmują:

- Czy na żywo testów jednostkowych wstrzymuje, gdy rozwiązanie jest wbudowana i debugowania
 
- Czy na żywo testów jednostkowych wstrzymuje, gdy system baterii spadnie poniżej określonego progu.
- Czy na żywo testów jednostkowych jest uruchamiany automatycznie po otwarciu rozwiązania.
- Katalog do przechowywania danych.   
   **Usuń dane utrwalone** przycisk umożliwia usunięcie wszystkich istniejących danych. Jest to przydatne, gdy na żywo testów jednostkowych zachowuje się w sposób nieprzewidziany lub nieoczekiwany, które sugeruje utrwalonych danych została uszkodzona.   
- Interwał, po którym przypadkiem testowym upłynie limit czasu; Wartość domyślna to 30 sekund. 
- Maksymalna liczba procesów testów, które tworzy Live testów jednostkowych. 
- Maksymalna ilość pamięci, który przetwarza Live testów jednostkowych, jaką może wykorzystać.
- Poziom informacje zapisane na żywo testów jednostkowych **dane wyjściowe** okna.   
   Dostępne są następujące opcje bez rejestrowania (**Brak**), tylko komunikaty o błędach (**błąd**), o błędach i komunikaty informacyjne (**informacji**, wartość domyślna), lub wszystkie szczegóły (**pełne** ).

Można także wyświetlić pełne dane wyjściowe w Live testów jednostkowych **dane wyjściowe** okna, przypisując wartość "1" do zmiennej na poziomie użytkownika środowiska o nazwie `VS_UTE_DIAGNOSTICS` i uruchomić ponownie program Visual Studio. 

Aby przechwycić szczegółowe komunikaty dziennika program MSBuild z testów jednostkowych na żywo do pliku, należy ustawić `LiveUnitTesting_BuildLog` zmiennej środowiskowej na poziomie użytkownika na nazwę pliku, który zawiera dziennik.

Po włączeniu na żywo testów jednostkowych (zobacz następną sekcję [uruchamianie, wstrzymywanie i zatrzymywania testów jednostkowych Live](#starting-pausing-and-stopping-live-unit-testing), można również otworzyć **opcje** okna dialogowego, wybierając **testu**, **Testy jednostkowe na żywo**, **opcje**.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Uruchamianie, wstrzymywanie i zatrzymywanie na żywo testów jednostkowych

Włącz testowanie jednostkowe na żywo, wybierając **testu**, **Live testów jednostkowych**, **Start** z menu najwyższego poziomu programu Visual Studio. Po włączeniu na żywo testów jednostkowych, opcje dostępne na **Live testów jednostkowych** zmiana menu z pojedynczego elementu **Start**, do **Wstrzymaj**, **zatrzymać**, i **zresetować oczyszczania**.

> [!NOTE]
> Po uruchomieniu testów jednostkowych na żywo w rozwiązaniu nie ma jednostkowy projekt testowy **Wstrzymaj**, **zatrzymać**, i **zresetować czystą** dostępne opcje **Live Testowanie jednostkowe** menu, ale na żywo testów jednostkowych nie można uruchomić. **Dane wyjściowe** okno wyświetla komunikat, który rozpoczyna się "nie kart sieciowych obsługiwanych badania przywoływane przez to rozwiązanie..."  

W dowolnym momencie możesz tymczasowo wstrzymać lub całkowicie zatrzymać Live testów jednostkowych. Można to zrobić, na przykład, jeśli są w trakcie refaktoryzacji i dowiedzieć się, że testy zostanie przerwany przez pewien czas. Dostępne są trzy menu Opcje:

- **Wstrzymaj**, który tymczasowo wstrzymuje Live testów jednostkowych. 
 
    Podczas testów jednostkowych na żywo jest wstrzymana, sieci wizualizacji pokrycia nie jest wyświetlany w edytorze, ale jest zachowane wszystkie dane, które zostały zebrane. Aby wznowić Live testów jednostkowych, wybierz **Kontynuuj** z menu Live testów jednostkowych. Testowanie jednostkowe na żywo wykonuje pracę niezbędne do nadążyć za wszystkie zmiany wprowadzone podczas została wstrzymana i odpowiednio aktualizuje symboli. 

- **Zatrzymaj**, aby całkowicie zatrzymać Live testów jednostkowych. Testowanie jednostkowe na żywo spowoduje odrzucenie wszystkich danych, które on zebrane.

- **Resetuj wyczyść**, co uniemożliwia Live testów jednostkowych, usuwania istniejących danych i ponownego uruchomienia testów jednostkowych na żywo.

- **Opcje**, co spowoduje otwarcie **opcje** okna dialogowego opisanego w [testów jednostkowych Konfigurowanie Live](#configuring-live-unit-testing) sekcji.
 
##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Wyświetlanie wizualizacji pokrycia w edytorze podczas pisania

Raz włączone na żywo testów jednostkowych aktualizacji, które dotyczy każdego wiersza kodu w edytorze programu Visual Studio, aby pokazać, czy kod pisania testów jednostkowych i czy przekazywane testy, które obejmują go.  Na poniższej ilustracji przedstawiono wierszy kodu z przekazywaniem i niepowodzeniem testy, a także wierszy kodu, które nie są objęte testy. Wiersze ozdobione zielony "✓" są objęte przekazując testy, ozdobione czerwony symbol "x" wiersze są objęte jeden lub więcej testów Niepowodzenie i wiersze dekorowane za blue "➖" nie są objęte żadnego testu.

  ![Obraz](./media/lut-codewindow.png)

Na żywo testów jednostkowych wizualizacji pokrycia jest natychmiast zaktualizować podczas modyfikowania kodu w edytorze kodu. Podczas przetwarzania edytowanych wartości, zmiany wizualizacji, aby wskazać, że dane nie są aktualne, dodając round czasomierza obraz poniżej przekazywanie, niepowodzeniem, a nie pasuje do symboli, jak przedstawiono na poniższym rysunku.

  ![Obraz](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>Uzyskiwanie informacji o pomyślnym lub niepomyślnym testów

Najeżdżając symbol Zakończono powodzeniem lub niepowodzeniem w oknie Kod widać, ile testów są naciśnięcie tego wiersza. Po kliknięciu symbol widoczny stan poszczególnych testów, jak przedstawiono na poniższym rysunku:
 
  ![Obraz](./media/lut-failedinfo.png) 

Oprócz nazwy i wyniki testów, umożliwia etykietka narzędzia należy uruchomić ponownie zestaw testów, a także Uruchom zestaw testów za pomocą debugera. W przypadku wybrania jednego lub więcej testów w etykietce narzędzia można również uruchomić lub debugowania tylko te testy. Dzięki temu można debugować testów bez konieczności opuszczania okna kodu. Podczas debugowania, oprócz obserwowania wszystkie punkty przerwania może już ustawiono, wykonanie programu wstrzymuje gdy debuger wykonuje [ `Assert` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) metodę, która zwraca nieoczekiwany wynik. 

Po ustawieniu kursora nie powiodło się testu w etykietce narzędzia rozszerza zapewnienie dodatkowych informacji na temat błędu, jak pokazano na poniższej ilustracji. Dwukrotne kliknięcie na nieudanych testów w etykietce narzędzia, można przejść bezpośrednio do niego.

  ![Obraz](./media/lut-failedmsg.png) 

Po przejściu do testu nie powiodło się na żywo testów jednostkowych również wizualnie wskazuje w podpisie metody testów, które zostały pomyślnie sprawdzone (wskazane zlewce połówkowej pełnej wraz z zielony "✓"), nie powiodło się (zlewce połówkowej pełnej wraz z czerwonym znakiem "🞩"), lub nie zaangażowane w Live testów jednostkowych (zlewce połówkowej pełnej wraz z blue "➖"). Metody inne niż testu nie są oznaczone przy użyciu symbolu. Na poniższym rysunku przedstawiono cztery rodzaje metod.
 
  ![Obraz](media/lut-testsource.png)
 
## <a name="diagnosing-and-correcting-test-failures"></a>Diagnozowanie i poprawiania błędów testu

Z testu nie powiodło się można łatwo debugować kod produktu, wprowadź zmiany i kontynuować tworzenie aplikacji. Testowanie jednostkowe na żywo jest uruchamiana w tle, nie trzeba zatrzymać i ponownie uruchomić testów jednostkowych na żywo podczas debugowania, edytowania i kontynuowania cyklu.

Na przykład niepowodzenia testu na poprzedniej ilustracji spowodowane przez niepoprawny założeń w metodzie testowej, która zwraca znaki inne niż alfanumeryczne `true` przekazany do <xref:System.Char.IsLower%2A?displayProperty=fullName> metody. Gdy firma Microsoft rozwiąże metody testowej, uważamy, że wszystkie testy zostały zaliczone pomyślnie. Gdy robimy, nie mamy wstrzymać lub zatrzymać Live testów jednostkowych.

## <a name="live-unit-testing-and-test-explorer"></a>Testy jednostkowe na żywo i Eksploratora testów

Zwykle **Eksploratora testów** udostępnia interfejs, który pozwala uruchamiać, debugować i Analizuj wyniki testów. Testowanie jednostkowe na żywo integruje się z **Eksploratora testów**. Podczas testów jednostkowych na żywo jest wyłączona lub została zatrzymana, **Eksploratora testów** wyświetlany jest stan testów jednostkowych czas ostatniego uruchomienia testu. Zmiany kodu źródłowego wymagają, ponownie uruchom testy. Z kolei po włączeniu na żywo testów jednostkowych testów stan jednostki w **Eksploratora testów** natychmiast zaktualizować. Nie trzeba jawnie Uruchom testy jednostkowe. 

> [!NOTE]
> Możesz otworzyć **Eksploratora testów** wybierając **testu**, **Windows**, **Eksploratora testów** z menu najwyższego poziomu programu Visual Studio.  

Można zauważyć w **Eksploratora testów** oknie, w którym są wygasić niektórych testów. Na przykład po włączeniu na żywo testów jednostkowych po otwarciu projektu wcześniej zapisany, **Eksploratora testów** okno ma pojawił się wszystkie, oprócz testu nie powiodło się, jak przedstawiono na poniższym rysunku. W takim przypadku Live testów jednostkowych ma ponownie uruchom testu nie powiodło się, ale nie została uruchomiona ponownie testów powiodło się, ponieważ na żywo testów jednostkowych firmy utrwalone danych wskazuje, że nie wprowadzono żadnych zmian, ponieważ testy zostały ostatnio uruchomione pomyślnie.

  ![Obraz](media/lut-test-explorer.png)

Możesz ponownie uruchomić dowolne testy, które pojawiają się pojawił się po wybraniu **Uruchom wszystkie** lub **Uruchom** opcje z **Eksploratora testów** menu lub po wybraniu co najmniej jednego testu w **Eksploratora testów** menu, prawym przyciskiem myszy i wybierając **Uruchom wybrane testy** lub **Debuguj zaznaczone testy** w menu podręcznym. Ponieważ testy są uruchamiane, bąbelkowy zapasowej górnej.

Istnieją pewne różnice między Live testów jednostkowych automatyczne uruchamianie i aktualizowanie wyników testów oraz jawnie Uruchamianie testów z **Eksploratora testów**. Różnice te obejmują:

- Uruchomiona lub debugowanie testów z okna narzędzia Eksplorator testów uruchamia regularne plików binarnych, natomiast na żywo testów jednostkowych uruchamia instrumentowanych danych binarnych. 
- Testowanie jednostkowe na żywo nie powoduje utworzenia nowej domeny aplikacji do uruchamiania testów, ale raczej uruchamia testy z domeny domyślnej. Uruchom testy z **Eksploratora testów** okna tworzenia nowej domeny aplikacji.
- Testowanie jednostkowe na żywo uruchamia testy w każdym zestawu testowego sekwencyjnie. Po uruchomieniu wielu testów z **Eksploratora testów** okna i **Uruchom testy równolegle** przycisk jest zaznaczony, testy uruchamiane równolegle.

## <a name="live-unit-testing-and-large-solutions"></a>Testowanie jednostkowe na żywo i dużych rozwiązaniach

Rozwiązania jest 10 lub więcej projektów, podczas uruchamiania testów jednostkowych na żywo i nie ma żadnych danych lub w przypadku wybrania **testu**, **Live testów jednostkowych**, **zresetować czystą** Opcja menu najwyższego poziomu programu Visual Studio, Visual Studio wyświetla to okno dialogowe do ostrzega o tym, że dynamiczne wykonywania dużej liczby testów w dużych projektów może poważnie obniżyć wydajność. W przypadku wybrania **OK**, Live testów jednostkowych wykonuje wszystkie teksty w rozwiązaniu. W przypadku wybrania **anulować**, możesz wybrać testów do wykonania. Aby uzyskać informacje, jak to zrobić, zobacz następującą sekcję [Włączanie i wyłączanie projekty testowe i metod testowych](#including-and-excluding-test-projects-and-test-methods).  

 ![Na żywo dialogowego dużych projektów testów jednostkowych](media/lut-large-project.png)

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Włączanie i wyłączanie projekty testowe i metody testów

Rozwiązania z wielu projektów testu można kontrolować, co projektów i jakie poszczególnych metod w projekcie brać udziału w Live testów jednostkowych. Na przykład jeśli rozwiązanie z setkami projekty testowe, można wybrać docelowego zestawu projekty testowe do udziału w Live testów jednostkowych. Istnieje wiele sposobów, aby to zrobić, w zależności od tego, czy chcesz wykluczyć wszystkie testy w projekt lub rozwiązanie, czy chcesz dołączyć lub wykluczyć większości testów, lub czy chcesz wykluczyć testy indywidualnie. Testowanie jednostkowe na żywo zapisuje stan dołączania/wykluczania jako ustawienia użytkownika i są przechowywane dane po zamknięciu i otworzyć ponownie rozwiązanie. 

**Z wyjątkiem wszystkie testy w projekt lub rozwiązanie**

Po uruchomieniu testów jednostkowych na żywo, aby wybrać poszczególnych projektów testów jednostkowych, wykonaj następujące czynności:

1.  Rozwiązania w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy i wybierz polecenie **testy na żywo**, **wykluczyć** do wykluczenia całego rozwiązania.
1.  Kliknij prawym przyciskiem myszy każdy projekt testowy, który ma zostać objęte testami, a następnie wybierz pozycję **testy na żywo**, **Include**.

**Wykluczanie pojedynczych testów z okna edytora kodu**

Okna edytora kodu służy do dołączania lub wykluczania poszczególne metody. Kliknij prawym przyciskiem myszy na podpis metody testowej w oknie edytora kodu, a następnie wybierz **testy na żywo**, **obejmują [wybranej metody]**, **testy na żywo**,  **Wyklucz [wybranej metody]**, lub **testy na żywo**, **wykluczyć wszystkie elementy oprócz [wybranej metody]**, gdzie "wybranej metody" jest nazwą metody wybranych w kodzie okno. 

**Z wyjątkiem testy programowo** 

Możesz zastosować <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atrybutu programowo wykluczone z raportowania ich pokrycia w Live testów jednostkowych metody, klasy lub struktury.

Aby wykluczyć poszczególnych metod z testów jednostkowych na żywo umożliwia także następujące atrybuty:

- Dla xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Dla NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Dla przełącznika MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]` 
 
## <a name="see-also"></a>Zobacz także

[Narzędzia do testowania kodu](https://www.visualstudio.com/vs/testing-tools/)   
[Blog testy jednostkowe na żywo](https://go.microsoft.com/fwlink/?linkid=842514)   
[Często zadawane pytania dotyczące testowania jednostek na żywo](live-unit-testing-faq.md)    
[Wideo Channel 9: Testowania w programie Visual Studio 2017 jednostek na żywo](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)

